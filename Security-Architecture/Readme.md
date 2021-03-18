# Security - Architecture studies

# Experience in Qlik Sense security concepts (section access and security rules) 
**To provide secure information management, these key risks need to be mitigated:**  
* Unrealiable reporting;
* Multiple Versions of truth;  
* User requirements not met;  
* Performance Issues;  
* Information disclosed to unauthorized person;  

**IT gorvernanve framework allow:**  
* Known the risks unrealiable  reports allow;  
* Define control to prevent or limit the impact of those risks;  
* Define clear roles and responsabilities;   
* People perform only activities they are allowed and trained;


<p align="center">
  <img width="750
  " height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Security-Architecture/Images/Security%20by%20organization%20size.JPG">
</p>

**Autehcntication x Authorization**
* AUTHENTICATION = The act os checking if the indentity is true or not. In qlik, it happens trought athenticating a USER ID trhought the proxy system (when you do your windows log in) to validade if is an authentic user or not.
* AUTHORIZATION = allow user to see only what he is meant to see. In qlink it happens trought the authorization of user to perform tasks in streams, like access, edit, delete...

**Business Rules**
Usually divided in IT Users and Business Users
* IT USERS = access to QMC, ETL, create apps, maintin server and DB, tasks ans security
* BUSINESS USERS = Display apps on the streams they have access to

**Authorization Steps**
1 - Resource Authorization to hub, qmc, streams and apps  (security rules)
<p align="center">
  <img width="750
  " height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Security-Architecture/Images/Step%201%20-%20Secutity%20rules.JPG">
</p>
For IT users, you can create a group ADMIN, which has access QMC and have many permissions. For Business users, you create a business group, with access to see hub only.

2 - Data Filter (Section Access)
<p align="center">
  <img width="750
  " height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Security-Architecture/Images/step%202%20-%20Data%20filter.JPG">
</p>
With section access, you can limit the data some user can see by a field. Ex: make a user see only the vendor ID XX, or Country XXX, to limit its access.

### YOU CAN LIMIT ACCESS TROUGHT USERS AND GROUPS

**Summary**
<p align="center">
  <img width="750
  " height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Security-Architecture/Images/Securitry%20Summary.JPG">
</p>





<p align="center">
  <img width="750
  " height="400" src="">
</p>
