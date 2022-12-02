# Rhetoric Search
 
Thank you for taking the time to look through the Rhetoric Search project! 

My aim with this work is to create simple rules in identifying English rhetorical devices with the hope of providing additional
inputs into machine learning models.

Many of these devices (e.g., Anadiplosis) are not common knowledge, so I included definitions written by Robert A Harris in his handy text,
"A Handbook of Rhetorical Devices." I reference this book often, as I appreciate that
it seeks to explain rhetoric in terms of its effects, which I don't often see in other writing textbooks.

I left this project as a Jupyter Notebook to show original outputs generated from my machine in the event of setup issues.

## Purpose
My functions will assume that original text columns have been broken out by sentences (a convention used in Tyler Rinker's sentimentr package (https://github.com/trinker/sentimentr). The first iteration of this script is rules based; future updates will probably integrate a machine learning pipeline that leverages transformers. Lambda functions applied onto pandas dataframes are a bit of a bottleneck, so these functions may encounter some difficulty in scaling without that transition (especially the first input step).

Output:
paragraphIndex,           sentIndex,              Text
0                     0              Thanks for downloading
0                     1              This package is useful for identifying rhetoric
0                     0              Have a wonderful day!
1

After the initial dataframe is created, a lambda apply function will detect instances of rhetorical devices.
df['hasSententialAdverb'] = df.apply(lambda x: find_SentAdverb (x,'sentSplit'), axis = 1)

The specific arguments required for each devise change depending on the user requirements, and are currently not documented.

## Setup Notes:
1) Verify a python 3 installation
2) Pip install the libraries included in the Jupyter notebook (spacy, pandas, numpy, Jupyter, re, and nltk). The latter item may not have much use after this commit.
3) Install spacy langauge model with the following command line: 
    "python -m spacy download en_core_web_lg"





## Notes/Assumptions/Disclaimers:

1) This script assumes that identifying rhetorical devices is useful at the sentence level. 
    Flagging instances of rhetorical devices within a sentence is possible and a promising next step for integration
    of machine learning.
2) Resuling analysis on rhetorical devices will need to assume that the author effectively employed them with some intent.
    An author's quality of writing and intended audience will likely effect the output.
3) Given the logic for identifying rhetoric comes from simple language rules, this script will have false positives/negatives.
    Additionally, there is no current handling for large bodies of work. This script will likely be most effective at
    1-20 pages of text.
4) At present time, certain elements of writing style are ignored. 
    Double quotes are converted to single quotes.
    Semi-colons are often treated as commas.
    All text is typically converted to lowcase.
