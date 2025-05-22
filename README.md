Dymend Teklab 

SEIS 630 

5/3/2025 

 

Final Write: CRM SYSTEM 

 

Introduction 

 

For my topic I decided to create my own version of a Customer Relationship Management System (CRM). They are used by businesses to both manage and analyze company data. It can track things like interactions with customers, automate tasks, offer views on potential leads or opportunities, and overall improve business growth. They are very important in today's world, and there are many services like Salesforce who have streamlined this process and offer it business. I had chosen to make my own version of a CRM system because I come from a background of Business Marketing. I graduated last year with my bachelors and have worked internships where we use CRM systems like Salesforce. I wanted to do something related to my field, and through working on this project as well as doing some research, I found my projects come with many benefits as well as cons of making your own version vs using one like Salesforce. At minimum I wanted to create the tables with the established constraints, and load some data into it. An optimistic goal I have is to create an API to be able to automate some data entry. 

 

 

Exploration  

 

At the start of this semester, I had about 3 months of coding experience which all came from the fall semester. I did not do any coding relly in undergrad. The reason I joined this program is because I talked to people in my internship and some mentors of mine, and they highly recommended it as marketing nowadays is very analytical. During the winter break before the spring semester I took a few courses through CodeAcademy on SQL to get some of the basics down. It really helped and when we got to picking a project to work on I wanted to do something related to my field and landed on this idea. I had asked ChatGPT beforehand if this was something viable as a project, as I had the idea originally to create a system using data modeler and import data, and it told me it was possible so I decided to go ahead with this idea.  

 

 

Building 

 

So to begin, I first had to create a visualization of what I wanted my system to look like. I decided to look at it from the lens of I am a B2B company and start thinking of what my Tables look like and what I would have in them. I came up with these 11 tables: 

Employee: Keeps tabs on all workers, there, roles, and there information  

  

Lead: Information on any potential clients the business could look into partnering with  

  

Opportunity: Once we have made first intial contact and have deemed the company/customer are actually interested in doing business with us.  

  

Task: This table is related to any activities or assignments employees have. This could be in relation to orders, internal admin work, scheduling meetings, e.t.c.  

  

Order_Tbl: Where all customer orders are tracked. Things like order date, order total, status, and customer id are found in this table  

  

Order_Line: This table is a child table of the order table and handles unit cost, quantity, and product descriptions  

  

Customer: This table keeps track of all our customers' information. For my example I envisioned a B2B company, so information would be things like company names, and signing dates  

  

Contact: This table tracks the information about who in these other companies we keep in contact with. In this table will hold their information, as well as how they preferred to be contacted  

  

Activity: This table keeps track of all the tasks that have already been completed  

  

Invoice: This table keeps track of all tabs we have. How much is owed, when it is owed, payment status is all features you would find in this table  

  

SupportTicket: The last table in our data structure keeps track of support tickets that have been created for any problems with our orders.  

 

Now that I had an idea of what I wanted my tables to look like, I began to start desgining. I first began with creating a Conceptual Data Model. Here I used the SQL Data Modeler system we had used in case to first create a logical build. Here is also where I established the relationships between each table. It would be alot to go over each one individually, however I used all relationships when creating my CRM and give an example of each one 

 

1:M: This relationship could be found when looking at Customer and Contacts. There could be multiple points of contact for a customer, but you would only have one customer associated with each contact. Especially since in this case “Customer” were companies and not individuals 

 

M:N: This relationship was common amongst tables like support tickets to orders. As multiple orders could have multiple support tickets and vice versa  

 

1:1:  This relationship could be found when looking at the invoice and order table. You would only have one invoice associated with one order and only have one order associated with one invoice. 

 

Once I had established the relationships between each table, it was time to forward engineer logical builds and create a relational build. Here is what that looked like afterward 

 

 

![Screenshot 2025-04-25 012326](https://github.com/user-attachments/assets/3a43ccee-1e25-42fb-8519-c410c6100250)


 

After establishing the relationships between each table, I imported it as a DDL File and opened it in SQL Developer. I saved this as CRM_Script which can be found in my onedrive folder. Here is what it looked like as a script:  

![Screenshot 2025-04-27 212705](https://github.com/user-attachments/assets/2e971631-5c4f-465b-9089-d41fd4e497ad)

  

This is just a small snippet, but it was more of the same throughout the DDL file. One thing to note is that I had used the Emp_ID for both the Task & Activity tables but did not establish it as foreign key from the Employees table. I created a CRM_Notes file to make these types of changes and did the following:  

  

![Screenshot 2025-04-27 213039](https://github.com/user-attachments/assets/c1efecd8-2022-4a94-bddd-b201101b2abd)

Now I have created my tables, established the relationships, and loaded them into SQL Developer. All I had to do was load the data in. I used ChatGPT to generate fake data sets for me and put them all onto one file called CRM_INSERT. Here is a sample of what that looked like.image5.png, Picture, Picture 

 
![Screenshot 2025-04-27 215327](https://github.com/user-attachments/assets/0e504d27-8a20-44e1-84f4-2d6d470ef238)
 

Discovering 

Throughout the duration of this course and project, I learned a lot about how to think when it comes to data architecture. Before this class I only really understood the concept of SELECT queries, but now I feel much more confident in my abilities to design and apply. Although I did not reach my optimistic goals within the deadlines of this activity, I still plan on working on this project, and advancing it as much as I can. I realized for myself that actively applying the lessons we have learned throughout this course has helped me so much in terms of retaining information. Here are just some of the few things I believe I have gotten to be much better at.  

 

Normalization 

This was a very important concept when creating the design. Oftentimes I would find myself thinking critically about whether my design choices make sense in a real world setting. For example, my choice to separate Customer, Contact, and Activity was very much intentional. I could of had all of that information on one table, however by creating multiple tables and establishing relationships between them through Foreign Keys, I was able to avoid any duplication when a customer might have multiple contacts 

 

Primary and Foreign Keys 

As I stated beforehand, I had noticed after viewing my CRM_Script that I had referenced the employees table in both task and activity with the Emp_id, however I failed to establish that relationship and create a constraint. After realizing that these tables needed to be associated with specific employees, I used Alter table statements to retroactively define foreign key constraints that enforce this relationship. 

 

Table Creation 

 

As I stated before hand, before taking this course my SQL experience was very minimal. Over the course of this semester my understanding of core concepts drastically improved. 

 

CREATE TABLE Invoice  

    (  

     Order_ID       VARCHAR2 (12)  NOT NULL ,  

     Payment_Status VARCHAR2 (25)  NOT NULL ,  

     Invoice_Number NUMBER (5)  NOT NULL ,  

     Invoice_Date   DATE  NOT NULL ,  

     Due_Date       DATE  NOT NULL ,  

     Amount_Due     NUMBER (11,2)  NOT NULL ,  

     Notes          CLOB  

    )  

; 

 

This is a sample of data I had taken from my CRM_Script. Here I can tell you the design choices that went into this Create table statement. For Order_ID i had to use VARCHAR2 because I wanted the ID a set of 12 numbers and letters. The payment status had a limit of only 25 characters, with the options being ‘Paid’, ‘Unpaid’, and or  ‘In-Process’. I had used the data source type for both when the invoice was issued and when it was due. I had to use a precision and scale of 11 and 2 because I handled a B2B company who would sell in big bulk so purchases could be quite expensive. I also included a CLOB because it would allow employees to write valuable information pertaining to certain invoices if need be.  

 

 

Conclusion  

As I stated beforehand, I do want to continue working on this project and advance my understanding of SQL through practice. I want to continue to learn about API’s and advance my understanding of these topics. Other than that though I am very proud of my work on this project. I set out a goal to complete and was able to do so.  
