# IEEE_R9_Industry_Ambassadors
README: Ambassador Scoring Program
This program helps you calculate scores for ambassadors based on their reported activities from a Google Sheet. It's designed to be used in a Google Colab environment for easy execution and data handling.

How it Works
The script reads data from a Google Sheet (either by uploading a CSV/Excel file or directly from a public Google Sheet URL), processes the entries, and calculates points for various activities such as recruiting new members, forming local groups, holding meetings, and promoting events. Crucially, only validated entries are included in the scoring.

The final output is a table showing each ambassador's score broken down by activity type, along with their total score, sorted from highest to lowest. Additionally, the program now generates a horizontal bar chart visualizing the total points for each ambassador, providing a quick and intuitive overview of the standings.

Setup and Usage
Follow these steps to get your ambassador scores:

Prepare Your Google Sheet

Ensure your Google Sheet has the following columns with exact matching headers:
Ambassador Name
Type of Report
Number of Participants in this Session (If this column is missing, participants will not contribute to the score)
Validated: This is a new, crucial column. For each entry you want to include in the score calculation, enter TRUE in this column. Entries without TRUE (e.g., blank, FALSE, No) will be ignored.
Publish your Google Sheet to the web as CSV:
Open your Google Sheet.
Go to File > Share > Publish to web.
Select the specific sheet (tab) you want to use.
Choose Comma-separated values (.csv) as the format.
Click Publish and copy the generated URL. This is the public_sheet_url you'll use in the code.
Alternatively, you can get a shareable link and construct the CSV export URL manually. For a sheet link like https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit?usp=sharing, the CSV export link would be https://docs.google.com/sheets/d/YOUR_SHEET_ID/export?format=csv&gid=YOUR_GID. (The gid is usually 0 for the first tab, or found in the URL when you select a specific tab: &gid=xxxxxx).
Open in Google Colab

Go to Google Colab.
Create a new notebook (File > New notebook).
Copy and paste the entire Python code into a cell in the Colab notebook.
Configure the Data Source

In the Python code, find the --- Option 1: Upload a file (CSV or Excel)to Colab --- and --- Option 2: Read from a Public Google Sheets (CSV format) --- sections.
Option 1: Upload a File (CSV or Excel)
This option is commented out by default. If you prefer to upload a local file, uncomment the lines within the Option 1 block.
When you run the cell, you'll be prompted to upload your CSV or Excel file.
Option 2: Read from a Public Google Sheets Link (Recommended)
This option is active by default.
Replace "https://docs.google.com/sheets/d/1LoeUQtTKKqp6Q9pOt05xs7QA931E2fHVKimXscsnSDU/export?format=csv&gid=0" with the public CSV link you obtained from your Google Sheet in step 1.
Run the Program

Click the "Play" button (triangle icon) next to the code cell in Google Colab, or press Shift + Enter.
The program will:
Fetch the data from your specified source.
Filter out non-validated entries.
Calculate the scores for each ambassador.
Print the "AMBASSADORS STANDINGS TABLE" directly in the Colab output.
Display a horizontal bar chart showing the total points for each ambassador, sorted from highest to lowest.
Download Results (Optional)

If you wish to download the results as a CSV file, locate the --- Download results as CSV --- section at the end of the code.
Uncomment the lines within this block.
Run the cell again. A file named ambassadors_scores.csv will be downloaded to your computer.
Understanding the Horizontal Bar Chart
After the score table, the program generates a horizontal bar chart titled "Ambassador Total Score Standings."

Purpose: This chart provides a visual leaderboard, making it easy to quickly identify top-performing ambassadors and compare their total points at a glance.
Axes:
The Y-axis lists the Ambassador Name.
The X-axis represents the Total Points.
Sorting: The chart is automatically sorted to display the highest-scoring ambassadors at the top, consistent with a leaderboard view.
Dynamic Sizing: The chart's height adjusts automatically based on the number of ambassadors to ensure that all names are clearly visible and do not overlap.
Troubleshooting
"CRITICAL ERROR: The column 'Ambassador Name' was not found.": This means the column header in your Google Sheet doesn't exactly match Ambassador Name (or Type of Report, Validated, etc.) as defined in the script. Check for typos, extra spaces, or capitalization mismatches.
"WARNING: The validation column 'Validated' was not found.": The script will still run, but all entries will be counted as if they were validated. Make sure you add the Validated column to your sheet if you intend to use this feature.
"Error when loading data from the link...": Double-check that your Google Sheet is correctly "Published on the web" as a CSV, and that the URL you're using is the correct CSV export link, not just the regular shareable link.
"The file was loaded, but it is empty or cannot be read correctly.": This can happen if the sheet is truly empty, or if there's an issue with the CSV format (e.g., incorrect delimiters, encoding issues). Try opening the CSV in a text editor to inspect its content.
Empty Scores / Missing Data: Ensure that the TRUE value (or whatever string you use) in the Validated column is consistent and that your Type of Report values also match the script's definitions ("Recruited New IEEE Member(s)", etc.).
Chart Not Appearing or Looking Odd:
Ensure import matplotlib.pyplot as plt is at the top of your script.
Verify that scores_df is not empty and contains valid Total_Score values.
If labels overlap, the dynamic sizing should generally prevent this, but for an extremely large number of ambassadors, manual adjustment of fig_height might be considered.
