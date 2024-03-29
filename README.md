# Whatsapp Group Chat Analysis: DSN FUNAAB
<p align="center">
  <img src="screenshots/thumbnail1.jpg" style= "width: 900px; height: 450px" title="hover text">
</p>

## Introduction
DSN FUNAAB is the student community of the Data Scientist Network at the Federal University of Agriculture, Abeokuta. It is the group of all data scientists and data enthusiasts in FUNAAB. The WhatsApp group was created to connect data scientists in the university and share resources, upcoming events, and opportunities with community members.

This project is an analysis of messages in the DSN FUNAAB Whatsapp group. The Data Extraction and Processing were done with Python and visualization using Power BI. I wrote a Medium post explaining my insights in more detail. Check it out HERE

## Problem Statement 
<p align="center">
  <img src="screenshots/DSN-Logo.png" style= "width: 500px; height: 250px" title="DSN logo">
</p>
As the newly appointed Team Lead of my University’s DSN group, I wanted to find out who the most active members in the group, the best time and days to post. These and many more led to me using my data analytics skill to solve this problem. 

## Data Sourcing 
The data sourcing for this task was simple since WhatsApp enables users to export chats with a few clicks of buttons. So the procedure is to open the group chat, click on the three dots on the top right corner, then ‘More’ then ‘’Export chat’, it then brings up a prompt that asks whether to export chat without media or not, for my case I exported without media. So I saved the raw ‘.txt’files of the exported chats to my drive.

<p align="center">
  <img src="screenshots/Export chat 1.jpg" style= "width: 200px; height: 450px" title="step 1">
  <img src="screenshots/Export chat 2.jpg" style= "width: 200px; height: 450px" title="step 2">
  <img src="screenshots/Export chat 3.jpg" style= "width: 200px; height: 450px" title="step 3">
  <img src="screenshots/Export Chat 4 .jpg" style= "width: 200px; height: 450px" title="step 4">
</p>

## Data Extraction and Preprocessing 
The data extraction process was done in a jupyter notebook, more precisely google collaboratory Notebook. The extraction can be grouped into the following major steps:
 - Reading the raw text file 
```python
# defining a function to read the raw text file
def read_file(file):
    '''Reads Whatsapp text file into a list of strings''' 
    x = open(file,'r', encoding = 'utf-8') #Opens the text file into variable x but the variable cannot be explored yet
    y = x.read() #By now it becomes a huge chunk of string that we need to separate line by line
    content = y.splitlines() #The splitline method converts the chunk of string into a list of strings
    return content
 ```
- Joining split lines and separating them with a full stop.
- Separating notifications from messages 
- Extracting date and time from chats

```python
# Defining function to extract date and time from chats 
def extract_date_time(msgs):
  time = [msgs[i].split(',')[1].split('-')[0] for i in range(len(msgs))]
  time = [s.strip(' ') for s in time]
  date = [msgs[i].split(',')[0] for i in range(len(msgs))]
  main = [msgs[i].split('-')[1] for i in range(len(msgs))]
  return pd.DataFrame(zip(date,time,main),columns=['date','time','raw'])
  ```
- Extracting `added_df`, this dataframe contains all actions about people added to the group. It contains the name/number of the adder, the name/number of the added members, and the time and date the person was added.
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

```python
# Defining The Mask Function
def anonymize(number):
"""
    This function masks all phone numbers by replacing the last 4 digits of all numbers with 'xxxx'
    Args:
        number (str): the number to be masked
"""
  try :
    if '+' in number:
      new_number  = number[:-4]
      new_number+= 'xxxx'
      return new_number
    else :
      return number
  except TypeError:
    return np.NaN
  ```
 ## Data Analysis and visualization
The cleaned dataset was explored using Python and then visualized using Power BI. There is no data model used in this project. 
The Report I made is shown below
<p>
  <img src="screenshots/whatsapp_analysis_final_draft.jpg" style= "width: 900px; height: 500px" title="Whatsapp analysis dashboard">
</p>

I then created a word cloud to visualize the qualitative data in order to find out the most commonly used words on the groupchat. The word cloud was done using Power BI and was used as the page background for the dashboard. 
<p>
  <img src="screenshots/WordCloud.png" style= "width: 900px; height: 500px" title="Word Cloud">
</p>

The DSN FUNAAB WhatsApp group is an interactive group that allows every member of the group to send messages at will, hence there are lots of engagements from multiple users. But, the data shows that Busayo is the most active member of the group which shows that he is excelling at his responsibility as he is the Team Lead of the community
<p>
  <img src="screenshots/most_active_members.jpg" style= "width: 600px; height: 400px" title="Most Active Members">
</p>

The period with the lowest overall activity in the group was Jan 2023- Feb 2023. Very few messages were sent during that period. This was caused by the school's second-semester examinations, it was an 'exam period' which implies no time for any extra-curricular activity, just academics.

<p>
  <img src="screenshots/weekly-messages.jpg" style= "width: 800px; height: 350px" title="Weekly Activity">
</p>

## Recommendations
Some recommendations I can make are:

- Busayo is the most active member and also the best person to reach out to for  issues.
- The weekends are the best days to post for maximum engagement.
- The best periods to send messages are 9 am - 11 am and 4 pm-11 pm.
