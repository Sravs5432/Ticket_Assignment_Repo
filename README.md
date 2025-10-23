# Streamlining Ticket Assignment for Efficient Support Operations (ServiceNow Project)

## 🚀 Project Overview
This project implements an automated system in ServiceNow to streamline support ticket assignment for ABC Corporation.  
The goal is to automatically route tickets to the appropriate support group (Platform or Certificates) based on the issue type, improving efficiency, reducing delays, and increasing customer satisfaction.


## 🎯 Objective
To develop an automated ServiceNow workflow that:
- Creates users, groups, and roles
- Defines access control (ACL)
- Builds a custom table for ticket management
- Uses Flow Designer to automatically assign tickets to relevant groups based on issue type


## 🧩 Key Features
- **Automated Ticket Routing:** Uses Flow Designer to assign tickets automatically.  
- **Role-Based Access Control:** Configured ACLs for secure access to data.  
- **Custom Table:** Tracks tickets, issues, and assignments.  
- **Group Management:** Users assigned to functional groups for better segregation.  
- **Reusability:** Exported as an Update Set (XML) for reuse in other ServiceNow instances.


## Implementation Steps

### 1. Create Update Set
- Created `Ticket_Assignment_Automation` under *System Update Sets*  
- Set it as **Current** to capture all configurations

### 2. Create Users
- Manne Niranjan
- Katherine Pierce

### 3. Create Groups
- Platform (Manager: Manne Niranjan)
- Certificates (Manager: Katherine Pierce)

### 4. Create Roles
- platform_role
- certification_role

### 5. Assign Roles and Users to Groups
- Platform group → Manne Niranjan, platform_role  
- Certificates group → Katherine Pierce, certification_role  

### 6. Create Custom Table
- Table: `u_operations_related`  
- Fields:
  - Ticket raised date (Date/Time)
  - Service request no (String)
  - Priority (String)
  - Name (String)
  - Issue (Choice)
  - Comment (String)
  - Assigned to user (Reference → User)
  - Assigned to group (Reference → Group)

### 7. Create ACL (Access Control)
- Configured ACLs for the custom table and fields like `Issue`, `Priority`, and `Ticket raised date`.  
- Restricted access to `admin`, `platform_role`, and `certification_role`.

### 8. Create Flows (Automation)
- **Flow 1:** *Regarding Certificates*  
  - Trigger: Record Created/Updated  
  - Condition: Issue is “Regarding Certificates”  
  - Action: Assign to Certificates group  

- **Flow 2:** *Regarding Platform*  
  - Trigger: Record Created/Updated  
  - Condition: Issue is “404 Error” or “Unable to login to platform”  
  - Action: Assign to Platform group  

### 9. Test Automation
- Verified tickets were auto-assigned to correct groups based on issue type.

### 10. Export Update Set
- Completed and exported update set as `Ticket_Assignment_Automation.xml`


## 📸 Screenshots
All screenshots are available in the `/screenshots` folder, including:
1. Update Set setup  
2. User creation  
3. Group and Role setup  
4. Table creation  
5. ACL configuration  
6. Flow Designer setup  
7. Ticket assignment test results  
8. GitHub repository view  

---

## 📂 Repository Structure
servicenow-ticket-assignment
├── README.md
├── /exports/
│ └── Ticket_Assignment_Automation.xml
├── /screenshots/
├──Project_Report.pdf
└── demo_video.mp4



## 🧠 How to Reuse This Project

1. Download `Ticket_Assignment_Automation.xml` from `/exports`.  
2. Go to **System Update Sets → Retrieved Update Sets** in your ServiceNow instance.  
3. Click **Import Update Set from XML** and import the file.  
4. Preview and **Commit** the update set.  
5. The project configuration will now appear in your instance.

---

## 📽️ Demonstration Video
Watch the demo in `/demo_video.mp4` to see the automated ticket assignment in action.

---

## 👥 Contributors
**Sravanthi Lopinti**  
ServiceNow Project Developer  


## 🪪 License
This project is open for academic and non-commercial use.
