# automation-toolkit

Here’s a main README file that provides a clear overview of all the scripts:

---

# Bash Scripts Collection

Welcome to the Bash Scripts Collection! This repository contains a set of scripts designed to help with various administrative tasks on Linux systems, particularly in a cPanel/WHM environment. Below is a summary of each script and its functionality.

## Scripts Overview

### 1. **Clear Frozen Mail Queue**

**File:** `clear_frozen_mails.sh`

**Purpose:** Automatically clears frozen emails from the Exim mail queue every 9 minutes. It continuously monitors and removes any emails that are stuck in the queue, helping to maintain server performance.

**Key Features:**
- Runs in an infinite loop.
- Logs the time of each clearance operation.
- Gracefully handles termination signals.

### 2. **Terminate cPanel Accounts**

**File:** `terminate_accounts.sh`

**Purpose:** Terminates multiple cPanel accounts based on a list of usernames. The script reads usernames from a file named `usernames` and removes each account using the cPanel command `/scripts/removeacct`.

**Key Features:**
- Reads usernames from a specified file.
- Skips accounts that do not exist or are already suspended.
- Logs the status of each termination operation.

### 3. **Audit Media and Large Files**

**File:** `audit_files.sh`

**Purpose:** Audits and generates reports of media files and large files within specified directories. The script finds media files (e.g., `.mp4`, `.mp3`, `.mov`) and files larger than 100MB, and stores the results in designated output directories.

**Key Features:**
- Searches through multiple directories.
- Generates separate reports for media files and large files.
- Configurable to suit different directory paths and output locations.

### 4. **Manage CPU Usage**

**File:** `manage_cpu_usage.sh`

**Purpose:** Continuously monitors CPU usage to identify users with 8-character usernames consuming the most CPU. The script terminates all processes for these users to manage high CPU consumption effectively.

**Key Features:**
- Identifies and kills processes for the top 10 CPU-consuming users with 8-character usernames.
- Logs the usernames of processes that were terminated.
- Runs indefinitely with a brief pause between iterations.

### 5. **Suspend cPanel Accounts**

**File:** `suspend_accounts.sh`

**Purpose:** Suspends cPanel accounts based on a list of usernames. The script reads usernames from a file named `username_list.txt` and suspends accounts using the cPanel command `/scripts/suspendacct`.

**Key Features:**
- Reads usernames from a specified file.
- Checks if the account exists and is not already suspended before attempting to suspend it.
- Logs the suspension status for each account.

## Getting Started

1. **Clone the Repository:**
    ```bash
    git clone [https://github.com/yourusername/your-repo.git](https://github.com/91Danny/Soft_Bash-Scripts-Collection.git)
    cd your-repo
    ```

2. **Setup:**
    - Make each script executable:
      ```bash
      chmod +x script_name.sh
      ```
    - Prepare any required input files (e.g., `username_list.txt`, `usernames`).

3. **Usage:**
    - Run each script as needed using:
      ```bash
      ./script_name.sh
      ```

## Notes

- Ensure you have the necessary permissions to run these scripts, especially those interacting with cPanel/WHM commands.
- Customize file paths and parameters in the scripts as per your environment and requirements.
- Monitor script outputs and logs to verify operations and troubleshoot if necessary.

---

This README provides a clear and concise explanation of each script’s purpose, setup, and usage, making it easy for visitors to understand and utilize the scripts.
