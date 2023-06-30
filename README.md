Sarah Landis & Connie Jacques

# Hope Hunters: A Missing Persons Aggregate Site
### <i>A MERN Application</i>

---
# Documentation

## 1. About
### Purpose
Each year, approximately 30,000 people are reported missing in Australia - that's one person every 18 minutes[^1]. Unfortunately, not all of these cases are exposed to the public in timely manner, if at all. The more people who are aware of a recently missing person, the greater the likelihood is of finding them. 

The purpose of this website is to provide a platform for both members of the general public and law enforcement to post and share information about missing persons in NSW. Allowing members of the public to engage with reports and share details via social media about missing persons will increase the chances of locating the missing individuals by engaging a wider network of individuals and therefore decreasing the amount of time it takes to distribute key information.

Using this site will hopefully assist in reuniting families, bringing closure to loved ones, and raising awareness about cases in NSW. Every effort in the search counts and matters, and as a community using this site, we can do our part to help.

### Functionality
Users will be able to login using their email and password and access their Hope Hunters account. From their account, a user has the ability to then create a new missing persons "file", update/delete any files they've created, or update/delete their account.

Law enforcement and admin will also be able to login with their credentials and 
achieve the same functionality. However, admin and law enforcement accounts have the ability to update or delete any missing persons "file" regardless of who created it. Additionally, admin accounts are able to retrieve information of all accounts, including police accounts.

Any member of the public will be able to use the site. Public members who do not have a Hope Hunter account will be able to view-only all missing persons files. Hope Hunters will have a search/filtration system which will allow users to filter the results by:
- Location a-z
- Name a-z
- Age ascending/descending
- Date Posted (chronological as default, newest first)

or search results by model fields:
- Location
- Name
- Police District
- Amber Alert
- Age
- Gender 
- Area suspected to be
- Last seen (postcode)
<!-- - ?Race  -->

### Features

<i>Features required to achieve the above functionality include:</i>

##### Front End
- Sign up form: 
The sign up form will have functionality to allow the user to identify as a law enforcement official. If the user selects this option, the form will change to accomodate sign up for police as different details are required. ** On sign up, user will receive an email containing a link to confirm their email and complete their sign up. Once signed up redirect to sign in.
>
- Sign in form: 
This form will recieve email and password.
>
- Update/delete account form: 
This form will perform the relevant crud tasks as required. The form will include a button to delete the account and all subsequent open missing persons files associated. If updating, any fields left blank will remain as whatever is stored in the database (i.e. only filled fields will change).
>
- Add missing person form: 
This form will be the same regardless of account type. The form will have fields based off the ERD.
>
- Update/delete missing person form: 
The purpose of this form is to perform the required crud tasks. The form will take input and first search for missing person, then update. There will be a button to delete the file entirely.

##### Back End
- User sign up with email verification:
Required validation to ensure email is an email prior to entering the database.
>
- Encrypted password (bcrypt + salted) stored in database:
Required protection of user passwords to safegaurd against malicious theft of data
>
- JWT authentication:
Required authentication to ensure relevant account has access to specific data
>

<br>
<i>Desired features to enhance overall functionality of the site and increase quality of UX:</i>

##### Front End
- Directly share listings to social media outlets via a 'Share' button with channel options
- Missing persons listings displayed in Facebook newsfeed style (continuous page with hidden scrollbar)
- Amber alert responsive infinite scrolling banner
- Support page with crime stoppers info, grief support, mental health resources, etc.

##### Back End
- Retrieve 30 listings at a time from the database for the continuous page. Only once they’ve been viewed, get the new 30, etc.
- Store persons images directly to database

### Target Audience
The target audience for this site as briefly explained above, is the general public. With police busy with major crimes across different sectors and far too many annual missing person cases being filed, this site aims to enlist the assistance and knowledge from the general public.

In today's interconnected digital world, there lies strength in numbers. The power and gravity of collective action is important to understand in this context. With social media acting as a catalyst, the swift dissemination of information is made much easier and is hopefully able to play a crucial role in assisting someone's safe return home. Additionally, having direct access to sharing a 'file' onto social media may be a lifesaver, as you may not know the person but an old friend of yours is now friends with that person's parent - you never know how many connections away you are from either the missing person directly or atleast someone who may have information. 

Our goal is to minimize the delay in information reaching the public as well as help law enforcement pool together every possible avenue of potential connection to better help locate a missing person.

### Tech Stack

## 2. Dataflow Diagram

## 3. Application Architecture Diagram
---
# Design & Project Flow

## 4. User Stories

## 5. Design Processes & Wireframing

## 6. Project Management


### Sources Used: 
[^1]: Henderson, M., Henderson, P. and Kiernan, C. (2000). Missing Persons: Incidence, Issues and Impacts. [online] Available at: https://www.aic.gov.au/sites/default/files/2020-05/tandi144.pdf.

