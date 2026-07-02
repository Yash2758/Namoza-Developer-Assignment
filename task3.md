# Task 03 – Integration Design

## Flowchart

User Submits Form
        ↓
Landing Page (HTML/JS)
        ↓
Backend API / Webhook
        ↓
HubSpot CRM API
(Create / Update Contact)
        ↓
Karix WhatsApp API
(Send Confirmation Message)
        ↓
Google Ads Conversion Tracking


The landing page form will be connected to HubSpot using a backend API/webhook approach. When a user submits the consultation form, the frontend JavaScript will send the form data to a backend endpoint using a POST request. The backend will then connect with the HubSpot Contacts API to create or update the patient record.

The data stored in HubSpot will include Name, Phone Number, Clinic Preference, Lead Source, and Lead Status. Since the form does not collect email addresses, phone number based checking will be added before creating a new contact. This is important because HubSpot normally handles duplicate checking using email, so without custom phone number checking duplicate patient records may get created.

After the contact is successfully stored in HubSpot, the backend will trigger the Karix WhatsApp Business API to send a confirmation message to the patient. This message will confirm that the enquiry has been received and that the clinic team will contact them shortly.

At the same time, the frontend will fire the consultation_form_submitted conversion event using Google Ads conversion tracking through GTM and GA4. This will help the marketing campaigns optimise towards actual consultation enquiries instead of only page visits.

The biggest failure point in this setup is API failure or delay from HubSpot or Karix. If either API becomes slow or unavailable, the patient data or WhatsApp confirmation may fail. To handle this, a retry mechanism and error logging system should be added on the backend. Failed requests can be stored temporarily and retried automatically after a few seconds.

The WhatsApp message is required to be sent within 2 minutes, so API delays, internet/server issues, or queue congestion can affect this SLA. To monitor this, API response logs and failed request alerts should be maintained. Basic monitoring dashboards and email alerts can also help identify issues quickly so they can be fixed before lead response time increases.
