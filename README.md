# Bank Account SMS Notifier

A simple Python simulation of a bank account that sends SMS notifications for deposits and withdrawals using the [Twilio](https://www.twilio.com/) API. Includes a custom exception class for handling invalid account operations.

## Features

- Deposit and withdraw funds from a simulated bank account
- Custom `InvalidAccountError` exception for invalid operations (e.g. insufficient funds, non-positive deposits)
- Automatic SMS notifications for successful transactions and errors via Twilio
- Basic error handling using `try` / `except` / `finally`

## Requirements

- Python 3.7+
- [`twilio`](https://pypi.org/project/twilio/) Python package

Install dependencies:

```bash
pip install twilio
```

## Setup

1. Sign up for a [Twilio account](https://www.twilio.com/try-twilio) and get:
   - Account SID
   - Auth Token
   - A Twilio phone number (with country code, e.g. `+1XXXXXXXXXX`)

2. Update the `BankAccount` class with your credentials:

```python
self.account_sid = 'your_account_sid'
self.auth_token = 'your_auth_token'
self.twilio_number = '+1XXXXXXXXXX'
```

3. Set the recipient phone number when creating a `BankAccount` instance (must be in E.164 format, e.g. `+91XXXXXXXXXX`).

## Usage

Run the script:

```bash
python bank_account.py
```

You'll be prompted to enter a withdrawal amount and a deposit amount. The account balance updates accordingly, and an SMS is sent confirming the result (or explaining why the operation failed).

### Example

```python
account = BankAccount("U0998XXXXXX97", 10000, "+91XXXXXXXXXX")
account.withdraw(2000)   # Sends SMS: "Withdrawal of ₹2000.00 successful..."
account.deposit(500)     # Sends SMS: "Deposit of ₹500.00 successful..."
```

## Code Structure

| Component | Description |
|---|---|
| `InvalidAccountError` | Custom exception raised for invalid withdrawal/deposit amounts |
| `BankAccount.__init__` | Initializes account details and Twilio client |
| `BankAccount.send_sms` | Sends an SMS via Twilio |
| `BankAccount.withdraw` | Withdraws funds if sufficient balance is available |
| `BankAccount.deposit` | Deposits funds if the amount is positive |




## License

MIT License — feel free to use and modify.
