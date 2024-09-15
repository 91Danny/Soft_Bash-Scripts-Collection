# Exim Frozen Mail Queue Clearing Script

## Overview

This bash script automates the process of clearing frozen emails from the Exim mail queue on a server. It runs continuously, removing frozen mails every 9 minutes and logging the timestamp of each operation.

The script also has a cleanup mechanism that safely terminates it when interrupted (e.g., via `SIGINT` or `SIGTERM` signals), ensuring that the script is properly removed after execution.

## How It Works

1. **Date and Time Logging**: The script logs the start time, the time when frozen mails are cleared, and the termination time.
2. **Exim Command**: It identifies frozen mails in the Exim mail queue and removes them.
3. **Continuous Operation**: It runs in an infinite loop, clearing frozen mails every 9 minutes.
4. **Signal Handling**: The script traps termination signals (`SIGINT` or `SIGTERM`) and runs a cleanup function to display the termination time and delete the script file.

## Prerequisites

- **Exim**: Ensure that Exim is installed and running on the server.
- **Bash**: Bash must be available on the system (common on most Linux distributions).
- **Permissions**: The script requires proper permissions to access and manipulate the Exim mail queue.

## Setup

1. Clone or download the script:
    ```bash
    git clone https://github.com/yourusername/your-repo.git
    cd your-repo
    ```

2. Make the script executable:
    ```bash
    chmod +x clear_frozen_mails.sh
    ```

## Usage

1. Run the script:
    ```bash
    ./clear_frozen_mails.sh
    ```

2. The script will:
   - Start clearing frozen mails from the Exim queue.
   - Log each clearance event with a timestamp.
   - Continue running every 9 minutes until manually stopped.

3. To stop the script, use `CTRL+C` or send a termination signal. This will trigger the cleanup function, log the termination time, and delete the script.

### Sample Output:
```
Script started at 2024-09-15 12:00:00
Frozen mails cleared at 2024-09-15 12:09:00
Frozen mails cleared at 2024-09-15 12:18:00
...
Script terminated at 2024-09-15 12:30:00
```

## Notes

- The script waits for 9 minutes between clearing the frozen mail queue. You can modify the `sleep 540` line if a different interval is desired.
- Ensure the script has proper permissions to manage the Exim queue.
  
## Signal Handling

The script traps `SIGINT` (e.g., from `CTRL+C`) and `SIGTERM`, ensuring a graceful shutdown and self-removal after termination.

