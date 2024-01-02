# DriveWorks Live - Integration Theme Example - Fullscreen Form
### Release: 21.1
#### Minimum DriveWorks Version: 18.0

A distributable template that renders a predefined Project fullscreen - controlled via a config file.

---

Please note: DriveWorks are not accepting pull requests for this example.  
Join our [online community](https://my.driveworks.co.uk) for discussion, resources and to suggest other examples.

---

### Overview:
- Dynamically injects the DriveWorks Live Client library script using the configured server url (see `config.js`).
    - Provides an example of loading from a static URL, if preferred.
- Connects to the DriveWorks Live Integration Theme API.
- Renders a DriveWorks Form fullscreen - with no other UI.
- Uses very simple HTML/CSS/JS - which is freely modifiable and expandable.
- Loads an external configuration file (`config.js`).
    - These options can be stored inline, if preferred.
- Displays an optional loading state - to avoid an initial blank screen.

### To use:
1. Clone this repository, or download as a `.zip` file.

2. Enter your Integration Theme details into `config.js`.
    * `serverUrl` - The URL that hosts your Integration Theme, including any ports.
    * `groupAlias` - The public alias created for the Group containing the Project to render - as configured in `DriveWorksConfigUser.xml`.
        * This *must* be specified for each Group you wish to use.
        * This allows you to mask the true Group name publicly, if desired.
        * See [Integration Theme Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings) for additional guidance.
    * `projectName` - The name of the Project to render.
    * `specificationPingInterval` - [optional] The interval at which to 'ping' the server automatically.
        * This ensures a session is kept alive during inactivity, if desired.

3. Ensure that the Integration Theme server is running, using any of the available methods (e.g. Personal Web Edition, DriveWorks Live, IIS).
    * For more information, see [Selecting the Integration Theme](https://docs.driveworkspro.com/Topic/IntegrationThemeSelect).

4. Host the example locally or on a remote server.
    * Ensure `<corsOrigins>` in `DriveWorksConfigUser.xml` permits requests from this location.
    See [Integration Theme Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings) for additional guidance.

### Troubleshooting:

If encountering any issues, please check the browser's console for error messages (F12).  

If you are unable to use the dynamic library loading demonstrated in this example:
1. In `index.html`, uncomment "Option A" & replace "YOUR-DRIVEWORKS-LIVE-SERVER-URL.COM" with the URL of your own DriveWorks Live server that is serving `DriveWorksLiveIntegrationClient.min.js` - including any ports.
    * This should be the URL that hosts the Integration Theme, and serves it's landing page.
    * To check that this URL is correct, attempt to load `DriveWorksLiveIntegrationClient.min.js` in a browser. It should return a minified code library.
2. Remove the "Option B" `<script>` tag.

### Potential Issues:

* When serving this example for a domain different to your DriveWorks Live server, e.g. api.my-site.com from www.company.com, 'SameSite' cookie warnings may be thrown when the Client SDK attempts to store the current session id in a cookie.
    * This appears as "Error: 401 Unauthorized" in the browser console, even with the correct configuration set.
    * To resolve:
        * Ensure you are running DriveWorks 18.2 or above.
        * Ensure HTTPS is enabled in DriveWorks Live's settings.
        * Ensure a valid SSL certificate has been configured via `DriveWorksConfigUser.xml`.
        * Ensure if using an incognito/private window, third-party cookies are not blocked (see browser settings).
        * See [Integration Theme Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings) for additional guidance.

---

This source code has been made available to demonstrate how you can integrate with DriveWorks using the DriveWorks Live API.
This code is provided under the MIT license. For more details, see the included LICENSE file.

The example requires that you have the latest DriveWorks Live SDK installed, operational and remotely accessible.
