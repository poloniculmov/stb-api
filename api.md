# STB API Documentation

## Lines API

Lists all available lines.

####Endpoint
`https://info.stbsa.ro/rp/api/lines`
####Options
Accepts `lang` query parameter, possible values are `ro` and `en`.

####Response

Api responds with a JSON object with two attributes `lines` and `ticket_info`. `lines` is a an array that contains 
multiple line objects.  

       {
         "id": 184,
         "name": "336",
         "type": "BUS",
         "color": "#0070c0",
         "has_notifications": false,
         "price_ticket_sms": "0.30 EUR + TVA",
         "ticket_sms": "U336",
         "organization": {
           "id": 1,
           "logo": "https://info.stbsa.ro/src/img/avl/stbsa/logos/logo.png"
         }
       },

`ticket_info` is an object that lists ticket information. It currently only contains day ticketes.

    {
        "tickets": [
          {
            "sms": "ZI",
            "description": "Valabil pe toate liniile urbane",
            "name": "Abonament de o zi",
            "price": "1.50 EUR + TVA"
          }
        ],
        "sms_number": "7458",
        "disclaimer": "Pentru control este obligatoriu să prezentați mesajul SMS de confirmare a plății biletului, care specifică codul biletului emis, linia și perioada de valabilitate. Pentru abonați, tariful este exprimat în lei pe factura de servicii la cursul stabilit de operatorii de telefonie. Pentru cartele reîncărcabile valoarea fără TVA a tarifului este scăzută din creditul disponibil. Tarif SMS trimis la 7458: 0.05 EUR+TVA în Orange și Telekom; gratuit în Vodafone și Digi.  Regulament de utilizare: www.stbsa.ro | Suport clienți: 021 311 1398 | E-mail: info@stbsa.ro"
      }
      
## Line details API

###Endpoint
`https://info.stbsa.ro/rp/api/lines/:id`      

###Options
`:id` is the id of the line, as returned by the Lines API, not the number of the line. 

Accepts `lang` query parameter, possible values are `ro` and `en`.

####Response

Api responds with a JSON object.

    {
        "id": 115,
        "name": "336",
        "type": "BUS",
        "color": "#0070c0",
        "stops": [],
        "has_notifications": false,
        "price_ticket_sms": null,
        "ticket_sms": null,
        "organization": {
            "id": 1,
            "logo": "https://info.stbsa.ro/src/img/avl/stbsa/logos/logo.png"
        },
        "segment_path": "wifnGm~w}CdBjBNe@VTZXz@r@x@t@v@p@HFrAfA~BhBx@n@xAhAd@\fAARI\?@yDK}Q?eBCmBQ}]IcK?cJIqKCqLGkIGaNHuCAqJEqCIkU?oNO}QE_WKcYE{CAiCEiOA_IKm@eAkEs@_DQmAOgDIgASoAYoA{EeMwBuHaAcEc@aBa@kAKe@@_@f@gAhA}CzBqFzEwKrCeJl@oBdC_JIc@e@c@GQBeDEaFUmf@DONUJ[@o@Mo@CMGOUS?a@K}b@QgVUoDo@gHo@gGIiDw@_CiAqKOiBAy@@o@G_A[c@OCOHIR@b@Hp@f@|AbAnJXpDJzBDRNRLb@PvA^`EvAjMRp[Tr`@Az@EZ?b@JjA?`AHtNAzALbTFvB@~BGhAc@|AUp@If@FRLTTVNRHTF^@f@BzCPt^JpMHjLeGL{GZDl@n@xBl@tA~AdEZn@ZfAR|@VvANbDL|AtBrJBxJ@zFBjDBfKFvEHv[PtW@vIBvDJjFB|TD`GGtK@zBBzG?r@@zD@nC@hEC`@FrSFxFA~BBbJJjHPl\FhNEpCDtAIb@i@?WEUYaFaEsAcA_LoJQJCH@RFT",
        "direction_name_tur": "Piata Rosetti",
        "direction_name_retur": "Complex Comercial Apusului"
    }     

`stops` is an array that describes all the stops for the line.

    {
        "id": 7395,
        "lat": 44.438204,
        "lng": 26.014633,
        "name": "Complex Comercial Apusului",
        "description": "Str. Apusului, Bucuresti"
    }
    
## Line Direction API

### Endpoint
`https://info.stbsa.ro/rp/api/lines/:line_id/direction/:direction_id`

### Options
`:line_id` is the id of the line, as returned by the Lines API. `:direction_id` is either `0` or `1`, representing `direction_name_tur` and `direction_name_retur`.       

Accepts `lang` query parameter, possible values are `ro` and `en`.

### Response

Api responds with a JSON object.

    {
        "id": 115,
        "name": "336",
        "type": "BUS",
        "color": "#0070c0",
        "stops": [],
        "has_notifications": false,
        "price_ticket_sms": null,
        "ticket_sms": null,
        "organization": {
            "id": 1,
            "logo": "https://info.stbsa.ro/src/img/avl/stbsa/logos/logo.png"
        },
        "segment_path": "wifnGm~w}CdBjBNe@VTZXz@r@x@t@v@p@HFrAfA~BhBx@n@xAhAd@\fAARI\?@yDK}Q?eBCmBQ}]IcK?cJIqKCqLGkIGaNHuCAqJEqCIkU?oNO}QE_WKcYE{CAiCEiOA_IKm@eAkEs@_DQmAOgDIgASoAYoA{EeMwBuHaAcEc@aBa@kAKe@@_@f@gAhA}CzBqFzEwKrCeJl@oBdC_JIc@e@c@GQBeDEaFUmf@DONUJ[@o@Mo@CMGOUS?a@K}b@QgVUoDo@gHo@gGIiDw@_CiAqKOiBAy@@o@G_A[c@OCOHIR@b@Hp@f@|AbAnJXpDJzBDRNRLb@PvA^`EvAjMRp[Tr`@Az@EZ?b@JjA?`AHtNAzALbTFvB@~BGhAc@|AUp@If@FRLTTVNRHTF^@f@BzCPt^JpMHjLeGL{GZDl@n@xBl@tA~AdEZn@ZfAR|@VvANbDL|AtBrJBxJ@zFBjDBfKFvEHv[PtW@vIBvDJjFB|TD`GGtK@zBBzG?r@@zD@nC@hEC`@FrSFxFA~BBbJJjHPl\FhNEpCDtAIb@i@?WEUYaFaEsAcA_LoJQJCH@RFT",
        "direction_name_tur": "Piata Rosetti",
        "direction_name_retur": "Complex Comercial Apusului"
    }     

`stops` is an array that describes all the stops, in order, for the selected direction.

    {
        "id": 7395,
        "lat": 44.438204,
        "lng": 26.014633,
        "name": "Complex Comercial Apusului",
        "description": "Str. Apusului, Bucuresti"
    }

##Line Vehicles API

Returns a list of all the vehicles going in the selected direction, with their GPS coordonates.

### Endpoint
`https://info.stbsa.ro/rp/api/lines/:line_id/vehicles/:direction_id`
 
### Options
 `:line_id` is the id of the line, as returned by the Lines API. `:direction_id` is either `0` or `1`, representing `direction_name_tur` and `direction_name_retur`.       
 
 Accepts `lang` query parameter, possible values are `ro` and `en`.

### Response

API responds with an array of vehicles.

    [     
       {
           id: 2054,
           lat: 44.451049,
           lng: 26.088817,
           code: "6572",
           transport_type: "BUS"
       },
    ]
    
## Stop Details API

Returns all the lines that stop at a certain stop

### Endpoint
`https://info.stbsa.ro/rp/api/lines/stops/:stop_id`

### Options
`:stop_id` is the id of the stop. 

Accepts `lang` query parameter, possible values are `ro` and `en`.
    
### Response     

Response is an object with details about the stop and an array of `lines`.

    {
        lines: [],
        name: "Gara de Nord",
        description: "Bd. Dinicu Golescu, Bucuresti",
        transport_type: "TRAM"
    } 
    
    {
        ...
        lines: [
            {
                id: 216,
                name: "133",
                type: "BUS",
                color: "#0070c0",
                description: "Bd. Dinicu Golescu, Bucuresti",
                direction: 1,
                direction_name: "Gara Basarab",
                arriving_time: 60,
                arriving_times: null,
                is_timetable: false,
                timetable: null,
                organization: {
                id: 1,
                logo: "https://info.stbsa.ro/src/img/avl/stbsa/logos/logo.png"
                }
            }
        ] 
    }
    
`arriving_time` seems to be a real ETA in seconds, rounded up to a minute, if `is_timetable` is false. 

## Places API

Allows you to search for a place. 

### Endpoint
`https://info.stbsa.ro/rp/api/places`

### Options
Accepts `query` query parameter, the API uses it to search for the name of a place.

Accepts `lang` query parameter, possible values are `ro` and `en`.

### Response

An object with a `places` property.

    places: [
        {
            name: "CRC Dr Gazarului",
            lat: 44.38647,
            lng: 26.092342,
            type: "TICKET_OFFICE",
            stop_id: 9080
        },
    ]


## Stops List API

Returns a list of stops in a rectangle defined by two `lat`, `lng` pairs.

### Endpoint

`https://info.stbsa.ro/rp/api/lines/home/stops/:lat_start/:lng_start/:lat_end/:lng_end`

### Options

Accepts `lang` query parameter, possible values are `ro` and `en`.

### Response
API responds with an array of stops.

    [
        {
            id: 3840,
            lat: 44.438666,
            lng: 26.140625,
            name: "Lt. Victor Manu",
            type: "STATION"
        },
    ]       