# Counting Items per Day in Weekly Data  

## Me
I have a text file where a subset of the data is as follows, I want to count the amount of items after each day in each week and return a list of days and items where day would be associated with the week e.g. "Week 1 Monday" and items would be the amount of items counted from trhe file:  

### Week 1 (actual):  
#### Monday: 
    Installed Android Studio, following MSN vid
    Updated Global Tasks lists
    Sabaq + Class
    Anything else not included  
#### Tuesday:  
    Went to uni all day (8.15am-6.45pm)
    Sabaq + Class
    Anything else not included  
#### Wednesday:
    Went to uni all day (8.15am-6.45pm)
    Sabaq + Class
    Anything else not included  
#### Thursday:
    Went to uni all day (8.15am-6.45pm)
    Sabaq + Class  
#### Friday:
    Went to uni all day (8.15am-6.45pm)
    Sabaq + Class
    Anything else not included  
#### Saturday:
    Played games all day
    Watched TV with family  
#### Sunday:
    Went to gym with Dad
    Uploaded new football edit that Hamza sent
    Sabaq + Class
    Anything else not included  
### Week 2 (actual):  
#### Monday:  
    Finished setting up first gig on 
    weekly business round-up
    Edited and uploaded Darwizzy awards vid
    Read Sabaq and did Class
    Recorded clips for & started editing new footy edit (Best player on every UCL team - part 1)
    Anything else not included  
#### Tuesday:  
    Went to uni all day (8.15am-6.45pm)
    Finished editing and uploaded above vid ⬆️
    Sabaq + Clas
    sAnything else not included  
### Week 3 (actual):  
#### Monday:  
    Went to gym by myself
    Shower + associated
    Sabaq
    Found ChatGPT prem predictions + Fifa 20 draft vid, ready for edit now, organised other vids as well into correct folders
    Class
    Finished recording clips for Python programmer channel return vid  
#### Tuesday:  
    Went to Uni all day (8:15am-6:45pm)
    Finished fixing CV
    Sent speculative job offer for EXA Networks placement  
#### Wednesday:  
    Went to uni (8.15am-12.45pm)
    Did demonstrator role at uni (10am-12pm)
    Had Internship feedback meetng w/ Prof Rami
    Went to Internship Award Evening
    Recorded more of Python channel return vid  
#### Thursday:  
    Went to uni (8.30am-5pm)
    Sabaq + Class
    Android Studio development (Flying Football)  
#### Friday:  
    Went to uni (9.15am-12.15pm)
    Went to gym with Dad
    Started working on WhatsApp AI bot for calls
    Created, organised and edited phone notes  
#### Saturday:  
    Driving Lesson
    Started editing Python channel return vid
    Saved Medium articles as Word docs (remaining 3 so far)
    Sorted out GCoutCalc history text file
    Discord call with Adam to test server features  
#### Sunday:  
    Sent WhatsApp polls for weekly meeting
    Went to other house
    Did Fc25 livestream 
    Sabaq + Class
    Made real progress with edit of Python programmer channel return vid
    Shower  

## Co-Pilot
Let's break this down, Sherlock-style! 🕵️‍♂️ I'll help you count the items for each day of each week from your data. Here’s a Python script to do the trick:

```python
# Sample data
data = """
Week 1 (actual):
    Monday:
    Installed Android Studio, following MSN vid
    Updated Global Tasks lists
    Sabaq + Class
    Anything else not included
    Tuesday:
    Went to uni all day (8.15am-6.45pm)
    Sabaq + Class
    Anything else not included
    ...
"""

# Function to process the text data
def count_items_per_day(text):
    week_day_counts = {}
    current_week = ""
    current_day = ""
    
    for line in text.split("\n"):
        line = line.strip()
        
        # Determine the week
        if line.startswith("Week"):
            current_week = line.split(" ")[1]
        
        # Determine the day
        elif line.endswith(":") and not line.startswith("Week"):
            current_day = line.replace(":", "").strip()
        
        # Count items for the current day
        else:
            if current_week and current_day:
                key = f"Week {current_week} {current_day}"
                if key not in week_day_counts:
                    week_day_counts[key] = 0
                if line:
                    week_day_counts[key] += 1
    
    return week_day_counts

# Call the function and print results
item_counts = count_items_per_day(data)
for day, count in item_counts.items():
    print(f"{day}: {count} items")

```

Paste this script into your Python environment. You can update the `data` variable with your full text data. This will give you a count of items for each day, week by week. Have fun with those numbers!  

## Me
In google sheets, how can I add colour coding to my cells such that for cells C4 till H9, the cell is green if the number above is less than or equal and red otherwise. Also for cells D10 to H10, I want a similar thing but checking the cells on the left  

## Co-Pilot
You can achieve this using Google Sheets' Conditional Formatting feature. Here's how to do it:

### For cells C4 to H9:
1. **Select the range** C4:H9.
2. Go to **Format** > **Conditional formatting**.
3. In the Conditional format rules sidebar, under **Format cells if**, choose **Custom formula is**.
4. Enter the formula: `=C4<=C3`.
5. Set the **Formatting style** to **Green**.
6. Click **Done**.

### For cells D10 to H10:
1. **Select the range** D10:H10.
2. Go to **Format** > **Conditional formatting**.
3. In the Conditional format rules sidebar, under **Format cells if**, choose **Custom formula is**.
4. Enter the formula: `=D10<=D9`.
5. Set the **Formatting style** to **Green**.
6. Click **Done**.

This will color the cells green if the value is less than or equal to the value in the cell above (for C4:H9) or to the left (for D10:H10), and red otherwise.

Does this help with what you were trying to achieve?  

*End of this Conversation*
