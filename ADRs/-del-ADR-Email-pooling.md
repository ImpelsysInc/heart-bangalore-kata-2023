# Record Architecture Decisions

## Status
Accepted

## Context
Polling the email and filtering the travel-related mails.

## Decision
**Implement the Mechanism to Retrieve User Mails with Filtering for Travel-Related**
In the context of the Road Warrior project, it's crucial to retrieve user emails and filter them to identify travel-related information, such as flight bookings, hotel reservations, and car rentals. This decision outlines the chosen approach and technologies to achieve this.



**Implementation Mechanism:**
1. **User Permission**: Once a user grants permission, the system will access their email account. For example, when integrating with Google Mail, an OAuth2-based mechanism will be used to obtain a traveler's access token, ensuring secure and authorized access to their emails.

2. **Email Retrieval**: The chosen approach for email retrieval will be based on JavaMail, a widely-used Java library for handling email communication. JavaMail provides the necessary functionality to connect to email servers, retrieve emails, and perform various email-related operations.

3. **Workflow for Microsoft Outlook**: The same workflow and mechanisms will be applied when integrating with Microsoft Outlook or other email providers. This ensures consistency in email retrieval and filtering across different email services.



**Rationale:**

- **User Privacy and Consent**: By obtaining user consent and using OAuth2 for authorization, the system ensures that it complies with privacy and security standards. Users have control over which emails the system can access.

- **JavaMail Reliability**: JavaMail is a well-established and reliable library for email communication. It provides features for connecting to various email servers, handling different email formats, and applying filters to categorize emails.

- **Consistency**: Using a consistent approach for email retrieval and filtering across different email providers simplifies development and maintenance. It allows the system to work seamlessly with multiple email services.

**Reference:**
This decision is recorded to provide clarity on how email polling and filtering will be implemented within the Road Warrior project.