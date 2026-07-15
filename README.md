# Mach10

Please note: Some of the other team members do not wish for our repository to go public. To respect their wishes, I will only write general details and include videographed documentation for portfolio purposes.
---

## Overview

Mach10 was designed around a practical aircraft operations workflow.

Users can manage aircraft, review fleet details, reserve aircraft, log flight activity, track maintenance and parts, review inspections and airworthiness directives, and view dashboard/analytics data from one integrated system.

The project includes:

* A React Router / Vite frontend for the user-facing web application
* A Django backend organized around aircraft, users, actions, and external service route groups
* PostgreSQL persistence for fleet, users, organizations, reservations, logs, maintenance, parts, inspections, and compliance-related records
* Dockerized frontend and backend services
* Helm charts for Kubernetes-style deployment
* Weather, METAR, S3 backup, and AI-assisted processing integration points

---

## Features

### Fleet and aircraft management

* Add, edit, view, and delete aircraft records
* Track aircraft class, make, model, tail number, location, registration, airport, Hobbs time, tach time, and cycles
* View aircraft-specific pages with operational, reservation, maintenance, and compliance context

### Reservations

* Reserve aircraft through logged-in or guest reservation flows
* View existing reservations for an aircraft
* Validate reservation windows, check-in times, and check-out times
* Block reservations when aircraft compliance state requires attention
* Display aircraft and reservation preview details before submission

### Flight logs

* Add manual flight logs
* Add guest flight logs
* Upload and process flight-log data through extraction workflows
* View aircraft-specific flight-log history
* Support dashboard and map-oriented views for flight activity

### Maintenance and parts

* Track maintenance items and maintenance history
* Manage aircraft parts and part history
* Store part notes, install history, serial numbers, time/cycle limits, and overhaul/life-limit fields
* Support maintenance log extraction and maintenance-estimation workflows

### Inspections and airworthiness directives

* Add and edit inspection records
* Record inspection completions
* Estimate inspection needs
* Track airworthiness directives and advisory records
* Resolve, edit, delete, and summarize AD status for aircraft

### Dashboard and analytics

* Retrieve dashboard events and dashboard summaries by organization
* View analytics data for operational and fleet activity
* Support map-point data for flight-log visualization

### External service integrations

* Weather forecast and date-status endpoints
* METAR-related aviation weather integration
* S3-based backup, restore, and purge workflows
* OpenAI-compatible AI processing modules for selected log, inspection, and maintenance workflows

---

## Tech Stack

### Frontend

* React
* React Router
* Vite
* TypeScript
* Material UI
* Tailwind CSS
* Axios
* Leaflet / React Leaflet
* FullCalendar
* Formik
* Yup
* Notistack

### Backend

* Python
* Django
* Django REST Framework
* PostgreSQL
* django-cors-headers
* Pillow
* boto3
* pandas
* airportsdata
* statsmodels
* pyodbc

### Deployment

* Docker
* nginx
* Gunicorn
* Helm
* Kubernetes
* PostgreSQL

---

## Repository Structure

```text
Mach10/
├── mach10-ui/          # React Router / Vite frontend
├── mach10-backend/     # Django backend and API services
├── docs/               # Architecture diagrams and supporting documentation
└── README.md           # Project overview
```

Frontend structure:

```text
mach10-ui/
├── app/
│   └── components/
│       ├── authentication/
│       ├── dashboard/
│       ├── fleet/
│       ├── forecast/
│       ├── new-tab-pages/
│       ├── plane-view/
│       ├── reservations/
│       └── users/
├── helm/
├── Dockerfile
├── package.json
└── README.md
```

Backend structure:

```text
mach10-backend/
├── DjangoProject/
├── mach10/
├── users/
├── actions/
├── externals/
├── helm/
├── helm-aircraft/
├── helm-users/
├── helm-actions/
├── helm-externals/
├── Dockerfile
├── requirements.txt
└── README.md
```

---

## Architecture

At a high level, Mach10 is organized around a frontend web app, a Django backend, shared PostgreSQL persistence, and optional external integrations.

```text
Users
  -> mach10-ui
       -> React Router routes
       -> aircraft, reservations, dashboards, logs, maintenance UI
       -> Axios clients
  -> mach10-backend
       -> /mach10     aircraft, reservations, logs, maintenance, parts, inspections, analytics
       -> /users      auth, profiles, roles, organizations, memberships
       -> /actions    server logs, error logs, audit logs
       -> /externals  METAR, S3 backup, restore, purge
  -> PostgreSQL
       -> users, organizations, fleet, reservations, flight logs, maintenance, parts, inspections
```

---
