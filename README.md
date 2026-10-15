# TRAIN TICKET BOOKING APPLICATION

## Overview
The **Train Ticket Booking Application** is a menu-driven, console-based application developed in C. It allows users to register, log in, view available trains, reserve tickets, cancel bookings, and view their active booking details.

The application uses linked lists for data management and file handling to store and retrieve records between program executions. It also provides an admin option to add new trains.

## Project Structure

```text
MINI/
├── funcall.h       # Function declarations
├── struct.h        # Structure definitions
├── main.c          # Main program and initial menu
├── input.c         # Integer input function
├── signup.c        # New user registration
├── signin.c        # User login
├── password.c      # Password validation
├── menu.c          # Menu displayed after login
├── train.c         # Train listing, searching and admin train addition
├── date_check.c    # Journey date validation
├── reserve.c       # Ticket reservation
├── cancel.c        # Ticket cancellation
├── booking.c       # Displays active booking details
├── save.c          # Saves train, passenger and cancellation data
├── sync.c          # Loads previously saved data at startup
├── free.c          # Frees dynamically allocated linked-list memory
└── Makefile        # Build configuration
```

## Features

- **User Registration:** Create a new account using a username and password.
- **User Login:** Authenticate registered users.
- **Password Validation:** Enforce password complexity requirements.
- **Train Listing:** View available trains and their routes.
- **Train Search:** Search for trains using the application's supported search options.
- **Admin Train Addition:** Add new trains through the admin account.
- **Ticket Reservation:** Reserve seats for a valid journey date.
- **Ticket Cancellation:** Cancel an existing reservation using the train number, journey date and seat number.
- **Booking Details:** View active ticket reservations.
- **Data Persistence:** Save user, train, passenger and cancellation records in text files.
- **Linked-List Management:** Manage dynamically allocated data and release memory when it is no longer required.

## Technologies Used

- **Programming Language:** C
- **Data Structures:** Structures and linked lists
- **File Handling:** Text files for persistent storage
- **Build Tool:** GNU Make
- **Development Environment:** GCC-compatible C compiler and terminal

## Compilation

1. Open a terminal.
2. Navigate to the `MINI` directory.
3. Compile the application using:

```bash
make
```

## Execution

Run the compiled application from the project directory:

```bash
./a.out
```

## Clean Build Files

To remove the compiled executable and other generated files configured in the Makefile, run:

```bash
make clean
```

## Default Train Information

The application creates the following default trains on the first run.

| Train Number | Train Name | Source | Destination | Seats |
|---|---|---|---|---:|
| 101 | Chennai_Express | Nellore | Chennai | 20 |
| 102 | Godavari_Express | Hyderabad | Vijayawada | 20 |
| 103 | Vande_Bharat | Nellore | Hyderabad | 20 |

## User Registration and Password Rules

Users must sign up with a username and password before logging in.

Passwords must satisfy the following conditions:

- At least 8 characters long.
- Include at least one uppercase letter.
- Include at least one lowercase letter.
- Include at least one numeric digit.
- Include at least one special character.

## Admin Functionality

To access the **Add Train** option, sign up using the username:

```text
TRAIN_ADMIN
```

The application requires train numbers and train names to be unique.

**Naming convention:** Enter train names, source stations and destination stations without spaces. Use underscores (`_`) to represent spaces.

Examples:

- `Chennai_Express`
- `New_Delhi`
- `Bangalore_City`

> Note: The admin role is assigned based on the username in this project. This is a learning implementation, not a secure role-based authentication system.

## Journey Date Rules

The application accepts journey dates only for:

- Today
- Tomorrow
- The day after tomorrow

Use the following date format:

```text
DD-MM-YYYY
```

Example:

```text
15-10-2026
```

## Ticket Cancellation

To cancel a ticket, provide:

1. Train number
2. Journey date
3. Seat number

When a cancellation is processed, the booking is removed from `passengers_info.txt`, so it no longer appears in the active booking details. A cancellation record is appended to `cancelled_info.txt`.

This allows the application to maintain a separate history of cancelled reservations.

## Data Storage and Persistence

The application automatically creates and uses the following text files:

| File | Purpose |
|---|---|
| `trains_info.txt` | Stores train information |
| `passengers_info.txt` | Stores passenger and active booking information |
| `usr_logins.txt` | Stores registered user login information |
| `cancelled_info.txt` | Stores cancellation history |

The `sync.c` module reads previously saved information when the program starts, while the `save.c` module handles saving application data.

**Important:** Keep these text files in the same directory as the executable. Do not delete them if you want to retain previously saved records.

## Application Workflow

1. Start the application.
2. Sign up or log in.
3. Access the menu displayed after login.
4. View or search for trains.
5. Reserve a ticket for a valid journey date.
6. View active booking details or cancel an existing reservation.
7. Exit the application. Saved records can be loaded during the next execution.





