           **Subject:** Plant_Display System Details

        **Audience:** End Users – Local-Global

          **Updated:**  6/2/2020 11:35:00 AM

 #Documents

[1.0.0 Document Administration. 2](#_Toc509835410)

[1.1.0 Version Control. 2](#_Toc509835411)

[1.2.0 Standard Disclaimer. 2](#_Toc509835412)

[1.3.0 Additional Document Information. 2](#_Toc509835413)

[2.0.0 Overview.. 3](#_Toc509835414)

[3.0.0 Sleep Setting. 3](#_Toc509835415)

[4.0.0 Global_Plant_Floor_Policy_Override. 3](#_Toc509835416)

[4.1.0 Settings. 3](#_Toc509835417)

[4.2.0 Criteria. 3](#_Toc509835418)

[4.3.0 How To Implement. 3](#_Toc509835419)

[5.0.0 Global_OEE_Policy_Override (Display System) 3](#_Toc509835420)

[5.1.0 Settings. 3](#_Toc509835421)

[5.2.0 Criteria. 4](#_Toc509835422)

[5.3.0 How To Implement. 4](#_Toc509835423)

  

# [1.0.0](#TOC) Document Administration

## [1.1.0](#TOC) Version Control

It is necessary that the utmost care be taken to ensure that all users of this document are using only the latest version.

Each time the document is modified, the chart below will be updated with the pertinent information, thus allowing the users of this document to adopt changes immediately.

|   |   |   |   |   |
|---|---|---|---|---|
|**Version**|**Modified by**|**Date**|**Section**|**Modification**|
|1.0|Jesse Norrad|March 26, 2018|All|Starting fresh document for Plant/Display System Details|
|1.1|Jesse Norrad|October 18, 2018|5.3.0|Modified to specify steps for if a new user account is needed or already exists.|
|1.2|Jesse Norrad|March 14, 2019|4,5|Changed titles to exclude group names|
|1.3|Jesse Norrad|April 16, 2019|5|Added notes about password generation and settings.|
|1.4|Jesse Norrad|July 2, 2019|6|New section. Added matrix overview.|
|1.05|Jesse Norrad|July 4, 2019|6|Updated image to include ‘OU’ on the OUs.  Changed versioning to allow for double digit minor versions.|

## [1.2.0](#TOC) Standard Disclaimer

This document is only intended for internal use by McCain Foods Limited Computing Services employees.  McCain Foods Limited is in no way responsible if using this documentation results in any damage to any software or hardware components. Any Trademarks or Trademarked images used in this document are owned by their respective companies.

## [1.3.0](#TOC) Additional Document Information

|   |   |
|---|---|
|Template for this document|Computing Services Document Template (0.1.4).dot|
|Author|Jesse Norrad|
|Last saved by|Jesse Norrad|
|Owner|GTS Workplace Management|
|Approver||
|Date approved||

  

# 2.0.0 Overview

The purpose of this document is to explain the criteria for what use cases qualify a user account to have the plant floor or display system group policies applied to them and how to implement those.

# 3.0.0 Sleep Setting

Sleep settings are not forced by group policy and can be changed in the Control Panel at any time.  In my experience, users often will use the term “sleep” to refer to the screen saver which is not the same thing, so please ensure when you are discussing with users to take the time to make sure that you know exactly what they are asking for.

# 4.0.0 Plant Floor System

## 4.1.0 Settings

This set of policies applies the following forced settings:

·         Screen saver timeout is set to 7200 seconds (2 hours)

·         Screen saver password protection is disabled.

There are additional settings that are provided in to the form of a power plan named “McCain Plant System Power Plan”.  When the policies have been applied for the first time you must access the Power Settings in the Control Panel and select this power plan.  These settings initially set the system to not go to sleep along with other related options.  These options are not forced and can be changed in the Power Settings.

## 4.2.0 Criteria

·         The user account must be a generic or shared user account that is used on shared plant floor computers.

## 4.3.0 How To Implement

·         Via an Account Request, the user account must be moved into the appropriate “Shared Plant Users” OU for the region/country.

·         Via an Account Request, the user account must be added to the “Global_Plant_Floor_Policy_Override” AD group.  Account Maintenance will seek Director level approval before doing this.  Regular user accounts should never be placed in this group.

·         When logged in for the first time as the user account from above, go into the Control Panel and then Power settings and make the “McCain Plant System Power Plan” the active power plan.

# 5.0.0 Display System

## 5.1.0 Settings

This set of policies applies the following forced settings:

·         Disables screen saver password protection

·         Disables the screen saver timeout so that it does not automatically go to the screen saver

·         Disables the logon message for Windows 10 computers.

## 5.2.0 Criteria

·         The user account must be a specific “role based” account which exists for the sole purpose of logging onto dedicated display systems which display statistics or other information to large screens.

·         Ideally the PC is in a secure location that is not easily accessible and/or is where someone can see it at all times (so that a visitor to a location cannot easily gain physical access to the PC).

## 5.3.0 How To Implement

·         A user account dedicated for use on display systems is required. 

o    New user account: Submit an account request to have a new user account created, asking for it to be placed in the “Role Based Users” OU for the region.  Ask for it to be made a member of the “Global_OEE_Policy_Override” group as well.  IBM will seek approval from the owner of the group before making that change.  Ask IBM to randomly generate a password for the account while also asking that it be set so that the user cannot change the password and so that the password never expires.  Lastly, ask for the “Logon To” settings to be modified to only include the display computer(s) it will be used on.

o    User account already exists: Verify that it is in the “Role Based Users” OU for the region and is in the “Global_OEE_Policy_Override” group.  Submit an account request for the user account to fix either of those if they are not correct.  For the group modification, IBM will seek approval from the owner of the group before making that change.  The account should hopefully already have a generated password and be set so that the user cannot change it and so that it doesn’t expire.  If not, ask for that to be done, keeping in mind that you may need to update the auto logon settings for any PC that is already using it.  Also ask to have the “Logon To” settings modified to include the display computer(s) that you are configuring.

·         In the account request, ask to have the computer(s) that the account will be used for added to the “Global_Logon_Message_Policy_Override” AD group.  A regular computer account should never be placed in this group.  IBM will seek approval from the owner of the group before making that change.

·         Using your admin account, move the computer(s) into the proper “Role Based Computers” OU for the region/country.

·         Download [SysInternals Autologon](https://docs.microsoft.com/en-us/sysinternals/downloads/autologon) and use it to set up a secure auto logon on the computer(s). 

·         On the first logon with the display account, access the Power Settings via the Control Panel and modify the settings so that the computer never goes to sleep and never turns off the display.  If any of power customizations are required configure those now.

# 6.0 Matrix

![](file:///C:/Users/sanderso/AppData/Local/Temp/1/msohtmlclip1/01/clip_image002.jpg)

Link to XLSX document: [http://csteam.mccain.com/sites/GTSDocs/Repository/Plant_Display_System_Matrix.xlsx](http://csteam.mccain.com/sites/GTSDocs/Repository/Plant_Display_System_Matrix.xlsx)