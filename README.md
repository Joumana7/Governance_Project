## Movie Dataset Cleaning, Validation, and Privacy Pipeline
## Dataset Description

This dataset contains detailed information about various movies including:

    Year of release

    Cast and stars

    Genres (e.g., Adventure, Romance, Action)

    Audience Ratings

    Runtime

    Additional numerical columns like VOTES and Gross

The dataset initially contained missing values (NaNs), duplicate records, and outliers which required extensive data cleaning and validation.
# Problem Definition

The dataset exhibited common data quality issues:

    Null and missing values (NaNs)

    Duplicate rows

    Outliers in numerical columns

    Schema inconsistencies

    Privacy-sensitive information (e.g., movie names)

This project applies a complete data preparation pipeline using Pandas, Great Expectations, and data privacy techniques to clean, validate, and secure the dataset.

## Methodology
1.  Data Cleaning

Performed using Pandas:

    Loading the dataset (movies.csv) into a DataFrame

    Identifying and removing duplicates

    Counting missing values per column

    Computing total and percentage of missing cells

    Handling missing data:

        Dropped rows with missing values

        Replaced missing values in numerical columns (VOTES to Gross) with 0

    Outlier Detection:

        Used boxplots and Interquartile Range (IQR) to identify outliers

        Controlled plot range with plt.ylim(500, 1000)

2.  Data Validation

Used Great Expectations and Pandera to enforce schema integrity:

    Checked for null values in key columns like MOVIES

    Ensured RATING values were between 0 and 100

    Verified uniqueness in MOVIES column

    Ensured RunTime values were within a reasonable range (0–100)

    Used expect_column_values_to_be_in_set() for domain-specific values in VOTES and Gross

    Defined and saved a custom expectation suite and viewed the validation results

3.  Security & Privacy

Implemented privacy-preserving transformations:

    Randomized string values across object-type columns

    Used anonymize() and fake_names() from the anonymizedf library to anonymize MOVIES

    Swapped values in RunTime column for additional privacy

    Generated synthetic data using the Faker library for MOVIES and VOTES

    Tokenized text in ONE-LINE column using NLTK for natural language processing tasks

    Hashed sensitive text (e.g., ONE-LINE) using SHA-256

## Results

    Cleaned dataset is free of duplicates, missing values, and validated against schema expectations.

    Numerical outliers were identified and interpreted visually.

    Sensitive textual data was tokenized, anonymized, and hashed.

    Generated synthetic data enables privacy-preserving experiments.

## Conclusion

    Data Cleaning ensured structural and content integrity

    Validation guaranteed that the dataset met defined schema expectations

    Privacy and Security measures anonymized and protected identifiable information

These techniques promote data reliability, privacy compliance, and trustworthiness for further analysis and modeling.
