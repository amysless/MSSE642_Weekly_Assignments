## Real-World Attack Flow

### Step 1: Exposure of Stored Data
An attacker discovers a misconfigured cloud storage location containing a recent database backup. The backup includes user email addresses, password representations, and encrypted payment-related fields.

### Step 2: Offline Credential Recovery
Because password protection is weak, the attacker performs offline password cracking. Offline attacks are dangerous because they:
- Do not trigger login rate limits
- Do not require interaction with the application
- Can be scaled using GPUs and large password lists

As a result, the attacker recovers a significant portion of user passwords.

### Step 3: Account Takeover
Using the recovered credentials, the attacker logs into user accounts and:
- Views personally identifiable information (PII)
- Modifies account details
- Makes unauthorized purchases using stored payment methods

Password reuse may also allow the attacker to compromise accounts on other platforms.

### Step 4: Decryption of Sensitive Data (Key Mismanagement)
Because encryption keys are not properly protected, the attacker is able to decrypt sensitive fields from the exposed backup. This escalates the incident from account compromise to broader financial data exposure.
