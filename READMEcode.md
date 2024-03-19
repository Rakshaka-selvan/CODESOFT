class ContactBook:
    def __init__(self):
        self.contacts = {}

    def add_contact(self, name, phone_number, email, address):
        self.contacts[name] = {'Phone_number': phone_number, 'Email': email, 'Address': address}
        print("Your Contact has been added successfully !")

    def view_contact_list(self):
        if self.contacts:
            print("Contact List:")
            for name, details in self.contacts.items():
                print(f"Name: {name}, Phone: {details['Phone_number']}, Email: {details['Email']}, Address: {details['Address']}")
        else:
            print("Contact list is empty.")

    def search_contact(self, search_key):
        if search_key in self.contacts or search_key in [details['Phone_number'] for details in self.contacts.values()]:
            print("Contact found:")
            if search_key in self.contacts:
                print(f"Name: {search_key}, Phone: {self.contacts[search_key]['Phone_number']}")
            else:
                for name, details in self.contacts.items():
                    if details['Phone_number'] == search_key:
                        print(f"Name: {name}, Phone: {search_key}")
        else:
            print("Contact not found.")

    def update_contact(self, name, new_phone_number, new_email, new_address):
        if name in self.contacts:
            self.contacts[name]['Phone_number'] = new_phone_number
            self.contacts[name]['Email'] = new_email
            self.contacts[name]['Address'] = new_address
            print("Contact updated successfully.")
        else:
            print("Contact not found.")

    def delete_contact(self, name):
        if name in self.contacts:
            del self.contacts[name]
            print("Contact deleted successfully.")
        else:
            print("Contact not found.")


def main():
    contact_book = ContactBook()
    while True:
        print("\nContact Book Menu:")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            name = input("Enter name: ")
            phone_number = input("Enter phone number: ")
            email = input("Enter email: ")
            address = input("Enter address: ")
            contact_book.add_contact(name, phone_number, email, address)
        elif choice == '2':
            contact_book.view_contact_list()
        elif choice == '3':
            search_key = input("Enter name or phone number to search: ")
            contact_book.search_contact(search_key)
        elif choice == '4':
            name = input("Enter name of contact to update: ")
            new_phone_number = input("Enter new phone number: ")
            new_email = input("Enter new email: ")
            new_address = input("Enter new address: ")
            contact_book.update_contact(name, new_phone_number, new_email, new_address)
        elif choice == '5':
            name = input("Enter name of contact to delete: ")
            contact_book.delete_contact(name)
        elif choice == '6':
            print("Exiting from the contact list..............")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 6.")


if __name__ == "__main__":
    main()
