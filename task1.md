
# Task 01 – GTM Event Schema

## consultation_form_started

* Trigger Type: Form interaction trigger
* Key Parameters: page_url, device_type, form_name
* Purpose: To track users starting the consultation form

## consultation_form_submitted

* Trigger Type: dataLayer push on submit
* Key Parameters: patient_name, patient_phone, source
* Purpose: Main lead conversion tracking

## booking_step_1_complete

* Trigger Type: dataLayer push
* Key Parameters: clinic_location, specialty, step_number
* Purpose: Funnel tracking for booking process

## booking_step_2_complete

* Trigger Type: dataLayer push
* Key Parameters: patient_name, preferred_date, step_number
* Purpose: Identify drop-off before final confirmation

## booking_confirmed

* Trigger Type: dataLayer push
* Key Parameters: booking_id, clinic_location, specialty
* Purpose: Final successful booking conversion

## call_button_click

* Trigger Type: Click trigger
* Key Parameters: page_path, clinic_name, phone_number
* Purpose: Track call enquiries

## whatsapp_chat_opened

* Trigger Type: Link click trigger
* Key Parameters: page_url, device_type, campaign_name
* Purpose: Measure WhatsApp engagement

## patient_guide_download

* Trigger Type: Form submit + file download
* Key Parameters: patient_name, phone_number, guide_name
* Purpose: Track downloadable guide leads

## clinic_page_view

* Trigger Type: Page view trigger
* Key Parameters: clinic_name, city, page_type
* Purpose: Understand clinic-wise traffic

## blog_scroll_50

* Trigger Type: Scroll depth trigger
* Key Parameters: article_name, scroll_percentage, category
* Purpose: Measure blog engagement

## blog_scroll_100

* Trigger Type: Scroll depth trigger
* Key Parameters: article_name, scroll_percentage, category
* Purpose: Track completed article reads


# Booking Funnel Tracking

The booking consultation form consists of several steps and so GTM alone cannot track completion of these steps effectively since the frontend developer has to send the step data to the datalayer when each step is completed.

## Step 1

In Step 1, the event will fire once the user has selected the clinic location and speciality.

```json id="njlwm7"
{
  "event": "booking_step_1_complete",
  "step_number": 1,
  "step_name": "location_specialty_selected",
  "clinic_location": "Bengaluru",
  "specialty": "Knee Pain"
}
```

## Step 2

In Step 2, the event will fire once the patient information is entered.

```json id="sjlwm5"
{
  "event": "booking_step_2_complete",
  "step_number": 2,
  "step_name": "patient_details_entered",
  "patient_name": "Rahul Sharma",
  "preferred_date": "2026-07-05"
}
```

## Step 3

In Step 3, the event will fire once the booking is confirmed.

```json id="vjlwm8"
{
  "event": "booking_confirmed",
  "step_number": 3,
  "step_name": "booking_confirmed",
  "clinic_location": "Bengaluru",
  "specialty": "Knee Pain"
}
```

This step data can then be used in GA4 funnel exploration to see the number of users who progress through the funnel from one step to the next and where they drop off in the booking process.

---

# Conversion Action

The conversion action I will import into Google Ads is `booking_confirmed`.

I have chosen this event since this reflects the strongest user intention and indicates that the patient has completed the booking process successfully. Other events such as page view and button click events indicate user interest, but are less important than confirmed bookings.
