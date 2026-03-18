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