# Integrated Pharmacy Management and Prescription System

A web-based pharmacy management application designed to simplify the daily operations of local medical stores by integrating inventory management, billing, sales tracking, supplier purchase records, monthly financial reporting, and digital prescription storage.

## Project Overview

Local pharmacies handle multiple operational tasks every day, including maintaining medicine stock, generating customer bills, recording supplier purchases, calculating monthly profits, and storing patient prescriptions.

Managing these activities across separate registers, files, or applications can make it difficult to retrieve records, track stock accurately, and prepare financial reports.

The **Integrated Pharmacy Management and Prescription System** aims to centralize these operations in a single application, providing a structured way to record, manage, search, and report pharmacy data.

A key feature of the project is prescription management, which allows authorized users to upload and retrieve original prescription images using patient and doctor information without relying on AI to interpret handwritten prescriptions.

## Objectives

- Centralize pharmacy inventory and transaction records.
- Simplify medicine search and stock management.
- Generate bills and maintain daily sales records.
- Record supplier purchases, quantities, and costs.
- Calculate monthly sales, expenses, and profit estimates.
- Provide configurable tax estimation based on verified tax rules.
- Store and retrieve prescription images using searchable metadata.
- Maintain reliable, secure, and organized pharmacy records.

## Features

### 1. Inventory Management

- Add, edit, view, and search medicine records.
- Record product names, manufacturers, and other relevant details.
- Track batches, expiry dates, purchase costs, and available quantities.
- Identify low-stock and expired or near-expiry batches.
- Update stock when purchases and sales are recorded.

### 2. Billing and Sales Management

- Search for medicines by typing their names.
- Add multiple products to a bill.
- Enter quantities and calculate line totals and invoice totals.
- Generate printable invoices.
- Record completed sales and payment information.
- Track daily sales, sold products, and transaction history.
- Support controlled handling of returns and cancellations.

### 3. Supplier and Purchase Management

- Add and manage supplier details.
- Manually record supplier purchases and received products.
- Record purchase dates, supplier invoice references, quantities, and unit costs.
- Calculate purchase totals.
- Update inventory when purchases are confirmed.
- View purchase history by supplier and date.

This module records completed purchases and received goods. Automatic delivery scheduling and live delivery tracking are outside the initial scope.

### 4. Monthly Financial Reports and Tax Estimation

- Generate daily and monthly sales summaries.
- Track purchase costs and operating expenses.
- Estimate cost of goods sold and gross profit.
- Calculate simplified operating profit estimates.
- Summarize financial-year figures.
- Provide configurable tax estimates based on a defined and verified tax model.

Tax estimation will be separated from ordinary monthly profit calculations. Actual tax liability depends on the applicable rules and the pharmacy owner's business structure. Automated tax-return filing is not part of the initial scope.

### 5. Prescription Management

- Upload and store original prescription images.
- Record patient information and doctor details.
- Store prescription dates and upload timestamps.
- Search prescriptions by patient name, doctor, date, or prescription ID.
- Optionally associate prescriptions with relevant sales or invoices.
- Restrict access to authorized users.
- Maintain relevant record-change and access logs.

The application will not automatically interpret handwritten prescriptions or determine which medicines have been prescribed. The original uploaded image remains the source of truth.

### 6. Dashboard and Reporting

The dashboard is intended to provide an overview of:

- Today's sales and number of bills.
- Products sold and quantities.
- Current stock and low-stock products.
- Expired and near-expiry batches.
- Supplier purchase history.
- Monthly revenue and profit estimates.
- Recently uploaded prescriptions.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend programming language |
| Django | Web framework, application logic, authentication, and database integration |
| PostgreSQL | Relational database |
| HTML5 | Page structure |
| CSS3 | Styling and layout |
| JavaScript | Interactive frontend behavior |
| Bootstrap | Responsive user interface |
| Pillow | Prescription image validation and processing |
| ReportLab | PDF invoice and report generation |
| Git and GitHub | Version control and collaboration |
| Visual Studio Code | Development environment |

## Planned Architecture

The application will use a modular Django architecture.

- **Accounts:** Authentication, user roles, and permissions.
- **Inventory:** Products, batches, stock levels, and expiry tracking.
- **Billing:** Invoices, invoice items, payments, and sales.
- **Suppliers:** Supplier information and purchase records.
- **Prescriptions:** Prescription metadata and protected image storage.
- **Reports:** Daily sales, monthly financial summaries, and tax estimates.
- **Audit:** Relevant record changes and activity history.

PostgreSQL will serve as the central database. Uploaded prescription images will be stored in protected file storage, with their metadata and storage references maintained in the database.

## Development Roadmap

The project will be developed incrementally:

1. Set up the development environment and Django project.
2. Design the database schema and configure PostgreSQL.
3. Implement product and inventory management.
4. Implement supplier and purchase records.
5. Implement billing, invoices, and daily sales tracking.
6. Implement prescription uploads, metadata, and search.
7. Implement financial reports and tax estimation.
8. Build the integrated dashboard.
9. Test stock updates, calculations, permissions, and record consistency.
10. Document the application and prepare the final demonstration.

## Installation and Setup

### Prerequisites

Install the following:

- Python 3.11 or a compatible supported version.
- PostgreSQL.
- Git.
- Visual Studio Code or another code editor.

### 1. Clone the repository

If you have not already cloned it:

```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Create and activate a virtual environment

**Windows PowerShell**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**Linux or macOS**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

Once the project's `requirements.txt` file has been created:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure the database

Create a PostgreSQL database and a dedicated database user. Configure the connection through environment variables or a local environment file that is excluded from version control.

Do not commit database passwords, secret keys, or other credentials to Git.

### 5. Apply migrations

After the Django project and database models have been configured:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create an administrator account

```bash
python manage.py createsuperuser
```

### 7. Start the development server

```bash
python manage.py runserver
```

Open the local development address displayed in the terminal, usually:

`http://127.0.0.1:8000/`

**Note:** The initial Django project and `inventory` app are set up. PostgreSQL configuration and the remaining application modules are planned for later steps.

## Testing Strategy

The application will be tested at both module and workflow levels.

Key scenarios include:

- Recording a purchase updates inventory exactly once.
- A completed sale deducts the correct quantity from the correct batch.
- Insufficient or expired stock is handled according to the application's rules.
- Invoice totals match saved transaction records.
- Returns and cancellations do not create duplicate stock adjustments.
- Monthly financial calculations match independently verified examples.
- Prescription searches return the correct records.
- Unauthorized users cannot access restricted prescription images.
- Invalid inputs and failed transactions do not corrupt stored data.

## Security and Data Protection

Prescription records contain sensitive personal information. The implementation will therefore aim to include:

- Authenticated access and role-based permissions.
- Server-side validation of user input.
- Validation and size limits for uploaded images.
- Protected prescription file storage.
- Secure handling of application secrets.
- Database backups and recovery procedures.
- Appropriate record-retention and access-control policies.

Real patient data should not be used for development or demonstration without appropriate authorization and safeguards.

## Project Scope and Limitations

The initial version focuses on pharmacy operations and record management. The following are not planned for the initial release:

- Barcode scanner integration.
- AI-based prescription interpretation.
- Automatic medicine recommendations.
- Live delivery vehicle tracking.
- Automated tax-return filing.
- Integration with existing commercial pharmacy software.

These features may be evaluated later if the project requirements change.

## Expected Outcome

The intended outcome is a functioning, integrated pharmacy management application that enables a local medical store to manage inventory, record purchases and sales, generate invoices, prepare monthly financial reports, and securely retrieve prescription records from one system.

The project will be evaluated on functional correctness, database design, integration between modules, usability, data protection, and reliability.

## Project Status

**Status:** In development

Features listed in this README represent the planned scope and should not be considered implemented until completed and tested.

## License

License to be determined.
