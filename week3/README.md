# OWASP A01: Broken Access Control — Recap

## Overview
**OWASP A01: Broken Access Control** refers to vulnerabilities that occur when an application **fails to properly enforce authorization rules**, allowing users to access resources or perform actions beyond their intended permissions.

This category focuses on **who is allowed to do what**, ensuring that authenticated users can only access data and functionality explicitly authorized for their role and ownership.

---

## What Is Access Control?
Access control determines whether a user is authorized to:

- View specific data  
- Modify or delete resources  
- Perform administrative actions  
- Access restricted endpoints or workflows  

Broken access control occurs when these checks are **missing, improperly implemented, or enforced only on the client side**.

---

## Common Causes of Broken Access Control

- Missing server-side authorization checks  
- Relying on client-side controls (hidden fields, disabled buttons)  
- Insecure Direct Object References (IDOR)  
- Predictable or enumerable object identifiers  
- Overly permissive roles or misconfigured permissions  
- Trusting user-supplied role or privilege data  
- Failure to enforce access control consistently across endpoints  

---

## Real-World Examples

- Users accessing other users’ profiles by changing an ID in the URL  
- Normal users invoking administrative API endpoints directly  
- Bypassing paywalls or approval workflows  
- Modifying JWT claims to escalate privileges  
- Accessing internal or deprecated endpoints via forced browsing  

---

## Impact
Successful exploitation of broken access control can result in:

- Unauthorized access to sensitive data  
- Account takeover and privilege escalation  
- Data breaches affecting large user populations  
- Loss of application integrity  
- Regulatory and compliance violations  
- Severe reputational damage  

---

## Mitigation Strategies

### 1. Enforce Server-Side Authorization
All authorization decisions must be enforced on the backend. Client-side restrictions should never be trusted to protect sensitive functionality. Every request must be validated to ensure the user is authorized to perform the requested action.

---

### 2. Deny by Default
Access should be denied unless explicitly permitted. New endpoints and features should inherit restrictive defaults until authorization rules are intentionally defined.

---

### 3. Validate Object Ownership
For any request involving specific resources (e.g., user profiles, orders, records), the server must verify that the resource belongs to the authenticated user. Requests for resources owned by other users should be rejected.

---

### 4. Apply Least Privilege
Users should only be granted the minimum permissions necessary to perform their tasks. Administrative and privileged actions should be strictly limited and isolated from standard user functionality.

---

### 5. Centralize Access Control Logic
Authorization rules should be implemented through centralized middleware, policy enforcement mechanisms, or role-based access control (RBAC) frameworks. This reduces inconsistencies and prevents missing checks across endpoints.

---

### 6. Protect and Validate Tokens and Claims
Authentication tokens must be securely validated on every request. Role or permission claims should never be trusted without verification, and sensitive authorization decisions should not rely solely on user-controlled data.

---

### 7. Log and Monitor Authorization Failures
Authorization failures should be logged and monitored for suspicious patterns such as repeated access denials, object ID enumeration, or role misuse attempts. This enables early detection of exploitation.

---

### 8. Hands-On Validation Using Replit (Prompt-Driven Simulation)

To reinforce mitigation concepts for OWASP A01, the Replit application developed in week 1 and enhanced in week 2 was extended to simulate both insecure and secure access control implementations. This allows users to observe how broken access control vulnerabilities are exploited and how proper authorization prevents abuse.

#### Goals

- Demonstrate how missing or weak access control checks lead to unauthorized data access and privilege escalation  
- Show how proper server-side authorization and ownership validation prevent exploitation  
- Provide an “ideal interaction” flow where users can:  
  1. Submit requests for protected resources  
  2. Observe how insecure access control fails  
  3. Toggle access control protections  
  4. Observe secure, enforced authorization behavior  

### Prompt You Can Use in Replit AI (Copy/Paste)
Added additional prompt:  
`add OWASP Broken Access Control Playground for secure and insecure methodologies`

---

## Conclusion
Broken Access Control remains one of the most critical application security risks because it enables attackers to bypass intended restrictions with minimal effort. When authorization checks are missing or improperly enforced, attackers can directly access sensitive data, escalate privileges, and compromise application integrity.

Preventing OWASP A01 vulnerabilities requires consistent, server-side enforcement of authorization rules, validation of resource ownership, and adherence to least-privilege principles. By centralizing access control logic, denying access by default, and actively monitoring authorization failures, organizations can significantly reduce the risk of unauthorized access in accordance with OWASP best practices.

