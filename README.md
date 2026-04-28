# PROG_Assignment_Haja-Jenabu-Bah_905006101
# Clinic Queue Management System
# Purpose: Manages patient check-ins and queue priority

# Constants
CLINIC_NAME = "Community Health Clinic"

def display_welcome():
    """Function 1: Displays the header and greeting"""
    print("-" * 30)
    print(f"WELCOME TO {CLINIC_NAME.upper()}")
    print("Supporting SDG 3: Good Health and Well-being")
    print("-" * 30)

def process_patient(count):
    """Function 2: Handles data input and logic for a single patient"""
    print(f"\nRegistering Patient #{count}")
    name = input("Enter Patient Name: ")
    
    try:
        age = int(input("Enter Patient Age: "))
    except ValueError:
        print("Invalid age. Defaulting to 0.")
        age = 0
        
    # Decision Structure (Logic)
    if age >= 60:
        category = "Priority (Senior Citizen)"
    elif age <= 12:
        category = "Priority (Pediatric)"
    else:
        category = "Standard"
        
    return name, age, category

def main():
    display_welcome()
    
    patient_records = []
    patient_count = 1
    
    # Loop for multiple records
    while True:
        name, age, category = process_patient(patient_count)
        
        # Store record in a list (Data Types)
        patient_records.append({
            "id": patient_count,
            "name": name,
            "age": age,
            "cat": category
        })
        
        patient_count += 1
        
        cont = input("\nAdd another patient? (yes/no): ").lower()
        if cont != 'yes':
            break

    # Final Output (Clear and Formatted)
    print("\n" + "="*40)
    print("DAILY PATIENT QUEUE SUMMARY")
    print("="*40)
    print(f"{'ID':<5} {'Name':<20} {'Age':<5} {'Category'}")
    print("-" * 40)
    
    for p in patient_records:
        print(f"{p['id']:<5} {p['name']:<20} {p['age']:<5} {p['cat']}")
    
    print("-" * 40)
    print(f"Total Patients Processed: {len(patient_records)}")
    print("Keep this log for hardcopy submission.")

if __name__ == "__main__":
    main()
