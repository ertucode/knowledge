- https://reactnative.dev/docs/running-on-device

1. Enable Debugging over USB

- Most Android devices can only install and run apps downloaded from Google Play, by default. You will need to enable USB Debugging on your device in order to install your app during development.
- To enable USB debugging on your device, you will first need to enable the "Developer options" menu by going to Settings → About phone → Software information and then tapping the Build number row at the bottom seven times. You can then go back to Settings → Developer options to enable "USB debugging".

2. Plug in your device via USB

- Let's now set up an Android device to run our React Native projects. Go ahead and plug in your device via USB to your development machine.

- Now check that your device is properly connecting to ADB, the Android Debug Bridge, by running adb devices.
shell

```bash
$ adb devices
List of devices attached
emulator-5554 offline   # Google emulator
14ed2fcc device         # Physical device
```

- Seeing device in the right column means the device is connected. You must have only one device connected at a time.
note

- If you see unauthorized in the list you will need to run `adb reverse tcp:8081 tcp:8081` and press allow USB debugging on the device.

