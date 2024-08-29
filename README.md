

![CI](https://github.com/camille1/pyliwc/actions/workflows/test.yaml/badge.svg)

# Welcome to `pyliwc`

> Linguistic Inquiry and Word Count* in Python

# Overview

`pyliwc` is a Python package designed to provide an interface for
analyzing text using the LIWC (Linguistic Inquiry and Word Count) tool.
This package allows users to interact with the LIWC CLI from within
Python, offering features for processing various data formats,
performing linguistic style matching, and analyzing narrative arcs in
text data. It can handle folders, text files or `Pandas` dataframes.

As the LIWC dictionary is proprietary software, this requires that you
have installed the latest version of the LIWC software on your machine,
with an activated licence (academic licence).

# Manifest

The LIWC (Linguistic Inquiry and Word Count) software by James W.
Pennebaker, Roger J. Booth, and Martha E. Francis has been instrumental
for countless researchers in analyzing linguistic and psycholinguistic
data. Linguistic Inquiry and Word Count (LIWC) is the gold standard of
dictionary-based approaches for analyzing word use. It can be used to
study a single individual, groups of people over time, or all of social
media.However, LIWC has traditionally been available through software,
necessitating the usage of an outside software to the Python
environement.

Recognizing the growing popularity of Python in the scientific and
research community, there is an important need for researchers and data
scientists for integrating LIWC directly into their Python workflows.
Thus, `pyliwc` brings (many of) the functionality of LIWC to a wider
audience without the need use the LIWC application as GUI. `pyliwc` is
open-source, released under the MIT license, and is designed to enable
researchers to perform sophisticated linguistic analysis directly in
Python.

# Features

The package offers a wide range of features, including:

1.  **LIWC Text Analysis:**

- Analyze text data from various sources, including CSV files,
  directories, Pandas DataFrames, and individual strings.
- Supports internal dictionaries (e.g., LIWC22, LIWC2015) as well as
  adhoc dictionaries
- Output results directly in a convenient Pandas DataFrame for easy
  integration with other data processing tools.

2.  **Linguistic Style Matching (LSM):**

- Perform person and group-level LSM analysis using a DataFrame to
  evaluate the alignment of linguistic styles in conversational data.
- Supports pairwise LSM calculations for detailed analysis of
  interpersonal communication dynamics.

3.  **Narrative Arc Analysis:**

- Analyze the narrative arc of text data to understand staging,
  progression, and cognitive tension, offering deep insights into
  storytelling elements.
- Graphics capabilities are included, allowing users to visualize
  narrative structures: staging, plot progression, and cognitive tension
  over time.
- Provides customizable scaling methods and segment options for precise
  control over the analysis process.

4.  **Integration with LIWC CLI:** Seamlessly execute LIWC commands and
    capture output for further processing, leveraging the full power of
    LIWC’s linguistic analysis capabilities. Multithreading support for
    improved performance and faster analysis across large datasets.

5.  **Output Options:** Flexible output formats, including CSV, JSON,
    and direct integration with Pandas DataFrames, ensuring
    compatibility with a wide range of data analysis workflows.

------------------------------------------------------------------------

**Missing Features:** In the current version, the following features
have not yet been ported : Word frequencies, Meaning extraction and
Contextualizer.

# Installation

You can install `pyliwc` via pip in Python.

Requirements : \* Python 3.6 or above \* LIWC software

**Using pip**

``` sh
pip install pyliwc
```

# Quickstart

Here’s a quickstart guide, explaining how to use `pyliwc` perform text
analysis.

`Liwc` is the main class for interacting with the LIWC CLI.

``` python
liwc = Liwc(liwc_cli_path='LIWC-22-cli', threads=None, verbose=True) 
```

**Parameters**: - liwc_cli_path (str): Path to the LIWC CLI executable.
Default is ‘LIWC-22-cli’. On WSL, it is required to add .exe at the end
‘LIWC-22-cli.exe’, - threads (int, optional): Number of threads to use.
Defaults to the number of CPU cores minus one. - verbose (bool,
optional): If True, display printing such as progress bar for large
files. Defaults to False.

The main Class of `Pyliwc` is `Liwc`.

<div class="alert alert-info">

Note: Make sure that you have `LIWC-22` software running on your
computer — it is required for using all methods

</div>

<!-- ![liwc22_interface.jpg](images/liwc22_interface.jpg) -->

<img src="./nbs/images/liwc22_interface.jpg" width="350">

**Analyze a string using the default dictionary (LIWC22)**

``` python
from pyliwc import Liwc

liwc = Liwc('LIWC-22-cli.exe')

text = "This is a sample text for LIWC analysis."

r = liwc.analyze_string_to_json(text)
```

    Picked up JAVA_TOOL_OPTIONS: -Dfile.encoding=UTF-8

``` python
{
    'Segment': 1,
    'WC': 8,
    'Analytic': 89.52,
    'Clout': 40.06,
    'Authentic': 15.38,
    'Tone': 20.23,
    'WPS': 8,
    'BigWords': 12.5,
    'Dic': 100,
    'Linguistic': 62.5,
    'function': 50,
    'pronoun': 12.5,
    'ppron': 0,
    'i': 0,
    'we': 0,
    'you': 0,
    ... ,
    'AllPunc': 12.5,
    'Period': 12.5,
    'Comma': 0,
    'QMark': 0,
    'Exclam': 0,
    'Apostro': 0,
    'OtherP': 0,
    'Emoji': 0
}

```

**Analyzing Texts from a `pandas` DataFrame**

``` python
import pandas as pd
df = pd.read_csv('../data/US-president.csv')
```

``` python
from pyliwc import Liwc

liwc = Liwc('LIWC-22-cli.exe')

liwc.analyze_df(df.Text, liwc_dict="LIWC22")
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>

|        | Segment | WC   | Analytic | Clout | Authentic | Tone  | WPS   | BigWords | Dic   | Linguistic | ... | nonflu | filler | AllPunc | Period | Comma | QMark | Exclam | Apostro | OtherP | Emoji |
|--------|---------|------|----------|-------|-----------|-------|-------|----------|-------|------------|-----|--------|--------|---------|--------|-------|-------|--------|---------|--------|-------|
| Row ID |         |      |          |       |           |       |       |          |       |            |     |        |        |         |        |       |       |        |         |        |       |
| 0      | 1       | 1592 | 52.22    | 93.17 | 34.71     | 79.12 | 16.58 | 22.49    | 91.21 | 66.46      | ... | 0      | 0      | 14.20   | 5.97   | 6.53  | 0.06  | 0      | 0.63    | 1.01   | 0     |
| 1      | 1       | 2389 | 51.22    | 95.37 | 36.07     | 54.01 | 20.25 | 19.21    | 90.37 | 68.48      | ... | 0      | 0      | 12.98   | 5.11   | 6.20  | 0.00  | 0      | 0.54    | 1.13   | 0     |
| 2      | 1       | 1457 | 46.94    | 98.19 | 42.58     | 82.46 | 16.19 | 21.89    | 91.08 | 66.78      | ... | 0      | 0      | 15.31   | 6.18   | 7.28  | 0.00  | 0      | 0.75    | 1.10   | 0     |
| 3      | 1       | 2548 | 43.37    | 91.33 | 50.66     | 45.63 | 15.35 | 17.39    | 93.21 | 71.15      | ... | 0      | 0      | 19.66   | 6.28   | 9.11  | 0.39  | 0      | 1.69    | 2.20   | 0     |

<p>4 rows × 119 columns</p>
</div>

- Change to other dictionary: “LIWC2015”

``` python
liwc_dict = "LIWC2015" 

liwc.analyze_df(df.Text, liwc_dict=liwc_dict)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
&#10;    .dataframe tbody tr th {
        vertical-align: top;
    }
&#10;    .dataframe thead th {
        text-align: right;
    }
</style>

|        | Segment | WC   | Analytic | Clout | Authentic | Tone  | WPS   | Sixltr | Dic   | function | ... | Colon | SemiC | QMark | Exclam | Dash | Quote | Apostro | Parenth | OtherP | Emoji |
|--------|---------|------|----------|-------|-----------|-------|-------|--------|-------|----------|-----|-------|-------|-------|--------|------|-------|---------|---------|--------|-------|
| Row ID |         |      |          |       |           |       |       |        |       |          |     |       |       |       |        |      |       |         |         |        |       |
| 0      | 1       | 1592 | 65.12    | 92.38 | 30.27     | 89.13 | 16.58 | 22.49  | 89.38 | 53.33    | ... | 0.38  | 0.38  | 0.06  | 0      | 0.00 | 0.25  | 0.63    | 0       | 0.00   | 0     |
| 1      | 1       | 2389 | 64.97    | 93.13 | 33.34     | 74.15 | 20.25 | 19.21  | 87.57 | 55.04    | ... | 0.13  | 0.21  | 0.00  | 0      | 0.63 | 0.08  | 0.54    | 0       | 0.08   | 0     |
| 2      | 1       | 1457 | 57.63    | 96.73 | 40.07     | 87.87 | 16.19 | 21.89  | 87.99 | 53.12    | ... | 0.55  | 0.34  | 0.00  | 0      | 0.07 | 0.14  | 0.75    | 0       | 0.00   | 0     |
| 3      | 1       | 2548 | 58.30    | 91.76 | 44.26     | 62.24 | 15.35 | 17.39  | 90.07 | 55.42    | ... | 0.90  | 0.39  | 0.39  | 0      | 0.16 | 0.63  | 1.69    | 0       | 0.12   | 0     |

<p>4 rows × 95 columns</p>
</div>
