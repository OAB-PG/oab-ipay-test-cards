# OAB iPay Payment Gateway – Test Cards

## Overview

This repository maintains the test card details and configured host response codes for the **Oman Arab Bank (OAB) iPay Payment Gateway**.

The purpose of this repository is to provide a centralized reference for developers, QA testers, integration partners, and support teams to validate different payment transaction scenarios.

## Test Card Summary

| Card Brand | Number of Cards |
|---|---:|
| Mastercard | 7 |
| Visa | 13 |
| **Total** | **20** |

## 1. Mastercard Test Cards

| No. | Card Number | Response Code | Expected Response |
|---|---|---|---|
| 1 | `5105105105105119` | 00 | Approved |
| 2 | `5204242424242420` | 00 | Approved |
| 3 | `5186001700008785` | 05 | Do not honor transaction |
| 4 | `5186001700009726` | 14 | Invalid account - retry |
| 5 | `5120350100064537` | 33 | Card expired, capture card |
| 6 | `5186001700008876` | 41 | Lost Card - Capture |
| 7 | `5120350100064545` | 12 | Invalid transaction - retry |

## 2. Visa Test Cards

| No. | Card Number | Response Code | Expected Response |
|---|---|---|---|
| 1 | `4012001037490006` | 00 | Approved |
| 2 | `4111111111111111` | 00 | Approved |
| 3 | `4242424242424242` | 00 | Approved |
| 4 | `4000000000003220` | 00 | Approved |
| 5 | `4000000000030006` | 00 | Approved |
| 6 | `4000000000049700` | 00 | Approved |
| 7 | `4622943127011048` | 61 | Cycle limit exceeded |
| 8 | `4622943127011055` | 91 | Service not available |
| 9 | `4622943127011071` | AB | Invalid CVV2 |
| 10 | `4622943127011089` | F1 | Declined by Fraud Monitoring |
| 11 | `4622943127010990` | S1 | Secure authentication required |
| 12 | `4622943127011006` | 12 | Invalid transaction - retry |
| 13 | `4622943127011014` | 30 | The message received was not within standards |

## 3. Host Response Code Reference

The following response codes are used by the Payment Gateway to identify transaction results and failure reasons.

### 3.1 Standard Host Response Codes

| Code | Description |
|---|---|
| 00 | Approved |
| 01 | Call issuer |
| 03 | Invalid Merchant ID |
| 04 | Invalid card, capture |
| 05 | Do not honor transaction |
| 08 | Approve with identification |
| 12 | Invalid transaction - retry |
| 13 | Cannot process amount |
| 14 | Invalid account - retry |
| 15 | The card is already active |
| 30 | The message received was not within standards |
| 31 | Issuer inoperative |
| 33 | Card expired, capture card |
| 36 | Account restricted, capture card |
| 37 | Call Security - Capture |
| 41 | Lost Card - Capture |
| 43 | Stolen Card - Capture |
| 51 | Insufficient funds - retry |
| 55 | Incorrect PIN, foreign |
| 57 | Not permitted |
| 61 | Cycle limit exceeded |
| 62 | Bad card |
| 65 | Limit reached for total number of transactions in cycle |
| 68 | Timer time out |

### 3.2 Additional Host Response Codes

| Code | Description |
|---|---|
| 75 | Excessive PIN failures |
| 76 | Wrong PIN, excessive PIN failures |
| 77 | The card has no accounts |
| 78 | Original transaction could not be found |
| 90 | Response status unknown |
| 91 | Service not available |
| 92 | Invalid Payment Parameter |
| 93 | Service blocked |
| 94 | Duplicate transmission |
| 95 | Reconciliation error |
| 96 | System Malfunction |
| 97 | Service not allowed for client |
| 98 | Invalid insurance number |

### 3.3 Service and Authentication Response Codes

| Code | Description |
|---|---|
| A1 | Service is already binded |
| A2 | Service is not binded |
| A3 | Invalid service data |
| A4 | MAC error |
| A5 | Debts absence |
| A6 | Invalid payment data |
| A7 | Additional information required |
| A8 | No such object in system |
| A9 | Object is not created in system |
| AA | Object is already created in system |
| AB | Invalid CVV2 |
| AC | Invalid Password |
| AD | Card is restricted |
| AE | Postcheck timeout |
| AF | Advice is rejected |
| AG | Payment execution delayed |
| AH | Incorrect customer_id or cardholder_id |
| AI | Biometric authentication failed - fingerprint does not exist |
| AK | Biometric authentication failed - invalid finger template type |
| AL | OTP code was not found or is invalid |
| AM | OTP code was already used |
| AN | OTP code has expired |

### 3.4 Fraud, Recurring Payment and Security Response Codes

| Code | Description |
|---|---|
| F1 | Declined by Fraud Monitoring |
| R0 | Stop a specific payment |
| R1 | Revoke authorization for further payments |
| R3 | Cancel all recurring payments for the card number in the request |
| S1 | Secure authentication required |

### 3.5 Unknown Response Codes

If the Payment Gateway receives an unrecognized response code, the default description is:

**Unknown result code**

## 4. Testing Guidelines

1. Use the test cards only in authorized test environments.
2. Select a card based on the required success or failure scenario.
3. Initiate the transaction through the OAB iPayment Payment Gateway.
4. Verify the response code returned by the configured host or simulator.
5. Validate the transaction status and error message displayed in the Payment Gateway.
6. Confirm the transaction details are correctly recorded in the payment transaction logs.

**Important:** The card-to-response mappings are documented as supplied. Actual results depend on the environment, simulator configuration, and host routing. These mappings have not been independently validated.

## 5. Security Guidelines

- Keep this repository private and accessible only to authorized teams.
- Verify that all listed card numbers are approved test data before publication or distribution.
- Do not add real customer card numbers, CVVs, PINs, credentials, or other sensitive payment data.
- Do not use these test cards against a live payment processor unless explicitly authorized.

## 6. Maintenance

Update this repository whenever new test cards, host response codes, or payment testing scenarios are introduced.

**Maintained by:** OAB iPayment Payment Gateway Team

**Purpose:** Development, Integration Testing, UAT and Technical Support.
