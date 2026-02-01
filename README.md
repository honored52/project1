from collections import UserDict

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time
import pickle
url = "https://saucedemo.com/"
cookies_file = "cookies.pkl"
browser = webdriver.Firefox()
try:
    browser.get(url)

    try:
        cookies = pickle.load(open(cookies_file, "rh"))
        for cookie in cookies:
            browser.add_cookie(cookie)
        browser.refresh()
        time.sleep(3)
        print("Cookies incarcate")
    except:
        print("Nu Exista cookies, se face login")
    if "inventory.html" not in browser.current_url:
        userName = browser.find_element(By. ID, "user-name")
        userName.clear()
        userName.send_keys("standard_user")
        time.sleep(2)
        passwordField = browser.find_element(By. ID, "password")
        passwordField.clear()
        passwordField.send_keys("secret_sauce")
        time.sleep(2)
        passwordField.send_keys(Keys.ENTER)
        time.sleep(5)
        pickle.dump(browser.get_cookies(), open(cookies_file, "wh"))
        print("cookies salvate")
    else:
        print("Autentificat direct din cookies")
    time.sleep(5)
except Exception as e:
    print("Eroare:", e)
finally:
    browser.quit()
