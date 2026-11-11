# OnlineCourse — Django Assessment Project

This project adds a course assessment feature to a Django online course application. It includes course questions, multiple-choice answers, learner enrolments, saved submissions, automatic grading, and an exam results page.

## Requirements

- Python 3.10 or later
- Django 5.0 (installed from `requirements.txt`)

## Run locally

Open a terminal in the folder containing `manage.py` and run:

```bash
python -m venv .venv
```

Activate the environment:

- Windows PowerShell: `\.venv\Scripts\Activate.ps1`
- macOS/Linux: `source .venv/bin/activate`

Install and initialise the project:

```bash
python -m pip install -r requirements.txt
python manage.py migrate
python manage.py seed_demo
python manage.py createsuperuser
python manage.py runserver
```

Open `http://127.0.0.1:8000/` for the course list and `http://127.0.0.1:8000/admin/` for Django Admin.

## Demo learner

The `seed_demo` command creates a sample learner and assessment:

- Username: `demo_student`
- Password: `StudentDemo123!`
- Course: Introduction to Python

Sign in at `http://127.0.0.1:8000/accounts/login/`, then open `http://127.0.0.1:8000/course/1/` (or select the course from the home page). To demonstrate a passing result, select `def` for question 1, `list`, `dictionary`, and `tuple` for question 2, and `5` for question 3. Submit the assessment. The results page displays **Congratulations!**, the score, percentage, and answer review.

The demo credentials are for local assessment demonstration only. Change or remove them before deploying the project publicly.

## Assessment implementation

- `onlinecourseapp/models.py`: `Question.course`, `Question.grade`, `Question.is_get_score()`, `Enrollment`, and `Submission.enrollment` / `Submission.choices`.
- `onlinecourseapp/admin.py`: course, lesson, question, choice, instructor, learner, enrolment, and submission administration. Questions and choices can be managed inline.
- `onlinecourseapp/views.py`: creates an enrolment and submission, attaches selected choices, calculates the grade, and renders the result.
- `onlinecourseapp/urls.py`: submit route uses `course_id`; result route uses both `course_id` and `submission_id`.

## Run tests

```bash
python manage.py test
python manage.py check
```

## Screenshots for submission

1. Admin screenshot: sign in to `/admin/`. Capture the page showing both **Authentication and Authorization** and **OnlineCourse** sections. Save it as `03-admin-site.png`.
2. Exam result screenshot: sign in as `demo_student`, complete the sample assessment with all correct answers, and capture the page showing **Congratulations!**, the score, and **Exam Results**. Save it as `07-final.png`.

Screenshots must be captured from your own running application. They are not generated or represented by placeholder images in this source ZIP.
