# Data-engineering-tasks
To explore most common performed tasks in data engineering

PDF Table Extraction to CSV

Welcome to the PDF Table Extraction repository! 🎉 This project demonstrates how to extract tables from a PDF and save them as a CSV file using Python. Whether you're dealing with reports, data sheets, or any PDF that includes tabular data, this script makes it easy to convert it into a usable format.

🛠️ What’s Inside

Python Script: A simple script that uses pdfplumber and pandas to extract tables from a PDF file and save them as a CSV file.
Step-by-Step Instructions: Clear guidance on setting up your environment, running the script, and saving the extracted data.
📜 How It Works

Setup: Install the required libraries with pip install pdfplumber pandas.
Extract Tables: The script opens a specified PDF, extracts tables from a chosen page, and converts them into a Pandas DataFrame.
Save to CSV: The DataFrame is saved to a CSV file on your local system, making it easy to use the data in other applications.

🚀 Getting Started

import pdfplumber
import pandas as pd

# Define the path to your PDF file and the output CSV file
pdf_path = 'your_input.pdf'
csv_output_path = 'filepath\\output_table.csv'

# Open the PDF file
with pdfplumber.open(pdf_path) as pdf:
    # Access a specific page (0-indexed)
    page = pdf.pages[10]
    
    # Extract all tables from the page
    tables = page.extract_tables()
    
    # Check if any tables are found
    if tables:
        # Choose a specific table (e.g., the first table)
        specific_table_index = 0
        table_data = tables[specific_table_index]

        # Create a DataFrame from the table data
        df = pd.DataFrame(table_data[1:], columns=table_data[0])  # First row is header

        # Print DataFrame (optional, for verification)
        print(df)

        # Save the DataFrame to a CSV file
        df.to_csv(csv_output_path, index=False, encoding='utf-8')
        print(f"Table saved to {csv_output_path}")
    else:
        print("No tables found.")
        
