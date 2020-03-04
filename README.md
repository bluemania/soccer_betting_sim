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

It seems theres a logical pattern to the URL structure given the following examples
## What's the pattern?
* rooturl/soccer/england/premier-league-2004-2005/results/
* rooturl/soccer/england/premier-league-2004-2005/results/#/page/8/
* rooturl/soccer/england/premier-league/results/
* rooturl/soccer/england/premier-league-2018-2019/results/#/page/2/
* rooturl/soccer/england/premier-league/results/#/page/3/

Gives us something like: rooturl/soccer/england/premier-league{years_info}/results/#/page/{number}/

Fortunately it doesnt seem to matter if the number is too high, website returns no data rather than an error.

From here it's a matter of finding the parent element in the website that best contains the data. We do this by using Chrome's inspect page feature. It looks like <table class=" table-main" id="tournamentTable"> is an ideal candidate, as it has an ID.

This seems to do the trick, and the scraping process took about 5 minutes.
