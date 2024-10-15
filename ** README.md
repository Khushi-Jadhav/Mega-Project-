# Mega-Project-
Final Year project 
This script automates the process of logging into Facebook, navigating to a user's profile, extracting images and captions from specific sections (like "Your Photos" and "Albums"), and saving them locally using Selenium WebDriver in Python. Below is a detailed explanation of what each part of the script does:

1. Setup and Configuration
The script begins by importing the necessary libraries:

Selenium WebDriver for browser automation.
EC, By, WebDriverWait from selenium.webdriver.support for waiting until elements are clickable or visible before interacting with them.
os for file system operations.
wget for downloading images from URLs.
time to manage delays between certain actions.
We then configure the Chrome WebDriver with specific options:

--disable-notifications: This disables browser notifications, which might otherwise interfere with the scraping process.
We initialize the WebDriver by creating an instance of webdriver.Chrome() and passing the configured options.

2. Logging into Facebook
The script navigates to Facebook using driver.get("http://www.facebook.com"). We then target the login elements using CSS selectors:

username and password fields are identified using the input[name='email'] and input[name='pass'] selectors respectively.
Once the fields are located, the provided Facebook credentials are entered. The script waits until the login button becomes clickable and submits the form by clicking the login button.

After logging in, a 5-second delay is introduced to allow Facebook to load the next page.

3. Navigating to Profile and Extracting Images & Captions
The script iterates over two Facebook sections: Your_Photos and Albums. For each section:

The script navigates to the user’s profile page for that section (e.g., https://www.facebook.com/profile.php?id=100077663996875Your_Photos).

Once the page is loaded, it scrolls down the page by executing JavaScript (window.scrollTo(0, document.body.scrollHeight);). This action is repeated to ensure that all relevant posts and images are loaded.

The script then targets all a tags (links) on the page and narrows them down to only image links (those starting with https://www.facebook.com/photo). This list of links is stored for further processing.

4. Extracting Image URLs and Captions
For each image link, the script navigates to the link and extracts the image URL:

Image URL: It finds all img tags on the page and extracts the src attribute from the first image found.

Caption: Using an XPath expression, the script searches for the caption text associated with the post. If no caption is found, it appends an empty string to maintain consistency in the captions list.

5. Saving Images and Captions
Once all the images and captions are extracted, the script proceeds to store them locally:

Images: A new directory called FB_SCRAPED is created to store the images. Each image is downloaded using the wget library and saved with a sequentially numbered filename (e.g., 0.jpg, 1.jpg, etc.).

Captions: Each caption is saved as a text file in the same directory. The captions are saved with filenames like caption_1.txt, caption_2.txt, and so on.

6. Completion and Output
At the end of the script, the total number of scraped images and captions is printed to the console.

Summary
This script automates the extraction of images and captions from a Facebook user's profile, classifies the posts, and downloads the data locally. It demonstrates how Selenium can be used to automate browser interactions and scrape dynamic content, handling scenarios such as delayed page loading and element retrieval. This solution is scalable and can be adapted for similar scraping tasks across other web platforms.






