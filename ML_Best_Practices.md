# Operational Best Practices for CSE ML & DS

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

5. To add to the above point, there are some tools and techniques that help to minimize the non-code differences (excluding markdown) in Jupyter cells (e.g. execution counts) but still fall short of being able to provide a clear pathway for code reviews

6. Model management and legacy should be included from day one, take a look at the section on tooling for a couple of options on that including MLFlow and DVC. 

7. Documentation Generation using tools like Sphinx (http://www.sphinx-doc.org/en/master/) while not possible for Jupyter notebooks is quite easy to implement for Python modules.

### Checklist before engagement

1. Obtaining data dictionary from the subject matter experts (if they exist on the customer side) - see here for great example http://www.nyc.gov/html/tlc/downloads/pdf/data_dictionary_trip_records_green.pdf

2. Have a deep-dive discussion with the customer-side and internal (if available) subject matter experts to understand and *document* the data interpretations

3. The above point has an emphasis on *document* because they can sometimes get lost in communication as the team composition changes over the lifetime of a project. It is essential that anyone joining the team be able to quickly get up to speed on what the data is, and what the interpretations of it are both from a software engineers and subject matter experts perspective so that there is a single, cohesive source of truth. 

4. Establishing a shared workflow across the customer and internal teams and the data science and engineering teams is crucial to the success of the project, helping to avoid problems such as large merges, conflicts in the code base towards the end of the project. One can borrow on that from the above section on the workflow for data science and machine learning projects.



## Hierarchy of techniques to attempt based on domain 

Often, deep learning will be the first thing proposed to tackle a particular problem, especially because of its popularity, but more seasoned data science and machine learning engineers will realize that it is not necessary given the size of the dataset and as an intro technique. There are quite a few basic techniques that can be tried at the beginning to get a headstart with *grokking* the data and ultimately, more effectively guide the machine learning experimentation pathway. 

The following sections will serve as a general outline for what can be done from a pathway perspective in trying out different modeling techniques.


### The General Pipeline for machine learning (data science)

* Initially analysis (ask the right domain questions, ask for success criteria, ask for data dictionaries, ask for domain experts)
	* exploratory analysis (feedback loop here - we don't want to trust the data we are handed and want to make sure it conforms to what the domain experts believe) && data visualization
* feature engineering && simple modeling work && data visualization
* optimization and more questions for the client
* deep learning


### Image processing 

* [OpenCV](https://opencv.org/)
	* [tutorials](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html)
	* [PyImageSearch Tutorial](https://www.pyimagesearch.com/2018/07/19/opencv-tutorial-a-guide-to-learn-opencv/)
	* [OpenCV Tutorials](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_tutorials.html)
* [PyImageSearch](https://www.pyimagesearch.com/)
* [Scikit-Image](https://scikit-image.org/)
* [Pillow](https://python-pillow.org/)
* [SimpleCV](http://simplecv.org/)

Overall the basic image processing space is woefully underwhelming.  That said, there is a lot of interesting work in the deep learning context:

* [PyImage Search Basics](https://www.pyimagesearch.com/2017/12/11/image-classification-with-keras-and-deep-learning/)
* [ImageAI example](https://www.analyticsvidhya.com/blog/2018/06/understanding-building-object-detection-model-python/)
* [ImageAI](https://github.com/OlafenwaMoses/ImageAI)
* [YOLOv3 Example](https://github.com/Basasuya/basasuya-yolo3)


DarkNet: (One or the other may not install on your system, so a few are listed)
* [DarkNet Wrapper for Python](https://github.com/madhawav/YOLO3-4-Py)
* [pip DarkNet package](https://pypi.org/project/darknetpy/)


### Natural Language Processing 


Core NLP Libraries


* [NLTK](https://www.nltk.org/)
* [Spacy](https://spacy.io/)
* [Scikit-Learn](http://scikit-learn.org/stable/) - not fully NLP but useful for many NLP tasks
* [NLP examples](https://github.com/susanli2016/NLP-with-Python)
* 

Good for word embeddings:


* [Gensim](https://radimrehurek.com/gensim/)


MultiLingual Support:


* [Polyglot](https://github.com/aboSamoor/polyglot)


### Natural Language Understanding
 

* [Rasa](https://rasa.com/docs/nlu/)


### Basic Prediction Tasks

TODO

### Time Series modeling

TODO

## Tools 

1. Pandas Profiling (https://github.com/pandas-profiling/pandas-profiling) does a great job of generating a HTML (or inline Jupyter) report from a pandas dataframe outlining different descriptive statistics about the data and drawing out a Spearman/Pearson correlation matrix allowing for quick insights into data 

2. When training machine learning models, it can be a slow process with sometimes unimaginative visualizations of the progress (often based on TQDM), you can spice that up by using Bunny (https://github.com/mcpherrinm/bunny) PRO TIP: you can customize the animal to your liking by editing the source code! 

3. Organizing the structure of the Machine Learning and Data Science project - https://github.com/drivendata/cookiecutter-data-science - does a great job of giving a well-defined and consistent structure for organizing the project. In their own words, *"A logical, reasonably standardized, but flexible project structure for doing and sharing data science work."*

4. MLFlow is a great way to capture parameters, artifacts and metrics from a machine learning model without too much effort. Very analogous to the logging module in Python. It provides a nice UI to tabulate the results. https://mlflow.org/ It also serves as a great tool to track *performance metrics for the models across iterations and strategies*

5. Another great tool for management of machine learning models, source code, intermediate data files, etc. is DVC (https://dvc.org/ )

### Datasets

1. Finding datasets to train / pre-train a model based on the domain is a little easier with this tool: https://toolbox.google.com/datasetsearch 

2. Also, great list of datasets here that are commonly used in benchmarking machine learning models: https://archive.ics.uci.edu/ml/index.php 

### Data cleaning and how to make your own labeled datasets

1. Structuring and cleaning of datasets is essential before plugging them into machine learning models ... 

2. There are a few tools like pandas that make manipulation of datasets easy. When 

### Data visualization 

1. Plotly Dash 

2. Altair 

3. Seaborn

4. Matplotlib

### Basic statistical analysis 

### Other libraries 

## Post engagement steps for the partner 

1. One of the big things in ensuring the longevity and continuous use of a machine learning project with a customer is to make sure to include: 

    1. For the ML-fluent technical audience on the customer side 

        1. Clear top-down flow to manage and run the project, reorganzing of the code to follow:
            1. Ingest data 
            2. Data exploration and visualization 
            3. Data cleaning 
            4. Initial feature selection 
            5. Train loop 
            6. Validation loop 
            7. Testing loop 
            8. Capturing metrics 
            9. Visualization of the results 

        2. For the non-ML-fluent technical audience on the customer side

            Have a well defined API that allows the technical folks to easily make changes without necessarily having to dig into the ML-related code

            1. Changing input data 
            2. Changing input features 
            3. Retraining based on new data 
            4. Generating reports and visualizations based on reruns using new data 

        3. For the non-technical audience on the customer side 

            1. Demonstration of meeting the business problem
            2. Exporting graphs on performance of the system 