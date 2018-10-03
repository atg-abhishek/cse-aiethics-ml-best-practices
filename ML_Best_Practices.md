# cse-aiethics-ml-best-practices

## General Guidelines 

### Purpose statement 

This repository will serve as a best practices document for the CSE group at Microsoft. The vision being to align not only with industry best practices so that we can derive the maximum value out of each of our engagements but to also help our partners have a well-documented roadmap to follow post our engagement with them.

## Contributing guidelines 

TODO: add the MSFT guidelines

### Engineering best practices for Data Science 

#### Workflow for Data Science

Workflow between software engineers (for the purpose of this document, the team that is working on the operationalization of the machine learning and data science pieces coming out of the Data Science team) and data science team is of crucial importance to ensure the rigor of engineering fundamentals and the reproducibility of the experimental nature of machine learning development.

One of the main points here is the workflow of iterating in a Jupyter notebook and sharing code written in that. To that end, we propose the following as a workflow: 

1. Code written in a notebook is great for experimentation (barring hidden state and other problems as brilliantly outlined in this talk by Joel Grus at JupyterCon 2018) and hence shouldn't be committed in lieu of code that is meant to run in production. 

2. Periodically (determined by the cadence of the sprint in an agile setting) the code from Jupyter should be transferred over to Python modules and subjected to: 

    1. Unit Testing 
    2. Linting (flake8 or pylint)
    3. ...

3. Linting is possible in Jupyter as well, see the following subsection link for information on that (TODO: link to be added)

4. Git is unable to resolve effectively the differences in Jupyter notebook versions that are committed into version control and hence should not be used as a mechanism for review of the code

5. To add to the above point, 

### Checklist before engagement

1. Obtaining data dictionary from the subject matter experts (if they exist on the customer side) - see here for great example http://www.nyc.gov/html/tlc/downloads/pdf/data_dictionary_trip_records_green.pdf

2. Have a deep-dive discussion with the customer-side and internal (if available) subject matter experts to understand and *document* the data interpretations

3. The above point has an emphasis on *document* because they can sometimes get lost in communication as the team composition changes over the lifetime of a project. It is essential that anyone joining the team be able to quickly get up to speed on what the data is, and what the interpretations of it are both from a software engineers and subject matter experts perspective so that there is a single, cohesive source of truth. 

## Hierarchy of techniques to attempt based on domain 

Often, deep learning 

### Image processing 

### Natural Language Processing 

## Tools 

### Data visualization 

### Basic statistical analysis 

### Other libraries 

## Post engagement steps for the partner 
