## react-native-video with ads

React Native Video package updated in order to show ads using the following properties:

* **adTagUrl** (Optional String): Set the doubleclick.net URL in this property.
* **onAdStart** (Optional Event): When the ad video started.
* **onAdComplete** (Optional Event): When all the ads were played.
* **onAdError** (Optional Event): When there is an error while trying to play an ad.
* **onAdPause** (Optional Event): When the user pauses the ad.
* **onAdSkip** (Optional Event): When the user skips the ad.

## Installing

```
yarn add https://github.com/Artear/react-native-video.git
```

## React Native sample code

```javascript

import Video from 'react-native-video'

<Video
    source={{ uri: 'https://ia600201.us.archive.org/12/items/BigBuckBunny_328/BigBuckBunny_512kb.mp4' }}
    controls={true}
    style={styles.backgroundVideo}
    adTagUrl={'https://pubads.g.doubleclick.net/gampad/ads?sz=640x480&iu=/124319096/external/single_ad_samples&ciu_szs=300x250&impl=s&gdfp_req=1&env=vp&output=vast&unviewed_position_start=1&cust_params=deployment%3Ddevsite%26sample_ct%3Dlinear&correlator='}
    resizeMode="contain"
    />

var styles = StyleSheet.create({
  backgroundVideo: {
    position: 'absolute',
    top: 0,
    left: 0,
    bottom: 0,
    right: 0,
  },
});

```
