# T3A2-A - Full Stack App (Part A)
## Sarah Landis & Connie Jacques Present Hope Hunters: A Missing Persons Aggregate Site
---
## Documentation

### 1. About
#### Purpose
Each year, approximately 40,000 people are reported missing in Australia - that's one person every 18 minutes[^1]. Unfortunately, not all of these cases are exposed to the public in a timely manner, if at all. The more people who are aware of a recently missing person, the greater the likelihood is of finding them. 

The purpose of this website is to provide a platform for both members of the general public and law enforcement to post and share information about missing persons in New South Wales. Allowing members of the public to engage with reports and share details via social media about missing persons will increase the chances of locating the missing persons by engaging a wider network of individuals and organisations, therefore decreasing the amount of time it takes to distribute key information.

The use of this website will hopefully assist in reuniting families, bringing closure to loved ones, and raising awareness about missing persons cases in NSW. Every effort in the search counts and matters, and as a community using this site, we can all do our part to help.

#### Functionality
Users are divided into two groups: members of the general public and Police, where a Police account will belong to a local police station rather than an individual officer. To sign up for an account, general users will be required to provide their full name, a valid, unique email address and a password. Police users will need to provide the station name, police area command, police district, email address (must contain @police.nsw.gov.au) and a password. Users will then be sent a verification link to the email address they provided and will be unable to sign in until they clicked the link to verify their email address. This will also prevent bots from creating user accounts.

Once they have sign up, users will be able to log in with their email and password. A JSON web token which is valid for seven days will be added to their document in the database when they click on the verification link sent to their email address. On each log in the expiry date for this token will be updated, meaning that if the user is active again within seven days they will not need to log in again. 

When logged in, all users will have access to a personalised dashboard where they will be able view their four most recent listings, a search bar if more than four listings exist, options to update or delete their listings, and update their user account details or delete their account. As admin and police users will have the ability to update or delete any missing person listing, they will likely need to use the search bar to locate the listing they wish to modify. 

Logged in users will be able to add missing persons listings. A listings must contain the individual's full name and age, and can also contain a url to a photo, the date they were last seen, current age, the area they are suspected to be in, last known location, hair colour, eye colour, complexion, height, weight, gender, distinctive features and amber alert status. Missing persons listings can also be deleted and updated to contain information not added initially.

The goal of the Hope Hunters website means that any member of the public will be able to view all missing persons listings. These listings will be displayed on the homepage and will be in the style of a Facebook newsfeed style continuous list with a hidden scrollbar. Listings on the homepage will be displayed in chronological order with the newest listings first, and a drop down menu will be available to optionally sort the listings by name (A - Z), location (A - Z), age (ascending or descending) or date (oldest first). A search bar will able be available to to search by location, name, police district, police area command, amber alert status, age, gender, complexion, area suspected to be and last seen (postcode).

#### Features

##### <i>Features required to achieve the above functionality, which comprises the minimum viable product, include:</i>

- <i>Sign up form</i>: The sign up form will have functionality to allow the user to identify as law enforcement. If the user selects this option, the form will change to accommodate sign up for police as different details are required. On sign up, the user will receive an email containing a link to verify their email address and complete their sign up. Once signed up the user will be redirected to sign in.
>
- <i>Sign in form</i>: This form will request the same email address and password used to sign up.
>
- <i>User's dashboard</i>: logged in users will have access to a personalised dashboard which will display the four most recent missing persons listings associated with their account and a search bar, as well as provide access a form to update or delete their account.
>
- <i>Update/delete account form</i>: This form will allow a user to update the details on record for their account. The form will include a button to delete the account. If updating, any fields left blank will remain as whatever is stored in the database (i.e. only filled fields will be updated). 
>
- <i>Add missing person form</i>: This form will be the same regardless of account type. The form fields will be based off the ERD attached below.
>
- <i>Update/delete missing person form</i>: This form will enable authorised users to update or delete a missing persons listing. The user will be required to locate the appropriate listing either their dashboard or via the homepage. Once they have located the listing, if they are authorised to modify the listings, they will be redirected to the form. The form will be same form used to add a missing person but on saving will be update only the modified fields in the database. There will be a button to delete the listing entirely.
>
- <i>Password encryption:</i> user's passwords will be hashed and salted in the front end before the data is attached in a request to the server. This will help to minimise the risk of a successful malicious attack in obtaining useful data.
>
- <i>Mongoose schemas to format models for collections in the database:</i> Data validation will be partly handled through the schemas to ensure consistency. Additional validation will be performed with the express-validator library. For example, express-validator will be used to ensure that a police user's email address will be required to contain the @police.gov.nsw.au postfix.
>
- <i>JWT authentication:</i> User documents in the database will be assigned a json web token with a seven day expiry on sign up. Their JWT will enable easy user authentication and will enable a user to remain logged in if they have used their account within the previous seven days, providing a nicer user experience.
>
- <i>Share a missing person listing to Facebook and by email:</i> All missing person's listings will contain the option to share directly Facebook or by email. User's will not be required to sign up to have access to this functionality.

##### <i>Nice to have features to enhance overall functionality of the site and increase quality of UX:</i>

- Directly share listings to additional social media outlets such as Twitter.
- Amber alert banner at the top of the home page with responsive infinite horizontal scrolling.
- Support page with crime stoppers info, grief support, mental health resources, etc.
- Option for a user to reset their password if they have forgotten it.
- Retrieve 30 listings at a time from the database for the continuous page. Only once they’ve been viewed, get the new 30, etc.
- Store missing persons images directly to database instead of a url to an image hosted on, for example, Photobucket. 

#### Target Audience
The target audience for this site, as briefly explained above, is the general public. With police busy with major crimes across different sectors and far too many annual missing person cases being filed, this site aims to enlist the assistance and knowledge of the general public.

In today's interconnected digital world there lies strength in numbers. The power and gravity of collective action is important to understand in this context. With social media acting as a catalyst, the swift dissemination of information is made much easier, and is hopefully able to play a crucial role in assisting someone's safe return home. Additionally, having direct access to share a listing to social media may be a lifesaver. You may not know the missing person, but social media contacts of yours may know them or have seen them. You never know how many connections away you are from a missing person, or whether someone you know has important information about them.

Our goal is to minimize the delay in information reaching the public, as well as in assisting law enforcement to pool together every possible avenue of a potential connection to better help locate a missing person.

#### Tech Stack
<i>Primary Programming Language:</i> 
JavaScript

<i>Front End:</i> 

- React
- HTML 
- CSS
- TailwindCSS
- Deployed to: GitHub Pages or Netlify



<i>Back End:</i>

- Server: Node
- Web Server Framework: Express
- ODM: Mongoose
- Deployed to: AWS EC2 Instance or Heroku 

<i>Database:</i>
MongoDB

- Deployed to: MongoDB Atlas

<i>Version Control:</i> 
Git

- Repository host: GitHub Organisation

<i>Text Editor:</i> VS Code

<i>Testing Frameworks:</i>

- Back end: Jest and Supertest
- Front End: React Testing Library

<i>Additional Dependencies:</i>

- Front end:
    - tailwindcss
    - react-router-dom
    - react-share
    - bcryptjs

- Back end:
    - nodemon (dev)
    - express-validator
    - jsonwebtoken
    - dotenv
    - helmet
    - cors
    - nodemailer
    - nodemailer-sendgrid-transport


### 2. Dataflow Diagrams

![General User Sign Up](./docs/data-flow-diagrams/general-user-sign-up-dfd.png)
![Police User Sign Up](./docs/data-flow-diagrams/police-user-sign-up-dfd.png)
![General User Sign In](./docs/data-flow-diagrams/general-user-sign-in-dfd.png)
![Police User Sign In](./docs/data-flow-diagrams/police-user-sign-in-dfd.png)
![Update General User Details](./docs/data-flow-diagrams/update-general-user-dfd.png)
![Update Police User Details](./docs/data-flow-diagrams/update-police-user-dfd.png)
![Delete General User Account](./docs//data-flow-diagrams/delete-general-user-dfd.png)
![Delete Police User Account](./docs/data-flow-diagrams/delete-police-user-dfd.png)
![Add New Missing Person](./docs/data-flow-diagrams/new-missing-person-dfd.png)
![Update Missing Person](./docs/data-flow-diagrams/update-missing-person-dfd.png)
![Delete Missing Person](./docs/data-flow-diagrams/delete-missing-person-dfd.png)
![Get Missing Persons](./docs/data-flow-diagrams/get-missing-person-dfd.png)

### 3. Application Architecture Diagram

![App Architecture Diagram](./docs/AAD.png)

An ERD is attached for the purpose of visualising the database schema/models that will be implemented.

![Hope Hunters MongoDB ERD for visualisation purposes](./docs//hope-hunters-erd.png)

---
## Design & Project Flow

### 4. User Stories and Personas
#### Stage 1 - Preliminary Users and Stories
>
In developing our site, it was apparent based off the intended functionality that there would be four types of users: public users (any user not logged-in), generic user (a user not of the other types who's logged in), admin, and police users. Any of these types of users can still interact with the site without being logged in, however a logged in user provides added functionality, with police and admin sharing the same levels of accessibility to the stored records of missing persons. Logged-in admin users have the ability and authorization to access records of all reports and all users (including police).

The preliminary user stories are as follows:

- Public User:
    >
    - As a public user, I want to view a list of missing persons.
    - As a public user, I want to search for a missing person.
    - As a public user, I want to share a missing person to a social media platform.
>
- Generic User (any user not of the admin/police type, and also logged in):
    >
    - As a logged-in generic user, I want to be able to see all the reports I've made.
    - As a logged-in generic user, I want to be able to update my account details.
    - As a logged-in generic user, I want to lodge new missing person reports.
>
- Logged-in Police:
    >
    - As a logged-in police user, I want to change my station details.
    - As a logged-in police user, I want to update the details of a currently logged case made by a generic user.
    - As a logged-in police user, I want to add a new missing person report.
>
- Logged-in Admin:
    >
    - As a logged-in admin user, I want to see a list of all users.
    - As a logged-in admin user, I want to see how many missing person reports are filed.
    - As a logged-in admin user, I want to view all the police stations are using the site.

#### Stage 2 - User Personas
After understanding the general needs of the intended users, in order to gain better insight on these users' needs, we created user personas. These personas are representative of the intended users of the site, and allows us to understand, as developers, what their needs are in the creation of features to be included in the site.

** Public users are generic users not logged-in; generic users are logged-in users that are also not police or admin.

- Betty is considered a public user.
    >
    ![Betty persona](./docs/betty-persona.png)
>
- Peter is considered a generic user (logged-in).
    >
    ![Peter persona](./docs/peter-persona.png)
>
- Michael is considered a police user (logged-in).
    >
    ![Michael persona](./docs/michael-persona.png)
>
- Julia is considered a generic user (logged-in).
    >
    ![Julia persona](./docs/julia-persona.png)
>
- Steve is considered a public user.
    >
    ![Steve persona](./docs/steve-persona.png)
>
- Megan is considered an administrative user (logged-in).
    >
    ![Megan persona](./docs/megan-persona.png)
>
#### Stage 3 - Refined User Stories
Upon reviewing and getting familiar with the personas of the intended users, we were able to further fine tune the user stories. This AGILE process allowed us to focus on the purpose of our site, rather than create useless features that a user wouldn't need.
>
- ##### Betty, Public User:
    >
    - As Betty, I want to view a list of missing persons so that I can see if any have been on the special news reports.
        - As Betty, I want to view a list of missing persons in my own time so that I can see if any have been on the special news reports that come on after I go to sleep.
    - As Betty, I want to view a list of missing persons so that I can easily see if I know anyone directly.
    - As Betty, I want to view a list of missing persons with big facial photos so I can easily read and understand.
    - As Betty, I want to search for a specific missing person so that I can provide useful information if I do know of them.
    - As Betty, I want to share a missing person to my social media so that I can share information to my elderly friends who may have knowledge.
        - As Betty, I want to share a missing person to my social media so that I can share information about any elderly friends who go missing for age-related reasons.
    - As Betty, I want to be able to use my desktop to look for missing persons because I do not own a mobile phone.
    >
    ##### Acceptance criteria:
    - Large facial images and easy-to-read text for elderly users
    - Easy to navigate layout (list) of missing persons
    - Ability to clearly search for a missing person using relevant search parameters (location, gender, age, etc)
    - A special feature/button that allows for simple sharing of info to external social media platform(s)
    - Appropriate rendering of content and full visibility of site on a desktop (no cutting off of any information)
>
- ##### Peter, Generic User (any user not of the admin/police type, and also logged in):
    >
    - As Peter, I want to use a website that pools information for me so that I can stop using multiple sites to find information.
    - As Peter, I want to be able to lodge a new missing report so that I can keep track of new uncovered cases from my internet sleuthing.
        - As Peter, I want to lodge new missing person reports so that I can be keep track of new uncovered Australian cases whilst internet sleuthing.
    - As Peter, I want to see a list of all my active reports so that I can play my part in maintaining the site with current information.
    - As Peter, I want to use a missing persons website so that I can browse/log on anytime that works with my schedule and still see current data.
    >
    ##### Acceptance criteria:
    - User friendly interface that allows for information to be displayed in a clear but efficient way
    - Incorporate a form for user to fill in and create a new missing persons report
    - Create a portal/dashboard for user account to allow users to view logged reports attributed to their account
    - Create a login form to allow users to enter details and access their dashboard
    - Ensure website and user portal is accessible and fully functional at all times for user convenience
>
- ##### Michael, Police User (logged-in):
    >
    - As Michael, I want to change my station details so that if I get stationed elsewhere, I won't lose my account. 
        - As Michael, I want to change my station details so that if I get stationed elsewhere, I can keep my account active and still be a valued member of the missing persons site.
    - As Michael, I want to update the details of a currently logged case made by a generic user so that case details can remain current.
        As Michael, I want to update the details of a currently logged case made by a generic user so that families and helpful civilians can work with the most current and reliable information.
    - As Michael, I want to add a new missing person report so that others can help in the search.
        - As Michael, I want to add a new missing person report to reach a greater audience more quickly because I do not have enough time to do a press conference for every missing person.
    - As Michael, I want to delete a missing person report so that families can recieve peace and closure once a case is closed.
    >
    ##### Acceptance criteria:
    - Create a login form to allow police to enter details and access their dashboard/portal
    - Include search option within dashboard for police to query the data
    - Ability to search current cases from a generic user and modify details
    - Create a form to add a new missing person to the database
    - Include a button to completely remove a missing person from the database
>
- ##### Julia, Generic User (any user not of the admin/police type, and also logged in):
    >
    - As Julia, I want to be able to create an account as I have been recently affected by a missing person.
        - As Julia, I want to be able to create a new account so I can share that my daughter has recently gone missing.
    - As Julia, I want to be create a new missing person report for my daughter so that people can help me find her.
    - As Julia, I want to be able to share my missing person report on my social media so that other people can view reliable and organized information.
        - As Julia, I want to be able to share my missing person report on my social media so that other people can view reliable and organized information and continue to share it easily on their profiles too.
    - As Julia, I want to lodge new missing person reports so that can raise awareness for other peoples' missing children.
    - As Julia, I want to be able to find relevant resources on the site so that I can get mental health support.
        - As Julia, I want to be able to find relevant resources on the site so that I can get mental health support without feeling like I am not doing enough to help find my daughter.
    >
    ##### Acceptance criteria:
    - Create a signup form for new users to enter details and become a member of the database
    - Create a form accessible from the dashboard, for logged-in users to create a new report
    - Incorporate a special feature so anyone can directly share report information to an external social media platform
    - Ability to view from the dashboard all reports logged to user account in order to keep track of currently active reports
    - Clearly display resource options such as counselling, emergency hotlines, tip hotlines, etc.
>
- ##### Steve, Public User:
    >
    - As Steve, I want to view a list of missing persons by locality so that I can bring more awareness to them during my news reports.
    - As Steve, I want to search a list of missing persons by different fields so that I can bring more awareness to the prevalence of missing children (example).
    - As Steve, I want to search for a missing person so that I can follow up leads if that person is not a high profile case.
        - As Steve, I want to search for a missing person so that I can get more public information including last whereabouts etc and use this to speak to the local community. 
    - As Steve, I want to share a missing person to my social media platform. 
        - As Steve, I want to share a missing person to my social media platform to reach my social media followers and bring attention to a particular case.
        - As Steve, I want to share a missing person to my social media platform because my generation does not watch the news often. 
    >
    ##### Acceptance criteria:
    - Include a search bar that allows users to specify accepted search parameters
    - Dynamically display data as per user search in a clear manner
    - Include a search bar that allow users to search by name and return single data
    - Incorporate a special feature so anyone can directly share clear and reputable report information to an external social media platform
>
- ##### Megan, Admin User (logged-in):
    >
    - As Megan, I want to see a list of all users so that I can keep track of the usage of the site.
        - As Megan, I want to see a list of all users so that I can see if the site is growing in popularity and gaining traction, or if the site needs to be altered.
    - As Megan, I want to see how many missing person reports are filed so that I can see how much of the database is being used.
    - As Megan, I want to view all the police stations are using the site so that I can reach out to any if required.
       - As Megan, I want to view all the police stations are using the site so that I can reach out to any about case detail change logs if required.
    - As Megan, I want to delete a user because they are reporting erroneous missing persons.
        - As Megan, I want to delete a user because they are reporting erroneous missing persons and discrediting the site by doing so.
    >
    ##### Acceptance criteria:
    - Create a login form to access a user dashboard/portal
    - Allow ability for admin users to access all current user data and display in a clear manner
    - Include search option within dashboard for admin to query the data
    - Include a button within the dashboard to delete any user if required

### 5. Design Processes & Wireframing

### 6. Project Management
The kanban project management style will be followed to structure the implementation of each step in undertaking this project. This style has been chosen because it will enable our team to visualise what tasks need to be undertaken, what is underway, what individual team members need to review, and what has been completed. Being able to see what has been done can help to foster a sense of accomplishment and provide motivation to keep going. And. by dividing tasks up into very small snippets that can be completed in a few hours, the list of remaining tasks does not seem so daunting and thus can allow team members to remain motivated and inspired. 

Our team has created a trello board to enable us to visualise this information. Our board is divided into seven columns: Part A To Do, Part B To Do, Connie In Progress, Sarah In Progress, Under Review, Completed, and Nice to Have. This structure was chosen to best facilitate visualisation of who is doing what currently and to aid in the prioritisation of tasks. Each card on the board contains a title, may include the name to the team member/s who have chosen to undertake the task, a colour indicated the estimated time it will take to complete the card (the key for this colour system can be found in the board's description) and a detailed description of what needs to be done. As tasks are undertaken and completed the are moved to the next appropriate column.

The flexibility of the kanban management style will enable our team members to review and return to tasks that have been completed with ease, should further work or revision be needed during the course of the project.

In addition to use of the trello board our team will be hosting daily check-ins on Discord and will be continuous contact via Discord. This will enable team members to share their progress, request assistance, discuss additional requirements, ask clarifying questions, and generally support each other.

Our trello board can be found here: https://trello.com/b/7NMGHoN7/full-stack-app

<i>Trello Board Description</i>

![Trello board description](./docs/trello/trello-description.png)
<br>
<i>Trello Board Progress Screenshots</i>

![Trello board progress 30/06/2023](./docs/trello/trello-screenshot1.png)
![Trello board progress 03/07/2023](./docs/trello/trello-screenshot2.png)
<br>
<i>Trello Board Card Examples</i>

![Trello board card example format readme.md](./docs/trello/trello-card-example1.png)
![Trello board card example AAD](./docs/trello/trello-card-example2.png)


#### Sources Used: 
[^1]: Henderson, M., Henderson, P. and Kiernan, C. (2000). Missing Persons: Incidence, Issues and Impacts. [online] Available at: https://www.aic.gov.au/sites/default/files/2020-05/tandi144.pdf.


[^2]: paletton.com. (n.d.). Paletton - The Color Scheme Designer. [online] Available at: https://paletton.com/#uid=43w0n0kJTrhn3OgmWBjUJdkVy5B [Accessed 3 Jul. 2023].



[^3]: Interaction Design Foundation (n.d.). What is Color Theory? [online] The Interaction Design Foundation. Available at: https://www.interaction-design.org/literature/topics/color-theory#:~:text=Color%20theory%20is%20the%20collection.



[^4]: Gross, R. (2019). Color meaning and symbolism: How to use the power of color in your branding. [online] Learn. Available at: https://www.canva.com/learn/color-meanings-symbolism/.


[^5]: U.S. Web Design System (USWDS). (2023). Typography. [online] Available at: https://designsystem.digital.gov/components/typography/#included-typefaces-2 [Accessed 4 Jul. 2023].


[^6]: Eye on Design. (2019). The U.S. Government’s Public Sans Is a Typeface Fit for Civic Duty. [online] Available at: https://eyeondesign.aiga.org/the-u-s-governments-public-sans-is-a-typeface-fit-for-civic-duty/ [Accessed 4 Jul. 2023].


[^7]: GitHub. (2023). Public Sans. [online] Available at: https://github.com/uswds/public-sans [Accessed 4 Jul. 2023].

