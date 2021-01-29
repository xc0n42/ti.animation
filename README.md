# Ti.Animation

<span class="badge-buymeacoffee"><a href="https://www.buymeacoffee.com/miga" title="donate"><img src="https://img.shields.io/badge/buy%20me%20a%20coke-donate-orange.svg" alt="Buy Me A Coke donate button" /></a></span>

![gif](animation.gif)


Appcelerator Titanium Android module to support smooth and scalable animations using [Airbnb Lottie](https://airbnb.design/lottie/).



> ⚠️ The versions iOS 2.0.0 and Android 3.0.0 contain a breaking change that removed the Facebook Keyframes library. We decided to go with a Lottie only library for the future, since it made the race for the best animation library. Also, the deprecated method `addViewToLayer` is now removed. Please continue to use `addViewToKeypathLayer`.

## Migrate from iOS < 2.0.0 and Android < 3.0.0

Instead of using `createLottieView`, simply use `createAnimationView` now. That's it!

## Requirements

- Axway Titanium SDK 7.0.0+
- Axway Titanium SDK 9.0.0+ for Ti.Animation 4.0.0+

## Library versions:

The Titanium modules use external libraries

|Library|Platform|Version|Build Date|
|---|---|---|---|
| [Airbnb Lottie](https://github.com/airbnb/lottie-android) | Android | 3.5.0 | 2020/11/09 |
| [Airbnb Lottie](https://github.com/airbnb/lottie-ios) | iOS | 2.5.2 | 2018/12/10 |


## Create a View

```js
var animation = TiAnimation.createAnimationView({
  file: '/file.json',
  loop: false,
  autoStart: false
});
```

or in Alloy:
```xml
<AnimationView id='view_lottie' module='ti.animation' />
```

## Update native Libraries

- iOS: Use Carthage and `carthage update` to compile the framework automatically. Then, copy the output from `ios/Carthage/Build/iOS` to `ios/platform/`.
- Android: change the version number in `build.gradle`

## Features/Documentation

## Methods:
Name | Parameter | Info | Platforms
--- | --- | --- | -- |
start() | | Starts an animation from the beginning | iOS, Android |
start(int from, int to) | Startframe, Endframe | Plays an animation from frame `from` to `to` | Android |
pause() | | Pause an animation | iOS, Android |
resume() | | Resumes an animation from the current point | iOS, Android |
stop() | | Stops an animation an resets it | iOS, Android |
addEventListener(String event, Callback function) | Event name as string<br>Callback function | Adds events to the animation view | iOS, Android |
setFile(String path) | File path as string | Sets the current animation, Files go into app/assets/ (Alloy) | Android |
setText(String layer, String text) | Layer, Text | Sets the text in the layer `layer` to `text` | Android |
addViewToKeypathLayer(TiUiView view, String layer) | View, Layer | Adds a given Ti.UI.View instance to a layer with the given name | iOS |
convertRectToKeypathLayer() | args | - | iOS |
convertPointToKeypathLayer() | args | - | iOS |
convertRectFromKeypathLayer() | args | - | iOS |
convertPointFromKeypathLayer() | args | - | iOS |
setValueDelegateForKeyPath() | args | - | iOS |


## Properties:
Name | Parameter | Info | Platforms
--- | --- | --- | --- |
progress | float | Get/set the current progress (in percentage) | Android |
loop | boolean | Get/set if the animation should loop | Android |
speed | float | Get/set the speed of the animation | Android |
duration | float | Get/set the duration of the animation | Android |
isPlaying | boolean | Get the animation status | Android |
cache() | boolean | - | iOS |

creation (tss) only:

Name | Parameter | Info | Platforms
--- | --- | --- | --- |
assetFolder|String|If your animation contains images put the folder inside the assetFolder (e.g. `images/` and put the image files inside `app/assets/images/`) | Android |
file | String | JSON file. Files go into app/assets/ (Alloy) | iOS, Android |
loop | boolean | loop the animation | iOS, Android |
autoStart | boolean | automatically start the animation | iOS, Android |


## Events:
Name |  Info | Properties | Platforms
--- |  --- | --- | --- |
complete | When the animation is done | Status:int, Loop:boolean | iOS, Android |
update | Fires during the animation | Frame:int, status:int (ANIMATION_START, ANIMATION_END, ANIMATION_CANCEL, ANIMATION_REPEAT, ANIMATION_RUNNING)  | Android |

## iOS Constants
used in setValueDelegateForKeyPath.type

Name |  Platforms
--- |  --- |
CALLBACK_COLOR_VALUE |  iOS |
CALLBACK_NUMBER_VALUE |  iOS |
CALLBACK_POINT_VALUE |  iOS |
CALLBACK_SIZE_VALUE |  iOS |
CALLBACK_PATH_VALUE |  iOS |

## Example
```xml
<AnimationView id='view_lottie' module='ti.animation' />
```

```js
'#view_lottie': {
  file: 'data.json',
  assetFolder: 'images/', // Android-only
  width: Ti.UI.SIZE,
  height: Ti.UI.SIZE,
  borderColor: '#000',
  borderWidth: 1
}
```

Please see the basic example in `example/app.js`. More examples can found in the [wiki](https://github.com/m1ga/ti.animation/wiki)


## Issue

If you scale your view bigger and you have some jagged lines you need to add `disableHardwareAcceleration:true` to your tss file. Performance will be slower in most cases but quality is better


## Resources

* At [LottieFiles](http://www.lottiefiles.com/) you will find a list of free Lottie animations.
* Elephant animation by <a href="https://lottiefiles.com/user/266156">LottieFiles - weejkqwjlkejlk2</a>

## Authors

- Hans Knöchel ([@hansemannnn](https://twitter.com/hansemannnn) / [Web](http://hans-knoechel.de))
- Michael Gangolf ([@MichaelGangolf](https://twitter.com/MichaelGangolf) / [Web](http://migaweb.de))

<span class="badge-patreon"><a href="https://www.patreon.com/michaelgangolf" title="Donate to this project using Patreon"><img src="https://img.shields.io/badge/patreon-donate-yellow.svg" alt="Patreon donate button" /></a></span>
