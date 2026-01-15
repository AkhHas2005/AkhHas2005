# Calculating Bi-Weekly Meeting Dates in Power Automate  

## Me
I'm currently working on a project using Power Automate and SharePoint. One of my variables involves determining the date of teh next triage meeting (every 2 weeks). In SharePoint I want to create a variable and use compose to set it to the date of teh next meeting. For example, if teh current date is 27th November and the previous meeting was on teh 17th, the next one should be on the 1st December. I want to store the initial meeting date (that determines teh bi-weekly cycle) as "17-11-25" and the current date will be received through my "Get response details" connector from MS forms as the date that has been chosen on teh submitted form, the next meeting should be taken from this date and correspond to the bi-weekly meeting cycle. I also want to output this date in an email saying when teh next triage meeting is in the format "date monthName year" e.g. "The next triage meeting is on 1 December 2025."  

## Co-Pilot
Got it — you want to calculate the **next bi-weekly triage meeting date** in Power Automate, based on a fixed starting point (17-11-25) and the date submitted via MS Forms. Then you’ll output that date in a friendly format for your email. Let’s break this down step by step:

---

## 🔹 Step 1: Store the initial meeting date
- Create a variable in your flow called something like **InitialMeetingDate**.
- Set it to `"2025-11-17"` (ISO format is best for calculations).

---

## 🔹 Step 2: Get the submitted date
- From your **Get response details** action, extract the chosen date field.
- Let’s call this variable **SubmittedDate**.

---

## 🔹 Step 3: Calculate the next meeting date
You want to find the next date in the bi-weekly cycle (every 14 days) that is **greater than or equal to** the submitted date.

Here’s how you can do it with an **Expression in a Compose action**:

```plaintext
addDays(variables('InitialMeetingDate'), 
mul(
div(
sub(
ticks(variables('SubmittedDate')), 
ticks(variables('InitialMeetingDate'))
), 
mul(14,864000000000)
), 
14
))
```

### Explanation:
- `ticks()` converts dates into long integer values.
- Subtracting ticks gives the difference between the submitted date and the initial meeting date.
- Divide by `14 days in ticks` → gives how many full bi-weekly cycles have passed.
- Multiply by 14 → gives the offset in days.
- Add that offset to the initial meeting date → gives the **last meeting date**.
- Then add 14 more days → gives the **next meeting date**.

---

## 🔹 Step 4: Format the date for email
Use another **Compose** (or directly in your email body) with:

```plaintext
formatDateTime(outputs('Compose_NextMeetingDate'), 'd MMMM yyyy')
```

This will output:
```
1 December 2025
```

---

## 🔹 Step 5: Insert into email
In your Outlook/Send Email action, you can write:

```plaintext
The next triage meeting is on @{outputs('Compose_FormattedDate')}.
```

---

✅ Result: If the submitted date is 27 Nov 2025, the flow will calculate the next meeting as **1 December 2025**, and your email will say:

**“The next triage meeting is on 1 December 2025.”**

---

Would you like me to **write out the exact Compose expressions** for each step (Initial, Next Meeting, Formatted Date) so you can copy-paste them directly into Power Automate, or do you prefer a more conceptual explanation of the logic?  

## Me
(Now Thursday, Dec 4)  
Ok so now I need help writing an email. I've told me manager that I'll be working from home on Tuesday (because I haven't got university this Tuesday, nothing imortnat is going on in office and I don't need to leave teh house for anything else that day, it'll also cost me £5 in bus tickets both ways), how can I email him for tracking purposes and in-case he forgets  

## Co-Pilot
Here’s a clean, professional draft you can use for your email. It keeps the tone polite and straightforward, while making sure your manager has a written record of your plan:

---

**Subject:** Working from Home – Tuesday  

**Body:**  
Hi [Manager’s Name],  

Just to confirm, I’ll be working from home on Tuesday. I don’t have university commitments that day, and there are no urgent tasks requiring me to be in the office. This arrangement will also save the travel cost.  

Please let me know if you’d prefer me to come in, otherwise I’ll plan to work remotely as agreed.  

Best regards,  
Hasan  

---

This way:  
- You’re **documenting the arrangement** clearly.  
- You’re **showing consideration** by leaving room for your manager to override if needed.  
- You’re keeping the tone professional and concise, without over-explaining.  

Would you like me to also draft a **shorter version** (like a quick reminder email) that you could send the day before, so it’s fresh in your manager’s inbox?  

*End of this Conversation*
