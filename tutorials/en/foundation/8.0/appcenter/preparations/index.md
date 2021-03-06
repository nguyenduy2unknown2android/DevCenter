---
layout: tutorial
title: Preparations for using the mobile client
breadcrumb_title: Preparations
relevantTo: [ios,android,windows,javascript]
weight: 1
---
## Overview
To use the mobile client to install apps on mobile devices, you must either generate the app by using the provided Eclipse and Visual Studio projects or use the version of the client provided for Android, iOS, or Windows 8 Universal, directly.

#### Jump to

* [Importing and building the project (Android, iOS, Windows Phone)](#importing-and-building-the-project-android-ios-windows-phone)
* [Customizing features (for experts): Android, iOS, Windows Phone](#customizing-features-for-experts-android-ios-windows-phone)
* [Microsoft Windows 8: Building the project](#microsoft-windows-8-building-the-project)
* [Deploying the mobile client in Application Center](#deploying-the-mobile-client-in-application-center)

### Prerequisites for building the Application Center installer
The Application Center comes with an Android, an iOS, and Windows 8 Universal version of the client application that runs on the mobile device. This mobile application that supports installation of applications on your mobile device is called the mobile client. The mobile client is a MobileFirst mobile application.

The MobileFirst project **IBMAppCenter** contains the Android, the iOS, and the Windows 8 Universal versions of the client.

The Windows 8 Universal project is provided as a Visual Studio project located at **IBMApplicationCenterWindowsStore\AppCenterClientWindowsStore.csproj.**

### Prerequisites specific to the Android operating system
The Android version of the mobile client is included in the software delivery in the form of an Android application package (.apk) file. The **IBMApplicationCenter.apk** file is in the directory **ApplicationCenter/installer**. Push notifications are disabled. If you want to enable push notifications, you must rebuild the .apk file. See [Push notifications of application updates](../push-notifications) for more information about push notifications in the Application Center.

To build the Android version, you must have the latest version of the Android development tools.

### Prerequisites specific to Apple iOS operating system
The iOS version for iPad and iPhone is not delivered as a compiled application. The application must be created from the MobileFirst project named **IBMAppCenter**. This project is also delivered as part of the distribution in the **ApplicationCenter/installer** directory.

To build the iOS version, you must have the appropriate MobileFirst and Apple software. The version of MobileFirst Studio must be the same as the version of IBM MobileFirst Foundation Server on which this documentation is based. The Apple Xcode version is V6.1.

> **Note:** For V8.0.0, use MobileFirst Studio 7.1. You can download MobileFirst Studio from the [Downloads page]({{site.baseurl}}/downloads). Click the Previous MobileFirst Platform Foundation releases tab for the download link. For installation instructions, see [Installing MobileFirst Studio](https://www.ibm.com/support/knowledgecenter/SSHS8R_7.1.0/com.ibm.worklight.installconfig.doc/devenv/t_installing_ibm_worklight_studi.html) in the IBM  Knowledge Center for 7.1.

### Prerequisites specific to Microsoft Windows Phone operating system
The Windows Phone version of the mobile client is included as an unsigned Windows Phone application package (.xap) file in the software delivery. The **IBMApplicationCenterUnsigned.xap** file is in the **ApplicationCenter/installer** directory.

> **Important:** The unsigned .xap file cannot be used directly. You must sign it with your company certificate obtained from Symantec/Microsoft before you can install it on a device.

Optional: If necessary, you can also build the Windows Phone version from sources. For this purpose, you must have the latest version of Microsoft Visual Studio.

### Prerequisites specific to Microsoft Windows 8 operating system
The Windows 8 version of the mobile client is included as a .zip archive file. The **IBMApplicationCenterWindowsStore.zip** file contains an executable file (.exe) and its dependent Dynamic-Link Library (.dll) files. To use the content of this archive, you download the archive to a location on you local drive and run the executable file.

Optional: If necessary, you can also build the Windows 8 version from sources. For this purpose, you must have the latest version of Microsoft Visual Studio.

## Importing and building the project (Android, iOS, Windows Phone)
You must import the **IBMAppCenter** project into MobileFirst Studio and then build the project.

Application Center requires MobileFirst Studio for importing and building the IBMAppCenter project. MobileFirst Studio is not part of IBM MobileFirst Foundation, but if you purchased this product, you are entitled to the full cross-platform version of the product as well.

> **Note:** For V8.0.0, use MobileFirst Studio 7.1. You can download MobileFirst Studio from the [Downloads page]({{site.baseurl}}/downloads). Click the Previous MobileFirst Platform Foundation releases tab for the download link. For installation instructions, see [Installing MobileFirst Studio](https://www.ibm.com/support/knowledgecenter/SSHS8R_7.1.0/com.ibm.worklight.installconfig.doc/devenv/t_installing_ibm_worklight_studi.html) in the IBM  Knowledge Center for 7.1.

1. Select **File → Import**.
2. Select **General → Existing Project into Workspace**.
3. On the next page, select **Select root directory** and locate the root of the **IBMAppCenter** project.
4. Select **IBMAppCenter** project.
5. Select **Copy projects into workspace**. This selection creates a copy of the project in your workspace. On UNIX systems, the IBMAppCenter project is read only at the original location. so copying projects into workspace avoids problems with file permissions.
6. Click **Finish** to import the **IBMAppCenter** project into MobileFirst Studio.

Build the **IBMAppCenter** project. The MobileFirst project contains a single application named **AppCenter**. Right-click the application and select **Run as → Build All Environments**.

#### Android
MobileFirst Studio generates a native Android project in **IBMAppCenter/apps/AppCenter/android/native**. A native Android development tools (ADT) project is in the android/native folder. You can compile and sign this project by using the ADT tools. This project requires Android SDK level 16 to be installed, so that the resulting APK is compatible with all Android versions 2.3 and later. If you choose a higher level of the Android SDK when you build the project, the resulting APK will not be compatible with Android version 2.3.

See the [Android site for developers](https://developer.android.com/index.html) for more specific Android information that affects the mobile client application.

If you want to enable push notifications for application updates, you must first configure the Application Center client properties. See [Configuring push notifications for application updates for more information](../push-notifications).

#### iOS
MobileFirst Studio generates a native iOS project in **IBMAppCenter/apps/AppCenter/iphone/native**. The **IBMAppCenterAppCenterIphone.xcodeproj** file is in the iphone/native folder. This file is the Xcode project that you must compile and sign by using Xcode.

See [The Apple developer site](https://developer.apple.com/) to learn more about how to sign the iOS mobile client application. To sign an iOS application, you must change the Bundle Identifier of the application to a bundle identifier that can be used with the provisioning profile that you use. The value is defined in the Xcode project settings as **com.your\_internet\_domain\_name.appcenter**, where **your\_internet\_domain\_name** is the name of your internet domain.

If you want to enable push notifications for application updates, you must first configure the Application Center client properties. See [Configuring push notifications for application updates for more information](../push-notifications).

#### Windows Phone 8
MobileFirst Studio generates a native Windows Phone 8 project in **IBMAppCenter/apps/AppCenter/windowsphone8/native**. The **AppCenter.csproj** file is in the windowsphone8/native folder. This file is the Visual Studio project that you must compile by using Visual Studio and the Windows Phone 8.0 SDK.

The application is built with the Windows Phone 8.0 SDK so that it can run on Windows Phone 8.0 and 8.1 devices. It is not built with the Windows Phone 8.1 SDK, because the result would not run on earlier Windows Phone 8.0 devices.

The installation of Visual Studio 2013 enables you to select the installation of the Windows Phone 8.0 SDK in addition to the 8.1 SDK. The Windows Phone 8.0 SDK is also available from [Windows Phone SDK Archives](https://dev.windows.com/en-us/develop/download-phone-sdk).

See [Windows Phone Dev Center](http://dev.windowsphone.com/en-us) to learn more about how to build and sign the Windows Phone mobile client application.

## Customizing features (for experts): Android, iOS, Windows Phone)
You can customize features by editing a central property file and manipulating some other resources.

To customize features: several features are controlled by a central property file called **config.json** in the directory **IBMAppCenter/apps/AppCenter/common/js/appcenter/**. If you want to change the default application behavior, you can adapt this property file before you build the project.

This file contains the properties shown in the following table.

| Property | Description |
|----------|-------------|
| url | The hardcoded address of the Application Center server. If this property is set, the address fields of the Login view are not displayed. | 
| defaultPort | If the url property is null, this property prefills the port field of the Login view on a phone. This is a default value; the field can be edited by the user. |
| defaultContext | If the url property is null, this property prefills the context field of the Login view on a phone. This is a default value; the field can be edited by the user. | 
| ssl | The default value of the SSL switch of the Login view. |
| allowDowngrade | This property indicates whether installation of older versions is authorized or not; an older version can be installed only if the operating system and version permit downgrade. |
| showPreviousVersions | This property indicates whether the device user can show the details of all the versions of applications or only details of the latest version. | 
| showInternalVersion | This property indicates whether the internal version is shown or not. If the value is false, the internal version is shown only if no commercial version is set. | 
| listItemRenderer | This property can have one of these values:<ul><li>full, the default value; the application lists show application name, rating, and latest version.</li><li>simple: the application lists show the application name only.</li></ul> |
| listAverageRating | This property can have one of these values:<ul><li>latestVersion: the application lists show the average rating of the latest version of the application.</li><li>allVersions: the application lists show the average rating of all versions of the application.</li></ul> | 
| requestTimeout | This property indicates the timeout in milliseconds for requests to the Application Center server. | 
| gcmProjectId | The Google API project ID (project name = com.ibm.appcenter), which is required for Android push notifications; for example, 123456789012. | 
| allowAppLinkReview | This property indicates whether local reviews of applications from external application stores can be registered and browsed in the Application Center. These local reviews are not visible in the external application store. These reviews are stored in the Application Center server. | 

### Other resources
Other resources that are available are application icons, application name, splash screen images, icons, and translatable resources of the application.

#### Application icons
Android: The file named icon.png in the **IBMAppCenter/apps/AppCenter/android/native/res/drawabledensity** directories; one directory exists for each density.

iOS: Files named iconsize.png in the **IBMAppCenter/apps/AppCenter/iphone/native/Resources** directory.

Windows Phone: Files named ApplicationIcon.png, IconicTileSmallIcon.png, and IconicTileMediumIcon.png in the **IBMAppCenter/apps/AppCenter/windowsphone8/native** directory.

#### Application name
Android: Edit the app_name property in the **IBMAppCenter/apps/AppCenter/android/native/res/values/strings.xml** file.

iOS: Edit the CFBundleDisplayName key in the **IBMAppCenter/apps/AppCenter/iphone/native/IBMAppCenterAppCenterIphone-Info.plist** file.

Windows Phone: Edit the Title attribute of the App entry in the **IBMAppCenter/apps/AppCenter/windowsphone8/native/Properties/WMAppManifest.xml** file.

#### Splash screen images
Android: Edit the file named splashimage.9.png in the **IBMAppCenter/apps/AppCenter/android/native/res/drawable/density** directories; one directory exists for each density. This file is a patch 9 image.

iOS: Files named Default-size.png in the **IBMAppCenter/apps/AppCenter/iphone/native/Resources** directory.

Hybrid splash screen during auto login: **/IBMAppCenter/apps/AppCenter/common/js/idx/mobile/themes/common/idx/Launch.css**

Windows Phone: Edit the file named SplashScreenImage.png in the **IBMAppCenter/apps/AppCenter/windowsphone8/native** directory.

#### Icons (buttons, stars, and similar objects) of the application
**IBMAppCenter/apps/AppCenter/common/css/images**.

#### Translatable resources of the application
**IBMAppCenter/apps/AppCenter/common/js/appcenter/nls/common.js**.

## Microsoft Windows 8: Building the project
Build the Application Center client project for Windows 8 in Microsoft Visual Studio 2013.

You must build the client project in Microsoft Visual Studio 2013 before you can distribute it.

Building the project is a prerequisite to distributing it to your users, but the Windows 8 mobile client is not intended to be deployed on Application Center for later distribution.

To build the Windows 8 project:

1. Open the Visual Studio project file called **IBMApplicationCenterWindowsStore\AppCenterClientWindowsStore.csproj** in Microsoft Visual Studio 2013.
2. Perform a full build of the application.

To distribute the mobile client to your Application Center users, you can later generate an installer that will install the generated executable (.exe) file and its dependent Dynamic-Link Library (.dll) files. Alternatively, you can provide these files without including them in an installer.

## Deploying the mobile client in Application Center
Deploy the different versions of the client application to Application Center.

The Windows 8 mobile client is not intended to be deployed in Application Center for later distribution. You can choose to distribute the Windows 8 mobile client either by providing users with the client .exe executable file and dynamic link library .dll files directly packaged in an archive, or by creating an executable installer for the Windows 8 mobile client.

The Android, iOS, and Windows Phone versions of the mobile client must be deployed to the Application Center. To do so, you must upload the Android application package (.apk) files, iOS application (.ipa) files, and Windows Phone application (.xap) files, Web directory archive (.zip) files to the Application Center.

Follow the steps described in [Adding a mobile application](../appcenter-console/#adding-a-mobile-application) to add the mobile client application for Android, iOS, and Windows Phone. Make sure that you select the Installer application property to indicate that the application is an installer. Selecting this property enables mobile device users to install the mobile client application easily over the air. To install the mobile client, see the related task that corresponds to the version of the mobile client app determined by the operating system.

