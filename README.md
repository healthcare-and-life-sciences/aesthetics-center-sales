![](/images/ahlsbanner.png)

# Aesthetics Center ReadMe

## **Overview**

The Aesthetics Center Sales Solution Accelerator delivers pre-configured flows, custom objects, record pages, and other configurations designed to streamline Aesthetics Center lead and sales management. All of these configurations are available for download into your Salesforce org free of charge.

## **Business Objective**

The objective of this accelerator is to provide a preconfigured starting point for Aesthetics Center sales team. 

## **Business Value and Benefits**

Driving **higher top-line revenue**, focuses sales on **better margin** procedures and **streamlines the pre-op process** to assure patients complete their journey.

* **Driving Higher Top-Line Revenue**
    * Eliminating the loss of leads
    * Tracking all interactions
* **Better Margin Procedures**
    * Streamline technologies
    * Create a technological foundation
    * Develop workflows for key milestones
* **Streamline the Medical Clearance Process**
    * Automate the pre-op clearance process
    * Provide support for clinical review
    * Provide an optimized process

## Industry Focus and Workflow

### Primary Industry:

* Healthcare and Life Sciences

### Intended End User:

* Aesthetics Center Sales Team and Sales Managers

## Package Includes:

Lightning App (1)

* Aesthetics_Sales
* Aesthetics_Sales_UtilityBar

Custom Objects (3)

* Medical Questionnaire
* Lead Status History
* Opportunity Status History

Tab (1)

* Medical Questionnaire

Flows (8)

* Aesthetics_Create_or_Update_Medical_Questionnaire
* Aesthetics_Create_Service_Appointment
* Aesthetics_Create_Update_Lead_Status_History_record_when_Lead_is_edited
* Aesthetics_Create_Update_Opportunity_Status_History_record_when_Oppty_is_edited
* Aesthetics_Gather_Lead_Information_Web2Lead
* Aesthetics_Relate_Medical_Questionnaire_and_Files_to_Oppty_Acct
* Aesthetics_Reschedule_Service_Appointment
* Aesthetics_Update_Opportunity_Stage_if_products_are_added

Record Types (4)

* Aesthetics Center - Account               
* Aesthetics Center - Lead         
* Aesthetics Center - Opportunity         
* Aesthetics Center - Person Account  
* Aesthetics Center - Task  

Page Layouts (9)

* Aesthetics Center - Account               
* Aesthetics Center - Lead                     
* Aesthetics Center - Opportunity         
* Aesthetics Center - Person Account               
* Aesthetics Center - Service Appt       
* Aesthetics Center - Task  
* Lead Status History Layout     
* Medical Questionnaire Layout                       
* Opportunity Status History Layout     

Compact Layouts (5)

* AestCtr_Account         
* AestCtr_Lead  
* AestCtr_Oppty            
* AestCtr_Person_Account        
* AestCtr_Service_Appt 

Path Assistants (2)

* AestCtr_Lead_Path
* AestCtr_Opportunity_Path

List Views (4)
* All - Medical Questionnaire    
* My New Leads 
* My Open Leads           
* My Open Opportunities          

Lightning Pages (5)

* Account_Record_Page_AestCtr
* Aesthetics_Center_Home_Page
* Aesthetics_Center_Oppty_Page
* Lead_Record_Page_AestCtr

Business Processes (2)

* AestCtr - Oppty Sales Process
* AestCtr - Lead Process

Actions (4)

* Medical_Questionnaire_AesCtr_Lead            
* Medical_Questionniare_AestCtr_Oppty        
* New_Appointment_AestCtr - Opportunity
* Reschedule_Service_Appt_AestCtr - Event
* LogACallAestCtr - Global
* NewTaskAestCtr - Global
* Send_Email_AestCtr - Global
     
Reports (6)

* Aesthetics Center Reports Report Folder
* Closed Opportunities by Lead Source 
* Converted Leads 
* Lead by Lead Source               
* Lead Conversion by Source                 
* Open Opportunities by Stage             
* Opportunities Closing Next 60 Days

Dashboard (1)
* Aesthetics Center Dashboard Folder
* Aesthetics Center Performance Dashboard 

Validation Rule - Opportunity (1)

* Prevent_Stage_Paid_In_Full

Asset File (1)

* HC_Logo
     
Global Value Set (1)

* Yes_No 

## Configuration Requirements

### Installation Steps:

1. Install the unmanaged package.

### Post-Install Configuration Steps:

1. Confirm that all the newly installed flows are active. 
2. Place the Aesthetics_Gather_Lead_Information_Web2Lead flow on an Experience Cloud page. 
    A. Update the picklist values on the Patient_Preferred_Service__c field on Lead and Opportunity objects to reflect that values you want in your Web2Lead form. 
        1. The Web2Lead form pulls from the Patient_Preferred_Service__c field on Lead.
    A. (Setup; Object Manager; Opportunity/Lead; Fields & Relationships; Stage/Status).
3. Complete lead conversion field mapping for the following custom Lead fields to Opportunity (Setup; Object Manager; Lead; Fields & Relationships; Map Lead Fields)
    A. Best Time to Contact
    B. Preferred Contact Method
    C. Patient Preferred Service
4. Create a queue for leads and tasks. This is used in the Aesthetics - Gather Lead Information (Web2Lead) flow. (Setup; Queues; New)
    A. Label it Aesthetics Center (Aesthetics_Center). 
    B. If you use a different naming convention or existing queue you'll need to update the Get_Aesthetics_Center_Queue_ID element. 
5. Suggested Lead and Opportunity field edits?
    A. Configure the Lead Status picklist on the Lead object to the below suggested values and add the values to the Aest Ctr - Lead Process. (Setup; Object Manager; Lead; Fields & Relationships; Status).
        1) New
        2) Qualified
        3) Pending Eval
        4) Nurturing
        5) Unqualified
        6) Converted
        7) Cold
    B. Configure the Opportunity StageName picklist values on the Opportunity object the below suggested values and add the values to the AestCtr - Oppty Sales Process. (Setup; Object Manager; Opportunity; Fields & Relationships; Stage).
        1) The ‘Paid - Partial’ and ‘Paid - In Full’ stages are specifically referenced  the **Aesthetics - Update Opportunity Stage if Products are Added** flow**. Prevent_Stage_Paid_In_Full** validation rule references ‘Paid - In Full’ stages. If you use a different naming convention or existing values you’ll need to adjust the flow and validation rule accordingly. 
            a) Qualification
            b) Pending - Info
            c) Paid - Partial
            d) Paid - In Full
            e) Closed Won
            f) Closed Lost
        2) For the new status values set the Probability and Forecast Category to your preference. 
6. We suggest adding the below fields to the AestCtr - Opportunity Path for the ‘Qualification’, ‘Pending - Info’, and ‘Paid -  Partial’ stages as well as specific guidance. Since multiple opportunity StageName values are custom we’re not able to include them them in the pachage. (Setup; Path Setting; AestCtr - Opportunity Path). 
    A. Assigned Team Member
    B. Total Paid
    C. Remaining Balance
7. Add the Reschedule (Reschedule_Service_Appt_AesCtr) action to the Event page layout. (Setup; Object Manager; Event; Page Layouts; Event Layout).

### Data Creation & Import Steps: 

* N/A

## Assumptions

* The target org is using Person Accounts
* The target org has Health Cloud or Sales Cloud licenses. 
    * If Salesforce Scheduler is being used for scheduling the target org will also need those licenses.  
* Salesforce Scheduler setup is complete in the target org, if it’s being used.
    * The Aesthetics_Reschedule_Service_Appointment flow assumes that Event Management is enabled in the Salesforce Scheduler Settings.  
* Experience Cloud setup is complete in the target org, if its being used for the Web2Lead flow.
*  Product and Product Book setup is complete in the target org.
* A customer is assuming Salesforce Lightning Experience — not Classic.
* The Accelerator uses the Lightning Design System standards and look. Customers may want to apply their own branding which can be achieved.

## Revision History
