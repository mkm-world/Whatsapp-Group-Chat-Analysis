# Whatsapp-Group-Chat-Analysis
## Introduction
DSN FUNAAB is the student community of the Data Scientist Network at the Federal University of Agriculture, Abeokuta. It is the group of all data scientists and data enthusiasts in FUNAAB. The WhatsApp group was created to connect data scientists in the university and share resources, upcoming events, and opportunities with community members.

This project is an analysis of messages in the DSN FUNAAB Whatsapp group. The Data Extraction and Processing were done with Python and visualization using Power BI. I wrote a Medium post explaining my insights in more detail. Check it out HERE

## Problem Statement 
As the newly appointed Team Lead of my University’s DSN group, I wanted to find out who the most active members in the group, the best time and days to post. These and many more led to me using my data analytics skill to solve this problem. 

## Data Sourcing 
The data sourcing for this task was simple since WhatsApp enables users to export chats with a few clicks of buttons. So the procedure is to open the group chat, click on the three dots on the top right corner, then ‘More’ then ‘’Export chat’, it then brings up a prompt that asks whether to export chat without media or not, for my case I exported without media. So I saved the raw ‘.txt’files of the exported chats to my drive.

## Data Extraction and Preprocessing 
The data extraction process was done in a jupyter notebook, more precisely google collaboratory Notebook. The extraction can be grouped into the following major steps:
 - Reading the raw text file 
- Joining split lines and separating them with a full stop.
- Separating notifications from messages 
- Extracting date and time from chats 
- Extracting ‘Added_df’, this dataframe contains all actions about people added to the group. It contains the name/number of the adder, the name/number of the added   members, and the time and date the person was added.
