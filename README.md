## react-native-video with ads

## Installing

```
yarn add react-native-orientation-locker
yarn add yarn add https://github.com/Artear/react-native-video.git
```

## Configuring

#### iOS

Add the following to your project's `AppDelegate.m`:

```diff
+#import "Orientation.h"

+- (UIInterfaceOrientationMask)application:(UIApplication *)application supportedInterfaceOrientationsForWindow:(UIWindow *)window {
+  return [Orientation getOrientation];
+}

@end
```

#### Android

Add following to android/app/src/main/AndroidManifest.xml

```diff
      <activity
        ....
+       android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
        android:windowSoftInputMode="adjustResize">
      </activity>
```

Implement onConfigurationChanged method (in `MainActivity.java`)

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

Add following to MainApplication.java
(This will be added automatically by auto link. If not, please manually add the following )

```diff
+import org.wonday.orientation.OrientationPackage;
+import org.wonday.orientation.OrientationActivityLifecycle;

    @Override
    protected List<ReactPackage> getPackages() {
      @SuppressWarnings("UnnecessaryLocalVariable")
      List<ReactPackage> packages = new PackageList(this).getPackages();
      // Packages that cannot be autolinked yet can be added manually here, for example:
      // packages.add(new MyReactNativePackage());
+     packages.add(new OrientationPackage());
      return packages;
    }

//...
```

## Sample React Native code

```javascript

import Video from 'react-native-video'

<Video
    source={{ uri: 'https://www.example.com/video.mp4' }}
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
