

CRXServe

CRXServe is a self-hosted proxy server designed for independent browser extension developers who want to host and serve the latest .crx files directly from GitHub releases. This solution enables developers to bypass the need for the Chrome Web Store or Microsoft Edge Add-ons by providing their own custom "webstore-like" experience. It allows users to easily download and install the latest version of extensions directly from a hosted server.

Features

Self-hosted solution for independent extension developers.

Serve the latest .crx files directly from GitHub releases.

Provides easy-to-follow installation instructions for users.

Fully configurable to host extensions for multiple projects.

Secure and simple setup to facilitate local or remote hosting.


Installation

Follow the steps below to set up CRXServe on your server or local machine:

1. Clone this repository

git clone https://github.com/yourusername/crxserve.git

2. Install dependencies

cd crxserve
npm install

3. Update GitHub URLs in the code

Open the index.js file and replace the GITHUB_CRX_URL and GITHUB_UPDATE_URL with the URL of your GitHub extension release.

Example:

const GITHUB_CRX_URL = 'https://yourusername.github.io/your-repository/releases/latest/download/Linkumori.crx';
const GITHUB_UPDATE_URL = 'https://yourusername.github.io/your-repository/releases/latest/download/updates.xml';

4. Start the server

npm start

The server will run on port 3000 by default (or any other port you specify in the code).

5. Access the server

Navigate to http://localhost:3000/ or your hosting URL to access the download page for your extension.

Installation Instructions for Users

After the server is running, users can follow these steps to install the extension:

1. Run the following commands in PowerShell as Administrator:

For Chrome:

reg add HKLM\SOFTWARE\Policies\Google\Chrome\ExtensionInstallAllowlist /v 1 /t REG_SZ /d kcpfnbjlimolkcjllfooaipdpdjmjigg /f
reg add HKLM\SOFTWARE\Policies\Google\Chrome\ExtensionInstallSources /v 1 /t REG_SZ /d https://yourdomain.com/* /f

For Edge:

reg add HKLM:\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallAllowlist /v 1 /t REG_SZ /d kcpfnbjlimolkcjllfooaipdpdjmjigg /f
reg add HKLM:\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallSources /v 1 /t REG_SZ /d https://yourdomain.com/* /f


Replace https://yourdomain.com/* with your actual domain or local server URL.


2. Restart the browser.


3. Visit http://localhost:3000/ (or your specified URL) to download the extension .crx file.


4. Go to chrome://extensions or edge://extensions.


5. Enable Developer Mode.


6. Drag and drop the downloaded .crx file into the extensions page to install the extension.



How It Works

Extension .crx file: The server fetches the latest .crx file from your GitHub release and serves it when users visit the /extension.crx endpoint.

GitHub releases: Simply upload your extension .crx file to your GitHub repository releases, and CRXServe will always fetch the latest version for you.


Contributing

Feel free to fork the project, submit issues, or make pull requests. Contributions and suggestions for improvements are always welcome.

License

This project is licensed under the Apache License 2.0. See the LICENSE file for more details.


---


