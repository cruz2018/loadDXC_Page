import unittest
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.firefox.options import Options


class FirefoxSearch(unittest.TestCase):

    # declare variable to store the URL to be visited
    base_url = "https://www.dxc.technology/es"

    # --- Pre - Condition ---
    def setUp(self):
        # declare and initialize driver variable
        self.driver = webdriver.Firefox()

        # browser should be loaded in maximized window
        self.driver.maximize_window()

        # driver should wait implicitly for a given duration, for the element under consideration to load.
        # to enforce this setting we will use builtin implicity_wait() function of our 'driver' object.
        self.driver.implicitly_wait(10) # 10 is in seconds

    # --- Steps ---
    def test_load_home_page(self):
        # to initialize a variable to hold reference of webdriver instance beig passed to the function as a reference.
        driver_firefox = self.driver
        # to load a given URL in browser window
        driver_firefox.get(self.base_url)
        # test whether correct URL/ web Site has been loaded or not
        self.assertTrue('Bienvenido a DXC en España', driver_firefox.title)
        assert('https://www.dxc.technology/es' == driver_firefox.current_url)

    # --- Post - Condition ---
    def tearDown(self):
        # to close the browser
        self.driver.close()

if __name__ == '__main__':
    unittest.main()
