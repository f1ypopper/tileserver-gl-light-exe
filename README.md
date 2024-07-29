## Process
`tileserver-gl-light` requires node for it to run. This project utilizes `Electron` to bootstrap `tileserver-gl-light` into a single executable appication.

The `tileserver-gl-light` entry file `main.js` has functions defined for starting the server namely `startWithInputFile`.

A callback function was defined for when the electron app is ready. This callback function is responsible for starting the server from the electron process.
```js
app.whenReady().then(async () => {
  console.log("starting server...");
  const file_path = opts["file"];
  //this function is predefined in tileserver src we just create a wrapper and call it.
  await startWithInputFile(file_path); 
});
```
Essentially this project creates an `Electron` wrapper around `tileserver-gl-light` and uses `electron-builder` to build single exe app.

## Build
> Make sure that [node-gyp](https://github.com/nodejs/node-gyp) is installed for Windows
- Install yarn: `npm i -g yarn`
- Install dependencies: `yarn install`
- Run the electron-builder: `node ./node_modules/electron-builder/cli.js`
- Check the newly created `/dist` dir for `.exe`