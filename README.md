# Issue #1583 repro vscode-js-debug

To run this example, you'll need to [setup your environment for React Native]( https://reactnative.dev/docs/environment-setup).

After that's done, you can start this example:

1. `$ yarn install`
2. `$ yarn expo run:ios`
3. Wait until the build is complete, and the simulator has opened.
4. Go to `http://localhost:8081/json/list`
5. Find the item with `title: "React Native Experimental (Improved Chrome Reloads)"`
6. Copy the `webSocketDebuggerUrl` property in [`.vscode/launch.json`](./.vscode/launch.json).
7. Run the debugger through vscode
8. Add a breakpoint to `App.js`, line 7
9. Press the button in the simulator
10. Expand the variable explorer (`closure 1` for example)
11. See the issue

## The underlying issue

It seems that `vscode-js-debug` expects `description` to be defined on the [`Runtime.RemoteObject`](https://chromedevtools.github.io/devtools-protocol/tot/Runtime/#type-RemoteObject). But, according to the spec, that's optional and results in the error encountered.
