Learning Practice: Defect Management

Application: North Vacation Booking
Date: November 19, 2026
Course: Application Testing

Step 1: Classify the Findings

During testing, I identified four product defects that do not match the application requirements.

#

Finding

Classification

Explanation

1

Application allows 13 guests.

Product Defect

The requirement allows a maximum of 12 guests, but the application accepts 13.

2

Application only provides one date field.

Product Defect

Users need both check-in and checkout dates to calculate reservation length and validate the stay.

3

Application does not include a $50 cleaning fee.

Product Defect

Every valid reservation must include a one-time $50 cleaning fee, but the application does not display or calculate it.

4

Application allows reservations for unavailable dates.

Product Defect

The application accepted a reservation for dates that were already booked, violating the availability requirement.

Additional Testing Notes

Guest validation: I tested entering zero guests. The application correctly rejected zero, so this test passed.

Reservation length: I could not fully test the 1–31-night requirement because the application only provides one date field.

Availability: I confirmed that the application accepts another reservation for dates that have already been booked.

Step 2: Write a Defect Report

I selected the unavailable-dates defect because it could cause customers to book the same rental for overlapping dates, creating reservation conflicts.

Defect Report: DEF-004

Field

Information

Defect ID

DEF-004

Title

Application allows reservations for unavailable dates

Date Reported

November 19, 2026

Reporter

Student Tester

Application or Feature

North Vacation Booking – Reservation System

Test Environment

macOS, React, TypeScript, Vite, local browser

Preconditions

Application is running, and an existing reservation has already been created for the rental and date being tested.

Steps to Reproduce

1. Open North Vacation Booking. 2. Create and confirm a reservation for a rental on a specific date. 3. Return to the booking form. 4. Select the same rental and date. 5. Submit another reservation. 6. Check whether the second reservation is accepted.

Expected Result

The application should reject the second reservation and display an error explaining that the requested dates are unavailable.

Actual Result

The application accepted the second reservation even though the rental was already booked for that date.

Severity

High

Priority

Urgent

Status

New

Related Requirement

All requested nights must be available.

Supporting Evidence

Screenshot of the original reservation and the second reservation being accepted for the same rental and date.

Why This Defect Matters

This defect could cause multiple customers to reserve the same rental for overlapping dates. It could lead to double bookings, customer complaints, and loss of trust in the application.

Step 3: Assign Severity and Priority

Severity measures how seriously a defect affects the application. Priority determines how quickly developers should fix it.

Defect

Severity

Priority

Explanation

Accepts more than 12 guests

Medium

High

Violates the guest limit and could result in reservations exceeding the allowed capacity. It should be fixed before release.

Missing checkout date

High

High

Prevents users from entering a complete reservation and makes it impossible to validate the number of nights.

Missing $50 cleaning fee

Medium

High

Causes incorrect reservation pricing because the required cleaning fee is not included.

Allows unavailable dates

High

Urgent

Can create double bookings and serious problems for customers. It needs to be fixed immediately.

Step 4: Root Cause and Process Improvement

Based on my code review, these are the possible causes of the identified defects.

Defect

Possible Root Cause

Process Improvement

Guest limit

Missing maximum guest validation in the booking form.

Add frontend and backend validation for 1–12 guests.

Missing checkout date

Booking form only collects one date.

Add separate check-in and checkout fields.

Cleaning fee

Cleaning fee calculation has not been implemented.

Add a $50 cleaning fee to every valid reservation.

Unavailable dates

Booking context adds reservations without checking date conflicts.

Check existing reservations before confirming a new booking.

Step 5: Defect Tracking and Retesting

Defects move through different statuses during the development process.

Status

Meaning

New

Defect has been identified and reported.

Assigned

Developer has been assigned to fix it.

In Progress

Developer is working on the fix.

Fixed

Developer has completed the correction.

Retesting

Tester is checking whether the fix works.

Closed

Tester confirms the defect is resolved.

Reopened

Defect still exists after the fix.

Current Defect Status

All four identified defects currently have an initial status of New.

After developers fix the issues, I would retest each defect using the original test steps. If the application produces the expected result, the defect can be marked as Closed. If the issue still exists, it should be Reopened.