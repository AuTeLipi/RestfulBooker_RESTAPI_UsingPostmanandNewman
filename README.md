# 🏨 Restful Booker API - Postman Automation with Newman


## 🔍 Project Overview
- This project leverages Postman and Newman to perform comprehensive testing of the Restful Booker API, which simulates hotel booking operations. It encompasses a full range of CRUD operations through both individual test cases and end-to-end (E2E) scenarios, ensuring robust validation of API behavior across diverse input conditions.
- Test cases are designed and maintained in Postman, while Newman facilitates automated execution via the command line, along with the generation of detailed HTML reports for test analysis.

<img width="1918" height="1031" alt="image" src="https://github.com/user-attachments/assets/f37f2f72-e1a9-4d38-9e68-7cb42ac8337f" />

---

## 🧰 Tools Used
- Postman – For designing and running API requests and assertions
- Newman – Command-line collection runner for Postman
- Newman HTML Extra – To generate detailed HTML reports
- Node.js – Required to run Newman

---

## 📂 Repository Structure
| File / Folder                                                             | Description                                    |
| ------------------------------------------------------------------------- | ---------------------------------------------- |
| `Project 02# - Restful Booker - With Requirement.postman_collection.json` | Main Postman collection containing all tests   |
| `Environment Variables Files/`                                            | Environment files for different test scenarios |
| `RestfulBooker_Postman_Newmans_Report.html`                               | Newman-generated HTML report                   |
| `Test Plan – Restful-Booker REST API.docx`                                | Test plan document                             |
| `Restful API - Hotel Booking (Testcases).xlsx`                            | Spreadsheet of all test scenarios              |
| `Bugs found/`                                                             | Folder containing known issues or bug reports  |

---

## 🔌 API Methods Tested
| Method   | Endpoint                       |
| -------- | ------------------------------ |
| `GET`    | /ping                          |
| `POST`   | /auth (Create Token)           |
| `POST`   | /booking (Create Booking)      |
| `GET`    | /booking (All IDs)             |
| `GET`    | /booking?firstname=\&lastname= |
| `GET`    | /booking?checkin=\&checkout=   |
| `GET`    | /booking/\:id                  |
| `PUT`    | /booking/\:id                  |
| `PATCH`  | /booking/\:id                  |
| `DELETE` | /booking/\:id                  |

---

## 🧪 Individual Test Cases

The test suite includes **37 individual test cases**, each designed to validate specific aspects of the Restful Booker API. These tests cover a wide range of **positive**, **negative**, and **edge case** scenarios to ensure comprehensive validation of the API's functionality and robustness.

### ✅ Valid Scenarios

* TC01 – Create booking with all valid fields
* TC02 – Create booking without optional field (`additionalneeds`)
* TC07 – Create booking with whitespace in fields
* TC14 – Retrieve single booking by valid ID
* TC16 – Filter bookings by `firstname`
* TC17 – Filter bookings by `checkin/checkout` dates
* TC19 – Full update of booking
* TC20 – Partial update of booking
* TC25 – Valid deletion of booking
* TC28 – Valid authentication token creation
* TC30 – Health check ping
* TC31 – Booking with minimum `totalprice = 0`
* TC32 – Booking with maximum `totalprice = 999999999`
* TC33 – Booking with empty optional field
* TC34 – Booking with same `checkin` and `checkout` date

### ❌ Negative Scenarios

* TC03 – Missing required field (`firstname`)
* TC04 – Invalid `totalprice` (non-numeric value)
* TC05 – Malformed/Invalid JSON
* TC06 – Special characters in booking fields
* TC08 – Booking with boundary/minimum date
* TC09 – Booking with future/maximum date
* TC10 – Invalid date format
* TC11 – `depositpaid` with non-boolean value
* TC12 – Empty JSON payload
* TC13 – Excessively long string in `additionalneeds`
* TC15 – Retrieve booking with non-existent ID
* TC18 – Invalid query parameter
* TC21 – Unauthorized full update without token
* TC22 – Full update with invalid token
* TC23 – Update with non-numeric `totalprice`
* TC24 – Update with invalid check-in date
* TC26 – Deletion of non-existent booking ID
* TC27 – Unauthorized deletion (missing token)
* TC29 – Invalid authentication token creation
* TC35 – Update with negative `totalprice = -1`
* TC36 – Create booking with invalid date logic (check-in in past, check-out in future)
* TC37 – Partial update with conflicting values (e.g., numeric `firstname`, boolean `lastname`)

---

## ✅ E2E Test Scenarios
| Test ID | Flow                                                           |
| ------- | -------------------------------------------------------------- |
| TS01    | Create Booking → Get Details → Update Booking → Partial Update |
| TS02    | Create → Get → Update                                          |
| TS03    | Create Multiple → Filter by Lastname                           |
| TS04    | Create → Attempt Invalid Update                                |
| TS05    | Ping → Create → Ping                                           |

---

## 🚀 How to Run the Tests

### 1. Install Newman

```bash
npm install -g newman
```

### 2. Run Collection

```bash
newman run "Project 02# - Restful Booker - With Requirement.postman_collection.json" ^
  -e "Env_TC19.postman_environment.json" ^
  -r cli,htmlextra ^
  --reporter-htmlextra-export "RestfulBooker_Postman_Newmans_Report.html"
```

> 💡 You can change the environment file (`-e`) for other test runs.

---

## 📊 Sample Report Summary

* **Total Requests**: 80
* **Assertions**: 178
* **Failures**: 13
* **Skipped**: 0
* **Avg Response Time**: 252 ms
* **Report Path**: `RestfulBooker_Postman_Newmans_Report.html`

<img width="1150" height="896" alt="image" src="https://github.com/user-attachments/assets/8e377955-9d5f-4dfa-8736-910c8f16ef6c" />

---

## 📎 Notes

* You can run E2E or individual test cases directly from the Postman Collection Runner.
* The report gives full visibility into each test case, its request, response, and assertions.

---

## 📚 Disclaimer

This project is created solely for learning and practice purposes. It is intended to demonstrate API testing concepts using Postman and Newman, and does not represent a real-world production system. The Restful Booker API used in this project is a public dummy API designed for educational testing.
