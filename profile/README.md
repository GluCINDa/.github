# Background & Goals
CGM (Continuous Glucose Monitoring) data isn't just crucial for managing diabetes on an individual level; it's also essential for research. Many studies rely on real-world data from participants' personal CGM devices, which usually comes in a variety of formats and without clear metadata about the data structure. Importing, harmonizing, and ensuring the quality of this data can be a time-consuming and tricky process.

# What does GluCINDa do?
That's where GluCINDa (Glucose: Coherent Import. Neat Data.) comes in! GluCINDa is a Python tool designed to handle the many different file formats (CSV, XLSX, TXT) and table structures (e.g., varying header rows, different column names, etc.). It even deals with cases where the file structure changes halfway through the document. GluCINDa detects glucose measurements with date/time info and converts everything into a harmonized dataset.

# What’s the output?
The final GluCINDa file includes key details like participant ID, date, time, glucose value, glucose unit, the original source column name, source file name, and additional notes if needed. Plus, there's a documentation file so that each parsed value is fully traceable. GluCINDa also generates a report with a summary of the extracted data and creates a separate CGM file.

# How to run
