Saturday data exploration fun project #1

Automated shell script based tool for finding correlation between data from csv files and creating a ranked list of top entities for the target value, adjusted for population size or something similar. 

For example, find correlation between different charteristics of the cities (number of library book loanes, education level, income level, even number of bars) and also output cities with the largest number of library book loanes adjusted for city populations. 

The data and its structure was taken from www.worldcitiescultureforum.com/data/

For the tool to work, you need to have a collection of csv files with same structure, each containing some data obseration (education level, number of bars and other highly correlated indicators) across some key dimensions (like cities, years, etc.)

Usage:
Run the correlation.sh shell script, giving it a name of the configuraion file as an argument.
For example, "sh correlation.sh congig.txt"

where the config file config.txt, passed as an argument of the shell script, must contain 5 lines (example file is in the repository):
1. Path to the folder with csv data files
2. Full name of the csv file with the target data to find correlations with (for example, number of book library loans) 
3. Full name of the csv file with the population numbers to normalize the data (for example, city population). If no need for such data, then leave a blank line 
4. Name of the columns that distinguishe rows (keys), separated by blanks (for example, city name and date)
5. Name of the column that contains the data in each csv file ("figure" for example case)

Input:
The csv files with data (line of config file) should each have a column with data observations (line 5 in the config file, like column "figure" in the example data), and each observation must be identified by key columns (line 4 in the config file, "city" in the example data.
Names for these columns must be similar acroos the csv files.

Output:
1. A png with the correlation matrix (correlation.png)
2. A csv file (adjusted_NameofYourTargetColumn.csv) with the sorted data for the target indicator adjusted per capita, largest to lowest. The value column containg a relative value, not absolute, for the target indicator per capita to compare values with each other, so the largest one will get value of 1, and others will get values proportional to these largest value.

Inspiration:
Upon receiving a daily portion of infographics from statista.com (recommed to any real-life-data-around-us curious mind), I noticed a ranking of largest public library systems in terms of number of book loans per year. The data wasn't adjusted for population size, so cities like New York, London and Mocow were on the top. 
First, I became curious which cities would have the most book loans per capita, and intuition told me some north european cities must be on the top of that list (cause what else do you do during the 9-month winters in developed Nordic countries - read of course!)
Second, I wanted to see what factors in terms of the city characteristics, culture and etc. correlate with the reading library books.
My hypothesis was that education, number of international students and things like that should correlate positevely, while bars, festivals and etc. should correlate negatively with the number of books loaned.

What have I found?
Given that I only have 31 data points and this all just for fun, so no ambitions to write a paper on this saturday data exploration project, below I present what I found:
1. A north european city (Helsinki) indeed made it to the top of the list of most books loaned per capita, however, only a dissapointing second place
2. City of San Francisco made it to the top. As it turns out, the city has a great public library system and strong reading encouraging programs 
3. Factors like education, number of international students and average income indeed positively correlate with each other and number of books loaned. So rich educated people in the cities with good universities, not surprisingly, either read a lot themselves, or infect other less rich citizens with desire to read the books to become rich and educated. Unfortunately, my super study does not reveal causation, only correlation, so cannot tell you a recipe for becoming rich at this point. As a personal advice: try moving to a city with a great public library system and marry someone there. Chances are the person will have a high income and eduction level.
4. Number of bars and festivals, to my surprise, did not negatively correlate with the number of books loaned. I thought book loving delicate people are shy and do not appreciate too much fun associated with bars and festivals. Hmm. Well, at least number of bars and festivals do positevely correlate with each other. Another words, if there are people in the city who do like to have fun, they will have it in different ways in different places and forms. Reading a book not being on the top of their agenda.
