# VS Code and Git setup

## Required software

- Visual Studio Code
- Git for Windows (or Git for your operating system)

VS Code includes its Git user interface, but it uses the Git installation on
your computer.

## Recommended extensions

The repository includes `.vscode/extensions.json`, so VS Code should offer to
install the recommended extensions when you open the folder.

- `GitHub.vscode-pull-request-github` — GitHub sign-in, pull requests, and issues.
- `editorconfig.editorconfig` — applies this repository's whitespace and line-ending rules.
- `stefan-h-at.source-engine-support` — syntax support for Valve/Source KeyValues files.

Optional:

- `ms-vscode-remote.remote-ssh` — install only if the AMP host exposes SSH and
  you intend to edit server files remotely.
- `eamodio.gitlens` — extra history and blame views; VS Code's built-in Git
  interface is sufficient for normal commits and pushes.
- `ms-vscode.powershell` — useful after PowerShell deployment/update scripts
  are added.

## Publish the included repository

The downloaded project already contains a `.git` directory and an initial
commit. Do not initialize it a second time.

1. Extract the archive.
2. Open the extracted `cs2-practice-server` folder in VS Code.
3. Sign in to GitHub from the Accounts menu if GitHub is your remote host.
4. Open Source Control (`Ctrl+Shift+G`).
5. Select **Publish Branch** or run **Git: Add Remote** from the Command Palette.
6. Choose a private repository unless you intentionally want the extracted
   third-party assets to be public.
7. Push the `main` branch.

### Existing remote repository

If you are copying this project into an already-cloned repository, delete the
included `.git` directory before copying the files. A nested `.git` directory
would create a separate embedded repository.

## Credential rule

Never commit the GSLT, RCON password, server password, Steam Web API key, or
other AMP-protected values. Keep them in AMP or in a local ignored file such as
`amp-launch-parameters.local.txt`.
