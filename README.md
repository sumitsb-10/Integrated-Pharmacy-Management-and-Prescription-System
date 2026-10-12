# Integrated-Pharmacy-Management-and-Prescription-System

1. Inventory management
Manually add and search for medicines by name.
Record batch number, expiry date, quantity and purchase price.
Update stock when purchases and sales are recorded.
Show low-stock and expiry alerts.
2. Billing and daily sales
Type a medicine name to add it to the bill.
Enter quantity and price.
Calculate the total and generate a printable invoice.
Track today's sales, products sold, and cancelled or returned bills.
3. Supplier and purchase records
Manually enter the supplier's name.
Record the products delivered, quantities, unit costs and total purchase cost.
Save the date and supplier invoice/reference number.
Update stock from the accepted quantities.
View purchase history by supplier or month.
4. Monthly financial reports
Calculate monthly sales and purchase totals.
Estimate cost of goods sold and gross profit.
Account for supported expenses and adjustments.
Show estimated taxable income and tax under a clearly defined tax model.
5. Prescription records
Upload the original prescription photograph.
Manually enter patient name, doctor name and relevant dates.
Search by patient, doctor or date.
Open the original image without AI interpreting the medicines.
6. Dashboard and history
Today's sales.
Monthly revenue and profit estimates.
Total purchases.
Current inventory value.
Recent prescriptions and purchase records.
The main rule: enter data once, then let the application use it everywhere. A recorded sale should update inventory and sales reports; a recorded purchase should update inventory and purchase reports. Avoid manually entering the same transaction into multiple modules.
Technology stack — keep it simple
Part Technology Purpose
Frontend HTML, CSS, JavaScript, Bootstrap Forms, dashboard, billing and search
Backend Python + Django Business logic, calculations, login and permissions
Database PostgreSQL Store all application records
Prescription images Local protected storage initially Store uploaded images; save their file paths in PostgreSQL
PDF invoices ReportLab Print or export invoices
Development VS Code, Git Write code and manage versions
3. The hardest part: monthly tax and profit
There is an important correction to your proposed tax feature.
Tax is not generally calculated as a flat percentage of one month's net profit. In India, income tax depends on the taxpayer's legal structure, annual taxable income, applicable tax regime, allowable deductions and other rules. Advance tax, where applicable, is also based on estimated tax liability for the financial year. 
For your application, separate these three concepts:
Sales revenue: Money earned from sales.
Net profit estimate: Revenue minus the cost of goods sold and relevant expenses.
Estimated income tax: An estimate based on the applicable annual tax calculation, not simply a percentage of monthly profit.
For example, if a pharmacy sells ₹1,00,000 worth of goods in a month and those goods cost ₹75,000, the gross profit is ₹25,000. If operating expenses are ₹10,000, the simplified profit estimate is ₹15,000 before other accounting adjustments.
That ₹15,000 is not automatically the amount on which you can calculate the final tax bill by applying an arbitrary rate.Your application can show monthly profit and use accumulated financial-year figures to estimate tax. The final calculation should be verified against the applicable tax rules and the owner's business structure.
For a college demonstration, build:
Monthly sales and purchase reports.
Cost-of-goods-sold and expense tracking.
Monthly profit estimates.
Financial-year tax estimation with a clearly specified tax model.
An explanatory note that the output is an estimate, not a filed return or professional tax advice.
Don't mix income tax with GST: they are different tax systems. Your revised project can focus on monthly profit and estimated income tax, without claiming to file GST returns or income-tax returns automatically.
