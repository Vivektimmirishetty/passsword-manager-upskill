# Password Manager Using Tkinter

Project Overview
Welcome to the Secure Password Manager project! This application provides a secure and convenient way to manage your passwords using a master password. Built with Python and Tkinter, this project offers features such as password generation, storage, and encryption.

Features
Master Password Protection: Secure access to all stored passwords with a master password.
Password Generation: Generate strong and secure passwords with ease.
Password Storage: Store and manage multiple passwords securely.
Password Encryption: Encrypt passwords before storing them in the database.
Clipboard Copy: Copy passwords to the clipboard for quick and easy use.
User-friendly Interface: Intuitive and easy-to-use graphical interface.
Components
Tkinter: For creating the graphical user interface.
SQLite: For storing master passwords and user credentials securely.
Hashlib: For password encryption.
Python Standard Libraries: For additional functionalities and handling.
Installation
Clone the Repository:

bash
Copy code
git clone https://github.com/yourusername/secure-password-manager.git
cd secure-password-manager
Install Required Libraries:
Ensure you have Python installed. Then, install the required libraries:

bash
Copy code
pip install tk
Usage
Running the Application:

Execute the main script to start the application:
bash
Copy code
python3 password_manager.py
Initial Setup:

If you are a new user, you will be prompted to create a master password. Enter and confirm your master password to proceed.
Login:

Existing users can log in using their master password.
Password Vault:

After logging in, you can add, update, delete, and copy passwords. You can also generate new passwords using the built-in password generator.
Code Explanation
password_manager.py
The main script (password_manager.py) includes the following functionalities:

Initialization:

python
Copy code
def __init__(self):
    self.db, self.cursor = init_database()
    self.window = Tk()
    self.window.update()
    self.window.title("Password Manager")
    self.window.geometry("650x350")
New User Setup:

python
Copy code
def welcome_new_user(self):
    self.window.geometry("450x200")
    # UI elements for new user setup
User Login:

python
Copy code
def login_user(self):
    for widget in self.window.winfo_children():
        widget.destroy()
    self.window.geometry("450x200")
    # UI elements for user login
Password Encryption:

python
Copy code
def encrypt_password(self, password):
    password = password.encode("utf-8")
    encoded_text = hashlib.md5(password).hexdigest()
    return encoded_text
Password Vault Screen:

python
Copy code
def password_vault_screen(self):
    for widget in self.window.winfo_children():
        widget.destroy()
    self.window.geometry("850x350")
    # UI elements for the password vault
Additional Functionalities
Save Master Password:

python
Copy code
def save_master_password(self, eb1, eb2):
    password1 = eb1.get()
    password2 = eb2.get()
    if password1 == password2:
        hashed_password = self.encrypt_password(password1)
        insert_command = """INSERT INTO master(password) VALUES(?)"""
        self.cursor.execute(insert_command, [hashed_password])
        self.db.commit()
        self.login_user()
    else:
        self.feedback.config(text="Passwords do not match", fg="red")
Check Master Password:

python
Copy code
def check_master_password(self, eb):
    hashed_password = self.encrypt_password(eb.get())
    self.cursor.execute("SELECT * FROM master WHERE id = 1 AND password = ?", [hashed_password])
    if self.cursor.fetchall():
        self.password_vault_screen()
    else:
        self.password_entry_box.delete(0, END)
        self.feedback.config(text="Incorrect password", fg="red")
Copy Text:

python
Copy code
def copy_text(self, text):
    self.window.clipboard_clear()
    self.window.clipboard_append(text)
Contribution
We welcome contributions to improve the Secure Password Manager. Feel free to fork this repository, submit issues, and send pull requests.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Happy coding and stay secure with the Secure Password Manager! For any questions or further assistance, please open an issue or contact me.

Contact
Author: Timmirishetty Vivek
Email: timmirishettyvivek@gmail.com
LinkedIn: Vivek Timmirishetty
This project aims to provide a secure and user-friendly solution for managing passwords. Your feedback and contributions are highly appreciated!
