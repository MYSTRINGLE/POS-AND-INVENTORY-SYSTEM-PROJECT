# POS and Inventory System
POS AND INVENTORY SYSTEM
========================

A full-stack Point of Sale (POS) and inventory management web application built with Django 5 and MySQL. The system is designed to help small and medium-sized retail businesses manage product stock in real time, process customer checkout transactions accurately, and monitor daily sales performance through role-based access control.


CORE FEATURES
-------------

1. Inventory Management
   - Product Catalog: Add, edit, categorize, and archive products with SKU or barcode identifiers, unit prices, and cost prices.
   - Real-Time Stock Tracking: Automatically deduct stock quantities upon completed sales and increment stock when restocking deliveries are recorded.
   - Low-Stock Alerts: Flag items whose inventory falls below a configurable reorder threshold.

2. Point of Sale (POS)
   - Fast Checkout Interface: Search or scan items into an active cart, adjust quantities, and calculate subtotals, taxes, and totals automatically.
   - Transaction Recording: Generate unique sale receipts and store itemized transaction records in MySQL.
   - Stock Validation: Prevent overselling by validating available inventory before finalizing a sale.

3. Reporting and User Management
   - Sales Summaries: View daily, weekly, and product-level sales and revenue reports.
   - Role-Based Access Control (RBAC): Separate permissions for Cashiers (processing sales) and Managers or Admins (managing inventory, pricing, users, and reports).


TECHNOLOGY STACK
----------------

- Backend Framework: Python 3.12, Django 5
- Database: MySQL
- Frontend: Django Templates, HTML5, CSS3, JavaScript
- Version Control: Git and GitHub
- CI/CD: GitHub Actions (.github/workflows/ci.yml)


PROJECT ARCHITECTURE AND PLANNED STRUCTURE
------------------------------------------

POS-AND-INVENTORY-SYSTEM-PROJECT/
  .github/
    workflows/
      ci.yml              - Automated GitHub Actions CI pipeline
  .gitignore              - Excludes venv, .env, cache, and local artifacts
  .env.example            - Template for required environment variables (WP 4.2)
  manage.py               - Django CLI entry point (WP 4.2)
  requirements.txt        - Python package dependencies (WP 4.2)
  README.md               - Project documentation


REPOSITORY AND GIT WORKFLOW RULES
---------------------------------

1. Long-Lived Branches
   - main: Production-ready branch; always stable and deployable.
   - develop: Integration branch where completed Work Packages are merged and tested.

2. Work Package Feature Branches
   - Every Work Package is developed on its own branch created from develop, named using its WBS ID (for example: wp-4.1-git-repository, wp-4.2-django-mysql-setup).
   - Direct pushes to main and develop are blocked by branch protection rules.

3. Commit Standards
   - All commit messages are written in the imperative mood (for example: Add CI workflow for WP 4.1, Configure MySQL database settings).

4. Issues and Pull Requests
   - Every Work Package is tracked via a GitHub Issue.
   - All merges into develop or main require a Pull Request linked to its corresponding issue (for example: Closes 1) and peer review before merging.

5. Security and Hygiene
   - Virtual environments (venv/), .env files, database credentials, and SECRET_KEY values are never committed to Git.


CONTINUOUS INTEGRATION (CI)
---------------------------

Every push and pull request targeting main or develop triggers the GitHub Actions CI workflow (.github/workflows/ci.yml), which automatically:
1. Checks out the repository code.
2. Sets up Python 3.12.
3. Installs dependencies from requirements.txt (once added).
4. Runs python manage.py check to catch configuration or syntax issues before code is merged.


LOCAL DEVELOPMENT SETUP
-----------------------

Note: Full Django application files and requirements.txt will be added in Work Package 4.2.

1. Clone the repository:
   git clone https://github.com/MYSTRINGLE/POS-AND-INVENTORY-SYSTEM-PROJECT.git
   cd POS-AND-INVENTORY-SYSTEM-PROJECT

2. Create and activate a virtual environment:
   - Windows (Git Bash):
     python -m venv venv
     source venv/Scripts/activate
   - macOS / Linux:
     python3 -m venv venv
     source venv/bin/activate

3. Install dependencies (once requirements.txt is available in WP 4.2):
   pip install --upgrade pip
   pip install -r requirements.txt

4. Configure environment variables:
   Copy .env.example to .env and fill in your local MySQL credentials and Django secret key.

5. Apply database migrations and start the development server:
   python manage.py migrate
   python manage.py runserver


ENVIRONMENT VARIABLES
---------------------

When .env is configured in WP 4.2, the application expects the following variables:

- SECRET_KEY: Django cryptographic secret key (example: your-secret-key-here)
- DEBUG: Enable or disable debug mode (example: True)
- DB_NAME: MySQL database name (example: pos_inventory_db)
- DB_USER: MySQL database username (example: root)
- DB_PASSWORD: MySQL database password (example: your-password)
- DB_HOST: MySQL server host (example: 127.0.0.1)
- DB_PORT: MySQL server port (example: 3306)


WORK PACKAGE ROADMAP
--------------------

- [x] WP 4.1 - Git Repository and CI Setup: Initialize repository, configure main and develop branches, add .gitignore, set up GitHub Actions CI workflow, document workflow in README.md, and open PR for review.
- [ ] WP 4.2 - Django Project and MySQL Setup: Initialize Django 5 project, configure MySQL database connection via environment variables, create .env.example and requirements.txt, and run initial migrations.
- [ ] WP 4.3+ - Core Domain Models, POS Checkout and Reporting: Implement inventory models, POS cart and checkout logic, role-based authentication, and sales reporting.


TEAM AND COLLABORATION
----------------------

- Developer: MYSTRINGLE (Repository architecture, Django backend, MySQL integration, and frontend templates)
- Collaborator / Reviewer: osijeff (Pull Request reviews, code quality verification, and merge approvals)