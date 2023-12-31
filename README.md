## T3A2-A - Full Stack App (Part A)
### Sarah Landis & Connie Jacques 

# Hope Hunters: A Missing Persons Aggregate Site
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
- Functionality for user's to contact an Admin.
- Admin Dashboard to enable logged in admin level users to view a list of all users, see a total number of missing person reports (maybe add this in on the homepage for all users to see) and view total number of police stations with an account.

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
In developing our site, it was apparent based off the intended functionality that there would be four types of users: public users (any user not logged-in), general user (a user not of the other types who's logged in), admin, and police users. Any of these types of users can still interact with the site without being logged in, however a logged in user provides added functionality, with police and admin sharing the same levels of accessibility to the stored records of missing persons. Police users can modify any general users' reports, and admin can modify any police or general users' reports.

The preliminary user stories are as follows:

- Public User:
    >
    - As a public user, I want to view a list of missing persons.
    - As a public user, I want to search for a missing person.
    - As a public user, I want to share a missing person to a social media platform.
>
- General User (any user not of the admin/police type, and also logged in):
    >
    - As a logged-in general user, I want to be able to see all the reports I've made.
    - As a logged-in general user, I want to be able to update my account details.
    - As a logged-in general user, I want to lodge new missing person reports.
>
- Logged-in Police:
    >
    - As a logged-in police user, I want to change my station details.
    - As a logged-in police user, I want to update the details of a currently logged case made by a general user.
    - As a logged-in police user, I want to add a new missing person report.
>
- Logged-in Admin:
    >
    - As a logged-in admin, I want to be able to modify any user-type's listing.
    - As a logged-in admin, I want to be able to delete any user-type's listing.
>

#### Stage 2 - User Personas
After understanding the general needs of the intended users, in order to gain better insight on these users' needs, we created user personas. These personas are representative of the intended users of the site, and allows us to understand, as developers, what their needs are in the creation of features to be included in the site.

** Public users are general users not logged-in; general users are logged-in users that are also not police or admin.

- Betty is considered a public user.
    >
    ![Betty persona](./docs/betty-persona.png)
>
- Peter is considered a general user (logged-in).
    >
    ![Peter persona](./docs/peter-persona.png)
>
- Michael is considered a police user (logged-in).
    >
    ![Michael persona](./docs/michael-persona.png)
>
- Julia is considered a general user (logged-in).
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
        - As Betty, I want to share a missing person to my Facebook and email so that I can share information about any elderly friends who go missing for age-related reasons.
    - As Betty, I want to be able to use my desktop to look for missing persons because I do not own a mobile phone.
    >
    ##### Acceptance criteria:
    - Large facial images and easy-to-read text for elderly users
    - Easy to navigate layout (list) of missing persons
    - Ability to clearly search for a missing person using relevant search parameters (location, gender, age, etc) from the homepage without a login or signup requirement
    - A special feature/button that allows for simple sharing of info to external social media platform(s)
    - Appropriate rendering of content and full visibility of site on a desktop (no cutting off of any information)
>
- ##### Peter, general User (any user not of the admin/police type, and also logged in):
    >
    - As Peter, I want to use a website that pools information for me so that I can stop using multiple sites to find information.
    - As Peter, I want to be able to lodge a new missing report so that I can keep track of new uncovered cases from my internet sleuthing.
        - As Peter, I want to lodge new missing person reports so that I can be keep track of new uncovered New South Wales cases whilst internet sleuthing.
    - As Peter, I want to see a list of all my active reports so that I can play my part in maintaining the site with current information.
    - As Peter, I want to use a missing persons website so that I can browse/log on anytime that works with my schedule and still see current data.
    >
    ##### Acceptance criteria:
    - User friendly interface that allows for information to be displayed in a clear but efficient way
    - Incorporate a form for user to fill in and create a new missing persons report
    - Create a portal/dashboard for user account to allow logged-in user to view and modify their logged reports 
    - Create a login form to allow users to enter details and access their dashboard
    - Ensure website and user portal is accessible and fully functional at all times for user convenience
    - Create a button to display all of a logged-in user's reports
>
- ##### Michael, Police User (logged-in):
    >
    - As Michael, I want to change my station's details so that the station account details stay current and all police officers at my station can use the site. 
    - As Michael, I want to update the details of a currently logged case made by a general user so that case details can remain current.
        - As Michael, I want to update the details of a currently logged case made by a general user so that families and helpful civilians can work with the most current and reliable information.
    - As Michael, I want to add a new missing person report so that others can help in the search.
        - As Michael, I want to add a new missing person report to reach a greater audience more quickly because I do not have enough time to do a press conference for every missing person.
    - As Michael, I want to delete a missing person report so that families can recieve peace and closure once a case is closed.
    >
    ##### Acceptance criteria:
    - Create a login form to allow police to enter details and access their dashboard/portal
    - Include search option within dashboard for police to query the data
    - Ability to search current cases from a general user and modify details
    - Create a form to add a new missing person to the database
    - Include a button to completely remove a missing person from the database
>
- ##### Julia, general User (any user not of the admin/police type, and also logged in):
    >
    - As Julia, I want to be able to create an account as I have been recently affected by a missing person.
        - As Julia, I want to be able to create a new account so I can share that my daughter has recently gone missing.
    - As Julia, I want to be create a new missing person report for my daughter so that people can help me find her.
    - As Julia, I want to be able to share my missing person report on my social media so that other people can view reliable and organized information.
        - As Julia, I want to be able to share my missing person report via Facebook and email so that other people can view reliable and organized information and continue to share it easily on their profiles too.
    - As Julia, I want to lodge new missing person reports so that can raise awareness for other peoples' missing children.
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
        - As Steve, I want to share a missing person to my Facebook or email to reach my followers and bring attention to a particular case.
        - As Steve, I want to share a missing person to my Facebook or email because my generation does not watch the news often. 
    >
    ##### Acceptance criteria:
    - Include a search bar that allows users to specify accepted search parameters
    - Dynamically display data as per user search in a clear manner
    - Include a search bar that allow users to search by name and return single data
    - Incorporate a special feature so anyone can directly share clear and reputable report information to an external social media platform
>
- ##### Megan, Admin User (logged-in):
    >
    - As Megan, I want to be able to login to the site so that I can update reports from any users as required.
        - As Megan, I want to be able to login to the site so that I can update or delete reports from any users as required.
    - As Megan, I want to be able to log reports from my account in case I am affected by a missing person.
    - As Megan, I want to delete a report because it has been solved.
        - As Megan, I want to delete a report because it has been solved or closed, and is no longer needing to be shown on the site.
    >
    ##### Acceptance criteria:
    - Create a login form to access a user dashboard/portal
    - Allow ability for admin users to view and edit any current missing person report
    - Create a form in the dashboard/portal for admin to modify any current missing person report
    - Include search option within dashboard for admin to query missing persons reports
    - Include a button within the dashboard to delete any report if required

### 5. Design Processes & Wireframing

#### Figma Wireframes
In designing this site, careful consideration was given to the various user types the application would cater to as well as determining the best way to incorporate the minimum viable product (MVP) features that would contribute to core functionality. These wireframes were created in effort to plan for the overall layout and user flow of the site across different electronic devices keeping mobile-first viewing and design in mind.

Figma, an industry standard software, was used to aid the creation of these wireframes which you can view in higher resolution [here](https://www.figma.com/file/wMKxyusVxR7e4V9zPe1JHL/Hope-Hunters-Wireframes?type=design&node-id=162-2072&mode=design&t=RsEU8JRCJn1tqZyX-0). 

- Homepage:
    >
    ![homepage wireframes](./docs/homepage-all.png)

- Login page:
    >
    ![login page wireframes](./docs/login-page.png)

- Hamburger Menu for Mobile Nav Only:
    >
    ![hamburger menu wireframe](./docs/hamburger-mobile.png)

- Dashboard (mobile, desktop, both):
    >
    ![dashboard wireframes](./docs/dashboard-mobile.png)
    >
    ![dashboard wireframes](./docs/dashboard-desktop.png)
    >
    ![dashboard wireframes](./docs/dashboard-all.png)

Prototypes are also useful in the planning stages of a website as they allow the developer to visualize the flow of actions a user may take when interacting with rendered elements. To view the interactive version of these prototypes, click here for the [desktop version](https://www.figma.com/proto/wMKxyusVxR7e4V9zPe1JHL/Hope-Hunters-Wireframes?type=design&node-id=30-1357&t=RsEU8JRCJn1tqZyX-0&scaling=scale-down&page-id=19%3A818&starting-point-node-id=30%3A1357&show-proto-sidebar=1) and here for the [mobile version](https://www.figma.com/proto/wMKxyusVxR7e4V9zPe1JHL/Hope-Hunters-Wireframes?type=design&node-id=45-1568&t=RsEU8JRCJn1tqZyX-0&scaling=scale-down&page-id=45%3A1567&starting-point-node-id=45%3A1568).

Visual representation of prototypes for both desktop and mobile below -

- Mobile prototype representation:
    >
    ![mobile prototype](./docs/mobile-prototype.png)
>
- Desktop prototype representation:
    >
    ![desktop prototype](./docs/desktop-prototype.png)
>
Mobile Device Prototypes:
>
- Homepage
    >
    ![mobile home prototype](./docs/mobile-home-proto.png)
>
- Hamburger menu
    >
    ![mobile hamburger menu prototype](./docs/mobile-ham-proto.png)
>
- Login page
    >
    ![mobile login prototype](./docs/mobile-login-proto.png)
>
- Signup page
    >
    ![mobile signup prototype](./docs/mobile-signup-proto.png)
>
- Dashboard 
    >
    ![mobile dashboard prototype](./docs/mobile-dash-proto.png)
>
Desktop Device Prototypes:
>
- Homepage
    >
    ![desktop home prototype](./docs/desktop-home-proto.png)

- Report a Missing Person (login) page
    >
    ![desktop login prototype](./docs/desktop-login-proto.png)

- Dashboard 
    >
    ![desktop dashboard prototype](./docs/desktop-dash-proto.png)

#### Other Design Processes
- Font(s):
    >
    Based on the determined users - police, general public of all ages, admin - choosing an appropriate fontface and overall style for enhanced readability was a priority. The information we are hosting on this site is important and urgent in nature, so delivering it in a direct and clear manner is paramount.
    >
    "[Official] websites need clear and consistent headings, highly legible body paragraphs, clear labels, and easy-to-use input fields."[^5] 
    >
    Public Sans: 
    The chosen body font. 
    Headers will be emphasized using appropriate font weight.
    >
    ![publicsans](./docs/public-sans.png)[^7]
    >
    Public Sans is a font used widely by the U.S. Government across their official sites and was actually designed by the United States Web Design System - it is well known for its "plain, straightforward style, [and is] appropriate for interfaces and running text. Its large x-height makes it legible at small sizes."[^5] 
    >
    The smaller font sizes have greater letter spacing which makes it highly suitable for running and body text as the letters are further apart, thus making it easier to read at small sizes.[^5] 
    >
    This typeface "is meant to be neutral, legible, and consistent like a system font"[^6] and the "conventional angled vertices result in a sharper, stronger form."[^7]
    >
    ![font overlay](./docs/font-comparison.png)[^7]
    >
    With Roboto being too tall and stiff and SF Pro Text having too much character spacing as shown in the above overlay, Public Sans is the perfect combination of curvature, height, and character space, which achieves excellent readability and maintains a neutral form.
>
- Color Scheme:
    >
    When choosing colors for a website or application, it's important to determine your target audience and overall message you want to convey. Since this site is related to important and often urgent information, the goal was to evoke a sense of professionalism, officiality, and trustworthiness, a sense of hope for those searching, as well as a sense of urgency and priority for certain info.
    >
    Based on extensive research about color theory, the chosen colors for the site are below:
    >
    ![color swatches](./docs/color-swatches.png)[^2]
    >
    with an example site incorporating these colors:

    ![mocksite with colors](./docs/site-colors.png)[^2]
    >
    We chose a triadic design with an added complementary color. "Triadic [designs] take three colors which are equally distant on the color wheel (i.e., 120° apart: e.g., red/blue/yellow). These colors may not be vibrant, but the scheme can be as it maintains harmony and high contrast. It’s easier to make visually appealing designs with this than with a complementary scheme."[^3] 
    >
    ![triadic colors](./docs/triadic-colors.png)[^2]
    >
    With the content of our site relating to sensitive information, it was important to appropriately reflect our design goals whilst also evoking a "positive psychological impact on users"[^3].
    >
    We chose shades of blue as our primary color, as the main design goal of the site was to bring about a sense of professionalism, officiality, and trustworthiness. 
    >
    "Blue is a favorite color for companies that wish to convey reliability, trustworthiness, and communication (think Facebook, Twitter, and Samsung) and for expressing the authority of organizations like the police."[^4] Considering that the police are part of the intended users, it made sense to choose this as the primary color. Keeping the site visually neat and easy to read for users of all ages was also important.
    >
    Our secondary and complementary colors consist of shades of orange and yellow. 
    >
    Orange and yellow are both considered warm colors and therefore "evoke warmth due to their brightness and link to the sun. In general, they convey optimism, enthusiasm, and passion."[^4] This was extremely important to counteract the blue tones, which can be also be linked with sadness and depression. 
    >
    Orange is also a color representative of encouragement and hope. We chose the orange tones carefully as too bright an orange would incorrectly convey youthfulness and energy and should therefore be avoided for serious branding.[^4]
    >
    We included the yellow to act as a highlight color for important information on the site as "yellow is a cautionary color used in life vests, police cordoning tape, and hazardous areas."[^4] 
    >
    As it "is the most visible color from a distance (which is why it’s used for street signs)"[^4], it was logical to incorporate this color into our design scheme for the original intended purpose: to direct user attention.
    >
    Overall, these colors allow the users to focus on the information provided and use the user interface as a tool, rather than drowning the site in vibrant or extraneous colors further distracting the user from the intended information. 

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
![Trello board progress 05/07/2023](./docs/trello/trello-screenshot3.png)
![Trello board progress 06/07/2023](./docs/trello/trello-screenshot4.png)
<br>
<i>Trello Board Card Examples</i>

![Trello board card example format readme.md](./docs/trello/trello-card-example1.png)
![Trello board card example AAD](./docs/trello/trello-card-example2.png)
![Trello board card example User Stories](./docs/trello/trello-card-example3.png)

#### Sources Used: 
[^1]: Henderson, M., Henderson, P. and Kiernan, C. (2000). Missing Persons: Incidence, Issues and Impacts. [online] Available at: https://www.aic.gov.au/sites/default/files/2020-05/tandi144.pdf.


[^2]: paletton.com. (n.d.). Paletton - The Color Scheme Designer. [online] Available at: https://paletton.com/#uid=43w0n0kJTrhn3OgmWBjUJdkVy5B [Accessed 3 Jul. 2023].



[^3]: Interaction Design Foundation (n.d.). What is Color Theory? [online] The Interaction Design Foundation. Available at: https://www.interaction-design.org/literature/topics/color-theory#:~:text=Color%20theory%20is%20the%20collection.



[^4]: Gross, R. (2019). Color meaning and symbolism: How to use the power of color in your branding. [online] Learn. Available at: https://www.canva.com/learn/color-meanings-symbolism/.


[^5]: U.S. Web Design System (USWDS). (2023). Typography. [online] Available at: https://designsystem.digital.gov/components/typography/#included-typefaces-2 [Accessed 4 Jul. 2023].


[^6]: Eye on Design. (2019). The U.S. Government’s Public Sans Is a Typeface Fit for Civic Duty. [online] Available at: https://eyeondesign.aiga.org/the-u-s-governments-public-sans-is-a-typeface-fit-for-civic-duty/ [Accessed 4 Jul. 2023].


[^7]: GitHub. (2023). Public Sans. [online] Available at: https://github.com/uswds/public-sans [Accessed 4 Jul. 2023].

