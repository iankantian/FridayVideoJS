### Friday Videojs
This is a weekly project to explore video.js, as well as add some functionality to it, like VAST ads, playlists, etc.  Just a toy.

videojs-vast-plugin [![Build Status](https://travis-ci.org/theonion/videojs-vast-plugin.png?branch=master)](https://travis-ci.org/theonion/videojs-vast-plugin) [![Coverage Status](https://img.shields.io/coveralls/theonion/videojs-vast-plugin.svg)](https://coveralls.io/r/theonion/videojs-vast-plugin)
===================
This plugin reads a [VAST file](https://www.iab.net/vast), grabs the first video it can, and plays it as pre-roll advertisement before your video. It will also click through to whatever url the advertiser designates, track any clicks, and fire all of the correct pixel trackers at the right times.

### Usage of Vast Plugin
```
<script src="http://vjs.zencdn.net/4.4.3/video.js"></script>
<script src="vast-client.js"></script>
<script src="video.ads.js"></script>
<script src="videojs.vast.js"></script>
```

Add "ads" and "vast" to the plugins object, and pass a url:

    plugins: {
        ads: {},
        vast: {
            url: 'http://url.to.your/vast/file.xml'
        }
    }

And when you play that video, a pre-roll ad should play beforehand.

If you click on the ad, an `adclick` event will trigger.

Check out the [demo](https://github.com/theonion/videojs-vast-plugin/blob/master/example.html) for a more detailed example.

This plugin is technically an integration for video.js's [ads plugin](https://github.com/videojs/videojs-contrib-ads). For more information on the various states in the preroll process, please refer to the  [videojs-contrib-ads documentation](https://github.com/videojs/videojs-contrib-ads#state-diagram).

### Vast Options
- url: a URL to the xml file.
- skip: how long until the user can skip the ad. Defaults to 5, and a negative number will disable it.

### Credit
The Onion is not just a humor site, check out their github.  I'm using their Vast plugin which in tern uses dailymotion's  [vast client](https://github.com/dailymotion/vast-client-js) to read and parse the VAST files, and video.js's [ads plugin](https://github.com/videojs/videojs-contrib-ads) for switching from pre-roll to content.

This demo also uses Antonio Laguna's [playlist](https://www.npmjs.com/package/videojs-playlist) videojs-playlists.js, however I removed the need for jquery dependence for my own reasons.

### TODO
make a client that can add to the video playlist from a grid of previews.
allow audio ads to play
make a companion player for the Vast client, as that is untreated at this time.
