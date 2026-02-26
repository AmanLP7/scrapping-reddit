# DBT Project Mandates for Reddit Data Modeling

This document defines the foundational mandates and standards for the DBT project within the `scrapping-reddit` repository. These rules take precedence over general workflows.

## 1. Project Structure and Naming Conventions

- **Layered Architecture:** Models MUST be organized into clear layers:
  - `stg_`: Staging models that perform light cleaning and renaming of raw data.
  - `int_`: Intermediate models for complex transformations and business logic.
  - `fct_`: Fact tables (immutable event data, e.g., reddit_posts, reddit_comments).
  - `dim_`: Dimension tables (descriptive data, e.g., subreddits, authors).
- **Snake Case:** All table and column names MUST use `snake_case`.
- **Primary Keys:** Every model MUST have a unique surrogate key (e.g., `reddit_post_key`) or use the natural key (e.g., `post_id`) if guaranteed unique.

## 2. SQL Style and Development

- **Leading Commas:** Use leading commas in `SELECT` statements for easier debugging and diffs.
- **CTEs (Common Table Expressions):** Use CTEs for all transformations. The final statement should be a simple `SELECT * FROM final_cte`.
- **Indentation:** Use 4 spaces for indentation.
- **Keywords:** Use uppercase for SQL keywords (e.g., `SELECT`, `FROM`, `WHERE`).

## 3. Documentation and Testing

- **Mandatory Documentation:** Every new model MUST have a description in a `.yml` file.
- **Mandatory Tests:** At a minimum, `unique` and `not_null` tests MUST be applied to primary keys of all staging and fact models.
- **Relationship Tests:** Dimension keys in fact tables MUST have `relationships` tests to their respective dimension tables.

## 4. Reddit Specific Context

- **Source Data:** Raw data is assumed to be sourced from MongoDB/document store as described in `README.md`.
- **Sentiment Analysis:** Sentiment scores MUST be preserved as numeric values (e.g., `sentiment_score`) with standardized ranges (e.g., -1.0 to 1.0).
- **Timestamps:** All Reddit-related timestamps MUST be converted to `UTC` and stored as `TIMESTAMP` or `DATETIME` types.

## 5. Security and Credentials

- **Profiles:** NEVER commit `profiles.yml` or any credentials to the repository. Use environment variables for sensitive connection details.
