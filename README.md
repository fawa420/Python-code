item_codes = ["A1", "A2", "B1", "B2", "B3", "C1", "C2", "D1", "D2", "E1", "E2", "E3", "F1", "F2", "G1", "G2"]
descriptions = ["Compact", "Tower", "8 GB", "16 GB", "32 GB", "1 TB HDD", "2 TB HDD", "240 GB SSD", "480 GB SSD", "1 TB HDD", "2 TB HDD", "4 TB HDD", "DVD/Blu-Ray Player", "DVD/Blu-Ray Re-writer", "Standard Version", "Professional Version"]
prices = [75.00, 150.00, 79.99, 149.99, 299.99, 49.99, 89.99, 59.99, 119.99, 49.99, 89.99, 129.99, 50.00, 100.00, 100.00, 175.00]
def show_available_items():
    print("Available Items:")
    print("Item Code  Description              Price ($)")
    for i in range(len(item_codes)):
        print(f"{item_codes[i]:<10} {descriptions[i]:<24} ${prices[i]:.2f}")
chosen_components = []
def choose_components():
    show_available_items()
    chosen_case = input("Select a case (Enter item code A1 or A2): ")
    if chosen_case not in item_codes[:2]:
        print("Invalid choice for the case.")
        return
    chosen_components.append(descriptions[item_codes.index(chosen_case)])
    chosen_ram = input("Select RAM (Enter item code B1, B2, or B3): ")
    if chosen_ram not in item_codes[2:5]:
        print("Invalid choice for RAM.")
        return
    chosen_components.append(descriptions[item_codes.index(chosen_ram)])
    chosen_hdd = input("Select Main Hard Disk Drive (Enter item code C1 or C2): ")
    if chosen_hdd not in item_codes[5:7]:
        print("Invalid choice for Main Hard Disk Drive.")
        return
    chosen_components.append(descriptions[item_codes.index(chosen_hdd)])
    total_price = 200 + prices[item_codes.index(chosen_case)] + prices[item_codes.index(chosen_ram)] + prices[item_codes.index(chosen_hdd)]
    additional_items = 0
    while True:
        another_choice = input("Do you want to select other components? (yes/no): ")
        if another_choice.lower() != "yes":
            break
        print("Select a component:")
        for i in range(len(item_codes)):
            print(f"{item_codes[i]} {descriptions[i]} (${prices[i]:.2f})")
        chosen_component = input("Enter item code of the component you want: ")
        if chosen_component not in item_codes:
            print("Invalid choice for the selected component.")
            continue
        chosen_components.append(descriptions[item_codes.index(chosen_component)])
        total_price += prices[item_codes.index(chosen_component)]
        additional_items += 1
    discount = 0
    if additional_items == 1:
        discount = 0.05  
    elif additional_items >= 2:
        discount = 0.10  # 
    discount_amount = total_price * discount
    total_price_after_discount = total_price - discount_amount
    print(f"Total Price Before Discount: ${total_price:.2f}")
    print(f"Chosen Components:")
    for component in chosen_components:
        print(component)
    print(f"Discount Applied: {discount * 100}%")
    print(f"Amount Saved: ${discount_amount:.2f}")
    print(f"New Price After Discount: ${total_price_after_discount:.2f}")
choose_components()
    
