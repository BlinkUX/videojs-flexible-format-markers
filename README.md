

Video.js Flexible Format Markers
===================

![Alt text](https://raw.github.com/spchuang/videojs-markers/master/screenshot.png "Screen shot of videojs.markers")

This is an extension of the plugin that displays customizable markers upon progress bars of the video with [Video.js](https://github.com/videojs/video.js/). This could be used to show video breaks and show overlaid text on the video when playback reaches the specific break point.
This version allows custom formats for marker entries which is useful for enabling video markers for data formats pulled from independent sources such as transcripts or video documentation.

## Example
    player.markers({
        markerTip:{
          display: true,
          text: function(marker) {
            return marker.phrase;
          }
        },
        breakOverlay:{
          display: true,
          displayTime: 3,
          text: function(marker) {
            return marker.phrase;
          }
        },
        onMarkerReached: function(marker) {
          if(scope.markerCallback){
            scope.markerCallback(marker);
          }
        },
        format : {
          setTime : function(object, time){
            object.start = time;
          },
          time : function(object){
            return object.start;
          },
          setText : function(object, text){
            object.phrase = text;
          },
          text : function(object){
            return object.phrase;
          }
        },
        markers: angular.copy(scope.markers)
    });
    player.markers.init();

## Features
* All features of videojs-markers
* Custom specification of marker object format
* accessable init() function for asyncronous initialization


## History
- 0.5.0
   - add 'onMarkerClick' callback handler. When this returns false, the default behavior of seeking to the marker time will be prevented.
   - add new 'getMarkers' API 
   - remove constraints of using 'time' as the marker time attribute. Instead, a new markertip.time() function is added to resolve the time dynamically. This mean the time attribute can be represented in different attributes. This also made marker times modifiable (see new demo file). Note that the UI position of the marker will only be updated after you call marker.players.updateTime().
- 0.4
   - change display_time to displayTime
   - markers now takes an array of object containing time, text, overlay text
   - add markerReached callback
   - markerTip and overlay text is now a clalback function for higher flexibility
   - Add many markers APIs for adding and removing markers dynamically.
- 0.1
   - initial release


## License
This project is licensed under MIT.
