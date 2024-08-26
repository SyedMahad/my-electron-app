# Electron JS Sample Project

This is a basic Electron JS project that demonstrates the use of the Main Process, Renderer Process, and Preload Script. The project displays basic information about the environment and includes a simple ping-pong communication between the Renderer and Main Process.

## Project Structure

- **main.js**: Contains the Main Process logic, including window creation and handling IPC (Inter-Process Communication) events.
- **renderer.js**: Handles the Renderer Process, responsible for rendering the UI and interacting with the user.
- **preload.js**: Runs in the context of the Renderer Process but with Node.js integration disabled. It securely exposes selective Node.js functionality to the Renderer Process via `contextBridge`.
- **index.html**: The HTML file rendered in the window, displaying basic content.

## Files

### `main.js`

- Creates the main application window with an 800x600 resolution.
- Handles application life cycle events like window creation and closing.
- Uses `ipcMain.handle()` to respond to an IPC call from the Renderer Process.

### `renderer.js`

- Contains JavaScript that runs in the Renderer Process.
- Retrieves version information for Node.js, Chrome, and Electron via the `preload.js` script.
- Sends an IPC message to the Main Process and logs the response ("pong") to the console.

### `preload.js`

- Uses `contextBridge` to safely expose Node.js versions and a custom `ping` function to the Renderer Process.
- Ensures that Node.js functionality is securely accessed from the Renderer Process.

### `index.html`

- A simple HTML file that serves as the UI.
- Displays a welcome message and includes a placeholder (`<p id="info"></p>`) for displaying environment information.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) installed on your machine.

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/electron-sample.git
    ```

1. Navigate to the project directory:
    ```bash
    cd electron-sample
    ```

1. Install the dependencies:
    ```bash
    npm install
    ```

### Running the Application

1. Start the Electron application:
    ```bash
    npm start
    ```

1. A window should appear displaying a message: "Hello from Electron renderer!" and information about the versions of Chrome, Node.js, and Electron.

## Project Features

- **Main Process:**
    - Manages the application window.
    - Handles IPC events and provides responses to the Renderer Process.

- **Renderer Process:**
    - Interacts with the DOM and logs messages from the Main Process.

- **Preload Script:**
    - Securely exposes limited Node.js API to the Renderer Process.

## License

This project is licensed under the ISC License. See the [LICENSE](./LICENSE) file for details.

## Contributing

Feel free to submit issues or pull requests if you'd like to contribute to this project.

