# CPU Usage Management Script

## Overview

This bash script is designed to continuously monitor CPU usage and identify users whose usernames are exactly 8 characters long. It automatically terminates all processes for the top 10 users based on CPU usage. This script can help manage high CPU consumption by frequently killing processes of such users.

## How It Works

1. **User Monitoring**: The script gathers a list of users with exactly 8-character usernames and ranks them by CPU usage.
2. **Process Termination**: It identifies the top 10 users based on CPU usage and kills all processes for each of these users.
3. **Logging**: After killing the processes, it logs the usernames of those users whose processes were terminated.
4. **Looping**: The script runs indefinitely, with a brief pause between each iteration to avoid excessive resource consumption.

## Prerequisites

- **Bash**: Ensure Bash is installed (commonly available on most Linux distributions).
- **Permissions**: The script requires sufficient permissions to kill processes for the identified users (root or elevated privileges may be necessary).

## Setup

1. Clone or download the script:
    ```bash
    git clone https://github.com/yourusername/your-repo.git
    cd your-repo
    ```

2. Make the script executable:
    ```bash
    chmod +x manage_cpu_usage.sh
    ```

## Usage

1. Run the script:
    ```bash
    sudo ./manage_cpu_usage.sh
    ```

2. The script will:
   - Continuously monitor system processes and identify users with 8-character usernames.
   - Kill all processes for the top 10 CPU-consuming users with such usernames.
   - Log the killed users' usernames after each iteration.
   
3. The script pauses for 0.5 seconds between iterations to minimize its own CPU usage.

### Sample Output:
```
Killed processes of the following users:
user1234
user5678
userabcd
...
```

If no users with 8-character usernames are found in the top 10 CPU users, it will print:
```
No users with 8 character usernames found to kill.
```

## Notes

- This script targets usernames with exactly 8 characters. Modify the condition (`length($1)==8`) in the script if you need to target users with usernames of different lengths.
- The script runs indefinitely. Use `CTRL+C` to stop it or manage it as a background service if necessary.
- Be cautious while running this script, as it forcibly kills all processes for the identified users without any warning.
