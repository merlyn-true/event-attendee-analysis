# 🎥 Online Conference Attendance Analysis

## 📌 Project Overview
This project analyzes attendance data from an online conference by combining registration information and Zoom attendance logs. The goal is to understand attendee behavior, participation patterns, and location distribution using structured preprocessing and visual analysis.

## 🎯 Objectives
- Clean, merge, and preprocess registration and attendance datasets.
- Analyze attendee behavior, including join times, leave times, and time spent in session.
- Visualize insights related to location, session participation, and engagement duration.

## 📂 Data Sources
- **Eventbrite Registration Data** — 1,487 raw records  
- **Zoom Attendance Data** — 599 raw records  
Both datasets were cleaned to remove duplicates and standardized before analysis:
- 1,133 unique Eventbrite registrations (duplicates removed on first name, last name, email)
- 599 unique Zoom attendance records (duplicates removed across entire dataset)

## 🧹 Data Cleaning
Key cleaning steps included:
- Normalizing column names and adjusting column types for consistency.
- Removing duplicates in both datasets.
- Replacing inconsistent location values (e.g., *US → United States*).
- Handling missing or null values where necessary.

## 🔄 Preprocessing
Preprocessing involved:
- **Merging datasets on email** to identify:
  - Registered & Attended  
  - Registered but Did Not Attend  
  - Attended but Did Not Register  
- **Resolving multiple join/leave records** by:
  - Grouping by email  
  - Keeping the earliest join time and latest leave time  
- **Calculating time_in_session** for each attendee.
- Preparing subsets for visual analysis (location, join time, leave time, time in session).

## 📊 Analysis
The analysis focused on:
- Attendee distribution by **province** (Canada) and **country** (international).
- Behavioral patterns:
  - When participants joined
  - When they left
  - How long they stayed
- Visualizations created include:
  - Bar charts for attendee location  
  - Histograms for join time, leave time, and time in session  

## 📈 Results & Insights
### **Location Insights**
- Most attendees were based in **Canada**, especially **Ontario (322 attendees)**.
- **10 international attendees**, including **7 from the United States**.

### **Time Spent in Session**
- **125 participants** stayed **over 150 minutes (2.5 hours)**.
- Average time spent: **107 minutes**.

### **Join Time Behavior**
- **243 attendees** joined within the **first 20 minutes**.
- Average join time: **34 minutes after start**.

### **Leave Time Behavior**
- **300 attendees** left **after 150 minutes (2.5 hours)**.
- Average leave time: **140 minutes** (~2 hr 20 min).

## 🛠 Tools Used
- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib & Seaborn**
- **Jupyter Notebook**

## 🚀 How to Run
1. Fork and clone the repository:  
   ```bash
   git clone <repo-url>

2. Install required depedencies:
    ```bash
    pip install -r requirements.txt

3. Run the notebooks in order:
    - 01-cleaning.ipynb
    - 02-preprocessing.ipynb
    - 03-visualization.ipynb

4. All generated clean, processed datasets and plots will be saved in data/clean, data/preprocessed and output/charts folders, respectively.

## ⚠️ Data Privacy and Usage

### **Raw Data Not Included**
To protect personal information, the original raw data (Zoom attendance and Eventbrite registration) **is not included** in this repository.

### **Using Synthetic Sample Data**
We provide **synthetic sample datasets** (`sample_zoom.csv` and `sample_eventbrite.csv`) that mimic the structure, types, and key characteristics of the real data.  
These datasets allow you to **run the notebooks end-to-end** without exposing personal or sensitive information.

### **Structuring Your Own Data**
To use your own data with the notebooks:
1. **Zoom Attendance Dataset**
   - Columns:
     - `Attended` (always "Yes")
     - `User Name (Original Name)`
     - `Email`
     - `Join Time` (`YYYY-MM-DD HH:MM:SS AM/PM`)
     - `Leave Time` (`YYYY-MM-DD HH:MM:SS AM/PM`)
     - `Time in Session (minutes)`
     - `Is Guest` ("Yes"/"No")
     - `Country/Region Name`
2. **Eventbrite Registration Dataset**
   - Columns:
     - `Order #`, 
     - `Order Date`, 
     - `First Name`, 
     - `Last Name`, 
     - `Email`, 
     - `Quantity`, 
     - `Ticket Type`, 
     - `Attendee #`, 
     - `Order Type`, 
     - `Currency`, 
     - `Total Paid`, 
     - `Fees Paid`, 
     - `Eventbrite Fees`, 
     - `Eventbrite Payment Processing`, 
     - `Attendee Status`, 
     - `City`, 
     - `Province/Territory`, 
     - `Postal/Zip Code` 
     - and other optional survey columns
   - Date columns should be in `datetime` format.

### **Privacy Considerations**
- Do **not commit real personal data** (emails, names, addresses, phone numbers) to public repositories.
- Keep raw data in a secure local folder or a private cloud storage.
- Always anonymize or use synthetic data when sharing notebooks or code publicly.