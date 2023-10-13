# Flashcard Study Tool
## Features:

Create decks of flashcards on various topics.
Display one side of the card and reveal the other side on click.
Track study progress and mark cards as known/unknown.
Shuffle and test mode for self-assessment.

## Details
Features:
Deck Creation:

Users should be able to create a deck where they can add multiple flashcards.
Each deck can have a title and a description (e.g., "Spanish Verbs", "JavaScript Functions").
Flashcard Creation:

Within a deck, allow adding flashcards.
Each flashcard has a "front" (the question or prompt) and a "back" (the answer or response).
Studying Mode:

Users can choose a deck and start a study session.
They will be shown one side of a flashcard and can click/tap to flip it and see the other side.
Implement a "Next" button to move to the subsequent card.
Progress Tracking:

Track which cards the user knows and doesn't know.
At the end of a study session, show them their progress and possibly cards they struggled with.
Editing and Deletion:

Users can edit or delete individual flashcards or entire decks.
Shuffle Mode:

Allow users to shuffle the flashcards within a deck for varied study sessions.
Implementation Steps:
Set Up Your React App:

Use Create React App for a quick start.
Component Structure:

App: Main component, routing, and overall layout.
DeckList: Displays a list of all decks.
Deck: Displays details about a single deck and the list of flashcards in it.
Flashcard: Displays a single flashcard's front or back based on user action.
StudySession: Manages the logic for studying a deck.
State Management:

Consider using the useState and useEffect hooks for local state management.
For more complex state or if you plan to expand, libraries like Redux or React's useContext and useReducer hooks might be beneficial.
Data Persistence:

To start, you can use the browser's localStorage to persist the decks and flashcards.
If you wish to expand, consider integrating with a backend using APIs (e.g., Express.js with a MongoDB database).
Styling:

Use CSS Modules or CSS-in-JS libraries like styled-components to style your app.
Consider adding animations for card flips using CSS transitions or libraries like react-flip-toolkit.
Routing:

Implement routing using react-router-dom to navigate between the list of decks, individual decks, and study sessions.
Additional Features (Optional):

Search & Filter: Allow users to search or filter flashcards and decks.
User Accounts: Add authentication and let users create accounts to save their decks.
Import/Export: Let users import decks from or export to JSON files.
Tags: Allow adding tags to flashcards for better categorization.
Dark Mode: Implement a light/dark theme toggle.


PI

#INSTALL SELENIUM BEFORE RUNNING THIS CODE
#pip3 install selenium
'
D_TOKEN="{3D8F1F55-188B-4C3B-AAD6-FF93A08273FD}"
EMAIL_ADDRESS="sitemassoudyan@gmail.com"
EMAIL_PASSWORD="Hejsa123dethhererminNyeKODe"
EMAIL_ADDRESS_RECIEVER="massoudyan@hotmail.com"

from datetime import datetime, timedelta
from selenium.webdriver.chrome.service import Service
from selenium import webdriver
from selenium.webdriver.common.by import By

import time

# load dotenv
from dotenv import load_dotenv
import os

load_dotenv()

tokens = [os.getenv('D_TOKEN'), os.getenv('T_TOKEN')]

def book(token):
    # Daniel's token
    d_token = token

    # Calculate the date 2 weeks from today
    two_weeks_from_today = datetime.now() + timedelta(days=15)

    # Check if the date is a Monday. Monday the last team is yoga. the second to last team is Sauna.
    is_monday = two_weeks_from_today.weekday() == 0   
    
    # Check if the date is a Sunday. Sunday the last team is yoga. the second to last team is Sauna.
    is_sunday = two_weeks_from_today.weekday() == 7

    # Format the date
    formatted_date = two_weeks_from_today.strftime('%d-%m-%Y')

    # Initialize Selenium WebDriver
    browser_driver = Service('/usr/lib/chromium-browser/chromedriver')

    # Navigate to the starting page
    driver.get(f"https://www.eadministration.dk/kunde/kundemenu.asp?logintoken={d_token}")

    # Wait for the page to load
    time.sleep(2)

    # Navigate to the booking page
    driver.get(f"https://www.eadministration.dk/kunde/holdoversigt.asp?id=10&dag={formatted_date}")

    # Wait for the page to load
    time.sleep(2)

    # Find event
    if is_sunday:
        exit(1)
    if is_monday:
        checkbox = driver.find_element(By.XPATH, "//div[@id='hold']/table/tbody/tr[last()-1]/td")
    else:
        checkbox = driver.find_element(By.XPATH, "//div[@id='hold']/table/tbody/tr[last()]/td")

    # Click event
    checkbox.click()

    # Find assign booking
    assign_element = driver.find_element(By.CLASS_NAME, "assignbooking")

    time.sleep(1)

    # CLick assign
    assign_element.click()

    # Wait for the page to load
    time.sleep(2)
    driver.quit()

for t in tokens:
    book(t)

'


'
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

chrome_options = Options()
chrome_options.add_argument('--headless')  # Run headless to save resources
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')

driver = webdriver.Chrome(executable_path='/usr/lib/chromium-browser/chromedriver', options=chrome_options)

'

'
sudo apt-get install chromium-chromedriver

'
