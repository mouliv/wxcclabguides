---
title: 'Lab 7: Advanced Email Configuration'
---

# Table of Contents
- [Step 1. Email Workflow Overview](#step-1-gmail-account-configuration)
- [Step 2. Position In Queue Configuration](#step-1-gmail-account-configuration)
- [Step 3. Autoreply Configuration](#step-1-gmail-account-configuration)
- [Step 4. Improving Routing based on the Subject](#step-2-create-email-asset-and-register-to-webexcc)
- [Step 5. Screenpop configuration](#step-3-email-entry-point-and-queue-creation)
- [Step 6. Integration with Smartsheet using smartsheet APIs](#step-4-createupload-email-flow)


# Introduction

### Lab Objective

This lab will give you a detailed understanding of the predefined workflow logic. With that, you will be able to improve the script and do a more advanced configuration.
This lab includes multiple script customizations and shows how to create an HTTP Request which is needed for integration with external HTTP services (as an example it uses smartsheet API).


### Pre-requisite

- You have successfully compleated the Lab1 and Lab2 (Email Configuration).

# Lab Section

## Step 1. Email Workflow Overview

Before proceeding with the configuration task, you need to understand the flow logic. Please follow the diagram below and call the proctor if you have any questions.

<img align="middle" src="images/Lab7_workflow.png" width="1000" />



## Step 2. Position In Queue Configuration
In this task we will use the predefined node **PIQ and EWT**. This node provides the caller's current Position in Queue (PIQ) and the Estimated Wait Time (EWT). The flow developer can use these variables with flow logic to determine agent availability in a queue and route elsewhere when needed.
The node has three types of output flow branches. These branches get triggered based on return status and values of EWT and PIQ.
  - Success: Triggered when both EWT and PIQ APIs succeed and return nonnegative values.
  - Insufficient Information Flow: Triggered when the PIQ API returns a valid variable value, and EWT has the value as -1. 
  - Failure: This branch is triggered when PIQ API or EWT API fail and/or return invalid values. 

> **Note:** PIQ/EWT node can currently be used only after the Queue Task Node.


- Go to the **Services - My First Service** and open the **Email Inbound Flow**.

- Click on **EDIT** button in the upper right corner.

-  Drug and drop the **PIQ and EWT** node from the Node Palette to the main canvas.

<img align="middle" src="images/Lab7_workflow2.png" width="1000" />

- Delete the existin Queued link by clickin on it and pressing delete button. Re-connect **Queue Task** with **PIQ and EWT**

<img align="middle" src="images/Lab7_workflow2.png" width="1000" />

- Double click on the **PIQ and EWT** node and set:
 - **METHOD NAME** as **Fetch Position in Queue**
 - **NODE RUNTIME AUTHORIZATION** as **WxCC Authorization**
 - **QUEUE ID** as

<img align="middle" src="images/Lab7_workflow4.png" width="1000" />

-  and connecte all exit states of **PIQ and EWT** with **Update Conversation**.

> **Note:** There are 3 exit states for 

<img align="middle" src="images/Lab7_workflow3.png" width="1000" />


### 1. Google Account Setting – Enable POP3/IMAP setting


| **User email**                       |
| ------------------------------------ | 
| cl1webex**\<ID\>**@gmail.com   | 

> **Note:** Your \<ID\> was provided to you personally.  \<ID\> is the unique number equal to your POD.


- Login to the Gmail account with the credentials above[https://mail.google.com](https://mail.google.com){:target="_blank"}. The password is the same as for Webex admin account.

- Enable POP3/IMAP setting by clicking on settings icon on top right corner and selecting **See all settings**.

<img align="middle" src="images/Lab2_Gmail1.png" width="1000" />

- Now Click on **Forwarding and POP/IMAP**, enable the `POP Download` and `IMAP access` then click **Save Changes**.

<img align="middle" src="images/Lab2_Gmail2.png" width="1000" />




[Back to top](#table-of-contents)
---

### Congratulations, you have completed this section! 

<script>
function mainPage() {window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Home.html";}
function nextLab() 
 {
 window.location.href = "https://wxcctechsummit.github.io/wxcclabguides/LTRCCT-2013/Lab8_AgentProductivity.html";
 }
</script>

<div id="button-row">
<button onclick="mainPage()" style="
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Main Page</button>

<button onclick="nextLab()" style="
  position: absolute;
  right: 200px;
  border-radius: 5px;
  background-color: rgb(116,191,75);
  padding: 10px;">Next Lab</button>

</div>