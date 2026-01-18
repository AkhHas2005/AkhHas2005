# Questions for Client Interview on Workflow Management System  

## Me
Me and my friends are doing a university group project and we have an interview with clients coming up for the following project:  
P1. Workflow management system for non-crime related activity  
Yorkshire and Humber Regional Organised Crime Unit, has a department which requires an improved workflow management system for non-crime related activity. The department manages support activities to the YHROCU, with staff set either individual or collaborative tasks.  
A web-based system is required, which would enable tasks to be assigned to one, or multiple members of staff. The system needs to:  
- email the staff member when a task is assigned to them.
- enable the user to update the task status, due and review dates, and input progress updates to a rolling log.
- prevent staff from deleting a task, or any previous updates.
- allow supervisory access to view all tasks, with flexibility to enable tasks to be visible to either the assigned persons only, or to be viewed by all.
- allow a supervisor to close, or delete a task.
- provide a dashboard to categorise and summarise the tasks, with suitable filters, such as status or due date.
- have an export data function, such as CSV or PDF.
- have built in flexibility to allow adding new data fields to tasks, to allow future changes.
- have a search function for task searching.
- implement user authentication using OpenAuth or similar, to enable compatibility with existing infrastructure.

What questions can we ask, can you guide us with examples as if you are our team supervisor (a more experienced student who has taken this module before and has a high level of computer scienec expertise)  

## Co-Pilot
That sounds like an exciting and challenging project! Here are some suggested questions you might ask your clients during the interview to gather more information and ensure you understand their needs thoroughly:

### General Understanding
1. **What are the primary goals of the new workflow management system?**
2. **Can you provide examples of the types of tasks that need to be managed?**

### Task Management
3. **How are tasks currently assigned and tracked?**
4. **Are there any specific task categories or tags that need to be incorporated into the system?**

### Notifications
5. **Are there any specific requirements for the email notifications when tasks are assigned?**
6. **Should the notifications be customizable by the supervisors?**

### User Roles and Permissions
7. **Can you detail the different user roles and their specific permissions (e.g., staff members, supervisors)?**
8. **Are there any existing user management systems that we need to integrate with?**

### Task Updates
9. **What specific information should be included in the task status updates and progress logs?**
10. **How often do you expect users to update their tasks?**

### Supervisory Access
11. **What level of visibility do supervisors need for the tasks?**
12. **How flexible should the visibility settings be for different tasks?**

### Dashboard and Reporting
13. **What key performance indicators (KPIs) do you want to see on the dashboard?**
14. **Can you provide examples of the types of filters that will be useful for task categorisation?**

### Data Export
15. **What specific data formats do you need for exporting data (e.g., CSV, PDF)?**
16. **How frequently do you expect to export data?**

### Flexibility and Future Changes
17. **What type of new data fields do you foresee needing in the future?**
18. **How important is it for the system to be adaptable to changes in workflow processes?**

### Authentication
19. **Can you provide details about the existing infrastructure for user authentication?**
20. **Do you have a preference for specific authentication methods (e.g., OpenAuth)?**

### Additional Considerations
21. **Are there any compliance or security requirements that we need to be aware of?**
22. **Is there anything else you would like to see included in the system that we haven’t covered?**

By asking these questions, you can gain a deeper understanding of your clients' needs and ensure that your project meets their expectations. Best of luck with your interview and the project! 😊  

## Me
(Now Tuesday, Feb 4)  
I'm creating like a template for the project scope & objectives document, this is what I currently have but I want to replace each bullet point (as these are for another unrelated project) with information that can help my friends fill it out, similar to how I've done on teh first line:  
Objective: Develop [overall description of what to develop]  
Scope:  
- Let user create an access request through the Microsoft form
- Process the form through a Power Apps workflow
- Validate the request through a Validation workflow
- Send an email alert through an Email flow
- Email takes them to the app where they can approve or deny the request
- Automatically updates the SharePoint list with Requests Information
- Sends an email back to original requestor with relevant information
- Include change requests forms + relevant workflow
- Demonstrate & Train SAP Champions on how to use form & app
- Get feedback from SAP Champions and then perform feasibility study

Project Goals:  
- MAIN GOAL: Ensure approval process is smooth & all relevant information stored on SharePoin
- Setup an access request form that is simple to use and efficient
- Create a workflow that processes the form in Power apps
- Have meeting with SAP Champion and get necessary information about the requests and approval process
- Create a workflow in Power apps that validates requests against the required schema
- Create a workflow that sends an email to the relevant people depending on the request, with ability to access the app directly from the email
- Have a system interface that allows the SAP Champion to approve or deny the request
- Have a workflow in Power Apps that sends information back to SharePoint when there is an Access Request
- Create another workflow similar to the previous email workflow that sends information back to the original requestor
- Create a workflow that doesn’t involve the app but only email & SharePoint form
- Demonstration meeting with SAP Champions + get feedback
- Meeting between ourselves to discuss feedback, implement some things and review things that aren’t possible
- Get back to SAP Champions with improvements and mitigations
- Keep ourselves in the loop and maybe more of the Team

## Co-Pilot
Absolutely, here's a version of the template tailored for your project:

### Objective:
Develop a web-based workflow management system for non-crime related activities for the Yorkshire and Humber Regional Organised Crime Unit.

### Scope:
- Assign tasks to individual or multiple staff members through the web-based system.
- Send automated email notifications to staff members when a task is assigned to them.
- Enable users to update task status, due dates, review dates, and input progress updates to a rolling log.
- Prevent staff from deleting tasks or any previous updates.
- Allow supervisory access to view all tasks, with the flexibility to enable tasks to be visible to either the assigned persons only or to be viewed by all.
- Allow a supervisor to close or delete tasks.
- Provide a dashboard to categorize and summarize tasks with suitable filters, such as status or due date.
- Implement an export data function (e.g., CSV, PDF).
- Include flexibility to add new data fields to tasks to allow future changes.
- Implement a search function for task searching.
- Incorporate user authentication using OpenAuth or similar for compatibility with existing infrastructure.

### Project Goals:
- **MAIN GOAL:** Ensure the workflow management system improves task assignment, tracking, and completion efficiency.
- Develop a user-friendly interface for assigning and tracking tasks.
- Create a notification system that sends email alerts when tasks are assigned.
- Enable users to easily update task status and log progress.
- Implement robust access control to ensure only authorized personnel can modify or view tasks.
- Develop a comprehensive dashboard that provides supervisors with an overview of all tasks.
- Ensure data can be easily exported for reporting and analysis.
- Allow for future scalability by enabling the addition of new data fields.
- Provide a search function to quickly find specific tasks.
- Integrate the system with existing user authentication methods to ensure security and compatibility.

Feel free to adjust or expand upon these points to better suit your project’s specifics and needs. This should give your team a solid foundation to start with!  

## Me
No I mean don't put actual information for the project but just placeholders that also indicate what to write to replace the placeholders with  

## Co-Pilot
Got it! Here’s a template with placeholders that indicate what to write to replace them with:

### Objective:
Develop [Overall description of what the system is and what it will achieve].

### Scope:
- Assign tasks to [Describe who the tasks will be assigned to, e.g., individual or multiple staff members].
- Send [Type of notifications] to staff members when a task is assigned to them.
- Enable users to update [Types of task details that can be updated, e.g., status, due dates, progress updates].
- Prevent [Specify what should not be allowed, e.g., deleting tasks or previous updates].
- Allow supervisory access to [Describe the level of access supervisors will have and the flexibility required].
- Provide a dashboard to [Explain what the dashboard will do, e.g., categorize and summarize tasks with filters].
- Implement an export data function for [Specify data formats, e.g., CSV, PDF].
- Include flexibility to [Describe future changes or additions that the system should accommodate].
- Implement a search function for [Specify what will be searchable, e.g., tasks].
- Incorporate user authentication using [Specify authentication method, e.g., OpenAuth] for compatibility with existing infrastructure.

### Project Goals:
- **MAIN GOAL:** Ensure [Describe the main objective and overall benefit of the system].
- Develop a user-friendly interface for [Specify the main functionalities of the interface].
- Create a notification system that [Describe how the notification system will work and its purpose].
- Enable users to [Specify actions users will be able to perform, e.g., update task status and log progress].
- Implement robust access control to [Describe the importance of access control and what it will prevent or allow].
- Develop a comprehensive dashboard that [Explain the purpose and benefits of the dashboard].
- Ensure data can be easily exported for [Specify the reasons for exporting data and its formats].
- Allow for future scalability by [Describe how the system will accommodate future changes].
- Provide a search function to [Explain the importance and functionality of the search feature].
- Integrate the system with existing user authentication methods to [Describe the benefits of integrating with existing infrastructure].

Feel free to customize these placeholders with the specific details of your project!  

## Me
How I can I describe what a Scope is and what the project objectives are for my friends given the context?  

## Co-Pilot
Absolutely, I'd be happy to help you explain these concepts.

### Project Scope
The **scope** of a project outlines the specific tasks, deliverables, and boundaries of the project. It defines what will be included in the project and what will be excluded. The scope essentially sets the parameters for what the project team will work on and helps prevent "scope creep," which is when additional tasks or changes are added without proper review or approval. Here’s a more detailed explanation you can share with your friends:

**Project Scope:**
The project scope provides a clear and detailed description of the work that needs to be completed. It includes:
- **Tasks and Activities:** Specific tasks that need to be performed to achieve the project objectives.
- **Deliverables:** The tangible or intangible outcomes or products that will be delivered upon project completion.
- **Boundaries:** Defines what is within the scope of the project and what is outside of it. It helps clarify what will and won't be addressed by the project.
- **Constraints:** Any limitations or restrictions that the project team needs to be aware of, such as budget, time, or resources.
- **Assumptions:** Any assumptions made while defining the scope that may impact the project’s success.

### Project Objectives
The **project objectives** are the specific goals that the project aims to achieve. They are measurable and time-bound, providing a clear focus for the project team. Objectives should be SMART: Specific, Measurable, Achievable, Relevant, and Time-bound. Here’s a more detailed explanation for your friends:

**Project Objectives:**
The project objectives define the desired outcomes and success criteria of the project. They include:
- **Overall Goal:** A high-level statement that describes what the project aims to achieve.
- **Specific Targets:** Detailed and measurable goals that provide a clear direction for the project team. These could include metrics like time frames, quality standards, and budget limits.
- **Performance Indicators:** Metrics and standards used to measure the success and progress of the project.
- **Key Milestones:** Important checkpoints or phases within the project timeline that signify progress towards the final objectives.
- **Expected Benefits:** The advantages or improvements that the project will bring to the organization or stakeholders upon completion.

### Example
For your project, it might look something like this:

**Project Scope:**
- Assign tasks to staff members through the web-based system.
- Enable task status updates, due dates, review dates, and progress logs.
- Implement automated email notifications for task assignments.
- Provide supervisory access to view and manage all tasks.
- Develop a dashboard for task categorization and summarization.
- Include data export functionality (e.g., CSV, PDF).
- Implement a search function for task retrieval.
- Incorporate flexible and scalable features for future updates.

**Project Objectives:**
- **Overall Goal:** Develop an efficient and user-friendly workflow management system for the YHROCU’s non-crime-related activities.
- **Specific Targets:** Ensure task assignment, tracking, and completion processes are streamlined and automated.
- **Performance Indicators:** Measure user satisfaction, task completion rates, and system reliability.
- **Key Milestones:** Design phase, development phase, testing phase, deployment phase, and training phase.
- **Expected Benefits:** Enhanced efficiency, improved task management, and better resource allocation.

I hope this helps clarify the concepts for your friends!  

*End of this Conversation*
