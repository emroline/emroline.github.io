---
#subtitle: "Algorithms"
#author: anuroop
categories: [ Python, Python Examples]
#excerpt: 
tags: []
under_development: false
---

Here We will create web crawlers using Python3.
<!--end of excerpt-->

> Modules used: requests, beautifulsoup4, re.


### Crawler that extracts all the links from a webpage

Steps:
1. Get a url
2. Extract the source code of the web page at given url as string.
3. Extract and store href attribute of all the {% raw %}<a></a>{% endraw %} tags, in a set.
4. Return the set containing all the links.

Following is the complete code:
{% highlight python %}
{% raw %}

# Python3 web crawler
import requests 
from bs4 import BeautifulSoup 

def crawler(url):
    links = set() # We are using a set because set can only contain unique elements
    html_source_code = requests.get(url).text # source code of webpage
    soup = BeautifulSoup(html_source_code, 'html.parser')
    for link in soup.find_all('a'):
        links.add(link.get('href'))
    return links

  
# Driver code 
if __name__ == '__main__': 
    links = crawler("https://www.emroline.com/how-to-create-web-crawler-using-python/")
    for link in links:
        print(link)

{% endraw %}
{% endhighlight %}

### Crawler that extracts most frequent words

Steps:
1. Get a url
2. Extract the source code of the web page at given url as string.
3. Replace all the extra symbols with whitespaces.
3. Split the source string into words.
4. Store each word in a dictionary with their frequency.
5. Now extract the words with most frequency.

Following is the complete code:
{% highlight python %}
{% raw %}

# Python3 web crawler
import requests 
from bs4 import BeautifulSoup 
import operator 
from collections import Counter 
import re

# Extracts source code of webpage at given url as string
# Replaces all the extra symbols with white space.
# Splits the entire source code string into words.
# Stores all the words based on their frequency.
def crawler(url):
    wordlist = []
    html_source_code = requests.get(url).text
    soup = BeautifulSoup(html_source_code, 'html.parser')
    # the text on the web page is between <section></section> tags
    content = soup.find('section').text
    # use "content = soup.get_text()" to read text from whole source code.

    # here we have used regular expressions to replace all symbols with space.
    # [^\w] will match anything that's not alphanumeric or underscore
    content = re.sub(r'[^\w]', ' ', content)
    words = content.lower().split()
    for word in words:
        wordlist.append(word)
    create_dictionary(wordlist)
  
# Creates a dictionary containing each word's frequency.
# Returns list of top 10 most frequent words 
def create_dictionary(wordlist): 
    word_dict = {} 
    for word in wordlist: 
        if word in word_dict: 
            word_dict[word] += 1
        else: 
            word_dict[word] = 1
    c = Counter(word_dict) 
    # returns the most occurring elements 
    top = c.most_common(10) 
    print(top)

# Driver code 
if __name__ == '__main__': 
    words = crawler("https://www.emroline.com/papers/how-to-create-web-crawler-using-python") 


{% endraw %}
{% endhighlight %}
