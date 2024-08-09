# Google Apps Script: Book Entry Standardization Service

## Overview
This Google Apps Script automates the process of standardizing book entries in a Google Sheet. It leverages the Google Books API to fetch accurate book information (title and author) and creates a sheet to update the original data with this standardized data. Additionally, it logs the last reviewed time for each entry.

## Features
* Batch Processing: Efficiently handles large datasets by processing entries in batches, adhering to Google API rate limits.
* Data Validation: Ensures data accuracy by fetching information from the reliable Google Books API.
* Progress Tracking: Stores the last processed row to resume from interruptions.
* User-friendly Menu: Integrates a custom menu item in Google Sheets for easy script execution.

## Code Structure
* standardizeBookEntries(colIndexes, data): Fetches standardized book information from the Google Books API for a batch of entries.
* processData(data_sheet, maxRows, batchSize, colIndexes, formattedDateTime, newSheet): Manages the overall standardization process, including batching, API calls, data updating, and progress tracking.
* runStandardizationService(): Main function that initializes the process, gets necessary sheet references, and calls processData.
* onOpen(): Creates a custom menu in Google Sheets upon opening.

## How to Use

1. Prepare your data: Ensure your sheet has columns named "Book Title:", "Book Author:", and "Last Reviewed:".
1. Install the script: Copy and paste the code into a new Google Apps Script project.
1. Run the script: Open your Google Sheet and navigate to the custom menu: OBAW -> Standardize data.
1. View results: The script will create a new sheet named "Standardized Book Data - [timestamp]" with the updated entries.

## Important Notes
* API Key: The Google Books API might require an API key in the future. If so, you'll need to modify the code to include your key.
* Error Handling: The script includes basic error handling (muteHttpExceptions: true) to prevent crashes. Consider adding more robust error logging and recovery mechanisms.

## Dependencies
* Google Apps Script: The script is designed to run within the Google Apps Script environment.
* Google Books API: Used to fetch book information.
* Google Sheets API: Used to interact with spreadsheets.

# Future Enhancements
* Precise Matching: Implement a fuzzy matching algorithm, such as Levenshtein distance (would be the simplest and most flexible), to improve the accuracy of book title matching against the Google Books database. This will help handle search returns that might not match the titles as expected.
* User Experience Improvements:
  * Introduce a progress bar to visually indicate the processing status, to allow users to gauge the remaining time.
  * Add a "Completed" alert to notify the user when the standardization process is finished.
* Error Handling and Logging: Expand the current error handling to include more robust logging and recovery mechanisms. This will help diagnose and address potential issues more effectively.
