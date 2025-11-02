# NM2025TMID00288

## 🚀 Optimizing User, Group, and Role Management with Access Control and Workflows  
### ServiceNow Interactive Project README

---

## 🧩 Project Overview
This project demonstrates how to **optimize user, role, and access management** in ServiceNow for a small project management team.  
It focuses on creating structured roles, assigning access controls, setting up ACLs, and managing knowledge articles — ensuring accountability and smooth workflow between **Project Managers** and **Team Members**.

---

## 👥 Team Scenario

| Role | User | Responsibility |
|------|------|----------------|
| Project Manager | Alice | Manage projects, oversee tasks |
| Team Member | Bob | Work on assigned project tasks |

---

## ⚙️ Step 1: Create Users
1. Navigate to **All → System Security → Users**  
2. Click **New**  
3. Create users with the following details:
   - **User 1:** Alice (Project Manager)
   - **User 2:** Bob (Team Member)
4. Click **Submit** after each creation.

> 🧠 *Each user acts as a distinct identity for access control testing.*

---

## 🧰 Step 2: Assign Roles to Users

### For **Alice (Project Manager)**
1. Navigate to **All → System Definition → Tables**  
2. Open **Project Manager** user record.  
3. Click **Edit → Add Roles:**
   - `project_member`
   - `u_project_table`
   - `u_task_table`
4. Click **Save → Update**.

### For **Bob (Team Member)**
1. Open **Bob** user record.  
2. Click **Edit → Add Roles:**
   - `team_member`
   - `u_task_table`
3. Click **Save → Update**.  
4. Impersonate Bob to test role-based access.

> ✅ *Alice can view and modify both Project and Task tables.*  
> ✅ *Bob can only interact with Task tables relevant to team members.*

---

## 🧩 Step 3: Add Custom Roles
If roles like `u_project_table` or `u_task_table` were **not available** in the role selection list:

1. Navigate to **All → User Administration → Roles**  
2. Click **New**  
3. Create roles:
   - `u_project_table`
   - `u_task_table`
   - `project_member`
   - `team_member`
4. Save and assign them as described above.

---

## 🔒 Step 4: Assign Table Access to Applications
When a custom table is created, ServiceNow automatically creates an **application** and **module**.

1. Navigate to your app (e.g., *Project Table*).  
2. Right-click → **Edit Module**.  
3. Under **Roles**, add:
   - `project_member` for **Project Table** app.  
4. Repeat for **Task Table** app and assign:
   - `project_member`, `team_member`.

> 🎯 *This ensures only the right users can access or modify app data.*

---

## 🛡️ Step 5: Create Access Control Rules (ACLs)

### Elevate privileges:
- Click your **profile → Elevate Role → security_admin → Elevate.**

### Create ACLs:
1. Go to **All → System Security → Access Control (ACL)**  
2. Click **New**  
3. Fill the form **before saving:**

| Field | Example Value |
|--------|----------------|
| Type | `field` |
| Operation | `write` |
| Table | `u_task_table2` |
| Field Name | `comment` |
| Requires Role | `team_member` |

4. Submit.  
5. Repeat for other fields:

| Table | Field | Operation | Role |
|--------|--------|-----------|------|
| u_task_table2 | comment | write | team_member |
| u_task_table2 | status | write | team_member |
| u_task_table2 | description | read | team_member |
| u_task_table2 | assigned_to | read | project_member |

### Test ACLs:
- Impersonate **Bob**  
- Navigate to **Task Table2**  
- Verify Bob can edit **Comment** and **Status** fields only.

---

## 📘 Step 6: Knowledge Base Interaction

### Scenario
A caller cannot create a distribution list in Outlook, as the feature is renamed to **Contact Group**.

### Task Performed:
1. **Search Article:**
   - Go to **Knowledge → Articles**
   - Search for **“Create and Edit a Contact Group”**

2. **Flag Article:**
   - Flag it with the message:  
     ```
     The first procedure needs numbering corrected.
     ```

3. **Add Comment:**
   - Add comment under the article:  
     ```
     Can we have a similar article for Outlook 365?
     ```

> 🧾 *Demonstrates knowledge management and feedback workflow.*

---

## 🧪 Testing Summary

| Test Case | User | Expected Outcome |
|------------|-------|------------------|
| Alice edits Project Table | ✅ Success |
| Bob edits Comment & Status only | ✅ Success |
| Bob edits other fields | ❌ Access Denied |
| Knowledge Article flagged | ✅ Owner Notified |
| Comment added on article | ✅ Visible in discussion thread |

---

## 🧭 Conclusion
This project successfully demonstrates:
- Creation and role-based management of users.  
- Implementation of **table-level and field-level ACLs**.  
- Control of data visibility and modification based on user roles.  
- Application of **Knowledge Management** best practices (flagging, commenting, and collaboration).

---

## 🧠 Tech Stack
- **Platform:** ServiceNow  
- **Modules Used:**  
  - User Administration  
  - Role Management  
  - Table Access Control (ACL)  
  - Knowledge Management  
- **Test Users:** Alice (Project Manager), Bob (Team Member)

---

## 💬 Future Enhancements
- Add automated workflow for task assignment.  
- Integrate notification triggers for role changes.  
- Create article versioning automation for documentation updates.

---

👤 **Created By:** *Team ID: NM2025TMID00288*  
📅 **Date:** *November 2025*  
🔗 *ServiceNow Project — Access Control & Workflow Optimization*
