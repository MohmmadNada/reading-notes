# Web Scraping

## How to Web Scrape with Python in 4 Minutes
### Web Scraping
Web scraping is a technique to automatically access and extract large amounts of information from a website

Important notes about web scraping:
1. Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.
2. Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.

### Inspecting the Website
by inspect , and select the p , will get the link 

### Python Code
We start by importing the following libraries.
``` import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```
we set the url to the website and access the site with our requests library.
```
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```
parse the html with BeautifulSoup
```
soup = BeautifulSoup(response.text, “html.parser”)
```
```
soup.findAll('a')
```

Next, let’s extract the actual link that we want.
```
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```
We can use our urllib.request library to download this file path to our computer
```
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```
 should include this line of code so that we can pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.
```
time.sleep(1)

```

full code 
```
# Import libraries
import requests
import urllib.request
import time
from bs4 import BeautifulSoup

# Set the URL you want to webscrape from
url = 'http://web.mta.info/developers/turnstile.html'

# Connect to the URL
response = requests.get(url)

# Parse HTML and save to BeautifulSoup object¶
soup = BeautifulSoup(response.text, "html.parser")

# To download the whole data set, let's do a for loop through all a tags
line_count = 1 #variable to track what line you are on
for one_a_tag in soup.findAll('a'):  #'a' tags are for links
    if line_count >= 36: #code for text files starts at line 36
        link = one_a_tag['href']
        download_url = 'http://web.mta.info/developers/'+ link
        urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:]) 
        time.sleep(1) #pause the code for a sec
    #add 1 for next line
    line_count +=1
```
Resources :
* [Web Scrape with Python in 4 minutes](https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460)
* [What is Web Scraping?](https://en.wikipedia.org/wiki/Web_scraping)
* [How to scrape websites without getting blocked](https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/)
* [Track Amazon Prices](https://www.youtube.com/watch?v=Bg9r_yLk7VY)
* [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/)

