---
title: "Webscraping with Python"
teaching: 0
exercises: 30
questions:
- "How do I webscrape with Python?"
objectives:
- "Read an html page with Python"
- "Parse an html page with Python"
- "Identify all csv file links in an html page"
- "Save all csv files linked from an html page"
keypoints:
- "Web scrape to save all csv files linked from an html page "
---
## Web Scraping with Python
~~~
import requests #http://docs.python-requests.org/en/master/ 
url = "https://www.sec.gov/foia/docs/foia-logs.htm"
webpage = requests.get(url)
print(webpage.content)
~~~
{: .source}

What can you do with this?
~~~
filename = "SEC_FOIALogs.html"
file = open(filename, 'wb')
~~~
{: .source}
In Jupyter Notebook you can type a question mark after the function name to open a help menu.  So, viewing the help menu after executing `open?` will show that the `'wb'` in `open(filename, 'wb')` will open a new file that is writable with the name `"SEC_FOIALogs.html"` in binary mode.

~~~
file.write(webpage.content)
file.close()
~~~
{: .source}

Using a library to parse the page
~~~
from bs4 import BeautifulSoup #https://www.crummy.com/software/BeautifulSoup/ 
# Beautiful Soup Documentation: https://www.crummy.com/software/BeautifulSoup/bs4/doc/index.html?highlight=href 

soup = BeautifulSoup(webpage.content, 'html.parser')
print(soup.prettify())
print(soup.get_text())
soup.find_all('a')
~~~
{: .source}


Finding all of the links
~~~
for link in soup.find_all('a'):
    print(link.get('href'))
~~~
{: .source}

Find all of the links to csv files
~~~
for link in soup.find_all('a'):
    print(link.get('href').find('csv'))
~~~
{: .source}
Oops. It seems the `.find('csv')` function returns an error.  When we compare it with the earlier list, 
we'll see that there are some spaces. This indicates that there are some links that do not contain URLs, 
for whatever reason. 

To avoid the errors, we first need to test the link to make sure it is not empty.  
~~~
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        print(testlink.find('csv'))
~~~
{: .source}
And, now when we print `testlink.find('csv')`, there are no errors. The `find` function returns either the starting index where the search pattern is located, or a negative 1 to indicate the pattern does not occur in the string.  Now that we understand how the find function works, we can add a few lines to our `for` loop, so it only returns the URL text used in the `href` call.
~~~
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        if(testlink.find('csv') != -1):
            print(testlink)
~~~
{: .source}

Now, we want to save all of the csv files, but we want to use their file names. To do that, 
we need to extract the file name from the `testlink` string. If split the `testlink` string we 
are left with after the for loop is finished running, 
we'll see that it isn't a link that we can work with.
~~~
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        if(testlink.find('csv') != -1):
            keeptestlink = testlink
            print(testlink)

testlink.split('/')[-1]
print('testlink')
~~~
{: .source}

So instead, we create a temp variable that will save the last good, i.e. `.csv` link name.
~~~
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        if(testlink.find('csv') != -1):
            keeptestlink = testlink
            print(testlink)
keeptestlink.split('/')[-1]

headerurl = 'https://www.sec.gov'
print(headerurl+keeptestlink)
~~~
{: .source}
From this, we can create a header string, then print the two strings concatenated to each other to test if 
the string is a valid URL.  Remember, 
we are trying to reconstruct the URLs, so we can save the csv files linked from this page.
~~~
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        if(testlink.find('csv') != -1):
            keeptestlink = testlink
            print(testlink)
keeptestlink.split('/')[-1]

headerurl = 'https://www.sec.gov'
print(headerurl+keeptestlink)
~~~
{: .source}

Make sure you are a good netizen
~~~
import time
for link in soup.find_all('a'):
    testlink = link.get('href')
    if testlink is not None:
        if(testlink.find('csv') != -1):
            print(testlink)
            webpage = requests.get(headerurl+testlink)
            filename = testlink.split('/')[-1]
            file = open(filename, 'wb')
            file.write(webpage.content)
            file.close()
            time.sleep(5)
~~~            
{: .source}

## Web Scraping with Bash
`curl --limit-rate 10240 https://www.sec.gov/foia/docs/foia-logs.htm --output "test_foia.txt"`


{% include links.md %}

