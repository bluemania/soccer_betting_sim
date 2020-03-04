README.md

# Soccer Betting Simulator

The aim of this project is to use simple historic soccer results data to attempt to predict future games. This is primarily a project of learning, and there is no expectation to be able to outperform the market.

The final aim will be to have a website where you can plug in matchups and have odds reported back to you.

There are several steps involved in producing such a model;

* Finding and scraping the data
* Parsing and cleaning the data
* Creating simple features
* Exploratory data analysis
* Exploratory modelling
* Pipeline creation
* Feature creation
* Hold out test setup
* Model selection
* Model API and serving
* Front end setup

We will be working through these part by part.

## Finding and scraping the data

An initial google search yielded a pretty good set of data from [this site](https://www.oddsportal.com/soccer/england/premier-league/results/). It appears to have around 18 years of data, and with 380 matches in a season that amounts to 6,840 data points - a reasonable number for some basic machine learning models.

Some web scraping will be needed to extract the data quickly from all previous years. To do this we will gain an understanding of the website url structure, which website elements we wish to extract, use selenium to automate the extraction, and drive the process using python in a jupyter notebook.

```bash
pip install selenium
```

We also need to download chromedriver from [here](https://chromedriver.chromium.org/downloads).

