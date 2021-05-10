![GMGC logo](https://static1.squarespace.com/static/5c475b37e2ccd1edd9bb2b7e/t/5c52fbf24d7a9c391e48c199/1619481878604/?format=500w)

# Green Mountain Gospel Chapel Privacy & Security Document Pertaining To Technology

## [Software Accounts](#Software-Accounts)
For the purposes of the operation of the church for its congregation, any and all software accounts should be created using `service accounts`. These types of accounts are just accounts made that are tied to an email address that formatted in a special way. For example, a service account might look like `gmgc-support@gmail.com` or `gmgc-treasury@yahoo.com`. Notice that both email addresses to not contain names but identify roles within the organization followed by the provider after the `@` symbol. A bad service account would look like this: `bob@gmail.com` or `alice@gmail.com`. Those previous examples are personal accounts that should not be used on behalf of the church.
### [Why Use A Service Account](#Why)
A service account prevents issues from occuring in several different situations. For example, if the pastor has their personal email linked to all of the software accountsfor the church, it becomes a problem to transfer those accounts once a pastor decides to leave or is removed from the church. Service accounts can be managed by multiple people and can have access transfered much easier and faster in case of emergencies. Another example is when you use service accounts, its easier to identify by role who is accessing what service. One last situation is that service accounts only need the minimum priviledge necessary in order to operate their resource. This ensures that the account cannot go above and beyond their station in order to manage what they need to manage.

### [Service Account Recommendations](#Recommendations)
* Use only service accounts that describe a role. (This allows for easy identification of access.)
* While it is tempting to bundle all treasury accounts with financial software, service accounts should have a semblance of separation of duties. 
* Rotate account passwords every 90 days. (Ideally this should be sooner, but 90 days is a standard in non classified environments.)
* Service account authentication details should be stored on paper and kept in a safe. (If its digital, it can be hacked. Encryption is not necessary for service accounts in a secular environment unless it deals with `PII` (Personally Identifiable Information), `PHI`(Protected Health Information) or any type of information that can be used to identify a particular person.)
* Service account passwords should be longer than 12 characters. (With automation, password cracking becomes easier and easier. The longer you make a password, the hard it makes it for computers to come up with combinations to crack the password.)
* If possible, service accounts should have an `emergency access plan`. (If the person with access to the account leaves, another person can be slotted in faster than waiting on the person leaving to provide the credentials to get into the system.)

# Emergency Account Transfer
## [What To Do](#What-To-Do)
Below you will find a general plan on what to do for emergency account transfers in different situations. Feel free to update as needed.

## [Account Person has left and credentials cannot be located](#Not-Located)
1. Notify the Pastor, the Elders and the Deacons of your intent.
2. Contact the vendor of the sofare in question and put in a support ticket with their system. (Make sure you explain the situation in the ticket. The more detail you can provide the better. Be ready to provide any authorization details that may be asked of you.)
3. If no solution has been given in a sufficient amount of time, contact by phone the vendor of the software and ask for an escalation of the ticket. 
4. List the representative either from the Pastor, the Elders or Deacons as the escalation point of contact.
5. Once solution has been reached, collect transcripts from the tickets and phone calls if possible and create a copy for the Deacons and a copy for the Elders to retain. 

## [Account person has left and credentials are found](#Found)
 1. Log into service account and rotate password. 
 2. Update agreed upon password storage location.
 3. Use Service Account to access software and update that account password.
 4. Update password in password storage location.
 5. Inform Pastor, Elders and Deacons of the update and proceed as normal.

 ## [Password cannot be located for software anywhere](#Lost-Password)
 1. Try filling out a password reset request in the software using the service account. 
 2. Try contacting software vendor for assistance in resetting password. Be prepared to authenticate yourself and have either the Pastor, Elder or Deacon with you.
 3. Try using autofilled password to log into account. 

 ## Once a password has been changed, located or removed, update the agreed upon password storage location with the new password so we don't run into the same situation.


***
## [Inventory](#Inventory)
Inventory should be documented and updated when needed.

### **Hardware**
All hardware should be inventoried with the folloing pieces of identifiable information:
* Hardware Name - So we know what it is.
* Brand Name - So we know what to replace it with.
* Serial Number - So we can see if the part is still made or not.
* Date of purchase - For auditing.
* Reason for purchase - For transparency.
* Model Number - So we can replace the part exactly.

### **Software**
All software should be inventoried with the following pieces of identifiable information:
* Software Name - What it is.
* Reason Obtained - What it is used for.
* Price - What we paid for it.
* Version - To know what to version of software to go back to in case of catastrophic failure.
* License (if any) - For liability and terms of use.
* Vendor Obtained From - So we know where we got it from.
* Account Name (if any) - Service or personal account tied to this product.

***
# Data
When it comes to data at rest, hash and salt it on a per user basis. It does not need to be fancy encrypted, SHA256, SHA512, Argon2 hashes  should be fine. If supported, data that is hashed and salted at rest is better because it limit the damage done in case of a breach.  The best possible thing to do is hash data in transit and salt on a per user basis. Data in transit should be hashed if possible. 
## [Hashing](#Hashing)
Hashing is a one way data masking function that will prevent data from being read in clear understandable terms. What is meant by one way is that hashing cannot be reversed. To verify the data, you have to pass in the same data, and if the hash is different, the data is either considered incorrect or tampered with. The difference between hashing and encryption is that hashing cannot be reversed while encryption is made to be reversed.
## [Salting](#Salting)
Salting means to add a random string (or piece of data) to the end of a piece of data before it is hashed. What this does is add an extra layer of security so that if a hash is cracked, the attacker would still need to know the salt (or random data) to get the correct data to understand what it is.
***
# Remote Access Policy
Remote access should only be used in dire circumstances (Or as determined by Pastor or Elders or Deacons). If remote access is needed ( a justification should be recorded for auditing and transparency), the person that is remoting into the network should have a static IP address setup and the church's network firewall should be configured to allow traffic to and from the machines. Traffic should be restricted to necessary ports and services and should default to secured ports if at all possible. 

## Types of remote access
### SSH
This means Secure Shell, a command line or terminal is used to gain access to the network and do file operations. There is no window seen or mouse on the screen. It is a black screen with text only. If used, access time + reason for access should be logged and a copy sent to the Pastor, Elders and Deacons for posterity. For security, there should only be one set of key files that exist inside of a folder called `.ssh`. These files are used to authenticate the user trying to get remote access to the machine.
### Remote Desktop Viewer
This is a window that appears that shows the desktop of the target machine. If this  software is used, a service account should be used and access time + reason should be logged and submitted to Pastor, Elders and Deacons for posterity. 