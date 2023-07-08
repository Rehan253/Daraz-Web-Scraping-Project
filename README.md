
# Daraz Web Scraping Project

This Python-based project uses Selenium to automate data scraping from the Daraz website's "laptop" category. The scraped data is stored in a MySQL database. The bot automatically runs every Tuesday at 01:00 pm.

## Prerequisites
Before you start, make sure you have the following installed:

Python 3.7 or later

Google Chrome browser

**ChromeDriver:**
 Download the version that matches your Google Chrome version and your operating system. Unzip the file and place chromedriver.exe in a directory of your choice. You'll need to update the path in the script later.

**MySQL Database: **
Make sure to remember the username and password you use during the installation. You'll need it to connect to the database in the script.

## Setting Up the Project
**Clone the Git Repository: **
If you have Git installed, you can clone the repository by typing git clone [https://github.com/Rehan253/Daraz-Web-Scraping-Project] in the terminal. If you don't have Git, you can download the project directly from the repository page and unzip it.

**Installing Dependencies:**
This project comes with a requirements.txt file that lists all Python packages required by the project.
You can install all required packages with the following command:

pip install -r requirements.txt

This will automatically download and install all packages listed in requirements.txt.

**Update the Script: **
Open the Python script using a text editor. Find the line where chromedriver.exe path is specified:
Code: 

path = 'C:/SeleniumDriver/chromedriver.exe'


Replace 'C:/SeleniumDriver/chromedriver.exe' with the path where you placed your chromedriver.exe.

**Database Credentials:**
Also, replace the 'root' and '' in the following lines with your MySQL username and password respectively:

Code:
 mydb = mysql.connector.connect(
        host="localhost",
        user="root",
        password="",
        database="daraz_db"
    )


Now you're ready to run the script!

## Running the Script
Open the Python script using a text editor. Find the line where chromedriver.exe path is specified:
schedule.every().tuesday.at("13:00").do(job)

And change with the current time when you want to run this script.thn navigate to the directory where the script is located using your terminal. Once you're in the correct directory, type the following command:
Command:

Python .\main.py


Press Enter to execute the command. The script will now run and start gathering data.





## Database Schema
The project uses a MySQL database named 'daraz_db'. It has a table named 'laptops' with the following fields:
1-title: A string containing the name of the laptop (VARCHAR(500)).
2-price: A string containing the price of the laptop (VARCHAR(255).
3-rating: A string containing the rating of the laptop (VARCHAR(255)).

## Detailed Guide
The script starts by setting up logging and scheduling the scraping job to run every Saturday at 16:01. Once the job starts, it opens the Daraz laptops page and gets the number of total pages. It then goes through each page and extracts the URLs of the individual laptop pages.

For each laptop URL, it opens a new tab, extracts the title, price, and rating, and inserts them into the MySQL database. If it can't extract any of the details, it stores 'No Data' for that field.

After inserting the laptop's details into the database, it closes the laptop's tab and moves on to the next laptop URL. Once all the laptops on the current page have been processed, it clicks the 'Next Page' button and repeats the process for the next page.

Once all the pages have been processed, it logs all the records in the database and then closes the database connection and the Chrome browser.

## Scheduling

This bot is scheduled to run automatically every Tuesday at 01:00. It uses the schedule module in Python to achieve this.

## Logging
The bot logs all of its activities in a file named 'app.log'. This includes info logs about the bot's progress, as well as error logs whenever an exception occurs. This is useful for tracking the bot's execution and troubleshooting any issues that may arise.
## Conclusion
This Python-based web scraping project offers a powerful tool for automating the process of gathering laptop data from the Daraz website. Through detailed setup and running instructions, users, even without extensive technical knowledge, can successfully implement this solution.

Once set up, the script provides regular, automated data collection scheduled to run every Saturday. This regularity ensures up-to-date data availability for further market analysis. The inclusion of logging capabilities facilitates error tracking and performance enhancement over time
