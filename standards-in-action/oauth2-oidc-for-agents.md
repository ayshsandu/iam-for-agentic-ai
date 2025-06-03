# Standard: OAuth 2.0 & OpenID Connect (OIDC) for Agents

OAuth 2.0 is an authorization framework that enables applications (including agents) to obtain limited access to user accounts on an HTTP service. OpenID Connect (OIDC) is a simple identity layer built on top of OAuth 2.0. Together, they are powerful tools for agentic AI IAM.

**How they help:**

1.  **User Delegation (e.g., "Authorization Code Grant"):**
    *   **Scenario:** A user wants an AI agent to access their calendar or emails.
    *   **Solution:** The user authenticates with their service provider (e.g., Google, Microsoft). The agent receives an **Access Token** (often a JWT) with specific **scopes** (permissions like "read_calendar" or "send_email_as_user"). The agent never sees the user's password.
    *   **Benefit:** Secure, scoped, user-consented delegation.

2.  **Agent-to-Service Authentication (e.g., "Client Credentials Grant"):**
    *   **Scenario:** An autonomous agent (not acting for a specific user) needs to call a weather API or a stock market data service.
    *   **Solution:** The agent authenticates itself directly to the service using its own credentials (client ID/secret, or preferably a more secure method like private_key_jwt or mTLS client authentication). It receives an Access Token scoped for its own operations.
    *   **Benefit:** Secure machine-to-machine authentication.

3.  **Scoped Access:**
    *   OAuth `scopes` allow defining granular permissions (e.g., "read_only" vs. "read_write"). Agents should always request and be granted the minimum necessary scopes (Principle of Least Privilege).

4.  **Token Management:**
    *   **Access Tokens:** Short-lived, reducing the window of opportunity if compromised.
    *   **Refresh Tokens:** Allow agents to obtain new access tokens without repeated user interaction, but can be revoked centrally if needed.

5.  **Identity with OIDC:**
    *   OIDC provides **ID Tokens** (JWTs) containing verifiable information about the authenticated user. This can be used by the agent or services it interacts with to make authorization decisions or personalize experiences.

**Key Considerations for Agents:**
*   **Secure storage of client secrets and refresh tokens** is crucial for agents. Use dedicated secrets management solutions.
*   Implement proper **token validation** (signature, expiry, audience, issuer).
*   Always request the **narrowest possible scopes**.
*   Consider **DPoP (Demonstration of Proof-of-Possession)** to bind tokens to the agent, preventing their use if stolen.