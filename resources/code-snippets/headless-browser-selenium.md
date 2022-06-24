# Headless browser (Selenium)

Every Lair's base container includes the [Chrome headless browser](https://developers.google.com/web/updates/2017/04/headless-chrome), which you can interact with using Selenium or a similar package.

### Python

```python
from selenium import webdriver

options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
options.add_argument('user-agent=Mozilla/5.0 (Macintosh; Intel Mac OS X 10.10; rv:39.0) Gecko/20100101 Firefox/39.0')

browser = webdriver.Chrome(options = options)
browser.set_page_load_timeout(30)

browser.get('https://wayscript.com/')

ps = browser.page_source
print(ps)

browser.close()
```

{% hint style="warning" %}
Be sure to add the following options to ensure the webdriver can operate on WayScript:

`option.add_argument('--headless')`\
`option.add_argument('--no-sandbox')`\
`option.add_argument('--disable-dev-shm-usage')`
{% endhint %}
