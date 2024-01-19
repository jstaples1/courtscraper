# courtscraper

The purpose of the courtscraper app is to provide a better way to search for free courts at the UBC tennis center.  The current web interface requires the user to drill into each court to see what is available whereas courtscraper allows the user to pick a date and then see what court times are available for booking across all the courts at the UBC tennis center

- This code was developed using Python v3.10

Key Challenges:
- the UBC pages that display court times rely on a lot of client side javascript to execute so whatever tool you use to scrape the pages must be able to interpret modern javascript succesfully.  I failed to get HTMLUnit (JAVA) to interpret the required javascript properly and so I found using Chrome through selenium webdriver the most reliable way to do this.
- getting each court page to load and execute its client side javascript completely and reliably before interpreting the web page contents took approximately 5 seconds each which makes the webscraping of multiple courts slow for the end user
- using Chrome through selenium webdriver uses a fair amount of memory and running more than one headless instance of Chrome this way was too much for the free tier memory capacity of an instance of AWS EC2.  I decided to check for a running instance of chrome to limit the execution of the script and inform the user.
- chrome is constantly updating and getting a dockerfile to install compatible versions of Chrome and selenium webdriver that can work together can be difficult
