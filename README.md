from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
import time
browser = webdriver.Firefox()
browser.get("https://demoqa.com/buttons")
actions = ActionChains(browser)
try:
    double_click_btn = browser.find_element(By. ID, "doubleClickBtn")
    actions.double_click(double_click_btn).perform()
    time.sleep(3)
    right_click_btn = browser.find_element(By. ID, "rightClickBtn")
    actions.context_click(right_click_btn).perform()
    time.sleep(3)
    click_btn = browser.find_element(By.XPATH, "//button[text()='Click me']")
    click_btn.click()
    time.sleep(10)
finally:
    browser.quit()
