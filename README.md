# CodeForge C

A static, browser-first C workspace. Open `index.html` from a web host or serve the `outputs` directory over HTTP. The editor loads CodeMirror from a CDN; if it is unavailable, the source editor falls back to a plain textarea.

## Compiler

The app sends the active C file, other project files, and pre-submitted stdin to Wandbox (`https://wandbox.org/api/compile.json`). Wandbox compiles and runs each submission in its hosted environment. Source code and stdin leave the browser and are sent to Wandbox; do not submit secrets. Compiler availability and rate limits are controlled by the service. No API key is embedded in the frontend.

The API's request performs compilation and execution together; the **Compile + Run** action therefore also runs the program. Stdin is submitted before execution, so it is not an interactive live terminal. Cancel stops the browser request; it cannot guarantee cancellation of a job already accepted by the remote compiler.

## Local data and sharing

Projects, editor settings, recent files, and execution history are saved to this browser's local storage. Use **Export project ZIP** for backups. Shared links encode the selected source in the URL fragment; anyone who gets the link can read that code. There is no account, cloud project store, or private-link access control.

The ZIP archive contains source files and a project manifest. You can import `.c`/`.h` files or a ZIP/JSON backup into the workspace.

## Publish with GitHub Pages

1. Push these files to a GitHub repository.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/(root)`, then save.
4. Wait for GitHub Pages to finish publishing; the site link will appear on that Pages settings screen.

## External assets

DM Sans, JetBrains Mono, and CodeMirror are loaded from public CDNs. For offline or production use, host these assets yourself and configure a trusted compiler service with suitable privacy, abuse, and resource controls.
