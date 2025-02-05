---
title: Test Data
description: |
  Testing, are we? Good! Here's some data you can
  use to test and verify your integration!
menu_order: 1000
---

## Swedbank Pay Checkout Test Data

During a Swedbank Pay Checkout implementation, you can use the test data related
to the different payment instruments listed below. To see Swedbank Pay Checkout
in action, please visit our [demoshop]({{ page.front_end_url }}/pspdemoshop)

To test a checked-in user in the Demoshop, please use the following test data:

### Checkout test data for Norway

{:.table .table-striped}
| Type            | Data                         | Description                                                           |
| :-------------- | :--------------------------- | :-------------------------------------------------------------------- |
| `Email`         | `olivia.nyhuus@payex.com`    | The e-mail address of the payer.                                      |
| `Mobile number` | `+47 98765432`               | The mobile phone number of the payer. Format Norway: `+47 99999999`.  |
| `SSN`           | `{{ page.consumer_ssn_no }}` | The social security number of the payer. Format Norway: `DDMMYYXXXXX` |
| `ZipCode`       | `1642`                       | The city zip code. Format Norway: `XXXX`                              |

### Checkout test data for Sweden

{:.table .table-striped}
| Type            | Data                         | Description                                                             |
| :-------------- | :--------------------------- | :---------------------------------------------------------------------- |
| `Email`         | `leia.ahlstrom@payex.com`    | The e-mail address of the payer.                                        |
| `Mobile number` | `+46 739000001`              | The mobile phone number of the payer. Format Sweden: `+46 707777777`.   |
| `SSN`           | `{{ page.consumer_ssn_se }}` | The social security number of the payer. Format Sweden: `YYYYMMDDXXXX`. |
| `ZipCode`       | `17674`                      | The city zip code. Format Sweden: `XXXXX`                               |

### Checkout test data for Denmark

{:.table .table-striped}
| Type            | Data          | Description                                                          |
| :-------------- | :------------ | :------------------------------------------------------------------- |
| `Mobile number` | `+4522222222` | The mobile phone number of the payer. Format Denmark: `+45 22222222` |

## Credit Card Test Data

With regards to card payments, our external integration test environment is
connected to our POS system instead of a fake service. It is set up with an
internal acquirer. This gives us a production-like test environment, while also
giving us sandbox testing opportunities, such as 3-D Secure card enrollment and
error scenarios. No payment information will be sent to other acquiring
institutions.

### 3-D Secure Cards

{:.table .table-striped}
| Card type  | Card number        | Expiry                   | CVC   | Type of test data   |
| :--------- | :----------------- | :----------------------- | :-----| :------------------ |
| Visa       | `4761739001010416` | After the current month  | Any   | 3-D Secure enrolled |
| MasterCard | `5226612199533406` | After the current month  | Any   | 3-D Secure enrolled |

### 3-D Secure

For merchants using 3-D Secure (3DS1), this is the ACS (Access Control Server)
you will encounter in our test environments. Use the Visa or MasterCard listed
under 3-D Secure Cards above when doing a card payment. After pressing the
purchase button you will then be taken to a menu where you can select
Authentication status.

![3D-Secure Emulator without dropdown menu][3ds-emulator-no-dropdown]{:width="805px" :height="685px"}

![3D-Secure Emulator with dropdown menu][3ds-emulator-with-dropdown]{:width="805px" :height="685px"}

In this menu, there are a few different options to choose from. Choose the
status you want to test, click the Continue button and the status you selected
will be sent with the payment. After pressing **Continue**, you will be sent
back to the payment like a normal 3-D Secure authentication.

### OTP (3DS2)

For m©erchants using 3DS2, OTP (One-Time Password) is the ACS (Access Control
Server) you will encounter. Use the Visa or MasterCard listed under 3-D Secure
Cards above when doing a card payment. After pressing the purchase button you
will then be taken to a challenge form where you need to enter a code based
on the result you wish for. See the list of codes below the screenshot. After
pressing **Pay** you will be sent back to the payment like a normal 3-D Secure
authentication.

![OTP challenge form][otp-challenge-form]

### OTP Codes

{:.table .table-striped}
| OTP Value  | Transaction Status | Transaction Status Reason| ECI | Authentication Value|
| :--------- | :----------------- | :----------------------- | :-- | :------------------ |
| 1234       | Y                  |                          | 01  | JAmi21makAifmwqo2120cjq1AAA= |
| 1111       | N                  | 01                       | 01  |  |
| 2222       | R                  | 01                       | 01  |  |
| 3333       | U                  | 01                       | 01  |  |
| 4444       | A                  | 01                       | 01  | Qm181okmdyqh6yQmYuq1890QAAA= |

### OTP Transaction Status

{:.table .table-striped}
| Transaction Status | Transaction Status Description |
| :----------------- | :----------------------------- |
| Y                  |  Authentication / Account verification successful |
| N                  |  Not authenticated / Account not verified; Transaction denied |
| R                  |  Authentication / Account verification rejected. Issuer is rejecting authentication/verification and request that authorization not be attempted |
| U                  |  Authentication / Account verification could not be performed; technical or other problem |
| A                  |  Attempts processing performed; Not authenticated / verified, but a prood of attempt authentication / verification is provided                      |

### Visa

{:.table .table-striped}
| Card number        | Expiry                  | CVC  |
| :----------------- | :---------------------- | :--- |
| `4925000000000004` | After the current month | Any  |
| `4581097032723517` | After the current month | Any  |
| `4581099940323133` | After the current month | Any  |

### MasterCard

{:.table .table-striped}
| Card number        | Expiry                  | CVC  |
| :----------------- | :---------------------- | :--- |
| `5226600159865967` | After the current month | Any  |
| `5226603115488031` | After the current month | Any  |
| `5226604266737382` | After the current month | Any  |
| `5226600156995650` | After the current month | Any  |

### American Express

{:.table .table-striped}
| Card number       | Expiry                  | CVC            | Type of test data |
| :---------------- | :---------------------- | :------------  | :---------------- |
| `377601000000000` | After the current month | Any (4 digits) | Amex & loopback   |

### JCB

{:.table .table-striped}
| Card number        | Expiry                  | CVC   |
| :----------------- | :---------------------- | :---- |
| `3569990010082211` | After the current month | Any   |

### Diners

{:.table .table-striped}
| Card number     | Expiry                  | CVC   |
| :-------------- | :---------------------- | :---- |
| `6148201829798` | After the current month | Any   |

### Maestro

{:.table .table-striped}
| Card number        | Expiry                   | CVC   |
| :----------------- | :----------------------- | :---- |
| `6764429999947470` | After the current month  | Any   |

### Dankort

{:.table .table-striped}
| Card number        | Expiry                   | CVC   |
| :----------------- | :----------------------- | :---- |
| `5019994016316467` | After the current month  | Any   |
| `5019994001307083` | After the current month  | Any   |

### Visa/DanKort

{:.table .table-striped}
| Card number        | Expiry                   | CVC   |
| :----------------- | :----------------------- | :---- |
| `4571994016401817` | After the current month  | Any   |
| `4571994016471869` | After the current month  | Any   |

### Forbrugsforeningen

{:.table .table-striped}
| Card number        | Expiry                   | CVC   |
| :----------------- | :----------------------- | :---- |
| `6007220000000004` | After the current month  | Any   |

### Failure Testing Cards

There are two different ways of testing Card Payments error scenarios. You can
test 3-D Secure errors using our 3-D Secure emulator, or you can use specific
amounts set to trigger errors in our test environment.

### Amount Error Testing Method

We have some preset amounts that will trigger error codes. While creating a
payment (operation `purchase`), enter one of the amounts from the list below in
the prices object (`"amount": <number>`) before submitting a payment. The error
message displayed behind the amounts will be sent with your payment in the test
environment.

The amounts that can be used to trigger error codes
(`transactionThirdPartyError`):

{:.table .table-striped}
| Amount   | Error Code                                | Description                              |
| :------- | :---------------------------------------- | :--------------------------------------- |
| `900313` | `REJECTED_BY_ACQUIRER_INVALID_AMOUNT`     | Invalid amount, response-code: 13        |
| `900330` | `REJECTED_BY_ACQUIRER_FORMAT_ERROR`       | Format error, response-code: 30          |
| `900334` | `REJECTED_BY_ACQUIRER_POSSIBLE_FRAUD`     | Possible fraud, response-code: 34        |
| `900343` | `REJECTED_BY_ACQUIRER_CARD_STOLEN`        | Card stolen, response-code: 43           |
| `900354` | `REJECTED_BY_ACQUIRER_CARD_EXPIRED`       | Card expired, response-code: 54          |
| `900351` | `REJECTED_BY_ACQUIRER`                    | Unknown error, response-code: 51         |
| `900359` | `REJECTED_BY_ACQUIRER_POSSIBLE_FRAUD`     | Possible fraud, response-code: 59        |
| `900361` | `REJECTED_BY_ACQUIRER_INSUFFICIENT_FUNDS` | Insufficient funds, response-code: 61    |
| `900362` | `REJECTED_BY_ACQUIRER`                    | Unknown error, response-code: 62         |
| `900391` | `ACQUIRER_HOST_OFFLINE`                   | Acquirer host offline, response-code: 91 |

## Invoice Test Data

### Invoice test data for Norway

{:.table .table-striped}
| Type    | Data             |
| :------ | :--------------- |
| SSN     | 26026708248      |
| Name    | Olivia Nyhuus    |
| Address | Saltnestoppen 43 |
| City    | 1642 Saltnes     |

### Invoice test data for Sweden

{:.table .table-striped}
| Type    | Data            | Alternative data        |
| :------ | :-------------- | :---------------------- |
| SSN     | 600307-1161     | 971020-2392             |
| Name    | Azra Oliveira   | Leia Ahlström           |
| Address | Helgestavägen 9 | Hökvägen 5              |
| City    | 19792 Bro       | 17674 Järfälla          |
| MSISDN  |                 | +46739000001            |
| email   |                 | leia.ahlstrom@payex.com |

### Invoice test data for Finland

{:.table .table-striped}
| Type    | Data             |
| :------ | :--------------- |
| SSN     | 100584-451P      |
| Name    | Järvilehto Kimmo |
| Address | Kiannonkatu 88   |
| City    | 90500 Oulu       |

## Invoice Service Test Data

Use any name, address etc.

## Swish Test Data

Testing a successful Swish purchase (in our external integration test
environment) can be done by using any valid Swedish mobile number. E.g:
`+46 739000001`. As with Vipps, the external integration test environment uses a
fake service with no app involved. To trigger an error message, set the
`description` value in `POST` Create Payment or `Create` Payment Order to one of
the following values:

{:.table .table-striped}
| Description | Simulates                                      |
| :---------- | :--------------------------------------------- |
| RF07        | Transaction declined                           |
| TM01        | Swish timed out before the payment was started |
| BANKIDCL    | Payer cancelled BankId signing                 |

[create-card-purchase]: /old-implementations/payment-instruments-v1/card/redirect#step-1-create-a-purchase
[3ds-emulator-no-dropdown]: /assets/img/3DS-emulator-no-dropdown.png
[3ds-emulator-with-dropdown]: /assets/img/3DS-emulator-with-dropdown.png
[otp-challenge-form]: /assets/img/otp-challenge-form.png
