The `root` directory is a typical multi-page app of Vite with Svelte JavaScript project.

The `xcode` directory is the root of the Xcode project where the Safari extension app is built.

For other directory structure instructions, please refer to [structure.md](structure.md).

# Environment
- [`Node.js`](https://nodejs.org/)
- [`Xcode`](https://geo.itunes.apple.com/app/id497799835)

# Dev
- `npm install`[^1]
- `npm run dev`[^1]

# Build
- `npm run build`[^1]
- `cd ./xcode`
- `xcodebuild`[^1][^2] or build with `Xcode` App

[^1]: These commands can also be executed directly through the VSCode Run Task. Please refer to: [/.vscode/tasks.json](../.vscode/tasks.json)
[^2]: Local setup may be required. Please refer to: [Building from the Command Line with Xcode FAQ](https://developer.apple.com/library/archive/technotes/tn2339/_index.html)

# Xcode

### Configurations
The Xcode project contains two configurations, which have independent `xcconfig` configuration files, and can run on your local at the same time without conflicts.

- `Debug`: No developer account is required, that is `Sign to Run Locally` by default, which will speed up the build during development. This is convenient for developers without an account, and contributors who only need to do simple local debugging.

- `Release`: A developer account is required, which means it can be used for distribution as well as running on real iOS/iPadOS devices. You will need to override your developer account information in `xcconfig` to complete the build.

### xcconfig
All `xcconfig` files are in the [`/xcode/xcconfig/`](../xcode/xcconfig) directory. Each `.xcconfig` file can be overridden by `.dev.xcconfig` in the same path, they will be ignored by `git`, so you can override any build settings locally.

For example, you can create an `Userscripts-Release.dev.xcconfig` file to override [`Userscripts-Release.xcconfig`](../xcode/xcconfig/Userscripts-Release.xcconfig) and fill in your own developer account information there:

`Userscripts-Release.dev.xcconfig`
```
DEVELOPMENT_TEAM = XXXXXXXXXX
```

Another example, if you want `Debug` builds to be also signed, so instead of enabling `Allow Unsigned Extensions` every time in Safari, you can create: 

`Userscripts-Debug.dev.xcconfig`
```
CODE_SIGN_IDENTITY = Apple Development
DEVELOPMENT_TEAM = XXXXXXXXXX
```

Note that all existing `.xcconfig` files already include `.dev.xcconfig` files of the same name, so they will be applied automatically once you create them. You only need to fill in the setting items that need to be overridden or added.

# Contribute
[Contributing guide](contributing.md)

# About
[Userscripts](https://github.com/quoid/userscripts) @ 2018-2023