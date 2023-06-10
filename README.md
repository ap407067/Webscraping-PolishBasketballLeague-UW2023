Short description of scrapers:
For Beautiful Soup:
The program starts by making a timestamp to measure the execution time of the web scraping process. The "start_time" variable captures the current time at the beginning. Additionally, a "limit" variable is used to indicate whether the 100-link limit has been reached or not. Then the specific URL from which player information is obtained is placed  in the code. A GET request is sent to the URL to retrieve the HTML content, which is then parsed using Beautiful Soup. Initially, an empty list called "player_links" is created to store the URLs of individual player pages. By searching for player items on the main page, the code iterates through each item, extracting the link to their respective pages. Then the base URL and the extracted link are joined together to form the complete URL, which is added to the "player_links" list. If the number of player links reaches 100, the "limit" variable is set to true, and the loop breaks. Subsequently, an empty DataFrame called "d" is initialized with columns to store player information. For each player link in "player_links", the code sends a request to the link and retrieves the HTML content of the player's page. Using Beautiful Soup scraper, relevant player information such as name, passport, date of birth, height, position, last team played, and year are extracted. All this information is stored in a dictionary named "player". Finally, the "player" dictionary is appended to the "d" DataFrame, and the resulting DataFrame is saved to a CSV file named "players.csv". The execution time of the scraping process is calculated by subtracting the "start_time" from the current time, and the total execution time is printed to the console.

For Scrapy:
The first spider crawls through the page to extract required links
Program defines a Scrapy spider named "suzuki" by subclassing the 'scrapy.Spider' class. Spider starts crawling from the provided URL. In the parse method, the spider receives the response from the initial URL. It extracts the links to individual player profiles from the HTML response using CSS selectors. The number of links to extract is determined by the counter variable, which is set to a large value (infty) or a specific limit (100) depending on the value of the limit flag. The extracted links are appended to a list called links. The program creates a pandas DataFrame using the links list, where each row represents a link. The DataFrame is then saved to a CSV file named "links.csv" using the to_csv method. Finally, the program prints each item (link) in the links list
Second one collects needed data from every link of input csv file:
It defines a Scrapy item class called Player to store players information. Next it creates Scrapy spider class called NewSpider that inherits from scrapy.Spider. The spider class defines the start_requests method, which reads the URLs from a file called "links.csv" and initiates requests to each URL. If the limit flag is set to False, the spider processes all URLs. Otherwise, if limit is set to True, the spider only processes a maximum of 100 URLs. The spider measures the start time before making the requests. For each URL, the spider sends a request and assigns the callback method parse to handle the response. The parse method is responsible for extracting player information from the response using CSS selectors and populating the Player item. The extracted player data is yielded as output, which is collected by Scrapy. After processing all URLs, the spider measures the end time and calculates the crawling time. Finally, the crawling time is printed to the console.

For Selenium:
Setting up the Environment: The program begins by importing necessary libraries and setting up the WebDriver options for Firefox. This headless WebDriver automates browser interactions in the background without displaying a graphical user interface.
Accessing the Website: The program then accesses the website specified by the URL. This is done through a GET request that the WebDriver sends to the website's server, emulating the process of a user accessing a website through a browser.
Parsing the HTML: Once the HTML of the webpage is retrieved, it's parsed using BeautifulSoup, a library that converts the HTML into a tree of Python objects. This makes it easy to navigate and search through the HTML structure.
Identifying Data to Scrape: The program identifies all the div elements that contain player information. It then loops over each of these divs and extracts the player's name and link. These data points are appended to a list for further processing.
Collecting Player Details: A pandas DataFrame is created to store all the players' details. The program then loops over each player's link in the list and navigates to the specific webpage of the player. Here, it retrieves the page source and scrapes the player's details, including their name, passport number, date of birth, height, position, and last team. If certain information is not present, the program is built to handle such exceptions gracefully.
Storing Data: The scraped data for each player is added to the DataFrame. This provides a structured format for the data, which is crucial for further analysis and processing.
Timekeeping and Cleanup: The program also keeps track of the total time taken for execution. Once the data scraping is complete, the program cleans up by closing the WebDriver instance.
Saving Data: Finally, the program saves the DataFrame as a CSV file for later use and analysis.
In summary, your program automates the process of data collection from a website. It navigates webpages, identifies and extracts necessary data, organizes the data in a structured format, and saves it for later use, all while keeping track of its execution time.
