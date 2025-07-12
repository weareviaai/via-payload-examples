```json
{
  "flights": {
    "cheapest_flight": {
      "total_price_all_travelers": 376.58,
      "currency": "GBP",
      "passenger_data": [
        {
          "passenger_type": "Adult",
          "number_of_passengers": 2,
          "included_baggage": [
            {
              "type": "CheckedBaggage",
              "descriptions": [
                "BAG MAX 23KG 51LB  208LCM 81LI",
                "MUSICAL INSTRUMENT 23KG 51LB",
                "MEDIA EQUIPMENT 23KG 51LB",
                "BICYCLE"
              ],
              "number_of_pieces": 1,
              "max_weight_kg": null
            },
            {
              "type": "CheckedBaggage",
              "descriptions": [
                "BAG MAX 23KG 51LB  208LCM 81LI",
                "MUSICAL INSTRUMENT 23KG 51LB",
                "MEDIA EQUIPMENT 23KG 51LB",
                "BICYCLE"
              ],
              "number_of_pieces": 1,
              "max_weight_kg": null
            }
          ]
        }
      ],
      "outbound_flight": {
        "duration_minutes": 170,
        "flight_legs": [
          {
            "departure_airport": "LHR",
            "departure_date_time": "2025-09-03T06:35:00",
            "arrival_airport": "AGP",
            "arrival_date_time": "2025-09-03T10:25:00",
            "flight_number": 412,
            "carrier": "BA",
            "duration_minutes": 170,
            "flight_class": "Economic O"
          }
        ]
      },
      "return_flight": {
        "duration_minutes": 180,
        "flight_legs": [
          {
            "departure_airport": "AGP",
            "departure_date_time": "2025-09-08T07:20:00",
            "arrival_airport": "LGW",
            "arrival_date_time": "2025-09-08T09:20:00",
            "flight_number": 8096,
            "carrier": "VY",
            "duration_minutes": 180,
            "flight_class": "Economic O"
          }
        ]
      },
      "matched_preferences_count": 1,
      "matched_preferences": [
        "arrival time: to 20:00"
      ],
      "unmatched_preferences": [
        "departure time: from 8:00"
      ],
      "number_of_connections": 0,
      "duration_at_destination": "116 hours",
      "flight_route_map": "https://maps.googleapis.com/maps/api/staticmap?...",
      "category_display_name": "Cheapest Flight"
    },
    "longest_stay_in_destination_flight": {
      "total_price_all_travelers": 584.11,
      "currency": "GBP",
      "passenger_data": [
        {
          "passenger_type": "Adult",
          "number_of_passengers": 2,
          "included_baggage": [
            {
              "type": "CheckedBaggage",
              "descriptions": [
                "BAG UP TO 23 KG AND 158 LCM"
              ],
              "number_of_pieces": 1,
              "max_weight_kg": null
            },
            {
              "type": "CheckedBaggage",
              "descriptions": [
                "BAG MAX 23KG 51LB  208LCM 81LI",
                "MUSICAL INSTRUMENT 23KG 51LB",
                "MEDIA EQUIPMENT 23KG 51LB",
                "BICYCLE"
              ],
              "number_of_pieces": 1,
              "max_weight_kg": null
            }
          ]
        }
      ],
      "outbound_flight": {
        "duration_minutes": 180,
        "flight_legs": [
          {
            "departure_airport": "LGW",
            "departure_date_time": "2025-09-03T09:40:00",
            "arrival_airport": "AGP",
            "arrival_date_time": "2025-09-03T13:40:00",
            "flight_number": 5945,
            "carrier": "VY",
            "duration_minutes": 180,
            "flight_class": "Economic S"
          }
        ]
      },
      "return_flight": {
        "duration_minutes": 175,
        "flight_legs": [
          {
            "departure_airport": "AGP",
            "departure_date_time": "2025-09-08T21:50:00",
            "arrival_airport": "LGW",
            "arrival_date_time": "2025-09-08T23:45:00",
            "flight_number": 2645,
            "carrier": "A0",
            "duration_minutes": 175,
            "flight_class": "Economic N"
          }
        ]
      },
      "matched_preferences_count": 1,
      "matched_preferences": [
        "departure time: from 8:00"
      ],
      "unmatched_preferences": [
        "arrival time: to 20:00"
      ],
      "number_of_connections": 0,
      "duration_at_destination": "128 hours",
      "flight_route_map": "https://maps.googleapis.com/maps/api/staticmap?...",
      "category_display_name": "Longest Stay In Destination Flight"
    },
    "best_travel_time_flight": {
      "total_price_all_travelers": 515.31,
      "currency": "GBP",
      "passenger_data": [
        {
          "passenger_type": "Adult",
          "number_of_passengers": 2,
          "included_baggage": [
            {
              "type": "CheckedBaggage",
              "descriptions": null,
              "number_of_pieces": 1,
              "max_weight_kg": 25
            },
            {
              "type": "CheckedBaggage",
              "descriptions": null,
              "number_of_pieces": 1,
              "max_weight_kg": 25
            }
          ]
        }
      ],
      "outbound_flight": {
        "duration_minutes": 180,
        "flight_legs": [
          {
            "departure_airport": "LGW",
            "departure_date_time": "2025-09-03T09:40:00",
            "arrival_airport": "AGP",
            "arrival_date_time": "2025-09-03T13:40:00",
            "flight_number": 6615,
            "carrier": "VY",
            "duration_minutes": 180,
            "flight_class": "Economic Z"
          }
        ]
      },
      "return_flight": {
        "duration_minutes": 175,
        "flight_legs": [
          {
            "departure_airport": "AGP",
            "departure_date_time": "2025-09-08T13:45:00",
            "arrival_airport": "LGW",
            "arrival_date_time": "2025-09-08T15:40:00",
            "flight_number": 6618,
            "carrier": "VY",
            "duration_minutes": 175,
            "flight_class": "Economic N"
          }
        ]
      },
      "matched_preferences_count": 2,
      "matched_preferences": [
        "departure time: from 8:00",
        "arrival time: to 20:00"
      ],
      "number_of_connections": 0,
      "duration_at_destination": "120 hours",
      "flight_route_map": "https://maps.googleapis.com/maps/api/staticmap?...",
      "category_display_name": "Best Travel Time Flight"
    }
  }
}
```
