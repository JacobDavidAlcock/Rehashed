# Automated DeHashed Scraper

A lightweight Bash script for penetration testers and security researchers to automate the process of paginating through DeHashed API search results. This script takes a raw `curl` command, extracts all emails and email/password combinations, and saves them into clean, deduplicated files.

## Features

- **Automated Pagination:** Efficiently loops through every page of a DeHashed search result until no more results are found.
- **Direct `curl` Command Input:** Simply copy the search command from your browser's developer tools and paste it directly into the script.
- **Dual Data Extraction:** Automatically separates all discovered emails from cleartext email and password combinations into two distinct files.
- **Configurable Delay:** Includes a `-t` flag to set a custom delay between API requests, helping to avoid rate-limiting issues.
- **Safe & Non-disruptive:** Reads data without altering search queries and securely prompts for your API token without saving it to disk.
- **Clean Output:** The final output files are automatically sorted and deduplicated, providing a clean, unique list of results.

## Prerequisites

Before running this script, you need to have the following standard command-line tools installed:

- `bash`
- `curl`
- `jq` (A lightweight and flexible command-line JSON processor)

### Installing `jq`

On Debian-based systems like Kali Linux or Ubuntu, you can install `jq` easily with `apt`:

```bash
sudo apt update && sudo apt install -y jq
```

On macOS, you can use Homebrew:

```bash
brew install jq
```

## Installation & Usage

### 1. Save the Script

Save the script from the Canvas to a file named `rehashed`.

### 2. Make the Script Executable

```bash
chmod +x rehashed
```

### 3. Run the Script

Execute the script from your terminal. You can optionally provide a delay flag (`-t`).

- To run with the default 2-second delay:

```bash
./rehashed
```

- To run with a custom 5-second delay:

```bash
./rehashed -t 5
```

### 4. Follow the Prompts

1. The script will ask you to paste the full, multi-line `curl` command. Which you can get from the network tab on developer tools when using DeHashed normally.
2. After pasting, press `Enter`, then press `Ctrl+D` to confirm.
3. If your command uses `[redacted]` as a placeholder, you will be securely prompted to enter your DeHashed API Bearer Token.

## Output

The script will generate two files in the same directory:

- `all_emails.txt`: A clean, deduplicated list of every email address found in the results.
- `email_password_combinations.txt`: A list of any associated `email:password` pairs that were discovered.

## Disclaimer

This tool is intended for use in authorized security testing and research scenarios only. Users must abide by the DeHashed terms of service. Unauthorized scanning or use of data is illegal. The user is responsible for ensuring they have explicit, written permission to test any targets or handle the resulting data. The author is not responsible for any misuse or damage caused by this script.

## License

This project is licensed under the MIT License.
