## react-native-video-with-ads

Currently supports Android and IOS

A `<Video>` component for react-native, forked from [react-native-video](https://github.com/react-native-community/react-native-video)!

For the most part, you should be able to use the documentation from [react-native-video](https://github.com/react-native-community/react-native-video)

## Table of Contents

* [Installation](#installation)
* [Usage](#usage)

## Installation

Using npm:

```shell
npm install --save react-native-video-with-ads
```

or using yarn:

```shell
yarn add react-native-video-with-ads
```

In the `ios` directory, setup your Podfile like it is described in the [react-native documentation](https://facebook.github.io/react-native/docs/integration-with-existing-apps#configuring-cocoapods-dependencies). 

Then add the pod for react-native-video-with-ads

```diff
  pod 'Folly', :podspec => '../node_modules/react-native/third-party-podspecs/Folly.podspec'
+  pod 'react-native-video-with-ads', :path => '../node_modules/react-native-video-with-ads/react-native-video.podspec'
end
```

In the `ios` directory, run `pod install`

In the project root, then run `react-native link react-native-video`

## Usage

The same as [react-native-video](https://github.com/react-native-community/react-native-video), with the following additions:

### Event props
* [onAdError](#onAdError)
* [onAdsComplete](#onAdsComplete)
* [onAdsLoaded](#onAdsLoaded)
* [onAdStarted](#onAdStarted)

### Methods
* [requestAds](#requestAds)
* [startAds](#startAds)

### Event props

#### onAdError
Callback function that is called when there is an error while loading an ad. When an error occurs the video will continue playback automatically. If you require additional functionality, use this callback

Payload: none

Platforms: Android ExoPlayer, iOS

#### onAdsComplete
Callback function that is called when all loaded ads have finished playing. This callback should be used to re-start your Video.

Payload: none

Platforms: Android ExoPlayer, iOS

#### onAdsLoaded
Callback function that is called when Ads have been loaded.
Payload: none

Platforms: Android ExoPlayer, iOS

#### onAdStarted
Callback function that is called when Ads have started to play. This should be used to pause your Video.

Payload: none

Platforms: Android ExoPlayer, iOS

### Methods
Methods operate on a ref to the Video element. You can create a ref using code like:
```
return (
  <Video source={...}
    ref => (this.player = ref) />
);
```

#### requestAds

Request ads from the give url

Example:
```
let url = "https://pubads.g.doubleclick.net/gampad/ads?sz=640x480&iu=/124319096/external/single_ad_samples&ciu_szs=300x250&impl=s&gdfp_req=1&env=vp&output=vast&unviewed_position_start=1&cust_params=deployment%3Ddevsite%26sample_ct%3Dlinear&correlator="
this.player.requestAds(url);
```

Platforms: Android ExoPlayer, iOS

#### startAds

Request that the loaded ads start playing

Example:
```
this.player.startAds();
```

Platforms: Android ExoPlayer, iOS

**MIT Licensed**
