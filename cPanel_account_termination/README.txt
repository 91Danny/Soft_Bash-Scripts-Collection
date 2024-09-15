# cPanel Account Termination Script

## Overview

This bash script automates the termination of multiple cPanel accounts using the `removeacct` command. It reads a list of usernames from a file named `usernames` and removes each account while retaining its DNS settings (using the `--keepdns` option).

## How It Works

1. **Username List**: The script reads usernames from a file named `usernames` located in the same directory.
2. **Account Removal**: For each username in the file, the script runs the `/scripts/removeacct --keepdns` command to terminate the account.
3. **Server-Friendly**: Optionally, you can add a sleep interval between each termination to avoid putting too much load on the server.

## Prerequisites

- **cPanel/WHM**: This script requires a server with cPanel/WHM installed, as it uses the `/scripts/removeacct` command.
- **Bash**: Bash must be installed (available on most Linux distributions).
- **Permissions**: The script should be run with the necessary permissions to execute cPanel/WHM commands.

## Setup

1. Clone or download the script:
    ```bash
    git clone https://github.com/yourusername/your-repo.git
    cd your-repo
    ```

2. Ensure the `usernames` file exists in the same directory as the script. This file should contain a list of cPanel usernames, one per line.

3. Make the script executable:
    ```bash
    chmod +x terminate_accounts.sh
    ```

## Usage

1. Run the script:
    ```bash
    ./terminate_accounts.sh
    ```

2. The script will:
   - Check for the existence of the `usernames` file.
   - For each username in the file, it will execute `/scripts/removeacct --keepdns` to terminate the account while keeping DNS records intact.
   
3. Optionally, you can uncomment the `sleep 5` line in the script if you'd like to add a delay between each account termination.

### Example `usernames` File:

```
user1
user2
user3
```

### Expected Output:
```
Removing account: user1
Removing account: user2
Removing account: user3
```

## Error Handling

- If the `usernames` file is missing, the script will display the following error and exit:
    ```
    Error: The 'usernames' file does not exist.
    ```

## Notes

- Ensure that the usernames in the `usernames` file are accurate, as the script will attempt to remove each account listed.
- If the server is handling a large number of accounts, consider adding a delay (`sleep 5`) between each termination to reduce server load.