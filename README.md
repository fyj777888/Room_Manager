# Room Manager

A lightweight browser-based room rental management tool for tracking room occupancy, student payment records, rental periods and room availability.

## Overview

Room Manager is a single-page web application designed to help manage **11 rooms** and their related student rental information. 
It allows users to add and delete rental periods, record payments, view room occupancy over time, and track each student's balance and payment history.

All data is stored locally in the browser using **localStorage**, and can also be exported/imported in **JSON** format for backup or transfer.

## Features

- Manage **11 rooms**: A1–A7, B1–B4
- Add rental periods for students
- Prevent:
  - room time conflicts
  - student double-booking conflicts
- Support two rental types:
  - **Whole-month rental**
  - **Special / partial-period rental**
- Automatically deduct monthly rent for whole-month rentals
- Add student payments or refunds
- View:
  - room occupancy timeline
  - student balances
  - payment history
- Export data as JSON
- Import saved JSON data
- Store all data locally in the browser

## Tech Stack

- **HTML**
- **CSS**
- **JavaScript**
- **Browser localStorage** for persistence

## How It Works

### 1. Add Rental Period
Users can create a rental record by entering:
- student name
- room number
- start date
- end date
- expected rent

The system automatically determines whether the rental is:
- a **whole-month rental**, or
- a **non-whole-month (special rental)**

For whole-month rentals:
- monthly rent is deducted automatically
- future monthly deductions are tracked based on the rental schedule

For special rentals:
- a one-time deduction is applied

### 2. Delete Rental Period
Users can delete an existing rental record.

When a rental is deleted:
- all related rent deductions are removed
- the deducted amount is refunded to the student balance

### 3. Show Data
The app provides two main data views:

#### Room Data
- Displays room usage across a 12-month timeline
- Visual rental bars show which student occupies which room and when

#### Student Data
- Displays all students and their current balances
- Supports filtering:
  - all students
  - paid students
  - unpaid students
- Each student has a detailed payment history modal

### 4. Add Payment
Users can manually add:
- payments
- refunds

Each transaction is saved into the student's history and updates their balance immediately.

### 5. Export / Import JSON
The application supports:
- exporting current data to a JSON file
- importing previously saved JSON files

The imported data is validated before loading to avoid:
- invalid room names
- bad date formats
- room conflicts
- student conflicts

## Data Storage

This project uses **localStorage** in the browser to persist data.

## Project Structure

At the current stage, the project is implemented in a **single HTML file**, which includes:

- page structure (`HTML`)
- styling (`CSS`)
- business logic (`JavaScript`)
