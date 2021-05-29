---
creation date: 2021-05-26 22:46
modification date: Wednesday 26th May 2021 22:46:22
tags: ["#dev", "#mobile-devt", "#linux"]
author: Jimmy Briggs
---

# Building React-Native App in WSL2
Install, build and debug a react native app in WSL2 (Windows Subsystem for Linux) and Ubuntu.

* [Install tools in Windows](#install-tools-in-windows)
* [Install tools in WSL2](#install-tools-in-wsl2)
* [Create android virtual device in Windows](#create-android-virtual-device-in-windows)
* [Start android virtual device in Windows](#start-android-virtual-device-in-windows)
* [Start adb server in Windows](#start-adb-server-in-windows)
* [Enable access to adb server from WSL2](#enable-access-to-adb-server-from-wsl2)
* [Enable access to metro bundler from Windows](#enable-access-to-metro-bundler-from-windows)
* [Create react native app in WSL2](#create-react-native-app-in-wsl2)
* [Build app in WSL2](#build-app-in-wsl2)
* [Debug app in Visual Studio Code from WSL2](#debug-app-in-visual-studio-code-from-wsl2)

## Install tools in Windows

* Install WSL2 and Ubuntu, see [here](https://docs.microsoft.com/de-de/windows/wsl/wsl2-install)
* Install Android Studion, see [here](https://developer.android.com/studio)
* Install Viusal Studio Code, see [here](https://code.visualstudio.com/)

## Install tools in WSL2

* Install java-8-openjdk in WSL2 (*sudo apt-get install openjdk-8-jre*)
* Install Android SDK cmdline tools in WSL2, see [here](https://gist.github.com/jjvillavicencio/18feb09f0e93e017a861678bc638dcb0) and adjust directory structure, see [here](https://stackoverflow.com/questions/60440509/android-command-line-tools-sdkmanager-always-shows-warning-could-not-create-se)
* Install nodejs in WSL2, see [here](https://github.com/nodesource/distributions#debinstall)

Set environment variables in .profile or .bash_profile

```
export ANDROID_HOME=/home/xxx/Android/cmdline-tools/latest
export ANDROID_SDK_ROOT=/home/xxx/Android

PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools
PATH=$PATH:$ANDROID_HOME/bin

export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```

## Create android virtual device in Windows

Create a virtual device (e.g. Nexus_5X_API_29) in windows with Android Virtual Device Manager from Android Studio.

## Start android virtual device in Windows

Start Android virtual device (e.g. Nexus_5X_API_29) in windows

```
"C:\Program Files (x86)\Android\android-sdk\emulator\emulator.exe" -avd Nexus_5X_API_29
```

## Start adb server in Windows

```
adb kill-server
adb -a nodaemon server start
```

Change firewall rule for **adb.exe** on first usage in Defender Popup or
with **Windows Defender Firewall** allowing access for the public profile, because 
the **vEthernet (Wsl)** adapter belongs to the public profile

## Enable access to adb server from WSL2

Set environment variable to access adb server, **WSL_HOST** is ip of **vEthernet (WSL)** interface in windows

```
export WSL_HOST=$(tail -1 /etc/resolv.conf | cut -d' ' -f2)
export ADB_SERVER_SOCKET=tcp:$WSL_HOST:5037
```

Somtimes adb crashes using the environment variable config. One solution is to use socat (thanks to @tuanna1601).

Unset the environment variable if necessary.
```
unset ADB_SERVER_SOCKET
```

Install socat (eg. sudo apt-get install socat). Socat relays the requests from wsl2 to windows using the following command:

```
socat -d -d TCP-LISTEN:5037,reuseaddr,fork TCP:$(cat /etc/resolv.conf | tail -n1 | cut -d " " -f 2):5037
```

## Enable access to metro bundler from Windows

The metro bundler is running in WSL2, listening on port 8081. Windows 10 version 2004 brings network forwarding from
WSL2 to Windows. So  the app can connect to the metro bundler from the emulator via Windows localhost.

Sometimes there are problems with the network forwarding. A work around is to use the following script. 

**WSL_CLIENT** is ip of WSL2.

```
iex "netsh interface portproxy delete v4tov4 listenport=8081 listenaddress=127.0.0.1" | out-null;
$WSL_CLIENT = bash.exe -c "ifconfig eth0 | grep 'inet '";
$WSL_CLIENT -match '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}';
$WSL_CLIENT = $matches[0];
iex "netsh interface portproxy add v4tov4 listenport=8081 listenaddress=127.0.0.1 connectport=8081 connectaddress=$WSL_CLIENT"
```

## Create react native app in WSL2

```
npx react-native init AwesomeProject
```

## Build app in WSL2

Add paraameter in file proguard-rules<span>.</span>pro to ignore okhttp3 warnings
```
-dontwarn okhttp3.internal.platform.*
```

Start metro JavaScript bundler and bind to an ipv4 address to enable port forwarding to windows
```
npx react-native start --host 127.0.0.1
```

Build app, set device as parameter deviceId from result of **adb devices**

```
npx react-native run-android --variant=debug --deviceId emulator-5554
```

## Debug app in Visual Studio Code from WSL2 

Start vs code in WSL2

```
code .
```
and install extensions for VS Code

* Remote - WSL
* React Native Tools

VS Code UI runs in windows and the VS Code Server runs in WSL2, see [here](https://code.visualstudio.com/docs/remote/wsl)

Add a launch configuration in file launch.json with specified type and target

```
"type": "reactnative",
"target": "emulator-5554"
```

Start debugging.
***
Links: [[Windows/WSL/WSL]] 
Source: [Building a react native app in WSL2 (github.com)](https://gist.github.com/bergmannjg/461958db03c6ae41a66d264ae6504ade)

