# API reference


<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Initialization

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L19"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc

>      Liwc (liwc_cli_path:str='LIWC-22-cli', threads:Optional[int]=None,
>            verbose:bool=False)

*Initialize the LIWC Class.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>liwc_cli_path</td>
<td>str</td>
<td>LIWC-22-cli</td>
<td>LIWC CLI Path.</td>
</tr>
<tr class="even">
<td>threads</td>
<td>Optional</td>
<td>None</td>
<td>Number of threads to use. Defaults to the number of CPU cores minus
one.</td>
</tr>
<tr class="odd">
<td>verbose</td>
<td>bool</td>
<td>False</td>
<td>Display printing and progress bar. Defaults to False.</td>
</tr>
</tbody>
</table>

## LIWC Analysis

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L164"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_string_to_json

>      Liwc.analyze_string_to_json (input_string:str, liwc_dict:str='LIWC22')

\*Analyze a single string and return the result as JSON.

Returns: dict:\*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>input_string</td>
<td>str</td>
<td></td>
<td>The string to analyze.</td>
</tr>
<tr class="even">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td>Dictionary to use for analysis. Defaults to “LIWC22”.</td>
</tr>
<tr class="odd">
<td><strong>Returns</strong></td>
<td><strong>dict</strong></td>
<td></td>
<td><strong>Analysis results in JSON format.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L146"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_string

>      Liwc.analyze_string (input_string:str, output_location:str,
>                           liwc_dict:str='LIWC22')

*Analyze a single string using LIWC and save to csv.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>input_string</td>
<td>str</td>
<td></td>
<td>The string to analyze.</td>
</tr>
<tr class="even">
<td>output_location</td>
<td>str</td>
<td></td>
<td>Path to save the analysis output (.csv).</td>
</tr>
<tr class="odd">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td></td>
</tr>
<tr class="even">
<td><strong>Returns</strong></td>
<td><strong>None</strong></td>
<td></td>
<td><strong>Dictionary to use for analysis. Defaults to
“LIWC22”.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L118"
target="_blank" style="float:right; font-size:smaller">source</a>

### analyze_df2

>      analyze_df2 (df:pandas.core.frame.DataFrame, text_col:str, index_col:str,
>                   return_input:bool=False, liwc_dict:str='LIWC22')

*Analyze text data from a DataFrame using LIWC.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>df</td>
<td>DataFrame</td>
<td></td>
<td>name of the dataframe.</td>
</tr>
<tr class="even">
<td>text_col</td>
<td>str</td>
<td></td>
<td>Name of the column containing text data.</td>
</tr>
<tr class="odd">
<td>index_col</td>
<td>str</td>
<td></td>
<td>Index of the df to be returned</td>
</tr>
<tr class="even">
<td>return_input</td>
<td>bool</td>
<td>False</td>
<td>Whether to return the input text with the output. Defaults to
False.</td>
</tr>
<tr class="odd">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td>Dictionary to use for analysis. Defaults to “LIWC22”.</td>
</tr>
<tr class="even">
<td><strong>Returns</strong></td>
<td><strong>DataFrame</strong></td>
<td></td>
<td><strong>pd.DataFrame: DataFrame containing the analysis
results.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L97"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_df

>      Liwc.analyze_df (text:pandas.core.series.Series, return_input:bool=False,
>                       liwc_dict:str='LIWC22')

*Analyze text data from a DataFrame using LIWC.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>text</td>
<td>Series</td>
<td></td>
<td>Pandas Series containing text data.</td>
</tr>
<tr class="even">
<td>return_input</td>
<td>bool</td>
<td>False</td>
<td>Whether to return the input text with the output. Defaults to
False.</td>
</tr>
<tr class="odd">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td>Dictionary to use for analysis. Defaults to “LIWC22”.</td>
</tr>
<tr class="even">
<td><strong>Returns</strong></td>
<td><strong>DataFrame</strong></td>
<td></td>
<td><strong>pd.DataFrame: DataFrame containing the analysis
results.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L76"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_folder

>      Liwc.analyze_folder (input_folder:str, output_location:str,
>                           liwc_dict:str='LIWC22')

*Analyze all text files in a folder using LIWC.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>input_folder</td>
<td>str</td>
<td></td>
<td>Path to the folder containing text files.</td>
</tr>
<tr class="even">
<td>output_location</td>
<td>str</td>
<td></td>
<td>Path to save the analysis output.</td>
</tr>
<tr class="odd">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td></td>
</tr>
<tr class="even">
<td><strong>Returns</strong></td>
<td><strong>None</strong></td>
<td></td>
<td><strong>Dictionary to use for analysis. Defaults to
“LIWC22”.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L54"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_csv

>      Liwc.analyze_csv (input_file:str, output_location:str,
>                        row_id_indices:str, column_indices:str,
>                        liwc_dict:str='LIWC22')

*Analyze text data from a CSV file using LIWC.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>input_file</td>
<td>str</td>
<td></td>
<td>Path to the input CSV file.</td>
</tr>
<tr class="even">
<td>output_location</td>
<td>str</td>
<td></td>
<td>Path to save the analysis output.</td>
</tr>
<tr class="odd">
<td>row_id_indices</td>
<td>str</td>
<td></td>
<td>Indices of row IDs in the CSV.</td>
</tr>
<tr class="even">
<td>column_indices</td>
<td>str</td>
<td></td>
<td>Indices of text columns in the CSV.</td>
</tr>
<tr class="odd">
<td>liwc_dict</td>
<td>str</td>
<td>LIWC22</td>
<td></td>
</tr>
<tr class="even">
<td><strong>Returns</strong></td>
<td><strong>None</strong></td>
<td></td>
<td><strong>Dictionary to use for analysis. Defaults to
“LIWC22”.</strong></td>
</tr>
</tbody>
</table>

``` python
# liwc = Liwc('LIWC-22-cli.exe', verbose=True)
# s = "As Leclerc entered the Invalides, with his cortege of exaltation in the sun of Africa and the battles of Alsace, enter here, Jean Moulin, with your terrible cortege."
# r = liwc.analyze_string_to_json(s)
```

``` python
# desired_keys = ['WC', 'Analytic', 'Clout', 'Authentic', 'Tone']
# filtered_dict = {key: r[key] for key in desired_keys if key in r}
# print(filtered_dict)
```

## Language Style Matching

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L346"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.analyze_lsm

>      Liwc.analyze_lsm (df:pandas.core.frame.DataFrame,
>                        calculate_lsm:str='person-and-group',
>                        group_column:str='GroupID',
>                        person_column:str='PersonID', text_column:str='Text',
>                        output_type:str='pairwise', expanded_output:bool=False,
>                        omit_speakers_number_of_turns:int=0,
>                        omit_speakers_word_count:int=10,
>                        segmentation:str='none')

*Analyzes Linguistic Style Matching (LSM) based on the provided
DataFrame.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>df</td>
<td>DataFrame</td>
<td></td>
<td>Input DataFrame containing the text data to be analyzed.</td>
</tr>
<tr class="even">
<td>calculate_lsm</td>
<td>str</td>
<td>person-and-group</td>
<td>Sets the type of LSM calculation. Options are:<br>- “person”:
Calculate only person-level LSM.<br>- “group”: Calculate only
group-level LSM.<br>- “person-and-group”: Calculate both person and
group-level LSM.<br>Default is “person-and-group”.</td>
</tr>
<tr class="odd">
<td>group_column</td>
<td>str</td>
<td>GroupID</td>
<td>The column name in <code>df</code> representing the Group ID.
Default is ‘GroupID’.</td>
</tr>
<tr class="even">
<td>person_column</td>
<td>str</td>
<td>PersonID</td>
<td>The column name in <code>df</code> representing the Person ID.
Default is ‘PersonID’.</td>
</tr>
<tr class="odd">
<td>text_column</td>
<td>str</td>
<td>Text</td>
<td>The column name in <code>df</code> representing the text data.
Default is ‘Text’.</td>
</tr>
<tr class="even">
<td>output_type</td>
<td>str</td>
<td>pairwise</td>
<td>Sets the type of output. Options are:<br>- “one-to-many”:
One-to-many comparison.<br>- “pairwise”: Pairwise comparison.<br>Default
is “pairwise”.</td>
</tr>
<tr class="odd">
<td>expanded_output</td>
<td>bool</td>
<td>False</td>
<td>Adds an option to get an expanded LSM output. Default is False.</td>
</tr>
<tr class="even">
<td>omit_speakers_number_of_turns</td>
<td>int</td>
<td>0</td>
<td></td>
</tr>
<tr class="odd">
<td>omit_speakers_word_count</td>
<td>int</td>
<td>10</td>
<td>Omit speakers if the word count is less than this value. Default is
10.</td>
</tr>
<tr class="even">
<td>segmentation</td>
<td>str</td>
<td>none</td>
<td>Segmentation options for splitting the text. Options are:<br>-
“none”: No segmentation.<br>- “not=<number>”: Number of turns per
segment.<br>- “nofst=<number>”: Number of segments by speaker turn.<br>-
“nofwc=<number>”: Number of segments by word count.<br>- “now=<number>”:
Number of words per segment.<br>- “boc=<characters>”: Segmentation based
on characters.<br>- “regexp=<regex>”: Segmentation based on a regular
expression.<br>Default is “none”.</td>
</tr>
<tr class="odd">
<td><strong>Returns</strong></td>
<td><strong>Union</strong></td>
<td></td>
<td><strong>The resulting LSM analysis. The output format depends on the
specified <code>output_format</code>.</strong></td>
</tr>
</tbody>
</table>

## Narrative arc

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L582"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.plot_narrative_arc

>      Liwc.plot_narrative_arc (df:pandas.core.frame.DataFrame,
>                               legend_labels:list=None)

*Plots the narrative arc for the given DataFrame, showing Staging, Plot
Progression, and Cognitive Tension.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>df</td>
<td>DataFrame</td>
<td></td>
<td>Input DataFrame containing the narrative arc data.<br>Note:
‘output_individual_data_points=True’ in narrative_arc to get all
required data to plot the narractive arc.</td>
</tr>
<tr class="even">
<td>legend_labels</td>
<td>list</td>
<td>None</td>
<td>List of labels for the legend, corresponding to each row in the
DataFrame.</td>
</tr>
<tr class="odd">
<td><strong>Returns</strong></td>
<td><strong>Figure</strong></td>
<td></td>
<td><strong>The resulting plot figure of the narrative
arcs.</strong></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

<a
href="https://github.com/camillelacan/pyliwc/blob/main/pyliwc/core.py#L493"
target="_blank" style="float:right; font-size:smaller">source</a>

### Liwc.narrative_arc

>      Liwc.narrative_arc (df:pandas.core.frame.DataFrame,
>                          column_names:Optional[list]=None,
>                          output_individual_data_points:bool=True,
>                          scaling_method:str='0-100', segments_number:int=5,
>                          skip_wc:int=10)

*Analyzes the narrative arc of text data based on the provided
DataFrame.*

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>df</td>
<td>DataFrame</td>
<td></td>
<td>Input DataFrame containing the text data to be analyzed.</td>
</tr>
<tr class="even">
<td>column_names</td>
<td>Optional</td>
<td>None</td>
<td>List of column names in <code>df</code> that should be processed. If
None, all columns are processed. Default is None.</td>
</tr>
<tr class="odd">
<td>output_individual_data_points</td>
<td>bool</td>
<td>True</td>
<td>If True, outputs individual data points for each segment. If False,
aggregates the data. Default is True.</td>
</tr>
<tr class="even">
<td>scaling_method</td>
<td>str</td>
<td>0-100</td>
<td>Method for scaling the data. Options are:<br>- “0-100”: Scale values
between 0 and 100.<br>- “Z-score”: Scale values using Z-score
normalization.<br>Default is “0-100”.</td>
</tr>
<tr class="odd">
<td>segments_number</td>
<td>int</td>
<td>5</td>
<td>Number of segments into which the text is divided for analysis.
Default is 5.</td>
</tr>
<tr class="even">
<td>skip_wc</td>
<td>int</td>
<td>10</td>
<td>Skip any texts with a word count less than this value. Default is
10.</td>
</tr>
<tr class="odd">
<td><strong>Returns</strong></td>
<td><strong>DataFrame</strong></td>
<td></td>
<td><strong>The resulting DataFrame with the narrative arc
analysis.</strong></td>
</tr>
</tbody>
</table>