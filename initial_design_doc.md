## Overview
This software for Bend Bike Shop is intended to create an easy way for the bike shop to rent out bikes. It can be used at a kiosk or online and will also be integrated with the shop to ensure accurate inventory and similar features.
## Actors
Customer, Manager, Owner, Employee
## Goals/Non-Goals
* Automated system to cancel rentals for unforeseen closure days
* Tracking for helmets
* Require an account
* Automated replacement charge for missing rentals
* Selling bikes through the system. Website is only for rentals
* No extending rentals via the website. You must talk to an employee
## Constraints
* Bikes are handled during business hours
* Payment must be verified and valid
* Customers can reserve bikes as guests without creating an account
* Customers can reserve bikes up to 6 months in advance
* Managers can edit/remove employee permissions
## Assumptions
* initial inventory is accurate and future audits remain accurate
* internet is provided reliably
* Employees will update bikes to be unavailable for maintenance
* Employees will have sufficient training on the application
## Non-Functional Requirements
* The cloud hosted platform must have an uptime of 99.5% or higher
* The system should be able to support the inventory of the 60 or so bikes that are owned by Bend Bike Shop
* The website should be fully compatible with the following browsers: Firefox, Chrome, Edge, Safari
* Payment terminals at the store should be reputable and securely store credit card info
* Customers should not be able to access employee portal
* Data must be identical and synced across all platforms and portals
## Use Case Diagrams
| Cell | Short description |
|---|---|
| Employee | Staff member who manages inventory and handles bike maintenance. |
| Manage inventory | Manage bicycle availability and inventory status. |
| Fix bike | Repair a bicycle that needs maintenance. |
| Begin maintenance | Mark a bicycle as undergoing maintenance. |
| List bike available | Mark a bicycle as available for rental. |
| List bike unavailable | Mark a bicycle as unavailable for rental. |
| Manager | Staff member with permissions for refunds, replacement fees, and administrative tasks. |
| Charge late fee | Apply a fee when a customer returns a bike late. |
| Process refund | Issue a refund to a customer. |
| Charge replacement fee | Charge a customer for a missing or replacement bicycle. |
| Customer | Person who rents or reserves bicycles. |
| Owner | Business owner with access to reports and employee permissions. |
| Cancel all reservations today | Cancel all reservations scheduled for the current day. |
| Cancel reservation | Cancel an individual bike reservation. |
| View business reports | View reports about business performance and rental activity. |
| View inventory reports | View reports about bicycle inventory and availability. |
| Manage employee permissions | Manage employee access levels and permissions. |
| Browse bikes | View available bicycle types and rental options. |
| Reserve bike | Reserve a bicycle for a selected date and rental period. |
| Process payment | Process payment authorization and rental charges. |

```mermaid
flowchart LR
    Employee([Employee]) --> ManageInventory([Manage inventory])
    Employee --> FixBike([Fix bike])
    Employee --> BeginMaintenance([Begin maintenance])

    ManageInventory --> ListAvailable([List bike available])
    ManageInventory --> ListUnavailable([List bike unavailable])
    BeginMaintenance --> ListUnavailable

    classDef action fill:#101820,stroke:#20c9b7,color:#ffffff
    class ManageInventory,FixBike,BeginMaintenance,ListAvailable,ListUnavailable action
```

```mermaid
flowchart LR
    Employee([Employee]) --> LateFee([Charge late fee])
    Manager([Manager]) --> Refund([Process refund])
    Manager --> ReplacementFee([Charge replacement fee])

    LateFee --> Customer([Customer])
    Refund --> Customer
    ReplacementFee --> Customer

    classDef action fill:#101820,stroke:#20c9b7,color:#ffffff
    class LateFee,Refund,ReplacementFee action
```

```mermaid
flowchart LR
    Manager([Manager]) --> CancelAll([Cancel all reservations today])
    CancelAll --> Customer([Customer])
    Customer --> CancelReservation([Cancel reservation])

    classDef action fill:#101820,stroke:#20c9b7,color:#ffffff
    class CancelAll,CancelReservation action
```
```mermaid
flowchart LR
    Owner([Owner]) --> BusinessReports([View business reports])
    Owner --> InventoryReports([View inventory reports])
    Owner --> Permissions([Manage employee permissions])

    Manager([Manager]) --> InventoryReports
    Manager --> Permissions

    Permissions --> Employee([Employee])

    classDef action fill:#101820,stroke:#20c9b7,color:#ffffff
    class BusinessReports,InventoryReports,Permissions action
```
```mermaid
flowchart LR
    Customer([Customer]) --> BrowseBikes([Browse bikes])
    Customer --> ReserveBike([Reserve bike])
    Customer --> CancelReservation([Cancel reservation])

    ReserveBike --> ProcessPayment([Process payment])
    ProcessPayment --> Employee([Employee])

    classDef action fill:#101820,stroke:#20c9b7,color:#ffffff
    class BrowseBikes,ReserveBike,CancelReservation,ProcessPayment action
```
## UX Diagrams
| Cell | Short description |
|---|---|
| Business homepage | Main navigation page for business management features. |
| Business report page | Display business performance and rental reports. |
| Inventory report page | Display inventory statistics and bicycle availability reports. |
| Employee permissions page | View and edit employee access permissions. |
| Inventory Page | Interface for managing bicycle inventory and availability. |
| Bike listed available banner | Confirmation that a bicycle has been marked available. |
| Bike listed unavailable banner | Confirmation that a bicycle has been marked unavailable. |
| Customer list page | Display customers and provide access to their records. |
| Customer charges screen | View and update charges associated with a customer. |
| Added late fee banner | Confirmation that a late fee has been added. |
| Added replacement fee banner | Confirmation that a replacement fee has been added. |
| Canceled charges fee banner | Confirmation that charges have been canceled. |
| View business reports | Navigate from the homepage to business reports. |
| View inventory reports | Navigate from the homepage to inventory reports. |
| Edit employee permissions | Navigate to the employee permissions page. |
| Back | Return to the business homepage or previous page. |
| List bike as available | Mark a bicycle as available and display confirmation. |
| List bike as unavailable | Mark a bicycle as unavailable and display confirmation. |
| Update charges | Open the customer charges screen to manage fees. |
| Go back | Return from the customer charges screen to the customer list. |
| Add late fee | Add a late fee to a customer's charges. |
| Add replacement fee | Add a replacement fee to a customer's charges. |
| Cancel charges | Cancel charges and display a confirmation message. |

```mermaid
flowchart TD
    Home[Business homepage]

    Home -->|View business reports| BusinessReportPage[Business report page]
    BusinessReportPage -->|Back| Home

    Home -->|View inventory reports| InventoryReportPage[Inventory report page]
    InventoryReportPage -->|Back| Home

    Home -->|Edit employee permissions| PermissionsPage[Employee permissions page]
    PermissionsPage -->|Back| Home
```
```mermaid
flowchart TD
    InventoryPage[Inventory Page]

    InventoryPage -->|List bike as available| AvailableBanner[Bike listed available banner]
    InventoryPage -->|List bike as unavailable| UnavailableBanner[Bike listed unavailable banner]

    class InventoryPage page
    class AvailableBanner,UnavailableBanner result
```

```mermaid
flowchart TD
    CustomerList[Customer list page]
    Charges[Customer charges screen]

    CustomerList -->|Update charges| Charges
    Charges -->|Go back| CustomerList

    Charges -->|Add late fee| LateFeeBanner[Added late fee banner]
    Charges -->|Add replacement fee| ReplacementBanner[Added replacement fee banner]
    Charges -->|Cancel charges| CancelledBanner[Canceled charges fee banner]

    class CustomerList,Charges page
    class LateFeeBanner,ReplacementBanner,CancelledBanner result
```
## Class Diagram
```mermaid
classDiagram
    class Customer {
        customer_id
        name
        email
        phone
    }

    class Employee {
        employee_id
        name
    }

    class Owner {

    }

    class Bike {
        bike_id
        bike_type
        rental_rate
    }

    class Payment {
        payment_id
        amount
    }

    class Reservation {
        reservation_id
        start_time
        end_time
        status
        total_cost
    }

    class Charge {
        charge_id
        amount
    }

    class Manager {

    }

    class MaintenanceRecord {
        maintenance_id
        description
        status
    }

    class Permission {
        permission_id
        permission_name
    }

    Customer --> Reservation
    Employee --> MaintenanceRecord
    Bike --> MaintenanceRecord
    Employee --> Permission
    Bike --> Reservation
    Customer --> Charge
    Reservation --> Charge
    Employee <-- Manager
    Manager <-- Owner
    Reservation --> Payment

```
## ER Diagram
```mermaid
erDiagram
    CUSTOMER ||--o{RESERVATION:books
    BIKE ||--o{RESERVATION:included_in
    RESERVATION ||--o{PAYMENT:paid_with
    CUSTOMER ||--o{CHARGE:pays
    EMPLOYEE ||--o{MAINTENANCE:performs
    BIKE ||--o{MAINTENANCE:serviced_by
    RESERVATION ||--o{CHARGE:includes


    CUSTOMER {
        int id PK
        string name
        string email
        string phone
    }
    BIKE {
        int id PK
        string type
        string status
        float rate
    }

    RESERVATION {
        int id PK
        int customer_id FK
        int bike_id FK
        datetime start
        datetime end
        string status
        float cost
    }

    PAYMENT {
        int id PK
        int reservation_id FK
        float amount
    }

    CHARGE {
        int id PK
        int customer_id FK
        int reservation_id FK
        float amount
    }

    EMPLOYEE {
        int id PK
        string name
        string role
        bool active
    }

    MAINTENANCE {
        int id PK
        int bike_id FK
        int employee_id FK
        string description
        string status
    }
```
## Interfaces
```py
def browse_bikes(start_time: datetime, end_time: datetime) -> list:
    # Purpose: Show available bikes.
    # Requires: Valid rental dates.
    # Outcomes: Returns available bikes.
    # Guarantees: Does not affect inventory.
    # Notes: Does not include bikes in maintenance.

def cancel_reservation(reservation_id: int) -> bool:
    # Purpose: Cancel a reservation.
    # Requires: An existing reservation.
    # Outcomes: Updates reservation status.
    # Guarantees: Prevents duplicate cancellations.
    # Notes: 

def reserve_bike(customer_id: int, bike_id: int, start_time: datetime, end_time: datetime) -> ReservationObj:
    # Purpose: Reserve a bike.
    # Requires: Available bike and valid dates.
    # Outcomes: Creates a reservation.
    # Guarantees: Prevents overlapping reservations.
    # Notes: 

def record_maintenance(bike_id: int, employee_id: int, description: str) -> MaintenanceObj:
    # Purpose: Record bike maintenance.
    # Requires: Existing bike and employee.
    # Outcomes: Creates a maintenance record.
    # Guarantees: Bike remains unavailable during maintenance.
    # Notes: Records completed repairs.

def add_charge(reservation_id: int, amount: float, charge_type: str) -> ChargeObj:
    # Purpose: Add a customer fee.
    # Requires: Valid reservation and amount.
    # Outcomes: Creates a new charge.
    # Guarantees: Prevents duplicate charges.
    # Notes: Used for late and replacement fees.

def update_bike(bike_id: int, status: str) -> bool:
    # Purpose: Update bike status.
    # Requires: Existing bike.
    # Outcomes: Saves the new status.
    # Guarantees: Maintenance bikes cannot be available.
```
## Invariants


## Failure Modes