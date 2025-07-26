# VIA AI Public Interfaces

## VIA Payload Examples 

This repo contains the following VIA payload samples:

1. **Flights**: When searching for flights only, the payload describes a list of categorized flight search results and their respective attributes
2. **Hotels**: When searching for hotels only, the payload describes a list of categorized hotels search results and their respective attributes
3. **Packages**: Dynamic packages are bundles between flight and hotel products that are offered together. Packages can be dynamic (e.g. any hotel offered with any flight) or static (flights offered with specific hotels) as indicated the relationship _vacation_id_
4. **Itinerary**: At the end of a successful user conversation, the VIA concierge generates an itinerary object representing all the selection the user has made for the travel plan. 
5. **Aggregated User Profile (AUP)**: The aggregated user profile represents all the information that VIA has learned about a particular user up to the current point of time. This is based on multiple conversations conducted with the user.  

> Note: Payload currently supports only flights and hotels

## Receiving VIA Platform Events using Webhooks

To receive VIA platform responses you will need to install a webhook via the VIA Console (see below). 
VIA will call your webhook with the following payload:

```json
{
  "timstamp": "<TIMESTAMP IN ISO FORMAT>",
  "project_id": "<PROJECT ID>",
  "event_id": "<EVENT_ID>", 
  "event_payload": {
    // Event specific payload
  }
}
```


## Setting up a Webhook

From the VIA Console, define a new webhook to receive reply messages. **You must enable and verify the webhook in order to activate it**.
VIA will attempt to call your webhook up to 5 tries using the following strategy:
```
(Next Attempt Timestamp) = (First Attempt Timestamp) + (Retry Attempt) * 5000 mSec 
```

### Authenticating Your Webhook

VIA implements a security mechanism for webhook authentication by employing a digital signature. This signature is crafted using a secret key provided during the webhook setup alongside the request body. The resulting data is encapsulated in the signature header property. The process to calculate the signature is as follows:

```HMAC-SHA256 = {Base64(HmacSHA256(body_bytes, YOUR_WEBHOOK_SECRET))}```

To verify the request came from VIA, compute an HMAC digest using your secret key and the body and compare it to the signature portion (after the space) contained in the header. If they match, you can be sure the webhook was sent from VIA. Otherwise, ensure your code returns an unspecific error immediately without invoking additional logic.

This signature header property contains the SHA algorithm used to generate the signature, a space, and the signature itself. 

```signature: sha256 HMAC-SHA256```

e.g. signature: sha256 37d2725109df92747ffcee59833a1d1262d74b9703fa1234c789407218b4a4ef

**You must verify your webhook from the VIA Console so that it will be called.** 

### Samplle VIA Webhook Receiver

Use the VIA Console to obtain your unique webhook secret. 

### node.js

```javascript
var express = require('express')
const crypto = require('crypto');
var app = express()

// Set your runtime variables
let secret = '<YOUR WEBHOOK SECRET>';
let port = 8080;

// Signature verification
const verifyHmac = (
    receivedHmacHeader,
    receivedBody,
    secret
) => {
    const hmacParts = receivedHmacHeader.split(' ')
    const receivedHmac = hmacParts[1]
    const hash = crypto
        .createHmac(hmacParts[0], secret)
        .update(receivedBody)
        .digest('hex')
    return receivedHmac == hash
}

app.use(express.raw({ type: "*/*" }))

// Main webhook entry point
app.post('/webhook', function (req, res) {

    // Some initial basic verification
    if (!req.headers.signature) {
        console.log('Signature doesn\'t exist');
        return res.sendStatus(500);
    }
    else {
        console.log('Signature: ' + req.headers.signature);
    }

    // Verify source from signature
    if (!verifyHmac(req.headers.signature, req.body, secret)) {
        console.log('Signature verification failed');
        return res.sendStatus(500);
    }

    console.log("Signature verified");

    // Extract payload
    let payload = JSON.parse(req.body);
    console.log(JSON.stringify(payload, null, 4));

    // Parse the actual payload here
    // TODO

    res.send('Ok')
})

console.log(`Listening for events on ` + port)
app.listen(port);
```

### Python

```python
from flask import Flask
from flask import request
import hashlib, hmac, json

app = Flask(__name__)

# Set your runtime variables
secret = '<YOUR WEBHOOK SECRET>'
port = 8080

# Signature verification
def verifyHmac(received_hmac_header, received_body, secret):
    hmac_parts = received_hmac_header.split(' ')
    received_hmac = hmac_parts[1]
    hash = hmac.new(bytes(secret, 'UTF-8'), received_body, hashlib.sha256).hexdigest()
    return received_hmac == hash

# Main webhook entry point
@app.route('/webhook', methods=['POST'])
def webhook():
    # Some initial basic verification
    if 'signature' not in request.headers:
        print("Signature doesn't exist")
        return '', 500
    else:
        print('Signature:', request.headers['signature'])

    # Verify source from signature
    if not verifyHmac(request.headers['signature'], request.data, secret):
        print('Signature verification failed')
        return '', 500

    print('Signature verified')

    # Extract payload
    payload = request.get_json()
    print(json.dumps(payload, indent=4))

    # Parse the actual payload here
    # TODO

    return 'Ok'

if __name__ == '__main__':
    print('Listening for events on ' + str(port))
    app.run(port=port)
```
