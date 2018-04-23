class: center, middle, vertigo

# Introduction to Web Audio

<hr>
## Guillaume Pellerin, Head Web Team @IRCAM

### IRCAM / NYU - 23/04/2018

<img src="https://soledadpenades.com/imgs/2014/webaudio-js.png" width="100px">
&nbsp;
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/1200px-HTML5_logo_and_wordmark.svg.png" width="100px">
&nbsp;
<img src="http://webaudio.gatech.edu/sites/default/files/images/wacv3_b1.png" width="100px">

### https://github.com/yomguy/WebAudio-Course-NYU

---
class: vertigo, tight

# Contents

1. Introduction

1. Systems, norms, protocols, standards and applications

    - Protocols
    - Browsers
    - Formats

1.  Languages and software architectures

    - Languages
    - Backend
    - Frontend

1. Web Audio API

    - Specifications
    - Implementations
    - Documentation
    - Examples

1. More use cases and tools

---
class: vertigo, tight

o Introduction

.pull-left[
## Web ?

- 1989 : Tim Berners-Lee created the World Wide Web at CERN
- HTTP : HyperText Transfer Protocol
- URL : Uniform Resource Locator
- HTML : HyperText Markup Language (hyperlink)
- Serveur / Client Web

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/WWW_logo_by_Robert_Cailliau.svg/601px-WWW_logo_by_Robert_Cailliau.svg.png" width="50%">

]

.pull-right[
```HTML5
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>title</title>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>
  <body>
    <!-- page content -->
  </body>
</html>
```
]


---
class: vertigo


# Introduction

## W3C : World Wide Web Consortium

- A member-driven organization composed of over 460 companies, universities, start-ups, etc. from all over the world.
- 44 technicals groups, including Working and Interest Groups where technical specifications are discussed and developed.
- Over 6,025 published technical reports, including 386 Web standards (or W3C Recommendations) - since January 1st ,1995.
- About 291 Community and Business Groups, where developers, designers, and anyone passionate about the Web have a place to hold discussions and publish ideas.
- Near 10,846 active participants constituting the W3C community.
- A technical staff composed of 67 people, spread on all five continents.


---
class: vertigo, tight

# Introduction

## Web 1.0 (1995)

```HTML
<bgsound src="sound1.mid">
<bgsound src="sound2.au" loop="infinite">
```

## Flash (1997)

- Player
- Medias server
- R.I.P.

## HTML5 (2008)

```HTML
<audio src="http://mainline.i3s.unice.fr/mooc/LaSueur.mp3" controls>
```

<audio src="http://mainline.i3s.unice.fr/mooc/LaSueur.mp3" controls></audio>

<br>

This HTML5 code:

- initiates a network request to stream the content,
- deals with decoding/streaming/buffering the incoming data,
- renders audio controls,
- updates the progress indicator, time, etc.

---
class: vertigo, tight

# Introduction

## HTML5 (2008)

```HTML
<audio src="http://mainline.i3s.unice.fr/mooc/LaSueur.mp3" controls>
```

<audio src="http://mainline.i3s.unice.fr/mooc/LaSueur.mp3" controls></audio>

<br>

It's possible to write a custom player: to make your own controls and use the JavaScript API of the <audio> and <video> elements; to call play() and pause(); to read/write properties such as currentTime; to listen to events (ended, error, timeupdate, etc.); and to manage a playlist, etc.

However, there are many things we still cannot do, including:

- Play multiple sounds or music in perfect sync,
- Play non-streamed sounds (this is a requirement for games: sounds must be loaded in memory),
- Output directly to the speakers; adding special effects, equalizer, stereo balancing, reverb, etc.
- Any fancy visualizations that dance with the music (e.g. waveforms and frequencies).

The Web Audio API will fulfill such missing parts, and much more.


---
class: vertigo

# Introduction

<iframe id="frame" src="https://femurdesign.com/theremin/" scrolling="auto" frameborder="0" allowfullscreen="" width="100%"></iframe>

https://femurdesign.com/theremin/

---
class: vertigo

# Introduction

<iframe id="frame" src="https://webaudiodemos.appspot.com/midi-synth/index.html" scrolling="auto" frameborder="0" allowfullscreen="" width="100%"></iframe>

https://webaudiodemos.appspot.com/midi-synth/index.html

---
class: vertigo

# Introduction

<iframe id="frame" src="http://juno-106.js.org/" scrolling="auto" frameborder="0" allowfullscreen="" width="100%"></iframe>

http://juno-106.js.org/

---
class: vertigo, tight

# Systems, norms, protocols, standards and applications

- IP
  - https://fr.wikipedia.org/wiki/Internet_Protocol
  - https://tools.ietf.org/html/rfc791
- TCP/UDP
  - https://fr.wikipedia.org/wiki/Transmission_Control_Protocol
  - https://tools.ietf.org/html/rfc793
- Client/server architectures
  - https://fr.wikipedia.org/wiki/Client-serveur
- Browsers
  - (NCSA Mosaic, NetScape, Mozilla)
  - FireFox
  - Chromium / Chrome
  - Safari
  - Internet Explorer
  - Opera, etc.
  - https://fr.wikipedia.org/wiki/Navigateur_web
- Rendering engine
  - HTML : KHTML > webkit > Safari & Chrome
  - JS : Chrome > V8 > NodeJS             

---
class: vertigo, tight

# Binary media formats for the web

## objectives : compression, streaming, embed metadata

- Image
  - JPEG
  - PNG (lossless)
- Audio
  - MP3
  - OGG Vorbis
  - OGG FLAC (lossless)
- Video
  - MP4
  - WebM
- Flash (R.I.P.)

https://developer.mozilla.org/fr/docs/Web/HTML/Formats_pour_audio_video


---
class: vertigo, tight

# Languages and software architectures

- Backend
  - languages PHP, Python, Ruby, C++, Go
  - metadata sharing formats : JSON, XML, HTML
  - frameworks : Symphony, Django, Ruby On Rails
- Frontend
  - HTML, HTML5
  - CSS, SASS
  - JavaScript, [ECMAScript 6](https://github.com/lukehoban/es6features)
  - frameworks : Angular (Google then Microsoft), React (Facebook), VueJS, etc..............
- Architectures & requests
  - MVC
  - AJAX
  - Restful APIs

---
class: vertigo


# Web Audio API

## Specifications

https://webaudio.github.io/web-audio-api/

## Documentation

https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API

## Implementations

- Now in **all** browsers, but not equally with all functionalities
- https://html5test.com/
- https://html5test.com/results/desktop.html

---
class: vertigo, tight

# Web Audio simple examples

- Gain node
  - https://developer.mozilla.org/en-US/docs/Web/API/GainNode
  - https://jsbin.com/davebu/edit?html,js,console,output
- Stereo panner
  - https://developer.mozilla.org/en-US/docs/Web/API/StereoPannerNode
  - https://jsbin.com/jarimu/edit?html,js,output
- Biquad filter
  - https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode
  - https://jsbin.com/tuvaxar/edit?html,js,output
- Convolver node
  - https://developer.mozilla.org/en-US/docs/Web/API/ConvolverNode
  - https://jsbin.com/belide/edit?html,js,console,output
  - http://webaudioapi.com/samples/room-effects/
- Dynamics Compressor node
  - https://developer.mozilla.org/en-US/docs/Web/API/DynamicsCompressorNode
  - https://jsbin.com/momixok/edit?html,js,console,output

---
class: vertigo


# Web Audio with canvas

- 2D real time visualizations: waveforms
  - https://jsbin.com/wigucu/edit
- 2D real time visualization: frequencies
  - https://jsbin.com/vemaho/edit
- 2D real time visualization: volume meters
  - http://jsbin.com/kazuzed/edit

---
class: vertigo

# Working with sound samples loaded in memory

- No streaming/decoding in real time means less CPU is used,
- With all samples loaded in memory, it's possible to play them in sync with great precision,
- It's possible to make loops, add effects, change the playback rate, etc.
- And of course, if they are in memory and uncompressed, there is no wait time for them to start playing: they are ready to be used immediately!  

## Examples

- https://jsbin.com/gojuxo/edit?html,js,console,output
- https://jsbin.com/gefezu/edit
- https://codepen.io/teropa/pen/PKoYXM/
- http://remixxer.com/app/




---
class: vertigo, tight



# Performance and tricks


## Speed vs. Latency vs. Priority

- [Latency](http://padenot.github.io/wac-14-keynote/#17)
- [AudioContext](https://developer.mozilla.org/fr/docs/Web/API/AudioContext)
- [ScriptProcessorNode](https://developer.mozilla.org/fr/docs/Web/API/ScriptProcessorNode)
- [asm.js](https://fr.wikipedia.org/wiki/Asm.js)
- [emscripten](http://kripken.github.io/emscripten-site/)
- [WebAssembly](http://webassembly.org/getting-started/developers-guide/)
- AudioWorklet (finally shipped in Chrome 66)
    - [Specifications](https://webaudio.github.io/web-audio-api/#audioworklet)
    - [Enter AudioWorklet](https://developers.google.com/web/updates/2017/12/audio-worklet)
    - [What, Why, and How? (video)](https://www.youtube.com/watch?v=g1L4O1smMC0)

## Gotchas

- https://github.com/Jam3/web-audio-player#webaudio-gotchas

---
class: vertigo, tight, tiny



# Awesome Web Audio!

## Resources

- https://github.com/alemangui/web-audio-resources
- https://github.com/notthetup/awesome-webaudio
- http://tinyletter.com/webaudioweekly
- http://www.bitwisemusic.com/


## Tutorials

- https://github.com/mmckegg/web-audio-school
- https://www.html5rocks.com/en/tutorials/webaudio/games/
- https://www.edx.org/course/html5-apps-games-w3cx-html5-2x
- https://aerotwist.com/blog/guitar-tuner/
- https://www.toptal.com/web/creating-browser-based-audio-applications-controlled-by-midi-hardware


---
class: vertigo, tight, tiny


# Awesome Web Audio!

.pull-left[
## More cool examples...

- http://webaudioplayground.appspot.com/
- http://audiocrawl.co/
- https://mainline.i3s.unice.fr/AmpSim3/
- https://femurdesign.com/theremin/
- https://codepen.io/teropa/pen/PKoYXM/
- http://augeas.github.io/Chaoscillator/
- http://tanguysynth.com/
- http://www.html5drummachine.com/
- https://www.modulargrid.net/e/racks/synth
- https://github.com/hoch/canopy
- https://github.com/gibber-cc/gibberish
]
.pull-right[

## ...and libraries

- https://tonejs.github.io/
- https://howlerjs.com/
- https://github.com/wavesjs
- http://collective-soundworks.github.io/soundworks/
- https://wavesurfer-js.org/
- https://github.com/bbc/peaks.js
- https://github.com/Parisson/TimeSide/
]


---
class: center, middle, vertigo


# Enjoy and have FUN!


<img src="https://soledadpenades.com/imgs/2014/webaudio-js.png" width="100px">
&nbsp;
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/1200px-HTML5_logo_and_wordmark.svg.png" width="100px">
&nbsp;
<img src="http://webaudio.gatech.edu/sites/default/files/images/wacv3_b1.png" width="100px">

<hr>

### Guillaume Pellerin / @yomguy / guillaume.pellerin@ircam.fr


Most of the resources of this document are taken from

Michel Buffa's [EDX MOOC HTML5 Apps and Games](https://www.edx.org/course/html5-apps-games-w3cx-html5-2x)

Thanks Michel!!
