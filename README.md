# nixa-expo-dynamic-app-icon

Programmatically change the app icon in Expo.

## Install

```
npx expo install nixa-expo-dynamic-app-icon
```

## Set icon file

add plugins in `app.json`

```typescript
 "plugins": [
      [
        "nixa-expo-dynamic-app-icon",
        {
          "red": { // icon name
            "image": "./assets/icon1.png", // icon path
            "prerendered": true, // for ios UIPrerenderedIcon option
            "platforms":  ["ios", "android"]  // optional platforms array. defaults to both platforms if emitted
          },
          "gray": {
            "image": "./assets/icon2.png",
            "prerendered": true,
            "platforms":  ["ios"]
          }
        }
      ]
    ]
```

## Check AndroidManifest (for android)

```
expo prebuild
```

check added line
[AndroidManifest.xml](./example/android/app/src/main/AndroidManifest.xml#L33-L44)

```xml
  ...
    <activity-alias android:name="expo.modules.dynamicappicon.example.MainActivityred" android:enabled="false" android:exported="true" android:icon="@mipmap/red" android:targetActivity=".MainActivity">
      <intent-filter>
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
      </intent-filter>
    </activity-alias>
    <activity-alias android:name="expo.modules.dynamicappicon.example.MainActivitygray" android:enabled="false" android:exported="true" android:icon="@mipmap/gray" android:targetActivity=".MainActivity">
      <intent-filter>
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
      </intent-filter>
    </activity-alias>
  ...
```

## Create new `expo-dev-client`

create a new `expo-dev-client` and begin using `expo-dynamic-app-icon`

## Use `setAppIcon`

- if error, return **false**
- else, return **changed app icon name**

```typescript
import { setAppIcon } from "nixa-expo-dynamic-app-icon";

...

setAppIcon("red", "default_icon_name") // set icon 'assets/icon1.png'
```

## Use `getAppIcon`

get current app icon name

- default return is `DEFAULT`

```typescript
import { getAppIcon } from "nixa-expo-dynamic-app-icon";

...

getAppIcon() // get current icon name 'red'
```
