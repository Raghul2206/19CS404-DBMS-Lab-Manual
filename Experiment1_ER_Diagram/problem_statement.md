### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_fitness.png)

<img width="791" height="865" alt="Screenshot 2025-08-29 225250" src="https://github.com/user-attachments/assets/b684b060-f82e-4d63-b975-962d4dbb1c56" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|    Member    |        MemberID ,Membership          |  Store member details     |
|      Trainer  |      TrainerID,Name,Email,PhoneNumber              |     Store Trainer details  |
|  Program      |      ProgramID,Cost              |  Programs like Zumbz/yoga     |
|    Session    |       SessionID,SessionDate             |    Tracks attendance   |
|    Payment    |          PaymentID,Amount          |   Tracks payments by members    |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |
|       Member-Program       |     M:N       |      Optional(Member),Mandatory(Enrollment)         | Member may or may not join programs      |
|          Trainer-Program    |      M:N      |            Optional(Trainer),Mandatory(Assignment)   |  Trainer may or may not run Programs     |
|       Member–Trainer       |     1:N       |        Mandatory (Session), Optional (Member/Trainer)       |    Session must have a member & trainer   |

### Assumptions
- 
- 
- 
- Program = recurring class; Session = specific instance.
- Payments cover both memberships and sessions.
- A Session links one Member and one Trainer.

---

@@ -64,31 +66,35 @@ The Central Library wants to manage book lending and cultural events.
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

<img width="728" height="852" alt="Screenshot 2025-08-29 225310" src="https://github.com/user-attachments/assets/711314cd-dd0f-44a0-a057-cbd449efdb81" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|    Member    |      MemberID (PK), Name, Address, Phone, Email              |   Library members    |
|      Book  |      BookID (PK), Title, Author, Category, ISBN, PubYear              |    Books in collection   |
|    Loan    |        LoanID (PK), LoanDate, DueDate, ReturnDate, FineAmount, MemberID (FK), BookID (FK)            |     Tracks book borrowing  |
|     Event   |         EventID (PK), Name, Description, EventDate, StartTime, EndTime, RoomID (FK)           |    Library cultural events   |
|    Speaker    |         SpeakerID (PK), Name, Bio, ContactInfo           |    Event speakers/authors   |
|      Booking  |             BookingID (PK), BookingDate, StartTime, EndTime, RoomID (FK), MemberID (FK)       |    Study room reservations   |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |
|      Member–Book        |       M:N     |        Mandatory for Loan, Optional for Member/Book       |   Members borrow books    |
|    Member–Event          |      M:N      |     Mandatory for Registration, Optional for Member/Event          |   Members register for events    |
|   Event–Speaker  |      M:N      |    Mandatory for EventSpeaker, Optional for Event/Speaker |    Events may have multiple speakers   |
|   Event–Room           |      1:N      |    Mandatory for Event, Optional for Room           |  Each event in one room     |
|  Room–Booking            |      1:N   |      Mandatory for Booking, Optional for Room         |   Rooms booked for study by members    |

### Assumptions
- 
- 
- 
- Overdue fines are stored per Loan record.
- BookCopy not modeled
- Rooms serve both events and study bookings.

---

@@ -106,38 +112,36 @@ A popular restaurant wants to manage reservations, orders, and billing.
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

<img width="654" height="807" alt="Screenshot 2025-08-29 225323" src="https://github.com/user-attachments/assets/a66f572c-2469-4876-867e-74fe02d8478a" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|    Customer    | CustomerID (PK), Name, Email, Phone |  Stores customer info     |
|   Waiter     | WaiterID (PK), Name, Shift, ContactInfo|   Waiter details    |
|    Table    | TableID (PK), TableNumber, Capacity, Location  |Restaurant tables |
|  Reservation   | ReservationID (PK), ReservationDate, ReservationTime, NoOfGuests, Status, CustomerID (FK), TableID (FK) | Table bookings|
| Order       |  OrderID (PK), OrderDate, OrderTime, Status, ReservationID (FK)| Orders linked to reservations|
| Dish       |  DishID (PK), DishName, Description, Price, CategoryID (FK)| Menu items|
|  Bill      | BillID (PK), BillDate, TotalAmount, ServiceCharge, Tax, Status, ReservationID (FK)|Final bill per reservation|
| Assignment       | AssignmentID (PK), WaiterID (FK), ReservationID (FK)|Resolves Waiter–Reservation|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |
|  Customer–Reservation            |   1:N         |  Mandatory for Reservation, Optional for Customer             |   One customer can have many reservations    |
|  Reservation–Table            |    1:N        |  Mandatory for Reservation, Optional for Table             |  Each reservation is for one table     |
|   Order–Dish           |      M:N      |    Mandatory for Order_Item, Optional for Order/Dish   |  An order can include many dishes     |
|   Reservation–Bill           |  1:1          | Mandatory for Bill, Optional for Reservation              | One bill per reservation      |
|   Waiter–Reservation           |   M:N         | Mandatory for Assignment, Optional for Waiter/Reservation              | Multiple waiters can serve a reservation      |

### Assumptions
- 
- 
- 
- Walk-in customers are still recorded
- One bill per reservation
- Split payments not modeled; could extend with a Payment entity.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
