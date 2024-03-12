![Agrigates Logo](https://agrigates.io/wp-content/uploads/2020/10/AgriGates_Header_Logo-300px.png)

[Data Annotation Tool](./DataAnnotationToolPython/pythonDataTool.md)

# AgTag User Manual

---

## Contents
- [Sensor](#sensor)
- [Edge](#edge)
- [Parser](#parser)
- [Annotation](#annotation)

---

## Sensor

---

## Edge

---
<!--
Honestly this parser stuff could just be the last part of edge
--- -->
## Parser

### Walkthrough of Process

The Parser is monitoring the output folder that the sensors dump data into. When it detects a new file, it parses the raw data into human readable data. 
It then groups the data based on the animal that the device was on using a user managed table. Finally it writes out the parsed data to the user's chosen location. 

### Setup

The Parser and source file directories will already be set up on the Edge. The user only needs to manage the settings and potential SQL connection. 
To do this, boot up ParserSettings.exe and this window will open:

![Paser Settings UI]()

By default the parser is only writing to local CSVs, and is reading the device to cow conversion information from a local excel file. Both of these require the user to 
repeatedly return to the edge to both retrieve data, and update the excel conversion. The excel table looks like:

![device to cow excel]()


If the user desires to do this in the cloud, they can export the data to SQL tables, 
and read the device to cow conversion from a SQL table. 

### Management

The ParserManagement.exe handles connecting to SQL from the user's end, managing the device naming, managing the device to animal conversion table, and extracting the data into csvs. There will be 4 tabs, one for each process. 
(Note these are all stand-ins while we develop this UI)

#### SQL Connection
First, the SQL connection tab will look like:

![SQL Connecting]()

The credentials will get saved in an encrypted file so as to facilitate future logins.

#### UUID to Device Name

The device naming tab will look like: 

![device to cow ui]()

For each of the devices, the user can assign a device name for easy of understanding in other processes. It is a lot easier to remember Device1 rather than 5330CBBD60ED

#### Animal Conversion

The animal conversion will look like: 

![device to cow ui]()

Here the user selects a decive name, pairs it to an animal ID, and selects the time range that the device will be on the animal. Once the device is actually removed from the animal the user should update the "Actual End" boxes. 

#### CSV Extraction

And the extract selection will look like:

![CSV extraction]()

The user can select an animal, and a time range, to download a csv of that data from the SQL table. The user can also use the download all feature to either download all the data within a time range, or simply download all the data. 
It should be noted that there will be a lot of data and downloading all of it may take time.





---

## Annotation


