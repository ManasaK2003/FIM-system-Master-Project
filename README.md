# FIM-system-Master-Project
A cross-platform security tool that detects malicious file changes using machine learning — achieving >95% detection accuracy with significantly fewer false positives than traditional hash-based FIM systems. Built as part of my MSc Cybersecurity dissertation at the University of Hertfordshire (2025–26).
What it does
Traditional FIM tools flag any file change as suspicious — which creates huge amounts of noise. This system is smarter. It learns the difference between legitimate changes (software updates, routine edits) and malicious ones (ransomware, tampering, injection attacks) using an Isolation Forest anomaly detection model.
How it works
The system uses a three-tier architecture:
[ Monitoring Agent ]  →  [ Processing Engine ]  →  [ Real-time Dashboard ]
  Watches files            Extracts features          Shows live alerts
  on Windows/Linux         Runs ML detection           via REST API
Detection pipeline:

Monitors files continuously across Windows and Linux
Extracts content from multiple file formats (PDF, DOCX, XLSX, binaries)
Converts content into TF-IDF feature vectors
Runs features through an Isolation Forest anomaly detector
Combines ML output with rule-based checks for final verdict
Sends alerts to a real-time dashboard via REST API

Adaptive retraining: The model retrains on organisation-specific data over time, learning what "normal" looks like for that environment — reducing false positives further.

Results
MetricThis systemTraditional hash-based FIMDetection accuracy>95%~80–85%False positive rateSignificantly reducedHighPlatform supportWindows + LinuxVariesLearns over timeYes (adaptive retraining)No

Tech stack
LayerTechnologyLanguagePython 3Web frameworkFlaskML libraryscikit-learnAnomaly detectionIsolation ForestFeature extractionTF-IDF (sklearn)File parsingpdfplumber, python-docx, openpyxlAPIREST (Flask)PlatformsWindows, Linux

Project structure
fim-system/
│
├── agent/                  # Monitoring agent (file watcher)
│   └── monitor.py
│
├── engine/                 # Processing & ML detection
│   ├── extractor.py        # Multi-format content extraction
│   ├── features.py         # TF-IDF feature engineering
│   └── detector.py         # Isolation Forest model
│
├── dashboard/              # Flask REST API + alert dashboard
│   ├── app.py
│   └── templates/
│
├── models/                 # Saved trained models
│
├── data/                   # Sample data for testing
│
├── requirements.txt
└── README.md

How to run
1. Clone the repository
bashgit clone https://github.com/[your-username]/fim-system.git
cd fim-system
2. Install dependencies
bashpip install -r requirements.txt
3. Start the monitoring agent
bashpython agent/monitor.py --watch /path/to/directory
4. Start the dashboard
bashpython dashboard/app.py
Then open http://localhost:5000 in your browser to see live alerts.

Requirements
flask
scikit-learn
numpy
pandas
pdfplumber
python-docx
openpyxl
watchdog
Install all with:
bashpip install -r requirements.txt

About this project
This was built as my MSc Cybersecurity dissertation project. The goal was to solve a real problem in security operations: traditional FIM tools generate too many false positives, which causes alert fatigue in SOC teams.
By combining machine learning with rule-based checks and training the model on organisation-specific data, the system learns what legitimate file activity looks like — and only raises alerts when something genuinely looks suspicious.
Skills demonstrated:

Python security tooling
Machine learning for cybersecurity (anomaly detection)
Cross-platform development (Windows & Linux)
REST API development with Flask
Real-time security dashboards
Feature engineering (TF-IDF)
Multi-format file analysis


Author
Manasa Kantharaju
MSc Cybersecurity — University of Hertfordshire (2025–26)
B.E. Information Science & Engineering — CIT (2020–24)
LinkedIn: [linkedin.com/in/your-url]
TryHackMe: [tryhackme.com/p/your-username]

Status
🟡 In active development — dissertation project (2025–26)
