<div align="center">

# 📨 IEI Portal

### *Automated member credentials & communication for the Institution of Engineers (India)*

A Node.js portal that turns a member spreadsheet into generated credentials and SMS notifications, in single, bulk or scheduled sends.

<br>

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express_5-000000?style=for-the-badge&logo=express&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Fast2SMS](https://img.shields.io/badge/Fast2SMS-FF6B00?style=for-the-badge)

[🐛 Report Bug](https://github.com/vaiii05/IEI-Portal/issues) · [💼 LinkedIn](https://www.linkedin.com/in/vaibhavi-rai-2b6110357/)

</div>

---

## 📌 Overview

Sending login credentials and announcements to hundreds of members by hand is slow and error-prone. **IEI Portal** automates it: upload an Excel sheet of members, generate a unique password for each, and deliver them over SMS through the Fast2SMS gateway, with logs and downloadable reports for every send.

---

## ✨ Features

| | Feature | Details |
|---|---|---|
| 📤 | **Excel Upload** | Import members with ID, name, email, phone, department and year |
| 🔑 | **Password Generation** | A unique credential is created per member |
| 📱 | **Single & Bulk SMS** | Batch processing for large member lists |
| ✍️ | **Custom Messages** | Send to manual numbers using editable message templates |
| 🎂 | **Birthday Greetings** | Scheduled daily at 9 AM with node-cron |
| 📜 | **Activity Logs** | Live send log with a downloadable Excel report |
| 🧪 | **Simulation Mode** | Test the full flow without sending real SMS |

---

## 🔄 Workflow

```mermaid
flowchart LR
    A[📊 Upload Excel] --> B[🔑 Generate Passwords]
    B --> C{Simulation<br>Mode?}
    C -- On --> D[🧪 Log Only]
    C -- Off --> E[📱 Send via Fast2SMS]
    D --> F[📜 Activity Log]
    E --> F
    F --> G[📥 Download Report]
```

---

## 🛠️ Tech Stack

| Layer | Technologies |
|---|---|
| **Server** | Node.js · Express 5 · Multer · CORS |
| **Scheduling** | node-cron |
| **Data** | SheetJS (xlsx 0.20.2) · pandas helper scripts |
| **SMS Gateway** | Fast2SMS |
| **Frontend** | Vanilla HTML · CSS · JavaScript |
| **Utilities** | Python scripts for data cleaning and sample data |

---

## 🚀 Getting Started

**Prerequisites:** Node.js 18+ and a [Fast2SMS](https://www.fast2sms.com) API key. Python 3 is optional, for the helper scripts.

```bash
# 1. Clone the repository
git clone https://github.com/vaiii05/IEI-Portal.git
cd IEI-Portal

# 2. Install dependencies
npm install

# 3. Add your API key
echo "FAST2SMS_API_KEY=your_api_key" > .env

# 4. Start the server
node server.js         # → http://localhost:3000
```

> 💡 `SIMULATION_MODE` is **on** by default in `server.js`, so nothing is actually sent while you test. Set it to `false` to send real SMS.

<details>
<summary><b>🐍 Run the Python helper scripts</b></summary>

```bash
pip install pandas openpyxl requests

python generate_members_excel.py     # create dummy member data
python process_members_excel.py      # clean phone numbers and prepare records
```
</details>

---

## 🔌 Endpoints

| Method | Route | Purpose |
|---|---|---|
| `GET` | `/` | Web interface |
| `POST` | `/upload-excel` | Upload the member spreadsheet |
| `POST` | `/bulk-send` | Send SMS to all members in batches |
| `POST` | `/send-manual-numbers` | Send SMS to custom numbers |
| `POST` | `/update-template` | Edit the message template |
| `GET` | `/sent-logs` | View the send log |
| `GET` | `/download-report` | Export the report as Excel |

---

## 📁 Project Structure

```
IEI-Portal/
├── server.js                    # Express server + cron scheduler
├── IEI_frontend/
│   └── index.html               # Web interface
├── bulk_send.js · bulk_send.py  # Standalone bulk-send scripts
├── send_student_sms.py          # Alternative SMS provider script
├── process_members_excel.py     # Clean and prepare member data
├── generate_members_excel.py    # Generate sample data
├── iei_dummy_members.xlsx       # Sample member sheet
├── PROJECT_ANALYSIS.md          # Detailed project documentation
└── SECURITY_FIX.md              # Dependency security notes
```

---

## 🔒 Security

- Uses SheetJS **0.20.2** to avoid known `xlsx` vulnerabilities. See [SECURITY_FIX.md](SECURITY_FIX.md).
- API keys live in `.env`, which must never be committed.
- Sample data contains dummy members only.

---

## 📚 More Documentation

See [PROJECT_ANALYSIS.md](PROJECT_ANALYSIS.md) for the full architecture and design notes.

---

<div align="center">

**Built by [Vaibhavi Rai](https://github.com/vaiii05)**
B.Tech IT (AIML Hons.), Fr. CRIT, Vashi 🎓

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/vaibhavi-rai-2b6110357/)

⭐ Star this repo if it helped you!

</div>
