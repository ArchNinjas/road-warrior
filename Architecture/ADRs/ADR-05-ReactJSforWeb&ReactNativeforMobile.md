# Javascript based hybrid application development framework for cross platforms 


## Status - Accepted

## Context - 

To build Ios , Android & web app, Road Warrior need 3 different skills and thus 3 different teams. The effort needed may be ~3 times of development & testing.




## Decision
JavaScript based platfroms like ReactNative supports cross-platform development on iOS and Android. They compile to native code and provide similar UI & UX like native mobile applications.
JavaScript components of web applications could be reused and ported into a native app via JavaScript frameworks.

Nearly full native performance. Device capabilities like contacts, camera, calendar etc can be invoked using Cordova SDK.

**Using ReactNative & ReactJS framework will reduce the efforts needed for development & testing during initial years**

## Consequences

Look and feel ( UI) may not be excatly as native apps. But this is a conscious decision for cost effective & speedy development across 3 platforms during initial years.
Once user base is captured & platform matures, the Javascript platform may be replaced eventually with respetive native development(Ios & Android) for native UI & UX.
