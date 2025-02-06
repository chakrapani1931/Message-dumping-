# Android SMS Dump
================

A simple script to dump SMS messages from an Android device.

## Features

* Dumps SMS messages from the Android SMS database
* Supports multiple Android versions (tested on Android 10 and 11)
* Requires root access to read the SMS database

## Requirements

* Python 3.x
* Android device with root access
* SQLite3 library

## Usage

1. Clone the repository: `git clone https://github.com/username/android-sms-dump.git`
2. Navigate to the repository directory: `cd android-sms-dump`
3. Run the script: `python sms_dump.py`

## Code

```python
import os
import sqlite3
from sqlite3 import Error

def get_sms():
    # Connect to the SMS database
    conn = sqlite3.connect('/data/data/com.android.providers.telephony/databases/mmssms.db')
    c = conn.cursor()

    # Query the SMS table
    c.execute("SELECT * FROM sms")

    # Fetch all the rows
    rows = c.fetchall()

    # Print the SMS messages
    for row in rows:
        print(f"Number: {row[2]}")
        print(f"Date: {row[6]}")
        print(f"Content: {row[11]}")
        print("------------------")

    # Close the connection
    conn.close()

get_sms()
