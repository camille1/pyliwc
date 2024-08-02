---
title: "PYLIWC: Linguistic Inquiry and Word Count in Python"
tags:
  - Python
  - Linguistic Inquiry
  - LIWC
  - Textual Analysis
  - Language Style Matching
authors:
  - name: Camille Lacan
    orcid: 0000-0002-0815-9046
    affiliation: "1"
affiliations:
  - name: IAE School of Management, University Perpignan Via Domitia, FR
    index: 1
output: pdf_document

date: 30 July 2024
bibliography: paper.bib
---

# Summary

Linguistic Inquiry and Word Count (LIWC), developed by @pennebaker_linguistic_2015, is a widely recognized tool for analyzing word usage through a dictionary-based approach. LIWC provides insights by counting word occurrences in texts and outputs the percentage of words that fall into one or more of over 80 linguistic (e.g., first-person singular pronouns, conjunctions), psychological (e.g., anger, achievement), and topical (e.g., leisure, money) categories. Researchers extensively use LIWC in social science research and linguistic studies to examine language. However, LIWC's reliance on third-party proprietary software makes it challenging to analyze large datasets such as social media conversations efficiently.

`pyliwc` addresses this limitation by allowing the use of the LIWC dictionary in Python. `pyliwc` includes functions to run LIWC analysis with internal or custom dictionaries, enabling efficient text analysis. This package handles large text corpora from Pandas DataFrames or text files, making it efficient for text analysis. Finally, `pyliwc` includes additional features like language style matching and narrative arc analysis, making it a comprehensive tool for linguistic and social science research.



# Statement of need

The rise of digital communication has led to an explosion of unstructured data, with text accounting for approximately 80-90% of this data [@boegershausen_fields_2022]. This includes data from social media posts, emails, forums, and other online interactions. Analyzing this vast amount of textual data is challenging due to the unstructured nature of such data, which complicates the extraction of meaningful insights [@berger_marketing_2022]. Traditional approaches to text analysis often struggle to scale with the growing volume and complexity of data [@humphreys_automated_2017]. A variety of software tools are available for text analysis, particularly in the realm of sentiment analysis.

Existing Python packages include:

-   TextBlob: Provides basic sentiment analysis and text processing capabilities.
-   VADER (Valence Aware Dictionary and sEntiment Reasoner): Specializes in sentiment analysis, particularly for social media texts.
-   spaCy: Offers advanced NLP features, including sentiment analysis through third-party extensions.
-   NLTK (Natural Language Toolkit): A comprehensive library for text processing with support for sentiment analysis via custom implementations.

In linguistics, one widely used set of dictionaries is the Linguistic Inquiry and Word Count -- LIWC [@boyd_development_2022]. The Linguistic Inquiry and Word Count (LIWC) dictionary is a prominent tool in text analysis. Developed by @pennebaker_linguistic_2015, LIWC categorizes words into various linguistic, psychological, and topical categories [@boyd_development_2022]. These include linguistic features (measures of verb tense, sentence structure, and other grammatical aspects), psychological categories (emotions, cognition, and social processes), substantive categories (e.g., leisure and money), and analysis of punctuation usage. LIWC’s dictionaries have been validated on a range of materials such as academic abstracts, literature texts, and other written corpora.

However, LIWC requires users to interact directly with its graphical user interface (GUI) for data analysis, leading to potential inefficiencies and errors in data handling. Users must export data from Python, process it in LIWC, and then re-import the results, which can be cumbersome and error-prone. Additionally, LIWC's GUI does not easily allow changes to dictionaries or manage large-scale data analysis effectively.

Thus, there is a significant need for researchers and data scientists who require the advanced capabilities of the LIWC dictionary but seek to integrate it directly into their Python workflows [@berger_marketing_2022; @berger_uniting_2019]. `pyliwc` addresses these challenges by integrating LIWC’s dictionary-based analysis directly in Python. This package eliminates the need for external software interaction, supports custom dictionary usage, and enhances the efficiency of processing large datasets. By streamlining the analysis process, `pyliwc` offers a practical and scalable solution for researchers and practitioners working with extensive textual data.


# Main features

The package offers a wide range of features, including:

-   LIWC Text Analysis:

    -   Analyze text data from various sources, including CSV files, directories, Pandas DataFrames, and individual strings.
    -   Supports internal dictionaries (e.g., LIWC22, LIWC2015) as well as custom dictionaries.
    -   Output results directly in a convenient Pandas DataFrame for easy integration with other data processing tools.

-   Linguistic Style Matching (LSM):

    -   Perform person- and group-level LSM analysis using a DataFrame to evaluate the alignment of linguistic styles in conversational data.
    -   Supports pairwise LSM calculations for detailed analysis of interpersonal communication dynamics.

-   Narrative Arc Analysis:

    -   Analyze the narrative arc of text data to understand staging, progression, and cognitive tension, offering deep insights into storytelling elements.
    - Includes graphical capabilities, allowing users to visualize narrative structures: staging, plot progression, and cognitive tension over time.

    -   Provides customizable scaling methods and segment options for precise control over the analysis process.

-   Integration with LIWC CLI:

    - Seamlessly execute LIWC commands and capture output for further processing, leveraging the full power of LIWC's linguistic analysis capabilities. This feature includes multithreading support for improved performance and faster analysis across large datasets.

-   Output Options:

    -   Flexible output formats, including CSV, JSON, and direct integration with Pandas DataFrames, ensuring compatibility with a wide range of data analysis workflows.

# Example of use: Analyzing U.S. Presidential Inaugural Addresses

This short example illustrates how to use the `pyliwc` package to analyze the linguistic styles and psychological attributes of inaugural addresses from four U.S. Presidents: George W. Bush, Barack Obama, Donald Trump, and Joe Biden. 


```python

from pyliwc import Liwc
import pandas as pd

# Initialize with the LIWC-22 dictionary
liwc = Liwc('LIWC-22-cli')

# Read the CSV file containing U.S. Presidents' speeches
df = pd.read_csv('../data/US-president.csv')

# Analyze the text data using pyliwc
result_df = liwc.analyze_df(df['Text'], liwc_dict='LIWC22')

# Print the results
print(result_df)
```

**Narrative Arc Analysis** aims to analyze the structure and flow of narratives within text data [@boyd_narrative_2020]. It provides insights into how narratives evolve over time and helps to identify the progression of thematic elements within a text.

```python

# Analyze the narrative arc of the speeches
arc = liwc.narrative_arc(
    df=df, 
    column_names=['Text'], 
    output_individual_data_points=0, 
    scaling_method='0-100', 
    segments_number=5
)
# Results of the narrative arc analysis
print(arc)

# Plot  the results of the LIWC analysis
liwc.plot_narrative_arc(df=arc)

```

The output of the narrative arc analysis is presented in the Table 1 and illustrated in the Figure 1.

**Table 1: Results of Narrative Arc Analysis**

| **President** | **WC** | **Overall** | **Staging** | **Progression** | **Cognive Tension** |
|------------|------------|------------|------------|------------|------------|
| **Bush**     | 1592   | 53.57       | 84.98       | 40.44           | 35.3                |
| **Obama**     | 2389   | 27.59       | 53.9        | 32.93           | -4.05               |
| **Trump**     | 1457   | -10.44      | -5.31       | -0.41           | -25.61              |
| **Biden**     | 2548   | 34.43       | 70.24       | 62.23           | -29.18              |

![**Narrative Arc of U.S.Presidential Inaugural Addresses**](Fig1_narrative_arc.png)

# Conclusion

The LIWC framework has facilitated numerous research projects across the social sciences, demonstrating its broad applicability [@humphreys_automated_2017; @berger_uniting_2019]. By leveraging LIWC's comprehensive dictionaries, `pyliwc` assists researchers in advancing linguistic research, conducting large-scale analyses, and deepening our understanding of human language.

#  Availability and Documentation
`pyliwc` is available under the MIT License. The library may be cloned from the GitHub
repository, or can be installed by pip: pip install pyliwc. Documentation is provided via Quarto, including a quickstart introducing major functionality and a detailed API reference.
Extensive unit testing is employed throughout the library.

# References

