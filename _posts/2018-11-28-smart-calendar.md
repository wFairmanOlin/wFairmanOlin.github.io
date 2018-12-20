---
layout: post
title: "Smart Calendar"
image: "/assets/img/fill.png"
---
## Smart Calendar-- The calendar of the future
Smart Calendar interfaces with Google Calendar to automatically schedule to-do items based on availability and user preference. Smart Calendar schedules what you want to do, when you want to do it. Over time it learns your work and rest patterns, for increased accuracy and improved user experience.

### Goal
By automating this scheduling process, we aim to reduce the stress of feeling overbooked, and take out overwhelming and repetitive decision making out of the process. We started this project with the intention to learn about applications of matrix algebra in user-facing applications.


### Program Architecture
Our overall program structure consists of a web interface and a scheduling program which interfaces with Google Calendar. Through the web interface, the user can create both time-defined events and to-do items without a set time. Time-defined events are scheduled directly to the user's Google Calendar, while to-do items are added to a list which the scheduling program schedules in the user's free time.

The scheduling program works by getting a list of busy and free time blocks from Google Calendar, then using a dynamic linear assignment algorithm to schedule to-do items in the free time blocks.

![](/assets/img/structure.png)

As the user uses the app, the program records data of what types of activities the user prefers to do at certain times of day or days of the week. This is used to create a cost matrix for doing a given activity at a certain time. This cost matrix allows the assignment algorithm to create a schedule that aligns with the user's habits and preferences.

In addition to remembering scheduling habits, the program takes user feedback into account to adjust the cost matrix. The user can accept or reject a proposed schedule from the web interface, and this feedback will update the stored preference data.

### Linear assignment
Our program relies on a linear assignment solver from SciPy to assign unscheduled tasks to available time slots. It breaks up the day into time blocks the same length as the longest event to schedule and assigns the longest events to time blocks in a way that minimizes cost. It does this several times to find the lowest cost by having the time blocks start at different offsets.

Once the longest events are scheduled, the next longest batch of tasks is scheduled in the same way, trying different time block offsets to optimize the schedule.

![](/assets/img/AR_2.png)

### Detailed Program Architecture
Below is a more detailed diagram of how different parts of our program interact.

![](/assets/img/Screenshot%20from%202018-04-24%2014-00-34.png)
