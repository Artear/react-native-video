## react-native-video with ads

React Native Video package updated in order to show ads during playback and handle the device orientation. The following properties were added to the ```<Video />``` component:

* **adTagUrl** (Optional String): Set the doubleclick.net URL in this property.

* **forceLandscapeOnStart** (Optional Boolean): To force landscape when the video player starts. Default value: **false**.

* **forcePortraitOnClose** (Optional Boolean): To force portrait when the video player is closed. Default value: **false**.

## Installing

```
yarn add react-native-orientation-locker
yarn add https://github.com/Artear/react-native-video.git
```

## Configuring

#### iOS

Add the following code to your project's **AppDelegate.m** file:

```diff
+#import "Orientation.h"

+- (UIInterfaceOrientationMask)application:(UIApplication *)application supportedInterfaceOrientationsForWindow:(UIWindow *)window {
+  return [Orientation getOrientation];
+}
```

#### Android

Add the following code to the **android/app/src/main/AndroidManifest.xml** file:

```diff
      <activity
        ....
+       android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
        android:windowSoftInputMode="adjustResize">
      </activity>
```

Implement the **onConfigurationChanged** method in the **MainActivity.java** file:

```diff
+import android.content.Intent;
+import android.content.res.Configuration;

public class MainActivity extends ReactActivity {

+   @Override
+   public void onConfigurationChanged(Configuration newConfig) {
+       super.onConfigurationChanged(newConfig);
+       Intent intent = new Intent("onConfigurationChanged");
+       intent.putExtra("newConfig", newConfig);
+       this.sendBroadcast(intent);
+   }

}
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
    forceLandscapeOnStart={true}
    forcePortraitOnClose={true}
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
