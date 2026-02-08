	from selenium import webdriver
	from selenium.webdriver.common.by import By
	from selenium.webdriver.common.keys import Keys
	from selenium.webdriver.chrome.options import Options
	from selenium.webdriver.common. action_chains import ActionChains
	import time
	url = " https://www.youtube.com "
	options = Options()
	options.add_argument("--window-size=1920,1080")
	browser = webdriver.Chrome(options=options)
	action = ActionChains(browser)
	try:
    print("Proceed to URL")
    browser.get(url)
    time.sleep(5)
    print("Insert search criteria")
    searchField = browser.find_element(By.NAME, "search_query")
    searchField.clear()
    searchField.send_keys("40 sec video")
    time. sleep(2)
    print("Search…")
    searchField.send_keys(Keys.ENTER)
    time.sleep(5)
    print("Click first video result")


    first_video = browser.find_element(By.XPATH, '(//a[@id="video-title"])[1]')
    video_title = first_video.get_attribute("title")
    print("Video selectat:", video_title)
    first_video.click()
    time. sleep(10)
    print("Video rulează:", video_title)
	except Exception as e:
    print("Eroare:", e)
	finally:
    time. sleep(10)
    browser.quit()
