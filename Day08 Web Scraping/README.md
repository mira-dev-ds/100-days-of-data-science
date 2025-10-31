
# 🕵️‍♀️ Python Job Scraper — TimesJobs

A simple web scraping project that automatically fetches the latest **Python developer job postings** from [TimesJobs.com](https://www.timesjobs.com/).
It filters jobs based on **posting date** and **skills**, helping you instantly find roles that match *your comfort zone* — or avoid the ones that don’t!



## 🚀 Project Overview

This project demonstrates **practical web scraping** using:

* `requests` for fetching HTML content
* `BeautifulSoup` for parsing and extracting job data
* `time` for scheduling repeated runs automatically

The script scans for **Python-related jobs**, filters only those posted **a few days ago**, and lets you exclude listings containing skills you’re **unfamiliar with**.



## 🧠 How It Works

1. The script fetches job listings from TimesJobs’ search page.
2. It parses the HTML and extracts:

   * **Company Name**
   * **Published Date**
   * **Skills Required**
   * **Job Link (More Info)**
3. You can input any skill you want to **filter out** (e.g. `"django"`, `"flask"`, `"aws"`).
4. The script then prints only the relevant job postings.
5. It automatically refreshes every few minutes (configurable).


## 🧩 Example Output

```
Enter the skills you are unfamiliar with: django
Filtering out django

Company Name: 3RI Technologies Pvt Ltd
Published Date: Posted few days ago
Skills: ['python', 'database', 'security', 'git', 'mobile']
More Info: https://www.timesjobs.com/job-detail/software-developer-3ri-technologies-pvt-ltd-pune-jobid-xyz123.html

Waiting 10 minutes.
```



## 🛠️ Technologies Used

* **Python 3**
* **BeautifulSoup4**
* **Requests**
* **LXML Parser**
* **Time** (for scheduling)



## ⚙️ How to Run

1. Clone or download this repository

   ```bash
   git clone https://github.com/yourusername/python-job-scraper.git
   cd python-job-scraper
   ```

2. Install required libraries

   ```bash
   pip install requests beautifulsoup4 lxml
   ```

3. Run the script

   ```bash
   python main.py
   ```

4. Enter the skill you’d like to filter out (e.g. `django`)
   The script will keep running and fetch new results periodically.

---

## 🔄 Customization

* **Change the keyword**:
  Update the `txtKeywords` parameter in the URL to search for other roles, e.g.

  ```python
  txtKeywords=data+science
  ```

* **Change refresh time**:
  Modify the `time_wait` variable in the script (currently set to 10 minutes).

---

## ⚠️ Disclaimer

This project is built **for learning purposes only**.
Respect the target website’s [robots.txt](https://www.timesjobs.com/robots.txt) and scraping policies.
Avoid making too many rapid requests.

---

## ✨ Learning Outcomes

* Basics of web scraping and HTML parsing
* Data extraction from live websites
* Automating and filtering web data
* Writing clean, reusable Python scripts

