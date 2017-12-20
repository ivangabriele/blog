---
layout: post
title:  "[Cordova] How to detect shaking ?"
date:   2014-03-07
banner_image: Cordova.jpg
tags: [Cordova, JS]
---

For I Met, I needed to detect shaking to allow users adding each other to their timeline by simply shaking their phone at the same time. I did a little search and found leecrossley’s [shake.js](https://github.com/leecrossley/cordova-plugin-shake/blob/master/www/shake.js) script but it didn’t work well. Thus I slightly improved it to write this one.

<!--more-->

```js
// Let's wait for the user to shake it !
shake.startWatch(onShake);

function onShake() {
  alert('Oh yeah, you shook it !');
}

// Stop watching for shaking event
shake.stopWatch();
```

Here is the script :

```js
var shake = (function () {
  var shake = {},
    watchId = null,
    options = { frequency: 300 },
    previousAcceleration = { x: null, y: null, z: null },
    shakeCallBack = null;

  // Start watching the accelerometer for a shake gesture
  shake.startWatch = function (onShake) {
    if (onShake) {
      shakeCallBack = onShake;
    }
    watchId = navigator.accelerometer.watchAcceleration(getAccelerationSnapshot, handleError, options);
  };

  // Stop watching the accelerometer for a shake gesture
  shake.stopWatch = function () {
    if (watchId !== null) {
      navigator.accelerometer.clearWatch(watchId);
      watchId = null;
    }
  };

  // Gets the current acceleration snapshot from the last accelerometer watch
  function getAccelerationSnapshot() {
    navigator.accelerometer.getCurrentAcceleration(assessCurrentAcceleration, handleError);
  }

  // Assess the current acceleration parameters to determine a shake
  function assessCurrentAcceleration(acceleration) {
    var accelerationChange;
    if (previousAcceleration !== null) {
      accelerationChange = Math.abs(Math.round(Math.abs(previousAcceleration.x) - Math.abs(acceleration.x))) + Math.abs(Math.round(Math.abs(previousAcceleration.y) - Math.abs(acceleration.y))) + Math.abs(Math.round(Math.abs(previousAcceleration.z) - Math.abs(acceleration.z)));
    }

    // Shake detected :
    if (accelerationChange > 10) {
      if (typeof (shakeCallBack) === "function") {
        shakeCallBack();
      }

      shake.stopWatch();

      setTimeout(shake.startWatch, 1000);

      previousAcceleration = {
        x: null,
        y: null,
        z: null
      }
    }
    else {
      previousAcceleration = {
        x: acceleration.x,
        y: acceleration.y,
        z: acceleration.z
      }
    }
  }

  // Handle errors here
  function handleError() {

  }

  return shake;
}
)();
```
