# Sports Hall Booking System

A ServiceNow Service Portal application that digitizes sports facility reservations — built on Service Portal, Flow Designer, and Business Rules to automate slot booking, approvals, and status tracking.

## Overview

Users can browse available sports halls, check real-time slot availability, submit booking requests, and track approval status — all through a custom Service Portal interface. Admins/approvers review requests through ServiceNow's native approval workflow, with automated email notifications and daily cleanup of stale pending bookings.

## Features

- **Hall Browser Widget** — displays live hall data (name, location, capacity, hourly rate) pulled via GlideRecord
- **Booking Form Widget** — dynamic hall/slot selection, submits real booking requests, cross-widget communication via `$rootScope.$broadcast`
- **My Bookings Widget** — status tracker with color-coded badges (Pending / Approved / Confirmed / Rejected)
- **Flow Designer Approval Workflow** — auto-triggers an approval request on booking creation; approver decision automatically updates booking status
- **Email Notifications** — automated email sent when a booking is approved
- **Scheduled Job** — daily cleanup script that auto-rejects bookings left pending for 24+ hours and releases the slot back to available

## Data Model

- **Sports Hall** — hall name, location, capacity, hourly rate, active flag
- **Booking Slot** — hall (reference), date, start/end time, status (Available/Booked)
- **Booking** — requester (reference to sys_user), hall (reference), slot (reference), status (Pending/Approved/Confirmed/Rejected/Cancelled), total charges

## Tech Stack

- ServiceNow Service Portal (Angular-based widgets)
- Flow Designer (approval automation)
- GlideRecord (server-side scripting)
- Bootstrap / Angular directives (ng-repeat, ng-model, ng-if)
- Email Notifications (sysevent_email_action)
- Scheduled Jobs (sysauto_script)

## Screenshots

See the `/screenshots` folder for the full user flow: hall browsing, booking submission, status tracking, approval, and email notification.

## Widget Source Code

Widget HTML, server scripts, and client controllers are included as text files for each of the three custom widgets:
- Hall Slot Browser
- Booking Form
- My Bookings

## Author

Built by Mouna as a hands-on ServiceNow project covering Service Portal development, Flow Designer automation, and end-to-end approval workflows.
