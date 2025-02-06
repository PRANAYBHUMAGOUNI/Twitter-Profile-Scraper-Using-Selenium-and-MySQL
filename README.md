# Twitter-Profile-Scraper-Using-Selenium-and-MySQL

This repository contains a Python script that scrapes Twitter profile information using Selenium and stores the data in a MySQL database. The script logs into Twitter, navigates to specified profile URLs, extracts profile details (such as bio, follower count, following count, location, and website), and saves the data for analysis or further processing.

## Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [Configuration](#configuration)
- [Usage](#usage)
- [Notes](#notes)
- [Troubleshooting](#troubleshooting)
- [Disclaimer](#disclaimer)

## Features
- **Automated Login**: Logs into Twitter using provided credentials.
- **Profile Scraping**: Scrapes bio, follower count, following count, location, and website from Twitter profiles.
- **Data Parsing**: Converts follower/following counts with 'K' or 'M' suffixes into integers.
- **Error Handling**: Manages exceptions and handles empty or missing data gracefully.
- **Data Storage**: Saves the scraped data into a MySQL database.

## Prerequisites
Ensure you have the following installed on your system:

- Python 3.x
- MySQL Server
- Microsoft Edge Browser
- Microsoft Edge WebDriver (compatible with your Edge browser version)

### Python Packages
Install the required Python packages using pip:
```bash
pip install selenium mysql-connector-python python-dotenv
```
- selenium
- mysql-connector-python
- python-dotenv

## Installation
### Clone the Repository
```bash
git clone https://github.com/PRANAYBHUMAGOUNI/twitter-profile-scraper.git
cd twitter-profile-scraper
```

### Download Microsoft Edge WebDriver
Download the WebDriver that matches your Edge browser version from the [official site](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/).
Extract the `msedgedriver.exe` file to a known location on your system.

## Database Setup
### Create the Database and Table

Access your MySQL command-line client or MySQL Workbench, and execute the following SQL commands:
```bash
-- Create the database if it doesn't exist
CREATE DATABASE IF NOT EXISTS twitter_scraper;
-- Use the newly created or existing database
USE twitter_scraper;
-- Create the table to store Twitter profile data
CREATE TABLE IF NOT EXISTS twitter_profiles (
id INT AUTO_INCREMENT PRIMARY KEY,
url VARCHAR(255) NOT NULL,
bio TEXT DEFAULT NULL,
following_count BIGINT DEFAULT NULL,
followers_count BIGINT DEFAULT NULL,
location VARCHAR(255) DEFAULT NULL,
website VARCHAR(255) DEFAULT NULL
);
```

### Verify the Table Structure
```bash
DESCRIBE twitter_profiles;
```
Ensure the table has the correct columns and data types.

## Configuration
### Set Up Environment Variables

Create a `.env` file in the project directory to securely store your Twitter credentials and other configurations.

```bash
TWITTER_USERNAME=YourTwitterUsername
TWITTER_PASSWORD=YourTwitterPassword
TWITTER_EMAIL=YourEmail@example.com
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_PASSWORD=YourMySQLPassword
MYSQL_DATABASE=twitter_scraper
EDGE_DRIVER_PATH=C:\path\to\msedgedriver.exe
```
Replace the placeholder values with your actual credentials and paths.

### Update the Script (If Not Using .env)

If you prefer not to use environment variables, you can directly input your credentials in the `main()` function of the script:
```bash
TWITTER_USERNAME = "YourTwitterUsername"
TWITTER_PASSWORD = "YourTwitterPassword"
TWITTER_EMAIL = "YourEmail@example.com" # Optional, if needed for verification
```

### Update the Edge Driver Path

Ensure the `EDGE_DRIVER_PATH` variable in the `setup_driver()` function points to the actual location of your `msedgedriver.exe` file:
```bash
EDGE_DRIVER_PATH = r"C:\path\to\msedgedriver.exe"
```

### List of Twitter URLs

Update the `TWITTER_URLS` list with the Twitter profile URLs you wish to scrape:
```bash
TWITTER_URLS = [
"https://twitter.com/GTNUK1",
"https://twitter.com/whatsapp",
# Add more URLs as needed
]
```

## Usage
### Run the Script

In the project directory, run the script using google colab or jupyter notebook

### Monitor the Output

The script will output log messages to the console, indicating the progress:
- Successful database connection
- Login status
- Processing of each URL
- Scraped data
- Data insertion status

## Notes
### Compliance with Twitter's Terms of Service

Be sure to comply with Twitter's Terms of Service and Developer Agreement. Excessive or aggressive scraping may lead to your account being suspended.

### Delay Between Requests

The script includes a `time.sleep(3)` call to pause for 3 seconds between processing each profile. You may adjust this value to be more considerate of Twitter's servers and reduce the risk of rate limiting.

### Handling Verification Steps

If Twitter prompts for additional verification during login (e.g., CAPTCHA or email verification), the script will notify you. You may need to handle these steps manually.

## Troubleshooting
### MySQL Connection Errors
- Ensure that your MySQL server is running and accessible.
- Verify that the credentials in your `.env` file or script match your MySQL user.
- Check that the `twitter_scraper` database and `twitter_profiles` table exist.

### Selenium Errors
- Confirm that the Edge WebDriver is compatible with your Edge browser version.
- Verify that the `EDGE_DRIVER_PATH` is correct.
- Ensure that all required Python packages are installed.

### Login Issues
- Double-check your Twitter credentials.
- Be aware that frequent login attempts may trigger security measures.
- If two-factor authentication (2FA) is enabled on your account, the script may not handle it. Consider using an account without 2FA for automated scripts.

### Data Not Saving Properly
- Ensure that the scraped data is correctly parsed and that counts are converted to integers.
- Check the console output for any error messages during the data insertion step.

## Disclaimer
This script is intended for educational purposes. Using automated scripts to scrape data from websites may violate the website's terms of service. It is your responsibility to ensure that your use of this script complies with all applicable laws, regulations, and terms of service.

**Important:**

- Use this script responsibly.
- Do not scrape data you do not have permission to access.
- Respect user privacy and data protection laws.






