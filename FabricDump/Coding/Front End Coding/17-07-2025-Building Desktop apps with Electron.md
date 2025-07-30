This video provides a practical guide on building cross-platform desktop applications for Windows, Mac, and Linux using familiar web technologies like **React** and **Electron**. It walks through the process of setting up an Electron app from scratch with React and demonstrates how Electron interacts with the native operating system by building a simple file explorer.

### Building Desktop Apps with React and Electron: A Practical Guide

**[00:00:00] Introduction and Purpose**
The video introduces the concept of building desktop applications with the same technology as web applications (React), highlighting benefits such as **reduced development time** and faster feature delivery. The tutorial focuses on creating a simple file explorer that allows users to view file sizes, navigate directories, and perform basic searches. The full source code is available in the description.

**[00:00:30] Setting Up an Electron and React Project**
While pre-configured templates exist, the video opts for a **from-scratch setup** using `create-react-app` to provide a deeper understanding of React and Electron integration.

*   **[00:00:45] Installing Dependencies:** Key dependencies include `electron`, `concurrently` (to run React and Electron simultaneously), `wait-on` (to ensure React is ready before Electron starts), and `cross-env` (for setting environment variables).
*   **[00:01:00] Configuring `package.json` Scripts:**
    *   `serv`: Uses `concurrently` to spin up React and Electron processes, setting `BROWSER=none` with `cross-env` to prevent React from opening in a browser.
    *   `electron`: Uses `wait-on` to ensure React (on port 3000) is running before launching Electron.
    *   `build`: Left blank initially, to be configured later for production builds.
*   **[00:01:30] Electron `main.js` Setup:**
    *   A `main.js` file (in the `public` folder) is created as Electron's entry point.
    *   It uses Electron's `app` object and its event-based API to hook into application lifecycle events.
    *   On the `ready` event, a `BrowserWindow` is created to display the React app's URL (localhost:3000).
    *   Additional listeners are added for custom logic specific to Mac OS.
*   **[00:02:00] Inter-Process Communication (IPC) and `@electron/remote`:**
    *   **IPC** is crucial for allowing the React (renderer) process to trigger events and access native operations in the Electron (main) process.
    *   The `@electron/remote` library is installed and initialized in `main.js`, and its module is enabled in the `BrowserWindow`. This allows React components to run functions in the background (main) process directly.
*   **[00:02:30] UI Setup:**
    *   **Bootstrap 5** is installed for UI styling, and its CSS is imported into the React `App.js` file.
    *   Initial React template files are cleared for the file explorer development.

**[00:02:45] Building the File Explorer Application**
The core logic for the file explorer is implemented within the React application.

*   **[00:03:00] Accessing Node.js Modules (`fs`, `path`):**
    *   The `fs` (file system) and `path` Node.js modules are used for reading files and handling path manipulations.
    *   **Crucially, `nodeIntegration: true` must be enabled** in the `BrowserWindow` options in `main.js` to allow direct access to these modules from the React renderer process via `window.require()`.
*   **[00:03:30] Getting Current Path and Files:**
    *   A React state `path` is created to track the user's current directory, defaulting to the Electron app's path, retrieved using `app.getAppPath()` from `@electron/remote`.
    *   `fs.readdirSync()` is used to get file names in a given path.
    *   `fs.statSync()` is used to determine if an item is a directory and get file sizes. A helper function converts byte sizes to a human-readable format.
    *   Files are sorted (directories first, then alphabetically).
    *   The expensive file reading/sorting operation is wrapped in **`useMemo`** to optimize performance, only re-running when the `path` changes.
*   **[00:04:15] Navigation and Search Functionality:**
    *   `openFolder` function: Updates the `path` state to navigate into a selected directory.
    *   `goBack` function: Uses `path` module functions to navigate to the parent directory.
    *   A `searchString` state variable is added to filter files based on their name (starts with the search string).
*   **[00:04:45] `FilesView` Component:**
    *   This component accepts an array of files and `onOpen`, `onBack` callbacks as props.
    *   It renders a table displaying file names, sizes, and appropriate folder/file icons.
    *   Clicking a folder triggers `onOpen`, and a "back" row triggers `onBack`.

**[00:05:15] Building for Production**
The final step is to package the application for distribution across different operating systems.

*   **[00:05:30] Installing `electron-builder` and `electron-is-dev`:**
    *   `electron-builder` is used for packaging the application.
    *   `electron-is-dev` is used in `main.js` to check if the app is running in development mode, allowing it to load from localhost or the compiled production code accordingly.
*   **[00:05:45] `package.json` Build Configuration:**
    *   A `build` section is added to `package.json` to define the app ID and files to be included in the build.
*   **[00:06:00] Build Command and Cross-Platform Caveats:**
    *   The `build` script in `package.json` is updated to first build the React application (`react-scripts build`) and then use `electron-builder` to package the Electron app.
    *   The main entry point in `package.json` is updated to point to the compiled code in the `build` directory instead of `public`.
    *   **Important Caveat:** Typically, you need to run the build command on the operating system you wish to build for (e.g., build Windows executable on Windows). Build pipelines can help manage cross-platform builds.
    *   Running `yarn electron build` will create an executable file (e.g., `.exe` on Windows) in the `dist` folder.

**[00:06:30] Conclusion**
The video successfully demonstrates how to build a functional file explorer using React and Electron, from initial setup to production deployment. It emphasizes the power of using web technologies for desktop application development and encourages viewers to explore the provided source code and join the community Discord.