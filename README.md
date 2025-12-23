# zion_prompt.py
import sys

# Mock data storage (replace with real DB later)
organizations = []
accounts = []
journal_entries = []
employees = []
assets = []
taxes = []

def main_menu():
    print("\n=== ZION FINANCIAL CONSULTANT ===")
    print("1. Organizations")
    print("2. Bookkeeping / Journal Entries")
    print("3. Payroll")
    print("4. Assets")
    print("5. Taxes")
    print("6. Reports")
    print("0. Exit")

    choice = input("Select option: ")
    if choice == "1":
        organization_menu()
    elif choice == "2":
        bookkeeping_menu()
    elif choice == "3":
        payroll_menu()
    elif choice == "4":
        assets_menu()
    elif choice == "5":
        taxes_menu()
    elif choice == "6":
        reports_menu()
    elif choice == "0":
        sys.exit()
    else:
        print("Invalid option.")
        main_menu()

# ===== Organizations =====
def organization_menu():
    print("\n--- Organizations ---")
    print("1. Add Organization")
    print("2. View Organizations")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        name = input("Organization Name: ")
        organizations.append({"name": name})
        print(f"Organization '{name}' added.")
    elif choice == "2":
        for idx, org in enumerate(organizations):
            print(f"{idx+1}. {org['name']}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    organization_menu()

# ===== Bookkeeping =====
def bookkeeping_menu():
    print("\n--- Bookkeeping / Journal Entries ---")
    print("1. Add Journal Entry")
    print("2. View Journal Entries")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        date = input("Date (YYYY-MM-DD): ")
        description = input("Description: ")
        debit = float(input("Debit Amount: "))
        credit = float(input("Credit Amount: "))
        journal_entries.append({
            "date": date,
            "description": description,
            "debit": debit,
            "credit": credit
        })
        print("Journal entry added.")
    elif choice == "2":
        for idx, entry in enumerate(journal_entries):
            print(f"{idx+1}. {entry['date']} | {entry['description']} | Debit: {entry['debit']} | Credit: {entry['credit']}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    bookkeeping_menu()

# ===== Payroll =====
def payroll_menu():
    print("\n--- Payroll ---")
    print("1. Add Employee")
    print("2. Run Payroll")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        name = input("Employee Name: ")
        salary = float(input("Monthly Salary: "))
        employees.append({"name": name, "salary": salary})
        print(f"Employee '{name}' added.")
    elif choice == "2":
        for emp in employees:
            print(f"{emp['name']} - Net Pay: {emp['salary']}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    payroll_menu()

# ===== Assets =====
def assets_menu():
    print("\n--- Assets ---")
    print("1. Add Asset")
    print("2. View Assets")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        name = input("Asset Name: ")
        value = float(input("Asset Value: "))
        assets.append({"name": name, "value": value})
        print(f"Asset '{name}' added.")
    elif choice == "2":
        for idx, asset in enumerate(assets):
            print(f"{idx+1}. {asset['name']} - Value: {asset['value']}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    assets_menu()

# ===== Taxes =====
def taxes_menu():
    print("\n--- Taxes ---")
    print("1. Add Tax Record")
    print("2. View Tax Records")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        tax_type = input("Tax Type (VAT/PAYE/WHT): ")
        amount = float(input("Amount: "))
        taxes.append({"type": tax_type, "amount": amount})
        print(f"{tax_type} tax of {amount} added.")
    elif choice == "2":
        for idx, tax in enumerate(taxes):
            print(f"{idx+1}. {tax['type']} - Amount: {tax['amount']}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    taxes_menu()

# ===== Reports =====
def reports_menu():
    print("\n--- Reports ---")
    print("1. Total Payroll")
    print("2. Total Assets")
    print("3. Total Taxes")
    print("0. Back")
    choice = input("Select option: ")
    if choice == "1":
        total_payroll = sum(emp['salary'] for emp in employees)
        print(f"Total Payroll: {total_payroll}")
    elif choice == "2":
        total_assets = sum(asset['value'] for asset in assets)
        print(f"Total Assets: {total_assets}")
    elif choice == "3":
        total_taxes = sum(tax['amount'] for tax in taxes)
        print(f"Total Taxes: {total_taxes}")
    elif choice == "0":
        main_menu()
    else:
        print("Invalid option.")
    reports_menu()

# ===== Start =====
if __name__ == "__main__":
    main_menu()
