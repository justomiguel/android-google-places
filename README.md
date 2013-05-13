# Android Wrapper for Google Places API

This library allows you to integrate the capabilities of google places in your App.
It uses the API provided by google for client to make an http request and parses the JSON to java objects easy to use (I hope).
You can also extend the base classes that represent queries, and and that that provide results to add functionality and customized information.

## Features

- Nearby  Search Request
- Text Search Request
- Place Details request
- Customized Request (based on previous)
- Support for all fields of the results of json google places.
- Integration and use of <a href="https://code.google.com/p/google-api-java-client/">Google APIs Client Library for Java</a>
- Use of Generics Java

## Todo

Any kind of help is welcome.

- Make better documentation :)
- Public javadoc
- Test Code 
- Radar Search
- Place Photo
- Place Actions
- Place Autocomplete
- Query Autocomplete
- Remove libs directory from repository
- Demo app for try this library (is already made but is not ready for you)

## Setup

1. Obtain an API key (Browser).  Visit the <a href="https://developers.google.com/places/documentation/">developer's guide</a> for more information.
2. Drop the googleplaces.jar in the lib folder of your Android project.
3. If necessary download or update the <a href="https://code.google.com/p/google-api-java-client/">google-api-java-client</a> ant put in yout libs directory all needed jar.

# Base Usage

You first need to instantiate the base class library passing your Api Key.

    GooglePlaces gp = new GooglePlaces(getResources().getString("YOUR API KEY");

So you have some of methods(for now) to make the request:

> - getNearbyPlaces(List<String>, String, int, double, double)
> - getNearbyPlaces(List<String>, int, double, double)
> - getNearbyPlaces(String, String, int, double, double)
> - getNearbyPlaces(double, double)
> - getNearbyPlaces(int, double, double)
> - getNearbyPlaces(int, double, double, boolean)
> - getTextPlaces(String text, boolean sensor )
> - getTextPlaces(String text)
> - getPlaceDetails(String reference)
> - getPlaceDetails(Query query)
> - getPlaces(Query query)
> - getPlaces(Query query, Class<? extends Result> resultClass)
    
Each of these methods return a Class that implements the Result Interface.<br>
For places will be the class PlaceResult and for the details will be the class PlaceDetails.<br>
Waiting for the javadoc, you can see directly into sources such parameters(all) are set by default in classes that extend  the base class: Query.<br>
You can access at all the optional parameters of the  API Google Places queries, and in the result are present all the fields provided by response.<br>
Below you will see how to create a personalized result.

### Text Search

Some Examples:

Base:

    PlacesResult result = gp.getTextPlaces("restaurant");
    
With Sensor Disabeld:

    PlacesResult result = gp.getTextPlaces("restaurant",false);
    
With Custom Location:

    TextSearchQuery query = new TextSearchQuery(getResources().getString(R.string.browser_api_key), textToSearch, true);
    query.setLocation(37.513692, 15.090934); 
    PlacesResult result = gp.getPlaces(query);

### Nearby Search

## Handling a place search response

    if (result.getStatusCode() == StatusCode.OK) {
        List<Place> placesList = result.getResults();
        foreach(Place place : placesList){
            //do something, for example add marker on the map
            mapFragment.getMap()
                .addMarker(new MarkerOptions()
                    .position(new LatLng(place.getLatitude(), place.getLongitude()))
                    .title(place.getName())
                    .snippet(place.getFormattedAddress())
					.icon(BitmapDescriptorFactory.defaultMarker(BitmapDescriptorFactory.HUE_CYAN)));
        }
    }

## Place Details

Coming very soon...

### Handling a place details response

Coming very soon...

# Advanced Usage

Coming very soon...

## Custom Query

Coming very soon...

## Custom Result

Coming very soon...

# Contributing

Fork, push, and send a pull request. Enjoy!

Please Visit <a href="a2plab.com">a2plab.com</a>
