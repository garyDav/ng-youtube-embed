<img src="https://raw.githubusercontent.com/ArunMichaelDsouza/ng-youtube-embed/master/icon.png" width="300" height="auto" alt="ng-youtube-embed icon"/>

# ng-youtube-embed [![npm version](https://badge.fury.io/js/ng-youtube-embed.svg)](https://badge.fury.io/js/ng-youtube-embed) [![NPM Downloads](https://img.shields.io/npm/dm/ng-youtube-embed.svg?style=flat-square)](https://www.npmjs.com/package/ng-youtube-embed) [![Latest Stable Version](https://img.shields.io/bower/v/ng-youtube-embed.svg?style=flat-square)](http://bower.io/search/?q=ng-youtube-embed)

AngularJS module to embed Youtube videos with support for Youtube player parameters and JavaScript API for iframe embeds.
> Superlight (less than 5KB) and easy to use! Supports Youtube video URLs and IDs. No 3rd party JS dependencies. 

### [Demo on CodePen](http://codepen.io/amdsouza92/pen/yNxyJV)

<br/>

## Installation

#### CDN 

Use ng-youtube-embed directly from jsdelivr CDN

```html
https://cdn.jsdelivr.net/angular.youtube-embed/0.4.3/ng-youtube-embed.min.js
```

#### via bower

You can install the package using bower. Make sure you have bower installed, then run : 

```html
bower install ng-youtube-embed --save
```

#### via npm

```html
npm install ng-youtube-embed --save
```

Or, [download](https://github.com/ArunMichaelDsouza/ng-youtube-embed/releases) the latest version and include ``ng-youtube-embed.min.js`` to your project.

Add ``ngYoutubeEmbed`` as a dependency in your angular app module.

<br/>

## Usage

You can use the directive with any of the available Youtube player parameters.

Include the ``video`` parameter and pass in the scope variable which contains the Youtube video URL or ID for which you want to render an iframe.

Example - 
```javascript
var myApp = angular.module('myApp', ['ngYoutubeEmbed']);

myApp.controller('myCtrl', ['$scope', function($scope) {
    $scope.videoURL = 'https://www.youtube.com/watch?v=OPmOXJtxxoo';
}]);
```
```html
<ng-youtube-embed 
	video="videoURL" 
    autoplay="true"
    color="white"
    disablekb="true"
    end="20">
</ng-youtube-embed>
```
Where ``videoURL`` is the scope variable containing the Youtube video URL.

#### One single parameter to embed videos using URL or ID

Works well with Youtube video IDs too. Pass in the scope variable which contains the Youtube video ID in the same ``video`` parameter.

Example - 
```javascript
var myApp = angular.module('myApp', ['ngYoutubeEmbed']);

myApp.controller('myCtrl', ['$scope', function($scope) {
    $scope.videoID = 'OPmOXJtxxoo';
}]);
```
```html
<ng-youtube-embed 
	video="videoID" 
    autoplay="true"
    color="white"
    disablekb="true"
    end="20">
</ng-youtube-embed>
```
Where ``videoID`` is the scope variable containing the Youtube video ID.

<br/>

## Parameters

ng-youtube-embed supports all of the available Youtube player parameters. To view the list with details, click [here](https://developers.google.com/youtube/player_parameters).

#### Supported parameters

#### ``video {string}``
This parameter specifies the scope variable containing the Youtube video URL or ID for which you want to render the iframe video player.

#### ``width {string} | Default: 500px``
This parameter specifies the width of the Youtube iframe embed player.
Provide a value in ``px`` or ``%`` in order to render a video player with custom width.

#### ``height {string} | Default: 350px``
This parameter specifies the height of the Youtube iframe embed player.
Provide a value in ``px`` or ``%`` in order to render a video player with custom height.

#### ``autoplay {boolean} | Default: false``
This parameter specifies whether the initial video will automatically start to play when the player loads.
Supported values are : ``true`` and ``false``.

#### ``ccloadpolicy {boolean}``
Setting the parameter's value to ``true`` causes closed captions to be shown by default, even if the user has turned captions off. The default behavior is based on user preference.
Supported values are : ``true`` and ``false``.

#### ``color {string} | Default: red``
This parameter specifies the color that will be used in the player's video progress bar to highlight the amount of the video that the viewer has already seen. Supported values are : ``red`` and ``white``.
> Note: Setting the color parameter to white will disable the ``modestbranding`` option.

#### ``controls {boolean} | Default: true``
This parameter indicates whether the video player controls are displayed.
Supported values are : ``true`` and ``false``.

#### ``disablekb {boolean} | Default: false``
Setting the parameter's value to ``true`` causes the player to not respond to keyboard controls.
Supported values are : ``true`` and ``false``.
> Currently supported keyboard controls are: 

> * Spacebar or [k]: Play / Pause
* Arrow Left: Jump back 5 seconds in the current video
* Arrow Right: Jump ahead 5 seconds in the current video
* Arrow Up: Volume up
* Arrow Down: Volume Down
* [f]: Toggle full-screen display
* [j]: Jump back 10 seconds in the current video
* [l]: Jump ahead 10 seconds in the current video
* [m]: Mute or unmute the video
* [0-9]: Jump to a point in the video. 0 jumps to the beginning of the video, 1 jumps to the point 10% into the video, 2 jumps to the point 20% into the video, and so forth.

#### ``enablejsapi {boolean} | Default: false``
Setting the parameter's value to ``true`` enables the player to be controlled via iframe or JavaScript player API calls. 
For more information on the iframe API and how to use it, see the [iframe API documentation](https://developers.google.com/youtube/iframe_api_reference). 
Supported values are : ``true`` and ``false``.

#### ``end {number}``
This parameter specifies the time, measured in seconds from the start of the video, when the player should stop playing the video. If you have a playlist, then this parameter will only work for the first video.
Supported value is a positive integer.

#### ``fs {boolean} | Default: true``
Setting this parameter to ``false`` prevents the fullscreen button from displaying in the player.
Supported values are : ``true`` and ``false``.

#### ``hl {string}``
Sets the player's interface language. 
The parameter value is an [ISO 639-1 two-letter language code](http://www.loc.gov/standards/iso639-2/php/code_list.php) or a fully specified locale. For example, ``fr`` and ``fr-ca`` are both valid values.
> Note: The interface language is used for tooltips in the player and also affects the default caption track. Note that Youtube might select a different caption track language for a particular user based on the user's individual language preferences and the availability of caption tracks.

#### ``ivloadpolicy {boolean} | Default: true``
Setting the parameter's value to ``false`` causes video annotations to be hidden by default.
Supported values are : ``true`` and ``false``.

#### ``listtype {string}``
This parameter, in conjunction with the ``list`` parameter, identifies the content that will load in the player. Valid parameter values are ``playlist``, ``search``, and ``user_uploads``.

> Note: If you specify values for the ``list`` and ``listType`` parameters, then you dont need to specify a video URL or ID in the the ``video`` parameter.

#### ``list {string}``
This parameter, in conjunction with the ``listtype`` parameter, identifies the content that will load in the player.

If the ``listtype`` parameter value is ``search``, then the ``list`` parameter value specifies the search query.

If the ``listtype`` parameter value is ``user_uploads``, then the ``list`` parameter value identifies the Youtube channel whose uploaded videos will be loaded.

If the ``listtype`` parameter value is ``playlist``, then the ``list`` parameter value specifies a Youtube playlist ID. In the parameter value.

> Note: If you specify values for the ``list`` and ``listType`` parameters, then you dont need to specify a video URL or ID in the the ``video`` parameter.

#### ``loop {boolean}`` | ``Default value: false``
This parameter only works when used in conjunction with the ``playlist`` parameter. It specifies whether to loop the entire playlist or not.
Supported values are : ``true`` and ``false``.

> Note: To loop a single video, set the ``loop`` parameter value to ``true`` and set the ``playlist`` parameter value to the same video URL or ID already specified in the ``video`` parameter.

#### ``modestbranding {boolean} | Default: false``
This parameter lets you use a Youtube player that does not show a Youtube logo. Set the parameter value to ``true`` to prevent the Youtube logo from displaying in the control bar.
Supported values are : ``true`` and ``false``.
> Note: A small YouTube text label will still display in the upper-right corner of a paused video when the user's mouse pointer hovers over the player.

#### ``origin {string}``
This parameter provides an extra security measure for the iframe API and is only supported for iframe embeds. If you are using the iframe API, which means you are setting the ``enablejsapi`` parameter value to ``true``, you should always specify your domain as the ``origin`` parameter value.

#### ``playlist {string}``
This parameter specifies a comma-separated list of video URLs or IDs to play.

#### ``playsinline {boolean} | Default: false``
This parameter controls whether videos play inline or fullscreen in an HTML5 player on iOS.
Supported values are : ``true`` and ``false``.

#### ``rel {boolean} | Default: true``
This parameter indicates whether the player should show related videos when playback of the initial video ends.
Supported values are : ``true`` and ``false``.

#### ``showinfo {boolean} | Default: true``
Setting the parameter's value to ``false`` causes the player to not display information like the video title and uploader before the video starts playing.
Supported values are : ``true`` and ``false``.

#### ``start {number}``
This parameter causes the player to begin playing the video at the given number of seconds from the start of the video. If you have a playlist, then this parameter will only work for the first video.
Supported value is a positive integer.

#### Deprecated parameters

#### ``url``
ng-youtube-embed now supports Youtube video URLs as well as IDs, so the old ``url`` parameter has been replaced in favour of the new ``video`` parameter.

#### ``autohide``
See Youtube iframe player deprecation notice [here](https://developers.google.com/youtube/player_parameters#release_notes_08_19_2015).

#### ``theme``
See Youtube iframe player deprecation notice [here](https://developers.google.com/youtube/player_parameters#release_notes_08_19_2015).

#### ``gaming``
ng-youtube-embed now has out of the box support for [gaming.youtube.com](https://gaming.youtube.com), there's no need to specify an extra parameter for that.

<br/>

## Contributors

- [Fabián Horacio Veliz](https://github.com/fabianVeliz)
- [Gustavo Salgado](https://github.com/gsalgadotoledo)

<br/>

## License

MIT Licensed

Copyright (c) 2015 Arun Michael Dsouza (amdsouza92@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

