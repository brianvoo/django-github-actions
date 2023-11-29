# Skeleton Django with Github Actions Workflow to Test then run a ZAP Baseline Scan
Skeleton Django with `django-admin startproject webguard` followed by `py manage.py runserver` to ensure skeleton runs.<br>

## Github Actions Workflow
The [single workflow](https://github.com/brianvoo/django-github-actions/blob/main/.github/workflows/django.yml) is a combination of 2 workflows: 
1. The suggested Django Test by Github Actions which steps include:<br>
    a. Provisioning ubuntu-latest machine with Python 3.10.6<br>
    b. Installing dependencies based on requirements.txt<br>
    c. Run test with `py manage.py test`
3. [ZAP Baseline Scan](https://github.com/marketplace/actions/zap-baseline-scan) by Zaproxy which will only run if the above is successful:<br>
    a. Run server with `py manage.py runserver`<br>
    b. Run scan using `zaproxy/action-baseline@v0.10.0` on target http://localhost:8000/

## Requirements to Run Locally
Prerequisites are Python 3.10.6 and virtualenv. 
1. Run `python -m venv venv` to create a virtual environment
2. Activate the environment with `venv\Scripts\activate`
3. Use `pip install -r requirements.txt` to install the required dependencies for this project
4. Run the project by `cd webguard` and `py manage.py runserver`
5. After which http://localhost:8000/ should show the Django install successful page.

## Summary
While security is a priority, decided to run app test before security test for better developer workflow.<br>

Overall good exposure to Github Actions and its workflows. A lot to be learned and improved as jobs in the workflow are not as descriptive, real-world apps would have more detailed tests, and ZAP Baseline scans might not be as thorough as other scans.
