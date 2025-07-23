# SolarScope | An Interactive Tool for Solar Energy and Bushfire Risk Insights

## Purpose
SolarScope is a web-based analytics platform developed to support informed decision-making around solar energy potential and bushfire risk awareness. It is designed to help users upload, visualize, and analyze daily global solar exposure data obtained from the Australian Bureau of Meteorology (BoM)’s Climate Data Online service. By focusing on real measurements from weather stations located in areas of interest, the system enables targeted environmental insight.

## Design and Use
SolarScope is built with a user-centric, modular architecture using Flask for the backend and JavaScript/Chart.js on the frontend. The design supports the following core functionalities:

### Data Upload & Storage:
Users can upload CSV files containing daily solar exposure readings (MJ/m²) from local weather stations. Each dataset is tagged with location metadata (city, latitude, longitude) and stored securely in a database.

### Access Control & Sharing:
Uploaded files can be marked as private, shared, or public. Shared files allow selected users to collaborate, while public files contribute to broader regional comparisons.

### Interactive Visualisation:
Users can select one or more datasets to explore trends over time — daily, monthly, yearly — using dynamic charts. The platform provides automated recommendations for solar farm suitability based on long-term solar exposure averages.

### Analysis & Reporting:
The platform performs in-browser or server-side analysis to detect:
- Seasonal patterns
- Outliers in solar data
- Residential solar panel suitability
- Bushfire risk alerts (based on consecutive high-exposure days during peak months)
- Forecasted bushfire risk (via regression modeling)

### Export Capabilities:
Charts and insights can be exported as PDF or PNG, including contextual summaries that assist with planning, reporting, or stakeholder communication.

### User Management:
Features include secure login, password recovery via security questions, profile editing, and email updates.

## MasterGroup62

| UWA ID   | Name                    | GitHub Username |
| -------- | ----------------------- | --------------- |
| 2******7 | Nancy Rao               | flappyfishhh    |
| 2******5 | Ethan Zhang             | EthanZ-SH       |
| 2******3 | Joshua Wang             | JoJohowl        |
| 2******8 | Chamodhi Withana Gamage | chamodhii       |

## Launching the Application

### Step 1: Clone the Repository

```bash
git clone https://github.com/flappyfishhh/cits5505-masters62.git
```

### Step 2: Navigate to the Project Directory

```bash
cd cits5505-masters62/
```

### Step 3: Create a Virtual Environment

```bash
python -m venv venv
```

### Step 4: Activate the Virtual Environment

- On Windows:

```bash
venv\Scripts\activate
```

- On macOS/Linux:

```bash
source venv/bin/activate
```

### Step 5: Install Python Dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Initialize the Database

Run database migrations to set up the database schema:

```bash
flask db upgrade
```

### (Optional) Step7: Seed the Database with Sample Data

Use the provided `seed_data.py` script to populate the database with sample users, files, and uploads.

```bash
python seed_data.py
```

### Step 8: Start the Application

```bash
flask run
```

Visit the app at: http://127.0.0.1:5000/

## Running Tests

This project includes both unit and end-to-end (E2E) tests using **Pytest** and **Selenium**.

Our Selenium tests use `webdriver_manager.chrome`, which automatically downloads the correct ChromeDriver when you run `pytest`.

If you're using a different browser or prefer manual setup, ensure the correct driver is installed and in your system PATH:
- For Chrome: [Download ChromeDriver](https://sites.google.com/chromium.org/driver/)
- For Firefox: [Download GeckoDriver](https://github.com/mozilla/geckodriver/releases)

### Run All Tests

```bash
pytest
```
This project includes a `pytest.ini` configuration file to manage test discovery and reporting.

### Test Structure
The test suite is organized as follows:

- `tests/`
  - `conftest.py` – Shared fixtures for unit and Selenium tests
  - `selenium/` – End-to-end browser-based tests
  - `unit/` – Unit tests for backend functionality
  - `assets/` – CSV test data for file upload & visualization

We use a **daemon thread** to run the test server during Selenium testing. It shuts down automatically when tests finish.

## Tools
- `seed_data.py`

  Populates the database with sample users, solar data files, and uploads. Useful for testing, demonstration, or quickly initializing development data.
  ```bash
  python seed_data.py
  ```
- `pytest.ini`

  Configuration file for `pytest`. It manages test discovery, markers, output formatting, and other testing behaviors to ensure consistent results across environments.

- `conftest.py`

  Contains shared fixtures used across unit and Selenium tests. Required for consistent test environment setup.

- `reset_dev_db.sh`

  Shell script to reset the development database. It drops all data, reapplies migrations, and restores a clean schema state.
  ```bash
  chmod +x reset_dev_db.sh && ./reset_dev_db.sh
  ```
