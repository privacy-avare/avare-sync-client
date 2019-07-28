# Avare-Sync-Client

client application of the Avare Sync setup working together with a Server setup according to the Avare-Sync-Server repo (https://github.com/privacy-avare/avare-sync-server)

## Setup

1. Fork the repository into your github account.
2. Change the server IP address in ServerConfig.js to the IP you set up the Avare-Sync-Server to.
3. Add and commit all changes

## Installation (Android)

1. Add the module as a dependency in your package.json

```sh
...
"dependencies": {
    ...
    "avare-sync-client": "github:<YOUR GITHUB ACCOUNT NAME>/avare-sync-client",
    ...
}
```

2. Run npm install to bring it along from your local npm repository.

```sh
npm install
```

## Changes

If you want to change something in the Setup (e.g. the Server IP address) you need to delete and reinstall the module.
To do so run

```sh
rm -rf node_modules package-lock.json && npm install
```

This will delete all installed modules and reinstall them.


## Usage

After setting up the client and installing it, here is a quick overview on how to use it and which methods are available.

### Example

```sh
import { setProfile, loadPreferences, setTime, setPreferences, uploadProfile, getProfile } from 'avare-sync-client'

...

// create new profile
this.props.dispatch(getProfile());

...

//upload the profile to the server
this.props.dispatch(uploadProfile(<profileID returned from getProfile()>, <timestamp of the last change on data>, <String with data to upload>));

...

//Force download of the data string stored on the server
this.props.dispatch(loadPreferences(<profileID returned from getProfile()>, <current time>)))

...
```

### Methods

-   `setTime(time)`
-   `setProfile(profile)`
-   `setPreferences(preferences, time)`
-   `getProfile()`
    This method sends a request to the server to create a new profile and delivers a unique profileID.
-   `loadPreferences(profile, time)`
    This method delivers the content saved to a unique profileID
-   `uploadProfile(id, clientProfileChange, preferences)`
    This method uploads the content(preferences) of a unique profileID to the server