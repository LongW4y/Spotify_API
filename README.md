# Welcome!

This is a project I made, which utilizes Spotify's API Key to obtain a maximum of 50 latest (but not unique) songs you have listened to within the latest 24 hours. 

Everything was written in Jupyter Notebook, utilizing Python v3.7, under Ubuntu Linux distribution, with the usage of GitHub version control system through Bash, not the application. 

## How to begin?

*First* off, familiarize yourself with the Jupyter environment. 

**Great** video to start with: https://www.youtube.com/watch?v=HW29067qVWk&t

*Second*, download just the necessary: data\_load.ipynb and modify the username(UID) to fit your username - which is not utilized in any way online, this will be the name of your directory in which the data will be stored.

*Third*, go to Spotify's site for developers:
https://developer.spotify.com/console/get-recently-played/

where you will have to log in to generate your own authorization token, which lasts for **exactly** 1 hour.

During this period you can listen to any songs, and after a couple of minutes after you have listened to a given song, you will be able to register it in your directory. 

## How does it work?
* First off, a *Python dictionary* is created for your user, which contains UID and the authorization token(TOKEN). 
* Then, another *Python dictionary* is created for headers - which were created for additional information. 
* After that, a request for the **latest** 50 songs(1-50, *modifiable*) is sent to Spotify. 
* After that, the data is being validated and all the redundant - older than 24 hours - records are being removed. If the data is anyhow not valid, an exception will be raised and present in the console. 
* Except for the error in the console, *program saves most of the actions performed within itself* in the log file, which is present in the \.\/previous\_records\/\[UID\]\/change\_log.txt with the dates of the actions recorded. 
* Validated data is returned as a **Pandas**(one of the most utilized libraries within the Data Science/Data Engineering communities) dataframe. 
* Then, the program checks whether your directory exists, and if it does not, it creates it.
* Later, the program checks if there exists a previous records, and if:
- it exists, compares the records of existing records with the ones received from Spotify and **deletes** repeated records from the dataframe. The record is classified as *repeated* if the value of *played\_at* is not unique.
- if it does not exist, then the received dataframe becomes the main dataframe, which will be saved in the \.\/previoues\_records\/\[UID\]\/ directory. 
* Every time a program is ran, a copy of the main .csv file, in which the main dataframe, is stored is created in the same directory, with the date at which the file was created. 

Hopefully, you will find this program useful in any way :)

If you would like to contact me, feel free to do so at: 

[My LinkedIn Page](https://www.linkedin.com/in/cezary-stanis%C5%82awski-29b5781b5/)

or write an email to my private inbox: longwaytoglory@gmail.com
