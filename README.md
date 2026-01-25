from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

url = "https://www.saucedemo.com/"
browser = webdriver.Firefox()
try:
    browser.get(url)
    userName = browser.find_element(By.ID, "user-name")
    userName.clear()
    userName.send_keys("standard_user")
    time.sleep(2)
    passwordField = browser.find_element(By. ID, "password")
    passwordField.clear()
    passwordField.send_keys("secret_sauce")
    time.sleep(2)
    passwordField.send_keys(Keys.ENTER)
    time.sleep(5)
except Exception as e:
    print("Eroare.", e)
finally:
    browser.quit()
