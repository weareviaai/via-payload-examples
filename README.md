# VIA AI Payload Examples


This repo contains the following VIA payload samples:

1. **Flights**: When searching for flights only, the payload describes a list of categorized flight search results and their respective attributes
2. **Hotels**: When searching for hotels only, the payload describes a list of categorized hotels search results and their respective attributes
3. **Packages**: Dynamic ackages are bundles between flight and hotel products that are offered together. Packages can be dynamic (e.g. any hotel offered with any flight) or static (flights offered with specific hotels) as indicated the relationship _vacation_id_
4. **Itinerary**: At the end of a successful user concersation, the VIA concierge generates an itinerary object representing all the selection the user has made for the travel plan. 
5. **Aggregated User Profile (AUP)**: The aggregated user profile represents all the information that VIA has learned about a particular user up to the current point of time. This is based on multiple conversations conducted with the user.  

> Note: Payload currently supports only flights and hotels
