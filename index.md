# 📊 EdgeHR Dashboard Analytics Module

This module provides advanced data visualization and business insights for the EdgeHR platform.
It includes dynamic charts for employee hiring trends, cumulative workforce growth, and overall business expansion analytics.

---

## 🚀 Features

### 1️⃣ Employee Hiring Trend (Company Dashboard)

Displays monthly hiring activity for the last 12 months.

**Includes:**

* Monthly new hires (Bar Chart)
* Cumulative total employees (Line Chart)
* Dual Y-axis visualization
* Dynamic gradient branding (Blue → Orange)
* Zero-data visual state handling
* Animated rendering
* Tooltip interaction
* Mobile responsive scaling

**Purpose:**
Helps companies understand hiring velocity and workforce growth patterns.

---

### 2️⃣ Business Growth Analytics (Super Admin Dashboard)

Shows platform-wide expansion metrics.

**Includes:**

* Total companies growth over time
* Total employees growth over time
* Gradient area charts
* Growth milestone highlighting
* Smart point visibility (only when growth occurs)
* Animated timeline visualization
* Company logo evolution strip

**Purpose:**
Provides macro-level SaaS business growth intelligence.

---

### 3️⃣ Cumulative Workforce Calculation

System calculates progressive employee growth using:

```
cumulative = previous_total + current_month_hiring
```

Used for:

* Growth forecasting
* Workforce trend analysis
* SaaS adoption tracking

---

### 4️⃣ Dynamic Time Window

Charts always show:

✔ Last 12 months rolling window
✔ Auto updates based on current date
✔ No manual configuration required

---

### 5️⃣ Brand-Aligned Visualization System

All charts follow EdgeHR visual identity:

* Primary Gradient: Blue → Orange
* Soft neutral grid system
* Rounded bar rendering
* Smooth curve interpolation
* Premium SaaS animation style

---

### 6️⃣ Mobile Responsive Analytics

Graph system adapts across devices:

* Desktop → Full analytic visualization
* Tablet → Reduced tick density
* Mobile → Scaled chart containers
* Optional horizontal scroll support

---

### 7️⃣ Performance Optimizations

* Lazy animation trigger on viewport entry
* Minimal DOM repaint
* Optimized dataset rendering
* Conditional point drawing logic
* Reduced legend rendering on small screens

---

## 🧠 Technical Stack

**Frontend Visualization**

* Chart.js
* Canvas API gradients
* Intersection Observer (animation trigger)

**Backend Data Processing**

* PHP (Procedural)
* MySQL aggregation queries
* Rolling date window logic

---

## 📂 Data Sources

### Employee Hiring Trend

```
employees.created_at
employees.company_id
```

### Business Growth

```
company.created_at
employees.created_at
```

---

## 📈 Analytics Value

This module enables:

✔ Hiring momentum tracking
✔ Workforce scaling visibility
✔ SaaS growth storytelling
✔ Investor dashboard insights
✔ HR decision intelligence
✔ Operational trend awareness

---

## 🎯 Future Enhancements (Planned)

* Predictive hiring AI curve
* Department-wise growth charts
* Attrition visualization
* Real-time workforce counter
* Hiring target vs actual analytics
* Interactive drill-down charts

---

## 🧑‍💻 Author

**Rahul Goswami**
EdgeHR Platform Developer

---

## 🏢 Product

EdgeHR — Smart Human Resource Management System

---






# 🎧 EdgeHR Helpdesk & Ticket Support System

A complete **Helpdesk Ticket Management & Support Chat System** built inside the EdgeHR platform.
This module allows companies to raise support tickets and communicate with the admin through a real-time styled chat interface.

---

## 🚀 Features

### 🎟 Ticket Management

* Companies can raise support tickets
* Ticket includes:

  * Subject
  * Description
  * Priority (Low / Medium / High / Critical)
  * Optional attachment (image/pdf)
* Ticket status lifecycle:

  * Open
  * In Progress
  * Resolved
  * Closed

---

### 💬 Ticket Conversation (Chat System)

* Admin and Company can reply inside ticket thread
* Chat UI styled like modern messaging apps
* Features include:

  * Left/right aligned messages (Admin vs Company)
  * Profile avatar support
  * Timestamp display
  * Auto scroll to latest message
  * Typing indicator animation
  * Default avatar fallback if image not available

---

### 🧑‍💼 Role Based Access Control

#### Admin

* View all tickets
* Reply to tickets
* Update ticket status
* See company profile logo in chat
* Full ticket management access

#### Company

* Raise support ticket
* View own tickets only
* Reply to admin messages
* View ticket conversation
* Access ticket history

---

### 📄 Ticket Listing

#### Company Side (`my-tickets.php`)

* Table listing of all raised tickets
* Columns:

  * Ticket ID
  * Subject
  * Priority
  * Status badge
  * Created date
  * View action button

#### Admin Side

* Centralized ticket dashboard
* Company identification included

---

### 📎 Attachment Support

* File upload while raising ticket
* Supported formats:

  * JPG
  * PNG
  * PDF
* Secure storage inside:

```
/uploads/tickets/
```

---

### 🖼 Avatar System

* Admin avatar from:

```
/uploads/admins/
```

* Company logo from:

```
/uploads/companies/
```

* Automatic fallback to default image if not available

---

### 🎨 UI/UX Enhancements

* Modern chat bubble UI
* Clean dashboard card layout
* Responsive table design
* Mobile optimized ticket view
* Bootstrap based layout system
* Typing animation indicator

---

### 🔐 Security Measures

* Session based authentication
* Role based access restriction
* Ticket ownership validation
* SQL injection safe query handling
* Secure file linking

---

### ⚙️ Tech Stack

* PHP (Core PHP)
* MySQL
* Bootstrap 5
* JavaScript
* HTML5 + CSS3

---

### 📂 Folder Structure (Relevant)

```
admin/
    tickets.php
    admin-ticket-view.php
    reply-ticket.php

company/
    raise-ticket.php
    my-tickets.php
    ticket-view.php

uploads/
    tickets/
    admins/
    companies/
```

---

### 🧠 Future Improvements (Planned)

* Email notification on ticket reply
* Real-time chat using AJAX / WebSocket
* Unread message badge
* Ticket search & filtering
* Pagination
* SLA tracking system
* File preview inside chat
* Admin assignment system
* Ticket priority automation

---

### 📌 Summary

This Helpdesk module enables seamless **Admin ↔ Company communication**, ensuring structured issue tracking, faster resolution, and improved user support experience within EdgeHR.

---

## 🧑‍💻 Author

**Rahul Goswami**
EdgeHR Platform Developer








## 🔐 Company & Employee Block / Unblock System

This module introduces a hierarchical authentication control system that allows the Super Admin to manage access permissions at both the company and employee levels.

---

### 📌 Feature Overview

The system enables:

- Super Admin to block or unblock any company
- Super Admin to block or unblock any employee
- Automatic login restriction based on block status
- Hierarchical authentication validation

---

### 🏢 Company Level Blocking

A new column named `auth` has been introduced in the **company table**.

| auth | Meaning |
|------|--------|
| 1    | Company can log in |
| 0    | Company is blocked |

When a company is blocked:

- Company login is denied
- All employees of that company are automatically restricted from logging in

This ensures centralized access control.

---

### 👨‍💼 Employee Level Blocking

A similar `auth` column is added in the **employees table**.

| auth | Meaning |
|------|--------|
| 1    | Employee can log in |
| 0    | Employee is blocked |

Employee login validation checks:

1. Company authentication status
2. Individual employee authentication status

Login is granted only if:


company.auth = 1 AND employee.auth = 1





---

### 🔎 Authentication Logic

Employee login query uses a JOIN:

```sql
SELECT e.*, c.auth as company_auth
FROM employees e
JOIN company c ON e.company_id = c.company_id
WHERE ...




Validation flow:

If company is blocked → login denied

If employee is blocked → login denied

Otherwise → login allowed




🧠 Design Philosophy

This system follows real-world SaaS HR architecture:

Company status is superior to employee status

Access control is hierarchical

Authentication state is separated from employment status

This allows flexibility such as:

Temporarily suspending employees

Suspending entire organizations

Maintaining HR lifecycle independently


🎨 UI Enhancements

The block/unblock feature is integrated into:

Company listing page

Employee listing page

Modern UI improvements include:

Icon-based action buttons

Soft color badges

Minimalist SaaS design approach




⚙️ Security Considerations

Authentication state is validated server-side

Login access is controlled at database level

Session initiation is blocked for unauthorized users    



🚀 Future Improvements

Planned enhancements:

Block reason logging

Block history tracking

Email notification on suspension

Role-based permission system

Soft suspension workflows

Audit logs



✅ System Status

✔ Company block system implemented
✔ Employee block system implemented
✔ Hierarchical login restriction active
✔ UI integration complete
✔ Production ready