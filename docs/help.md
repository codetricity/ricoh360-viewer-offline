# Help and Troubleshooting

Please post questions to the .guide developer community.

<https://community.theta360.guide/>

Jesse Casman wants you in the theta360.guide community.  🌇

![join community](images/troubleshoot/jesse_join_community.png)

## Build failing due to unsupported iOS version

You can bring the minimum deployment target down to iOS 16.

![change minimum deployment](images/troubleshoot/change_ios_minimum_deployment.png)

Example of setting minimum deployment to iOS 16.

![set to 16](images/troubleshoot/minimum_deployment.png)

Unless you modify the code, you cannot set the iOS target to 15 or lower due to the use of PhotosPicker in ContentView.swift.

![photospicker](images/troubleshoot/photos_picker_requirement.png)

## physical device not synced with Xcode

in Xcode menu Window -> Devices and Simulators, right-click and then select Unpair devices.

![unpair device](images/troubleshoot/unpair_device.png)

Unplug physical device, plug it back in. It will take several minutes to sync.

![ipad sync](images/troubleshoot/ipad_sync.png)
