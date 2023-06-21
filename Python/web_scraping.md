--------------------------------------------------------------------------------
= Web Scraping =
--------------------------------------------------------------------------------
  Requests Module            |
                             |
  Getting page / content     | Python has a requests library that makes getting
                             | content really easy.
                             |
                             | import requests
                             |
                             | webpage = requests.get('https://www.somepage.com/page')
                             |
  outputting content         | webpage.content
                             |
                             |
  *BeautifulSoup Module*       |
                             |
  outputting document        | from bs4 import BeautifulSoup
                             |
                             | doc = BeautifulSoup(webpage.content, 'html.parser')
                             |
                             | print(doc.prettify())      <-- prettify method to format output
                             |
  Output specific tag        | doc.title                  <-- doc is a BeautifulSoup4 object
  (will return 1st tag)      |
                             |
  Collect all tags           | doc.find_all('p')          <-- collects all "p" tags
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
