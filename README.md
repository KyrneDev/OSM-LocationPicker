## JQuery Location Picker plugin

This plugin allows to find and select location on [OpenStreetMap](https://www.openstreetmap.org) map using [Google geoode API](https://developers.google.com/maps) for address autocomplete and reverse geocoding.

Supports address autocomplete search and location select on map click.

Address autocomplete is using [Google Maps Api](https://developers.google.com/maps),
Maps displayed via [OpenLayers](http://openlayers.org)
 
Plugin saves location information in inputs and provides same data via callbacks.

![jquery-location-picker-demo](https://cloud.githubusercontent.com/assets/5731758/9176822/33649d4a-3f96-11e5-9235-3ade01b3d7c1.jpg)

 #jquery #location-picker, #maps, #autocomplete, #geocode, #OpenStreetMap, #OSM, #OpenLayers

## Features

* Location Search by address
* Address autocomplete
* Location pick on map click
* Reverse address geocode from location
* Initialize location picker with: 
  * current location
  * custom address 
  * custom location(latitude,longitude)
* Save location data in inputs or use in js callbacks
* Specify custom map and inputs elements

## Code Example & Minimal setup

See Sample.html demo for configuration and usage

Include required scripts:
```html
<script src='https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js'></script>
<script src='http://www.openlayers.org/api/OpenLayers.js'></script>
<script src='https://maps.googleapis.com/maps/api/js?v=3.exp&libraries=places'></script>
```
then add location picker plugin reference:
```html
<script src='js/location-picker.js'></script>
```

Example markup:
```html
<style>
  	#map { height: 400px; width:100%;}
  	.map-container { margin-top: 10px;}
</style>

    
<div class='location-picker'>
	<input type='text' id='txtAddress' class='form-control' placeholder='Enter your address here' data-type='address' />
	<input type='hidden' id='txtLocation' data-type='location-store' />

	<div class='map-container'>
		<div id='map' data-type='map'></div>
	</div>
</div>
```

Usage:
```html
<script>
$(function(){
		var locationPicker = $('.location-picker').locationPicker({
			locationChanged : function(data){
				$('#output').text(JSON.stringify(data));
			}
		});
});
</script>
```
## Location picker API Reference

locationPicker looks for elements with data-type='address', data-type='location-store' and data-type='map'
in specified selector by default. 

Those elements could be changed via initialization options. 

Location selected callback function, initial location information could be passed as well.

All available options are:
```html
<script>
var locationPicker = $('.location-picker').locationPicker({
			{
				address_el : 'input[data-type="address"]', // address autocomplete input
				map_el: '[data-type="map"]', // map element to render OSM map in
				save_el: '[data-type="location-store"]', // Location information is stored in this input in JSON format
				raw_data: false, /* if true, full place information is returned in JSON format 
				False by default, returns latitude, longitude and address string in JSON format
				*/			
				init:{ 
					current_location: true, // True by default, initializes location picker with current location 
					address : 'Put init adddress here',
					location : {lat: <latitude>, lng: <longitude>} // put initial location here
					},
				// callback method
				locationChanged : function(data){

					$('#output').text(JSON.stringify(data));
				}
			
		});
</script>
```
Location Picker methods:

* getData() - returns current location data
* getAddress() - returns address string
* setAddress(address) - sets location picker address and shows location on map
* setLocation(lat, long) - sets location and reverse geocodes it's address 


## Contributors

* CDK2020 (<https://redevs.org>)

## License

[The MIT License (MIT)](LICENSE)
