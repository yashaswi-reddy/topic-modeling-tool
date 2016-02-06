# Introduction #

This is a simple GUI-based application for topic modeling that uses the popular MALLET toolkit for the back-end.
Topic models provide a simple way to analyze large volumes of unlabeled text. A "topic" consists of a cluster of words that frequently occur together. Using contextual clues, topic models can connect words with similar meanings and distinguish between uses of words with multiple meanings. For a general introduction to topic modeling, see for example Probabilistic Topic Models by Steyvers and Griffiths (2007).

For instructions on downloading and installation, please visit the Quick Start page.

The GUI has two main windows - Basic and Advanced.

# Basic Options #

**Input** : The first step is to specify the location of data to import. The GUI supports importing from either a single file or from a directory.
When the input is a single file, each line of the file is taken as a document instance.
When importing from a directory, each text file is taken to be a document instance. In this case, also make sure that the directory contains only text files.

**Output Directory** : This is where all the output files produced by the system go. By default, this is the current directory of the JAR file.

**Number of topics** : This option sets the total number of topics T, fit by the topic modeling algorithm to the input document instances. Changing this parameter allows one to vary the granularity of produced topics. Although there is no hard-and-fast rule to set T, it is usually a good idea to take into account the size of the input dataset. Here are some recommended settings.

|No. of docs (D)|Topics (T)|
|:--------------|:---------|
|1,000          |10 - 20   |
|10,000         |20 - 60   |
|100,000        |50 - 200  |

# Building the Topic Model #

With at least the above basic options set, click on the Train Topics button to run the topic modeling algorithm. This may take several minutes to finish running depending on the size of the dataset (typically 5 minutes for a 10,000 document collection of news articles).

**Model Output**
Output produced by the system is available to the user in mainly two forms - as Comma Separated Value (CSV) files or as static HTML files. Both formats essentially contain similar information, only presented differently.

The CSV output consists of the following 3 files inside the _output`_`csv_ folder.

_Topics`_`Words.csv_ - Top words corresponding to each of the T topics.

_TopicsinDocs.csv_ -  T topics arranged in descending order of importance for each document.

_DocsinTopics.csv_ -  List of top documents (max. of 500) corresponding to each of the T topics.

The HTML output consists of an index file of topics _all`_`topics.html_, T topic web pages and D document web pages. Using the hyperlinks in these pages, one can navigate between topics and documents in a simple and fast manner.

# Advanced Options #

Besides the basic options provided in the first window, there are more advanced parameters that can be set by clicking the Advanced  button.

**Remove stopwords** - If checked, remove a list of "stop words" from the text.

**Stopword file** - Read "stop words" from a file, one per line. Default is Mallet's list of standard English stopwords.

**Preserve case** - If checked, do not force all strings to lowercase.

**No. of iterations** - The number of iterations of Gibbs sampling to run.
<br>Default is:<br>
<br>
- For T<100 default iterations = 200<br>
<br>- For T>500 default iterations = 1000<br>
<br>- Else default iterations = 2*T<br>
<br>
Suggestion: Feel free to use the default setting for number of iterations.  If you run for more iterations, the topic coherence <code>*</code>may<code>*</code> improve.<br>
<br>
<b>No. of topic words printed</b> - The number of most probable words to print for each topic after model estimation.  Default is print top-10 words.  Typical range is top-10 to top-20 words.<br>
<br>
<b>Topic proportion threshold</b> - Do not print topics with proportions less than this threshold value. Good suggested value is 5%.  You may want to increase this threshold for shorter documents.