MeetAtTheShow Mobile
======================
Mobile app to interact with [Meet At The Show](https://meetattheshow.com).

### Table of Contents
1. [Overview](#overview)
1. [Getting Started](#getting-started)
  1. [Install](#install)
  1. [Configure VS Code](#configure-vs-code)

### Overview

The app is built on top of [`React Native`](https://facebook.github.io/react-native/).  [`Redux`](http://redux.js.org/) is used for state management of the app.  [`Code Push`](http://microsoft.github.io/code-push/)
is used for deployment.  Unit Tests are configured to use [`Jest`](https://github.com/facebook/jest).

## Getting Started
### Install
  Install node, ideviceinstaller, and watchman:

```bash
$ brew update
$ brew install node
$ brew install ideviceinstaller
$ brew install watchman
```

  Install React Native CLI:

```bash
npm install -g react-native-cli
```

  Install [Code Push](http://microsoft.github.io/code-push/)

```bash
npm install -g code-push-cli
```

### Configure CodePush
Register using your GitHub account:
```bash
code-push Register
```

Register App with CodePush:
```bash
code-push app add <appName>
```

Install Plugin:
```bash
react-native link react-native-code-push
```

Add an entry to the `Info.plist` called `CodePushDeploymentKey` containing the deployment key given by CodePush.

After making changes to code, release an app update:
```bash
code-push release-react <appName> ios
```

### Configure VS Code

1.  Install [Editor Config for VSCode](https://github.com/editorconfig/editorconfig-vscode) extention for VS Code.
2.  Install the [React Native Tools](https://marketplace.visualstudio.com/items?itemName=vsmobile.vscode-react-native) extension for VS Code.
3.  Click on the Debug Icon ![Debug Icon](https://github.com/Microsoft/vscode-react-native/raw/master/images/debug-view-icon.png) and select React Native as the Debug Environment.
4.  If wanted, use the following launch.json in your .vscode folder to setup iPad Air and Device Debugging:
    1. The Debug iOS Simulator target can be changed to other devices or new configuration objects created for them if needed

```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Android",
      "program": "${workspaceRoot}/.vscode/launchReactNative.js",
      "type": "reactnative",
      "request": "launch",
      "platform": "android",
      "internalDebuggerPort": 9090,
      "sourceMaps": true,
      "outDir": "${workspaceRoot}/.vscode/.react"
    }, {
      "name": "Debug iOS Simulator",
      "program": "${workspaceRoot}/.vscode/launchReactNative.js",
      "type": "reactnative",
      "request": "launch",
      "platform": "ios",
      "target": "iPad Air",
      "internalDebuggerPort": 9090,
      "sourceMaps": true,
      "outDir": "${workspaceRoot}/.vscode/.react"
    }, {
      "name": "Debug iOS Device",
      "program": "${workspaceRoot}/.vscode/launchReactNative.js",
      "type": "reactnative",
      "request": "launch",
      "platform": "ios",
      "target": "device",
      "internalDebuggerPort": 9090,
      "sourceMaps": true,
      "outDir": "${workspaceRoot}/.vscode/.react"
    }
  ]
}
```
