# What is GluCINDa?
GluCINDa is a Python-based application developed to improve the accuracy of research involving Continuous Glucose Monitoring (CGM) data. Typically, such data are downloaded by patients from manufacturer portals, which often leads to significant heterogeneity in file structures (.csv, .txt, or .xlsx). These variations include differences in the number and order of columns, header languages, units of measurement, and other aspects. In our experience, some files even change structure multiple times within the same dataset. This complexity makes importing such data a challenge. GluCINDa was born from the desire to create a precise and efficient tool for extracting the valuable CGM data hidden within these files.

# How does GluCINDa work?
The core principle behind GluCINDa is simple: "If data are human-readable, they should be machine-readable." Instead of relying on AI, GluCINDa employs a statistical approach to first analyze the file and determine whether a row is nonsensical, a header, or actual data. It then isolates any columns that may contain glucose-related information. This is determined using two criteria: 1) the column header must relate to glucose, and 2) the values must be within a plausible blood glucose range. These extracted data are saved in a new file called parsed_all.csv.

In a second step, GluCINDa identifies columns with a median time interval of either 5 or 15 minutes, which are typical for CGM data. These refined data are stored in another output file, parsed_all_just_cgm.csv.

Throughout the process, GluCINDa generates detailed documentation (if configured) that allows for complete transparency regarding why each line was included in the final export. Every step of the data extraction process is fully traceable.

# Can I use GluCINDa for my research?
Absolutely! However, the GluCINDa development team takes no responsibility for the accuracy or completeness of the extracted data. If you find GluCINDa helpful, we would also appreciate it if you could cite our work in your research.
