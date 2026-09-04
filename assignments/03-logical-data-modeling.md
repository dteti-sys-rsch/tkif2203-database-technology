# Homework 2: Logical Data Modeling

**Course:** TKIF2203 – Database Technology  
**Instructor:** Dr. Guntur D Putra  
**Due Date:** Thursday, 10 September 2026 at **12.59** (Late submissions are not accepted.)  
**Submission:** Please submit your work through eLOK.

In Homework 1 you produced a Peter Chen ER diagram for the **UGM‑Fezz** social‑media app. This task takes that conceptual design and turns it into a **logical** (relational) schema.

## Objectives

1. **Map the ER constructs** from conceptual model to relations.
2. **Specify keys & constraints** – primary keys, foreign keys, (unique, not‑null).
3. Include a logical‑model diagram (Crow’s‑Foot). You may want to use [https://dbdiagram.io/](https://dbdiagram.io/) to neatly generate the diagram.

## Part 1: UGM-Fezz Modeling (40 Points)
Convert your previously modeled *UGM-Fezz* into logical database design with Crow's Foot notation. Please be mindful with the entity types, attribute types, the cardinality of the relation, etc.

## Part 2: Logical Modeling for Other Conceptual Design (60 Points)
Please conver the following conceptual database design into logical data modeling with Crow's Foot diagram. Each design is worth 15 points.

1. **General Hardware Company Database**
![General Hardware Company Database](02-images/1-general-hardware-company.jpg)

2. **World Music Association Database**
![World Music Association](02-images/2-world-music-association.jpg)

3. **Lucky Rent-a-Car Database**
![Lucky Rent-a-Car](02-images/3-lucky-rent-a-car.jpg)

4. **Sunshine Auto Repair Shop Database**

   The **Sunshine Auto Repair Shop** wants a database to track its customers, their vehicles, repair orders, mechanics, and parts.

   **Entities and their attributes:**
   - **CUSTOMER**: customer number, name, phone, email, address
   - **VEHICLE**: VIN, make, model, year, license plate
   - **MECHANIC**: mechanic number, name, specialty, hire date
   - **SERVICE_ORDER**: order number, order date, status, total cost
   - **PART**: part number, part name, unit price, quantity in stock

   **Business rules:**
   1. A customer may own one or more vehicles, but each vehicle belongs to exactly one customer.
   2. A vehicle may have many service orders over time, but each service order is for exactly one vehicle.
   3. A mechanic may handle many service orders, but each service order is handled by exactly one mechanic.
   4. A service order may use many different parts, and the same part may be used on many different service orders; the quantity of each part used on a given order must be recorded.

   Convert this description into a logical (relational) schema using Crow's-Foot notation. Identify primary keys, foreign keys, and any associative (bridge) entity needed to resolve the many-to-many relationship.

## Submission Instructions
* You may use tools like [https://dbdiagram.io/](https://dbdiagram.io/), **Draw.io** (select the "Entity Relation" library), or draw clearly by hand and scan your work.  
* Ensure all symbols follow the standard notation.
* Submit your answers in PDF format via eLOK. Remember to include your name and student id in your PDF file.
* Late submissions are not accepted.
