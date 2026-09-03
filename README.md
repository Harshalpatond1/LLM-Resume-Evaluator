# LLM-Resume-Evaluator
# ?? AI Resume Evaluator

An AI-powered resume evaluation system that analyzes resumes against a given job description and generates a candidate match score.

The system uses **Groq API with the Qwen model** to extract structured information from job descriptions and resumes, compare candidate skills and experience, and rank candidates based on their overall match percentage.

## ?? Features

* ?? Extracts information from **PDF and DOCX resumes**
* ?? Uses **AI/LLM for resume parsing**
* ?? Extracts structured information from job descriptions
* ?? Identifies candidate skills, education, experience, projects, and certifications
* ?? Compares resumes with job requirements
* ?? Generates an overall candidate match score from **0–100**
* ? Identifies matching skills
* ? Identifies missing important skills
* ?? Checks whether the candidate meets the experience requirement
* ?? Displays the **Top 2 candidates**
* ?? Displays the **Lowest 2 candidates**
* ?? Returns structured JSON using Pydantic models

## ??? Technologies Used

| Technology     | Purpose                               |
| -------------- | ------------------------------------- |
| Python         | Main programming language             |
| Groq API       | Provides access to the LLM            |
| Qwen           | AI model used for analysis            |
| Pydantic       | Data validation and structured output |
| python-dotenv  | Loads API keys from `.env`            |
| PyPDF / PyPDF2 | Extracts text from PDF resumes        |
| python-docx    | Extracts text from DOCX resumes       |
| JSON           | Handles structured AI responses       |

## ?? How It Works

The application follows these main steps:

```text
Job Description
       ?
AI Job Description Analysis
       ?
Structured Job Requirements
       ?
Resume Folder
       ?
Read PDF / DOCX Resume
       ?
AI Resume Parsing
       ?
Structured Resume Data
       ?
Compare Resume + Job Description
       ?
AI Match Score
       ?
Rank Candidates
       ?
Top 2 / Lowest 2 Candidates
```

## ?? Project Structure

```text
AI-Resume-Evaluator/
?
??? resumes/
?   ??? abhay resume.pdf
?   ??? ashish raj.pdf
?   ??? anshit verma.docx
?
??? .env
??? .gitignore
??? requirements.txt
??? main.py
??? README.md
```

> Rename your Python file to `main.py` if it currently has another name.

## ?? Installation

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
cd AI-Resume-Evaluator
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install groq python-dotenv pydantic pypdf python-docx
```

You can also create a `requirements.txt` file:

```text
groq
python-dotenv
pydantic
pypdf
python-docx
```

Then install everything using:

```bash
pip install -r requirements.txt
```

## ?? API Key Setup

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

The application loads the API key using `python-dotenv` and creates the Groq client from it.

### ?? Important

Never upload your `.env` file or API key to GitHub.

Add this to `.gitignore`:

```text
.env
venv/
__pycache__/
```

## ?? Adding Resumes

Create a folder named:

```text
resumes
```

Place candidate resumes inside it.

Supported formats:

```text
.pdf
.docx
```

The application automatically reads supported files from the `resumes` folder.

Example:

```text
resumes/
??? abhay resume.pdf
??? ashish raj.pdf
??? anshit verma.docx
??? priyanshu singh.pdf
```

## ?? Run the Project

After activating the virtual environment and adding your resumes:

```bash
python main.py
```

The program will process each resume and display its score.

Example:

```text
Processing: John_Doe.pdf
Score: 85.0

Processing: Rahul_Sharma.pdf
Score: 72.0

TOP 2 CANDIDATES

John Doe - 85.0 %
Rahul Sharma - 72.0 %

LOWEST 2 CANDIDATES

Candidate 4 - 48.0 %
Candidate 5 - 42.0 %
```

## ?? Resume Information Extracted

The AI extracts information such as:

* Candidate name
* Email
* Phone number
* Total experience
* Skills
* Work experience
* Company
* Job role
* Duration
* Skills used
* Education
* Projects
* Certifications

These fields are represented using Pydantic models in the application.

## ?? Job Description Analysis

The job description is converted into structured information including:

* Role
* Required skills
* Preferred skills
* Minimum experience
* Education requirements
* Responsibilities

If experience is not mentioned, the system is instructed to return `null`, and missing list information is returned as an empty list.

## ?? Candidate Evaluation

For every candidate, the system evaluates:

1. Candidate name
2. Matching skills
3. Missing important skills
4. Experience requirement
5. Overall match percentage
6. Final verdict

The final results are sorted from the highest score to the lowest score.

## ?? Security

* Keep your Groq API key inside `.env`
* Never commit `.env` to GitHub
* Never hard-code API keys in Python files
* Add `.env` to `.gitignore`

## ?? Future Improvements

Possible improvements for this project:

* ?? Build a web interface using FastAPI + HTML/CSS/JavaScript
* ?? Allow users to upload resumes through the website
* ?? Add candidate comparison dashboards
* ?? Add graphical score visualization
* ?? Add job-specific skill recommendations
* ?? Generate improvement suggestions for candidates
* ??? Store candidate results in a database
* ?? Add email notifications
* ?? Add user authentication
* ? Process multiple resumes efficiently
* ?? Generate downloadable candidate evaluation reports

## ?? Current Limitations

* The job description is currently provided directly inside the Python code.
* Resumes must be placed manually inside the `resumes` folder.
* The application currently runs through the command line.
* Each resume requires multiple LLM API calls.
* A fixed delay is used between API requests.
* There is currently no web-based user interface.

## ????? Project Purpose

This project demonstrates how **Generative AI, Large Language Models, structured data extraction, and document processing** can be combined to automate the initial resume screening process.

It can help recruiters quickly identify candidates whose skills and experience are most closely aligned with a particular job description.

## ?? License

This project is created for educational and project-development purposes.
