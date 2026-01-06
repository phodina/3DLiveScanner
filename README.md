# Content of this repository

## night_vision
Viewer of ToF sensor data. This project could be used as night vision: https://www.xda-developers.com/huawei-p30-pro-honor-view-20-night-vision/

## scanner
The main project of this repository containing 3D Live Scanner: https://youtu.be/ku_Slo-li3c

## Libraries
* arcore and arengine are AR SDKs which makes the 3D scanning possible
* common contains source codes used in multiple apps
* third_party contains several libraries with different licences

## Tests
* dataset_extractor is a Linux program to extract point cloud from dataset captured by 3D scanner in PLY format
* dataset_viewer is a Linux program for viewing dataset captured by 3D scanner

## Signing

```
nix-shell -p openjdk

keytool -genkey -v -keystore release-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias release-key

base64 release-keystore.jks > release-keystore.jks.b64
```

## ADB

To launch:
```
adb shell am start -n com.lvonasek.tofviewer/.TofViewerActivity
adb shell am start -n com.lvonasek.arcore3dscanner/.ui.Initializator
```

## Notes

On Samsung the ToF Camera is not accesible using the Camera2 API due to Samsung blocking the sensor.

```
samsung.android.uniplugin.isProbeTOFSensor = 0
```

Therefore the only way to talk to the camera is through the ARCore using the scanner.
