# WebCompat Go Faster add-on

This is the development repository for the Firefox WebCompat Go Faster add-on.

## Writing site patches, overrides and injections

Detailed information on our policies on writing overrides, as well as technical information, can be found in the [Mozilla Wiki](https://wiki.mozilla.org/Compatibility/Go_Faster_Addon/Override_Policies_and_Workflows).

## Build instructions

This guide assumes you've got a copy of `mozilla-central` checked out on your machine and you already have set up Node.js 5 or newer. The build script assumes your `mozilla-central` is located at `../fx-team` relative to inside the root folder. If not, please set the `EXPORT_MC_LOCATION` environment accordingly.

Running the extension without a built and set up `mozilla-central` is not possible at the moment.

If this is the first time you're working with this repository, install the dependencies with `npm install`.

### Exporting the sources to `mozilla-central`

1. Run `npm run jake export-mc` for Desktop or `npm run jake export-mc-android` for Android.
2. Find the exported files in your `mozilla-central` directory, ready to commit.

### Exporting the sources into Android Components

1. Make sure the `EXPORT_AC_LOCATION` environment variable is set to the root of your Android Components checkout.
2. Run `npm run jake export-ac`.
3. Find the exported files in your Android Components directory, ready to commit.

### Run the changed extension sources

#### Via `about:debugging`

If you want to debug this extension on recent Desktop versions, you can use `about:debugging`:

1. Open `about:debugging` in Firefox
2. Click the `Load Temporary Add-on...` button
3. Select `./src/manifest.json` and hit open.
4. Test!

#### Via `web-ext`

For Fennec, `about:debugging` is not an option. To test Fennec:

1. Run `npm start`
2. Test!

`npm start` calls [`web-ext`](https://github.com/mozilla/web-ext), check their documentation for available parameters, including debugging options.

### Building `webcompat.xpi`

1. Run `npm run jake export-xpi`.
2. Find the built `.xpi` inside the `build/` directory.

### Run the automated test suite

1. Run `npm run test`
2. Wait!

### Automatically check and adjust the code style

As `mozilla-central` is now mostly auto-formatted with prettier, and the config for that is really slim, this repo follows these guidelines. To automatically check and adjust the code style,

1. Run `npm run prettier`
2. Done.

## License

MPL.
