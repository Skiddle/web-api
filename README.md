# web-api
## Skiddle events Web API

Events search endpoint: **http://www.skiddle.com/api/v1/events/** (method: GET) Gets multiple events based upon search parameters (see below).

Event details endpoint: **http://www.skiddle.com/api/v1/events/12345/** (method: GET) Gets information for a single event.


## event search parameters

### Geographical:

**latitude:** (decimal, optional) Specify a latitude to find nearby events (eg 53.000)

**longitude:** (decimal, optional) Specify a longitude to find nearby events (eg -1.234)

**radius:** (integer, optional) Find events within the specified miles radius (eg 10)

**country:** (string, optional) Find events within a certain country, using a specific country code (eg GB)

**getdistance:** (bool, optional) Return the distance from your specified location _(for this parameter to work, you must also provide a latitude and a longitude)_

**_To use geo searching, all 3 of the above parameters must be specified._**


### Event filters:

**eventcode:** (string, optional) Filter by type of event. Note the category is selected by the event promoter when submitting the event so can be subjective! Choose from:

- FEST = Festivals
- LIVE = Live music
- CLUB = Clubbing/Dance music
- DATE = Dating event
- THEATRE = Theatre/Dance
- COMEDY = Comedy
- EXHIB = Exhibitions and Attractions
- KIDS = Kids/Family Event
- BARPUB = Bar/Pub event
- LGB = Gay/Lesbian event
- SPORT = Sporting event
- ARTS = The Arts


**ticketsavailable:** (bool, optional) Find only events with tickets available to purchase

**specialFeatured:** (bool, optional) Find events which are recommended by Skiddle

**imagefilter:** (bool, optional) Find only events which have an image attached

**minDate:** (string, optional) Find events on or after this date. Format as YYYY-MM-DD

**maxDate:** (string, optional) Find events before or on this date. Format as YYYY-MM-DD

**venueid:** (integer, optional) Find events at a particular venue. See the venues search for details (as an integer)

**b:** (integer, optional) Find events attached to a particular brandID (eg Ministry of Sound). See the brands search for details

**a:** (integer, optional) Find events that a particular artistID is tagged to (eg Riva Starr). See the artsits search for details


**order:** (string, optional) Specify sort order. Chose from:

- random = returns the events in a random order
- trending = will return the events in trending order for the preceeding week
- goingto = will order the events by the amount of people attending
- distance = will return the events from closest to furthest from your specified location _(for this parameter to work, you must also provide a latitude and a longitude)_


**limit:** (integer, optional) Specify number of records returned (max 100, default 20)

**offset:** (integer, optional) Specify record number to start at (for paging, in conjunction with limit, order) (default 0)
