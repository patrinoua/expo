# Support expo docs

`app.json` is a manifest format for describing web apps. It declares environment variables, add-ons, and other information required to run an app. You can find out more about it [here](https://devcenter.heroku.com/articles/app-json-schema).

If you want to be able to declare and use variables, which is not possible in json files, you can instead use `app.config.js`.

Information that should be included is `name`, `slug`, etc. 
Read about all the fields you can add [here](https://docs.expo.dev/versions/latest/config/app/).

For mobile applications you will often need to specify ios and android fields and provide some additional properties.

Here is an example `app.config.js`

```

const version = `2.1.0`
const buildNumber = 33

const config = {
  expo: {
    version: version,
    name: 'My App',
    slug: 'my-app',
    description: 'My app description',
    ios: {
      buildNumber: `${buildNumber}`,
      bundleIdentifier: 'com.my-username.my-app',
      googleServicesFile: './config/GoogleService-Info.plist',
      supportsTablet: true,
      icon: './src/assets/buddies/solid-icon.png',
      infoPlist: {
        NSLocationWhenInUseUsageDescription:
          'This makes it possible to show you other users around you.',
        NSPhotoLibraryUsageDescription:
          'This makes it possible to upload your profile picture',
        ITSAppUsesNonExemptEncryption: false,
      },
    },
    android: {
      versionCode: buildNumber,
      icon: './src/assets/my-app/icon.png',
      googleServicesFile: './config/google-services-buddies.json',
      package: 'com.my-username.my-app',
      useNextNotificationsApi: true,
      config: {
        googleSignIn: {
          apiKey: 'AIza***********************Tvvw',
        },
      },
      permissions: ['CAMERA', 'ACCESS_FINE_LOCATION', 'LOCATION_FOREGROUND'],
    },
    plugins: [
      [
        "expo-image-picker",
        {
          "photosPermission": "The app accesses your photos to let you share them with your friends."
        }
      ]
    ],
    userInterfaceStyle: "automatic",
    extra: {
      eas: {
        projectId: "1ba9***********************e6d",
        cli: {
          version: ">= 2.7.0"
        }
      }
    },
    privacy: 'public',
    platforms: ['ios', 'android'],
    githubUrl: 'https://github.com/my-username/my-app/',
    orientation: 'portrait',
    primaryColor: '#000000',
    splash: {
      resizeMode: 'contain',
      backgroundColor: '#ffffff',
      image: './src/assets/my-app/logo.png',
    },
    updates: {
      fallbackToCacheTimeout: 0,
    },
    assetBundlePatterns: ['**/*', 'src/assets/images/*']
  }
}

export default config

```

## More useful links

- [Full list of properties](https://docs.expo.dev/versions/latest/config/app/)
- [dynamic-configuration](https://docs.expo.dev/workflow/configuration/#dynamic-configuration)
- [Versioning your app](https://docs.expo.dev/distribution/app-stores/#versioning-your-app)
