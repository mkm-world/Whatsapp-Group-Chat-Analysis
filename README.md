# Whatsapp-Group-Chat-Analysis
<p align="center">
  <img src="screenshots/thumbnail1.jpg" style= "width: 900px; height: 450px" title="hover text">
</p>

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
- Extracting `added_df`, this dataframe contains all actions about people added to the group. It contains the name/number of the adder, the name/number of the added   members, and the time and date the person was added.
- Extracting `joined_df`, this dataframe contains all actions about people invited to the group. It contains the name/number of the subject, the time, and the date the person joined.
- Extracting `left_df`, this dataframe contains all actions about people leaving the the group. It contains the name/number of the member, the time, and the date the member left.
- Extracting `removed_df`, this dataframe contains all actions about people removed from  the group. It contains the name/number of the remover, the name/number of the removed, the time, and the date the person was removed.
- Extracting `messages_df`, The `messages_df` contains info about all the messages sent in the group. The columns include:
    - **Name**: name or phone number of the sender
     - **Content**: The content of the message
    - **Hour**: The hour the message was sent
    - **Date**: The day the message was sent
    - **Time**: The time the message was sent
    - **Letter_count**: Number of characters in the message
    - **Word_Count**: Number of words in the message

- Masking phone numbers in the chat. This was done to protect the privacy of the members of the group chat.
