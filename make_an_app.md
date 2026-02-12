# How to Build and Run the Mac App

## Build the Mac app

1. Make the CLI executable (from project root):
   ```bash
   chmod +x apps/backend/cli/autoclaude
   ```

2. Package the app:
   ```bash
   cd apps/frontend
   npm run package:mac
   ```

3. On success, the found the app at `apps/frontend/dist/mac-arm64/`. Open Folder & Move `Auto-Claude.app` to **Applications** if you want.

## Using the `autoclaude` CLI

The `autoclaude` binary is inside the app bundle, so it is not in your PATH by default. Use one of these options.

### Option 1: Add the CLI to your PATH

1. Edit your shell config:
   ```bash
   nano ~/.zshrc
   ```

2. Add this line (adjust the app path if you installed elsewhere):
   ```bash
   export PATH="/Applications/Auto-Claude.app/Contents/Resources/backend/cli:$PATH"
   ```

3. Reload and test:
   ```bash
   source ~/.zshrc
   autoclaude --list 
   ```

### Option 2: Symlink into /usr/local/bin

1. Confirm the app location (e.g. Applications):
   ```bash
   ls /Applications/ | grep -i auto
   ```
   The script path is: `/Applications/Auto-Claude.app/Contents/Resources/backend/cli/autoclaude`  
   If you installed the app elsewhere, use that path in the next step.

2. Create the symlink and ensure the script is executable:
   ```bash
   sudo ln -sf "/Applications/Auto-Claude.app/Contents/Resources/backend/cli/autoclaude" /usr/local/bin/autoclaude
   chmod +x "/Applications/Auto-Claude.app/Contents/Resources/backend/cli/autoclaude"
   ```

3. Verify:
   ```bash
   autoclaude --list
   ```
