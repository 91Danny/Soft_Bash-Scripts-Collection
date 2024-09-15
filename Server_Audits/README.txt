# Media and Large File Audit Script

## Overview

This bash script is designed to audit and generate reports of media files and large files within specified directories. It searches for media files (e.g., `.mp4`, `.mp3`, `.mov`) and large files (over 100MB) across multiple directories and stores the results in corresponding output directories.

## How It Works

The script performs two key functions for each directory listed in the search paths:
1. **Media File Audit**: It finds media files (`.mp4`, `.mp3`, `.mov`) while excluding specific paths (e.g., `wp-content`) and outputs their sizes.
2. **Large File Audit**: It searches for files larger than 100MB and records their sizes.

Both sets of results are saved in separate files within specified output directories.

## Prerequisites

- Ensure you have bash installed (common on most Linux distributions).
- Ensure the directories listed in the `search_paths` and `output_dirs` arrays exist and have the necessary permissions.

## Setup

1. Clone the repository or download the script:
    ```bash
    git clone https://github.com/yourusername/your-repo.git
    cd your-repo
    ```

2. Edit the script to customize the search paths and corresponding output directories:
    - **search_paths**: Directories to be searched.
    - **output_dirs**: Directories where the audit files will be saved.

    Example setup:
    ```bash
    search_paths=("/home" "/var/www" "/srv")
    output_dirs=("/audit/home" "/audit/www" "/audit/srv")
    ```

3. Ensure the output directories exist or create them:
    ```bash
    mkdir -p /output/directory/for/home /output/directory/for/path2 /output/directory/for/path3
    ```

## Usage

1. Make the script executable:
    ```bash
    chmod +x audit_script.sh
    ```

2. Run the script:
    ```bash
    ./audit_script.sh
    ```

## Output

- **Media_Audit**: Contains a list of media files (`.mp4`, `.mp3`, `.mov`) with their respective sizes, excluding any `wp-content` paths.
- **Large_Files**: Lists files larger than 100MB with their sizes.

These files will be saved in the corresponding output directories, as defined in the `output_dirs` array.

### Example Output:

- `/output/directory/for/home/Media_Audit`
- `/output/directory/for/home/Large_Files`

## Notes

- Modify the file extensions or size limits in the `find` commands to suit your needs.
- Ensure that the script has permission to access and write to the specified directories.

