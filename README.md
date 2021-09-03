# Delete-Assets

## Description
Basic app created to show the usage of `deleteRemovedAssets`.

## Steps to recreate
1) Make sure you have the most recent version of the RVM (6.6.0.1 as of 9/3/2021)
2) Host app assets in your localhost
   a) Make a zip containing anything and put it in your root directory of your local host. This has been done in this example.
3) Add the following block of code to your manifest to download the assest:
   ```
   "appAssets": [
    {
      "src": "http://localhost:8001/ziptest1.zip",
      "alias": "ziptest1",
      "version": "0.0.0.1"
    }
    ],
  
   ```
   
    a) Make sure you run your server for the zip file. It needs to be in a different server than the application itself
    b) Add this code above the `deleteRemovedAssets` key. Your manifest should look like this:
    
    ```
    {
    "licenseKey": "contract_identifier",
    "runtime": {
        "arguments": "--v=1 --no-sandbox --ignore-certificate-errors",
        "version": "20.91.62.4"
    },
    "startup_app": {
        "name": "Assests",
        "uuid": "33aa9062-9eb0-4875-b819-c90f38ef03eb",
        "url": "http://localhost:4000/index.html",
        "autoShow": true
    },
    "appAssets": [
    {
      "src": "http://localhost:8001/ziptest1.zip",
      "alias": "ziptest1",
      "version": "0.0.0.1"
    }
    ],
    "deleteRemovedAssets": true
    }
    ```
    
 4) Launch your app. This example uses the OpenFin CLI to launch this app. If you don't have it, create a server.js file
 5) Close the app
 6) Verify assets were downloaded in `%localappdata%/openfin/apps/{yourapp}/assets`
 7) Go to your app config and remove the app asset code
 8) Launch the app again
 9) Verify in the same location in step 6 that the app assets were deleted
