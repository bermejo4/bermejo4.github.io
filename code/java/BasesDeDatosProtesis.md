---
layout: post
title: Prothesis Network Database
---
*****
First of all, this project have been made in colaboration with other students that are denoted as "contributors" in the github repository.

It's imposible to show every code line of this project in this post. But if you want to access to the full project in github yo can do it with the github link in the bottom of the page. 

The project pretend to become a huge interconect stock network of any prothesis, where the main target is to find the better prosthetic that fits with the interests of the patient, but helped by his doctor medical criteria.

There are 4 user roles in this database (Doctors, Patients, Biomedical Engineers and Hospitals), all user role have the main 2 actions to use the database (Register or Login), but each user role have certain functions or actions to interact with the database that others haven't got:
 - Doctors: 
    - Select a Prosthetic.
    - Select date of fitting.
    - Search a patients documentation.
    - Add/Modify/Delete a patient.
    - Generate a Prosthetic XML.
    - Put additional information about theirselves.

 - Patients:
    - Select a Doctor.
    - View appointments.
    - Change theis credentials.

 - Biomedical Engineers:
    - Upload a new Prosthetic.
    - Modify a Prosthetic information.
    - View Uploaded Prosthetics.
    - Delete a Prosthetic.
    - Upload a new Prosthetic through XML.

 - Hospitals:
    - Buy a Prosthetic.
    - Generate Hospital XML.

The main character in this project are the prothesis, each of them have important data to differentiate to each other. These data are: 
- Type (leg, arm, ear...)
- Material.
- Dimensions.
- Failures(data for the biomedical engineers)
- Price.

Some of this data is to generic, and it's known, but it can be changed to fit it with the main purpose of the database developer or for specific prosthetic data in the real world. 

This program hasn't got a Java graphical user interface, ut there is an option in the main menu to show all the content of the database through a website style interface with html and css.

This project have been made by different languajes combinated:
- Java:
    - to develop input and output flow of data with the console.
    - to manage the Database (JDBC and JPA).
    - to manage errors.
- XML:
    - to have other form to structure the database.
    - it's going to help to show the database in html.
- XSLT:
    - to transform xml into html.
- HTML:
    - to show the content of the database.
- CSS:
    - to add style and color to the website interface.

### Interface:

* Main menu:
<div class="img-contenedor">
<img src="/images/codeImages/Java/DataBaseProsthetic/MainMenu.png" alt="MenuImage" title="MenuImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>

* Prosthetic data relationated with patients view:
<div class="img-contenedor">
<img src="/images/codeImages/Java/DataBaseProsthetic/prost.png" alt="ProsImage" title="prosImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    margin-bottom: 20px;
">
</div>

* Hospitals relationated with their doctors view:
<div class="img-contenedor">
<img src="/images/codeImages/Java/DataBaseProsthetic/Hosp.png" alt="HospImage" title="HospImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
">
</div>

* Biomedical Engineers relationated with their prosthetics view:
<div class="img-contenedor">
<img src="/images/codeImages/Java/DataBaseProsthetic/BE.png" alt="BeImage" title="beImage" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
">
</div>

*****

  <a href="https://github.com/bermejo4/Prosthetic-DB" target="_blank"> Link for code in GitHub</a>

*****


