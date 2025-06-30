# ✅ PRODIGY_04: Cross-Browser Testing with BrowserStack

## 📌 Task Description

Run automated tests across multiple browsers and devices using **BrowserStack** to ensure cross-browser compatibility of a login or form submission page.

---

## 🧪 Requirements

- Use **BrowserStack’s Selenium Grid** to run test scripts.
- Test on the following browsers:
  - Google Chrome  
  - Mozilla Firefox  
  - Safari 
  - Microsoft Edge
- Use a demo site (e.g., [https://www.saucedemo.com/](https://www.saucedemo.com/))
- Document any UI or functional issues across browsers.

---

## ⚙️ Tools Used

- **Selenium WebDriver**
- **BrowserStack Automate**
- **Python** (or other supported language)
- **Demo Site:** [https://www.saucedemo.com/](https://www.saucedemo.com/)
- export BROWSERSTACK_USERNAME='Kanishkaa'
Install required dependencies:
pip install selenium

💻 Sample Python Script (Selenium + BrowserStack)

import os
from selenium import webdriver

USERNAME = os.getenv("BROWSERSTACK_USERNAME")
ACCESS_KEY = os.getenv("BROWSERSTACK_ACCESS_KEY")

desired_caps = {
    'os': 'Windows',
    'os_version': '10',
    'browser': 'Chrome',
    'browser_version': 'latest',
    'name': 'Login Test - Chrome',  # test name
    'build': 'BrowserStack Sample Build'
}

driver = webdriver.Remote(
    command_executor=f'https://{USERNAME}:{ACCESS_KEY}@hub-cloud.browserstack.com/wd/hub',
    desired_capabilities=desired_caps
)

# Test Steps
driver.get("https://www.saucedemo.com/")
driver.find_element("id", "user-name").send_keys("standard_user")
driver.find_element("id", "password").send_keys("secret_sauce")
driver.find_element("id", "login-button").click()

# Validate login success
assert "inventory" in driver.current_url

driver.quit()


---

🌐 Browsers Tested

Browser	OS	Status	Notes

Chrome	Windows 10	✅ Pass	-
Firefox	macOS	✅ Pass	-
Safari	macOS	⚠ Minor	Button misalignment
Edge	Windows 11	✅ Pass	-



---

📝 Observations

Safari: Slight padding issue on the login button.

All other browsers executed the login flow successfully with no major layout shifts.
