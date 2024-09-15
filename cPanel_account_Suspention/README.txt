# cPanel Account Suspension Script

## Overview

This bash script automates the process of suspending cPanel accounts based on a list of usernames. It checks if each account exists and whether it is already suspended. If the account exists and is not yet suspended, it will suspend the account with a specified reason.

## How It Works

1. **Input File**: The script reads a list of cPanel usernames from a file named `username_list.txt`.
2. **Account Checks**:
   - It verifies if each username exists in the cPanel account list (`/etc/trueuserowners`).
   - It checks if the account is already suspended by looking in the `/var/cpanel/suspended/` directory.
3. **Suspension**:
   - If the account is not suspended, it suspends the account using the `/scripts/suspendacct` command with the reason "Migrated to Nucleus".
   - It logs the suspension status for each account.

## Prerequisites

- **cPanel/WHM**: The script requires a cPanel/WHM environment, as it uses the `/scripts/suspendacct` command.
- **Bash**: Bash must be installed (available on most Linux distributions).
- **Permissions**: Ensure you have the necessary permissions to execute cPanel/WHM commands and access the system files.
- ** Rename the script name from txt to .sh 

## Setup

1. Clone or download the script:
    ```bash
    git clone https://github.com/91Danny/Soft_Bash-Scripts-Collection/tree/main/cPanel_account_Suspention
    cd your-repo
    ```

2. Prepare the `username_list.txt` file:
    - Create a file named `username_list.txt` in the same directory as the script.
    - Add one cPanel username per line.

3. Make the script executable:
    ```bash
    chmod +x suspend_accounts.sh
    ```

## Usage

1. Run the script:
    ```bash
    sudo ./suspend_accounts.sh
    ```

2. The script will:
   - Read usernames from `username_list.txt`.
   - Check if each username exists and if it is already suspended.
   - Suspend accounts that are found and not already suspended.
   - Log the status of each operation.

### Example `username_list.txt` File:
```
user1
user2
user3
```

### Sample Output:
```
Suspended cPanel account: user1
Skipping user2 - Account is already suspended
Skipping user3 - Account not found
```

## Notes

- Ensure that `username_list.txt` is correctly formatted and located in the same directory as the script.
- The script logs actions for each username, so you can verify which accounts were successfully suspended and which were skipped.
- Modify the `suspension_reason` variable if a different reason is needed for the suspension.

