# Create a GitHub-ready README and supportive files for the user's project.
import os, shutil, textwrap

base = "/mnt/data/airline-powerbi-project"
os.makedirs(base, exist_ok=True)
os.makedirs(f"{base}/assets", exist_ok=True)
os.makedirs(f"{base}/data", exist_ok=True)
os.makedirs(f"{base}/docs", exist_ok=True)

# Copy dashboard image if available
src_img = "/mnt/data/Task5 Dashboard.png"
dst_img = f"{base}/assets/task5_dashboard.png"
if os.path.exists(src_img):
    shutil.copy(src_img, dst_img)

readme = f"""# Airline Data Management and Analysis Using Power BI

A clean, beginner-friendly Power BI project that connects three Excel datasets (Flights, Passengers, Tickets), cleans them in Power Query, models relationships, adds DAX measures, and builds an interactive dashboard with RLS and scheduled refresh.

## 🎯 Objective
Analyze and visualize airline operations for better efficiency and customer satisfaction using Power BI.

## 📂 Datasets
- **Flight_Information.xlsx** — FlightID, FlightNumber, Airline, Destination, Status  
- **Passenger_Information.xlsx** — PassengerID, FlightID, SeatNumber  
- **Ticket_Information.xlsx** — TicketID, FlightID, BookingStatus

> Place the three Excel files in `./data/` when you clone this repo.

## ✅ What’s Included
- Power Query steps (cleaning, conditional column, column-from-examples)
- Data Model (relationships on FlightID)
- DAX measures & calculated table
- Interactive report (slicers, bookmarks, airline pages)
- Power BI Service setup (RLS for Airline A, 5 PM refresh)

## 📸 Dashboard Preview
{"![Task 5 Dashboard](assets/task5_dashboard.png)" if os.path.exists(dst_img) else "_Add your screenshot at `assets/task5_dashboard.png` to render the preview here._"}

## 🧹 Power Query (M) — Key Snippets

**StatusCategory conditional column**
```m
each if [Status] = "On Time" or [Status] = "Arrived" then "Best" else "To Be Improved"
