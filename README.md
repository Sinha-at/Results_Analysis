# Results_Analysis
## _Test your conversational search system and analyze the results_


Results_Analysis is a package that allows users to:

- Interpret the results of a data file
- Compare the results of two files

This package is based on a research paper written by Abhishek Kaushik: https://arxiv.org/pdf/2104.03940.pdf,
if you are using the package please give credits to this research paper.

## Libraries used

Results_Analysis uses several python libraries to work properly:

Manipulate excel file:
- [pandas](https://pypi.org/project/pandas/) - Open excel and manipulate file
- [openpyxl](https://openpyxl.readthedocs.io/en/stable/) - Excel manipulation and save
- [IPython](https://pypi.org/project/ipython/) - Display dataframe
- [formulas](https://pypi.org/project/formulas/) - Compute and calculate excel formula
- [win32com](https://pypi.org/project/pywin32/) - Use and write excel files

graphics:
- [numpy](https://numpy.org/doc/1.23/)- Arrange data for graphic representation
- [dataframe_image](https://pypi.org/project/dataframe-image/0.0.7/)- Dataframe to image
- [aspose](https://pypi.org/project/aspose-words/)- Convert documents
- [wordcloud](https://pypi.org/project/wordcloud/)- Word cloud generator
- [matplotlib](https://matplotlib.org/)- Plot graph and chart

other:
- [warnings](https://docs.python.org/3/library/warnings.html)- Deal with python's warning
- [os](https://docs.python.org/3/library/os.path.html)- Path manipulation
- [pathlib](https://pathlib.readthedocs.io/en/pep428/)- Path manipulation
- [scipy](https://docs.scipy.org/doc/scipy/reference/)- Statistical testing (t-test/welsh-test)
- [statsmodels](https://www.statsmodels.org/stable/index.html)- Statistical testing (z-test)
- [imp](https://docs.python.org/3/library/imp.html)- Find module path
- [wget](https://pypi.org/project/wget/)- Download file from url


Results_Analysis itself is shared in a [GitHub repository](https://github.com/Sinha1111/Results_Analysis).

## File format
Files must be formatted excactly like [this file](https://docs.google.com/spreadsheets/d/1hjsJRMdZKLr5uegLY-H69nxv5on66eMK/edit?usp=sharing&ouid=106091935059439566018&rtpof=true&sd=true), make sure your matrices are in the correct order: Demographic Info (A-M), Pre-search Questionnaire (N-R), Post-Search Questionnaire (T-AQ), User Experience (AR-AY), Cognitive Load (AZ-BE), Software Usability: [System (BF-BK), Information(BL-BP), Interface (BQ-BT), overall (BU)], Searching as learning:[Search formulation (BV-BX), Content selection (BY-CC), Interaction with content (CD-CG), Post Search (CH-CK)], Knowledge gain (CL-CN)

## Default statistical test used

- Both sample sizes <=30 --> T-test
- Both sample sizes >30 --> Z-test
- Different sizes --> Welsh-test

## Installation

_Results_Analysis requires a version of python over 3 to run._

Download the package
```sh
pip install Results_Analysis
```

Import the package

```sh
import Results_Analysis
```
For this documentation we will use:
```sh
import Results_Analysis as ra
```

##Update the package:

```sh
pip install Results_Analysis --upgrade
```


## How are the results calculated ?

Quantitative analysis: This is based on the mean score of the participants in the study, statistical testing is carried out based on the population and nature of the experiment. When comparing a conventional system and a conversational system, we are able to perform dependent significant testing, since the population undertaking the experiment in both settings is the same. And, if we are comparing the mean score of the conversational interface with a standard benchmark, we can conduct independent significance testing

Qualitative analysis:  The different dimensions are annotated based on comparison of the mean values for the study participants. A mean value between 2 and 4 represents a neutral evaluation of the corresponding scale (yellow dimension), a mean > 4 represents a positive evaluation (green dimension) and mean < 2 represents a negative evaluation (red dimension). After comparing the mean, each question is annotated based on the dimensions. The dimensions are annotated by two independent analysts with the Kappa coefficient (Approx .85), then the dimension is counted for each section. As per the dimension, the section of the interface that needs to be improved can be identified. For example, if software usability gets more red dimensions, then the interface needs to be improved with respect to software usability.


# Analysis of one file

## Create Object

Create an object for one file
```sh
MyFile=ra.dataFile(path to your file)
```
> This operation usually takes a few minutes

## User Experience

## Quantitative analysis
Every one of these functions can take a save argument 'pdf' that will download the information in a pdf format

Information on:
DT 
```sh
MyFile.dt()
MyFile.dt(save='pdf')
```

Confidence Intervals
```sh
MyFile.confidence_Intervals()
MyFile.confidence_Intervals(save='pdf')
```

Scale Consistency
```sh
MyFile.scale_Consistency()
MyFile.scale_Consistency(save='pdf')
```

Benchmark
```sh
MyFile.benchmark()
MyFile.benchmark(save='pdf')
```

Results
```sh
MyFile.results()
MyFile.results(save='pdf')
```

Inconsistencies
```sh
MyFile.inconsistencies()
MyFile.inconsistencies(save='pdf')
```

#### Qualitative analysis

```sh
MyFile.User_Experience_Qual_Analysis()
MyFile.User_Experience_Qual_Analysis(save='pdf')
```
## Cognitive load
#### Quantitative analysis
Display information on the cognitive load part of the results. Can take a save argument 'pdf' that will download the information in a pdf format
```sh
MyFile.cognitive_load()
MyFile.cognitive_load(save='pdf')
```
#### Qualitative analysis
```sh
MyFile.cognitive_load_Qual_Analysis()
MyFile.cognitive_load_Qual_Analysis(save='pdf')
```
## Software Usability
Display all the comments about the Software Usability part of the results. Can take a save argument 'pdf' that will download the information in a pdf format and a type argument 'WordCloud' that will display the information in the format of a word cloud.
```sh
MyFile.Software_Usability_Coments(type='WordCloud', save='pdf')
```
#### Quantitative analysis
Display information on the Software Usability part of the results. Can take a save argument 'pdf' that will download the information in a pdf format
```sh
MyFile.Software_Usability()
MyFile.Software_Usability(save='pdf')
```
#### Qualitative analysis
```sh
MyFile..Software_Usability_Qual()
MyFile..Software_Usability_Qual(save='pdf')
```

## Searching Learning
#### Quantitative analysis
Display information on the searching as learning part of the results. Can take a save argument 'pdf' that will download the information in a pdf format
```sh
MyFile.Searching_Learning()
MyFile.Searching_Learning(save='pdf')
```
#### Qualitative analysis
```sh
MyFile.Searching_Learning_Qual()
MyFile.Searching_Learning_Qual(save='pdf')
```
##Knowledge Gain
#### Quantitative analysis
Display information on the Knowledge Gain part of the results. Can take a save argument 'pdf' that will download the information in a pdf format
```sh
MyFile.Knowledge_Gain()
MyFile.Knowledge_Gain(save='pdf')
```
#### Qualitative analysis
```sh
 MyFile.Knowledge_Gain_Qual_Analysis()
 MyFile.Knowledge_Gain_Qual_Analysis(save='pdf')
```

# Analysis of two file

## Create Object

Create an object for comparing two files.
Parameters: 
- path-path2: path to your two files
- link: the type of link between the data. Either dependant or independent (default= independent)
- test_diff_size: type of test used if the two samples are of different sizes. Can be welsh-test, t-test or z-test
```sh
CompFile=ra.ComparedDataFile(path to your first file, path to your second file)
CompFile=ra.ComparedDataFile(path to your first file,path to your second file,link='dependant', test_diff_size='welsh-test')
```
> This operation usually takes a few minutes
## User Experience

## Quantitative analysis
Every one of these functions can take a save argument 'pdf' that will download the information in a pdf format

Information on:
DT 
```sh
CompFile.dt()
CompFile.dt(save='pdf')
```

Confidence Intervals
```sh
CompFile.confidence_Intervals()
CompFile.confidence_Intervals(save='pdf')
```

Scale Consistency
```sh
CompFile.scale_Consistency()
CompFile.scale_Consistency(save='pdf')
```

Benchmark
```sh
CompFile.benchmark()
CompFile.benchmark(save='pdf')
```

Results
```sh
CompFile.results()
CompFile.results(save='pdf')
```

Inconsistencies
```sh
CompFile.inconsistencies()
CompFile.inconsistencies(save='pdf')
```

#### Qualitative analysis

```sh
CompFile.User_Experience_Qual_Analysis()
CompFile.User_Experience_Qual_Analysis(save='pdf')
```
## Cognitive load
#### Quantitative analysis
Display information on the cognitive load part of the results.
Parameters: 
- format (String): ‘tab’ to display the information in a table format or ‘graph’ to display the information in a graph format
- save (String): ‘pdf’ to download the pdf version
- alpha (float): level of significance. Default=0.05

```sh
CompFile.cognitive_load(format='graph')
CompFile.cognitive_load(format='tab', format='pdf', alpha = 0.05)
```
#### Qualitative analysis
```sh
CompFile.cognitive_load_Qual_Analysis()
CompFile.cognitive_load_Qual_Analysis(save='pdf')
```
## Software Usability
Display all the comments about the Software Usability part of the results. Can take a save argument 'pdf' that will download the information in a pdf format and a type argument 'WordCloud' that will display the information in the format of a word cloud.
Parameters: 
- format (String): ‘tab’ to display the information in a table format or ‘graph’ to display the information in a graph format
- save (String): ‘pdf’ to download the pdf version
- alpha (float): level of significance. Default=0.05
```sh
CompFile.Software_Usability_Coments(type='WordCloud', save='pdf')
```
#### Quantitative analysis
Display information on the Software Usability part of the results. Can take a save argument 'pdf' that will download the information in a pdf format
Parameters: 
- format (String): ‘tab’ to display the information in a table format or ‘graph’ to display the information in a graph format
- save (String): ‘pdf’ to download the pdf version
- alpha (float): level of significance. Default=0.05
```sh
CompFile.Software_Usability(format='graph')
CompFile.Software_Usability(format='tab', save='pdf', alpha = 0.05)
```
#### Qualitative analysis
```sh
CompFile.Software_Usability_Qual()
CompFile.Software_Usability_Qual(save='pdf')
```

## Searching Learning
#### Quantitative analysis
Display information on the searching as learning part of the results.
Parameters: 
- format (String): ‘tab’ to display the information in a table format or ‘graph’ to display the information in a graph format
- save (String): ‘pdf’ to download the pdf version
- alpha (float): level of significance. Default=0.05
```sh
CompFile.Searching_Learning(format='graph')
CompFile.Searching_Learning(format='tab', save='pdf', alpha = 0.05)
```
#### Qualitative analysis
```sh
CompFile.Searching_Learning_Qual()
CompFile.Searching_Learning_Qual(save='pdf')
```
##Knowledge Gain
#### Quantitative analysis
Display information on the Knowledge Gain part of the results.
Parameters: 
- format (String): ‘tab’ to display the information in a table format or ‘graph’ to display the information in a graph format
- save (String): ‘pdf’ to download the pdf version
- alpha (float): level of significance. Default=0.05
```sh
CompFile.Knowledge_Gain(format='graph')
CompFile.Knowledge_Gain(format='tab', save='pdf', alpha = 0.05)
```
#### Qualitative analysis
```sh
CompFile.Knowledge_Gain_Qual_Analysis()
CompFile.Knowledge_Gain_Qual_Analysis(save='pdf')
```

## Help

Information about every possible function and their parameters
```sh
 CompFile.info()
 MyFile.info()
```

## Examples

[Results_Analysis.ipynb]()

## License
MIT
