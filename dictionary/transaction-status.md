# Transaction status

A successful transaction must contain the following parameters in the response:

| **Parameter** | **Required Value / Format**      | **Description**                                              |
| ------------- | -------------------------------- | ------------------------------------------------------------ |
| status        | `"SUCCESS"`                      | Indicates overall success of the operation.                  |
| approvalCode  | _Present_                        | Authorization code received from the processing system.      |
| description   | `"approved"`                     | Human-readable response status.                              |
| actionCode    | `"0"`                            | High-level response code (0 typically means approved).       |
| responseCode  | `"00"`                           | Detailed response code.                                      |
| rrn           | `string(12)`, must not be `"-1"` | Retrieval Reference Number (RRN). Must be a 12-digit string. |

#### Transaction Status Definitions

The table below defines the possible values for the `status` parameter:

| **Status Value**              | **English Translation** | **Ukrainian Description** | **Technical Context**                                                                                                        |
| ----------------------------- | ----------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| SUCCESS                       | Success                 | Успіх                     | Transaction completed successfully.                                                                                          |
| FAIL                          | Failure                 | Помилка                   | Transaction failed (e.g., declined by issuer, system error).                                                                 |
| PENDING                       | Pending                 | На проведенні             | Transaction is currently being processed or awaiting final confirmation.                                                     |
| REQUIRED\_3DS                 | 3DS Required            | Проведення 3DS            | The transaction requires customer authentication via 3D Secure.                                                              |
| DESIRED\_THREEDS\_MODE\_ERROR | Desired 3DS Mode Error  | Бізнес помилка...         | Business Error: Occurs when the card does not support 3DS, but the merchant set `desiredThreeDSMode = MUST` (requiring 3DS). |
