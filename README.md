## react-native-video with ads

React Native Video package updated in order to show ads with the following property:

* **adTagUrl** (Optional String): Set the doubleclick.net URL in this property.

## Installing

```
yarn add https://github.com/Artear/react-native-video.git
```

## iOS

For iOS you will have to add the [Google Mobile Ads SDK](https://developers.google.com/admob/ios/quick-start#import_the_mobile_ads_sdk) to your Xcode project.

## Android

On Android the AdMob library code is part of Play Services, which is automatically added when this library is linked.

But you still have to manually update your AndroidManifest.xml, as described in the [Google Mobile Ads SDK documentation](https://developers.google.com/admob/android/quick-start#update_your_androidmanifestxml).

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
