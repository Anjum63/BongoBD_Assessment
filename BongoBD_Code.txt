import unittest
from selenium import webdriver

class Test(unittest.TestCase):
	def test_title(cls):
		cls.driver = webdriver.Chrome(executable_path=r'webdriver/chromedriver.exe')
		cls.driver.implicitly_wait(10)
		cls.driver.maximize_window()
		cls.driver.get("https://bongobd.com/")
		cls.driver.set_page_load_timeout(5000)
		pagetitle = cls.driver.title
		cls.assertEqual("BONGO | Watch Live Tv, Bangla Movies, Natoks Anytime Anywhere", pagetitle, "webpage title is not matching")
		print(pagetitle)

	def test_title_kids(cls_1):
		cls_1.driver.find_element_by_xpath("//span[normalize-space()='Kids']").click()
		cls_1.driver.set_page_load_timeout(2000)
		tabname = cls_1.driver.find_element_by_xpath("//span[normalize-space()='Kids']").text
		cls_1.assertEqual("BONGO | Kids", tabname ,"webpage title is not matching")
		print(tabname)
		cls_1.driver.set_page_load_timeout(2000)

	def run_video(self):
		self.driver.execute_script("window.scrollBy(0,1800)", "")
		self.driver.set_page_load_timeout(200)
		self.driver.find_element_by_xpath("//div[@class='MuiBox-root jss301 jss119']").click()
		self.driver.set_page_load_timeout(40000)
		self.driver.execute_script(self.driver.find_element_by_class_name("vjs-big-play-button bongo-big-play-button")[60000].click())
		self.driver.execute_script(self.driver.find_element_by_class_name("vjs-big-play-button bongo-big-play-button")[60000].click())

	@classmethod
	def close(clz):
		clz.driver.close()
		clz.driver.quit()
		print("Test completed")

if __name__ == "__main__":
    unittest.main()