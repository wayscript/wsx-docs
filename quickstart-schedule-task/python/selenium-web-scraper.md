# Selenium Web Scraper

### Create `selenium-app.py`

Use the boilerplate code below to create a `selenium-app.py` file. See [File system](../../platform/lairs/file-system.md) for more details on how to manipulate files in your workspace file system.

#### Boilerplate `selenium-app.py`

```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By

options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
options.add_argument('user-agent=Mozilla/5.0 (Macintosh; Intel Mac OS X 10.10; rv:39.0) Gecko/20100101 Firefox/39.0')


driver = webdriver.Chrome(options = options)
driver.set_page_load_timeout(30)

# Take action on browser
driver.get("http://www.python.org")

# Request browser information
title = driver.title

#Establish Waiting Strategy
driver.implicitly_wait(0.5)

#Find an element
elem = driver.find_element(By.XPATH, '/html/body/div/div[3]/div/section/div[1]/div[1]/h2')
print(elem.text)

#end driver session
driver.quit()
```

### Configure `cron` trigger

Open your Lair’s `.triggers` file and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](../../platform/lairs/triggers.md) for more details.

```
python selenium-app.py
```

### Test your task execution in development environment

Press “Run” to execute the run command and start your task’s process execution. Open your “Processes” list and select the running process to see the generated log.

### Deploy to production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, press “Deploy” to create a production environment for your task. See [Hosted environments](../../platform/lairs/deployments.md) for more details.

{% hint style="info" %}
In order for your scheduled task to run, you must [Deploy](../../platform/lairs/deployments.md) the lair!
{% endhint %}

#### Ad

#### Additional notes

For additional notes on using headless browsers, please visit our [code snippets](../../resources/code-snippets/headless-browser-selenium.md) page.

{% content-ref url="../../resources/code-snippets/headless-browser-selenium.md" %}
[headless-browser-selenium.md](../../resources/code-snippets/headless-browser-selenium.md)
{% endcontent-ref %}
