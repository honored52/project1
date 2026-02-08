	from selenium import webdriver
	import time

	url = "https://demoqa.com/buttons"

	option = webdriver.ChromeOptions()
	browser1 = webdriver.Chrome()
	browser2 = webdriver.Chrome()

	try:
    browser1.get(url=url)
    browser2.get(url=url)
    time.sleep(5)

	except Exception as e:
    print(e)

	finally:
    browser1.close()
    browser2.close()
    browser1.quit()
    browser2.quit()
