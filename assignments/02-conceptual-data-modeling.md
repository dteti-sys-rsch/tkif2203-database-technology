# Homework 1: Conceptual Data Modeling

**Course:** TKIF2203 – Database Systems  
**Instructor:** Dr. Guntur D Putra  
**Due Date:** Thursday, 3 September 2026 at **12.59** (Late submissions are not accepted.)  
**Submission:** Please submit your work through eLOK.

## Part 1: Basic Entity-Relationship Modeling (40 Points)
Suppose you are building a new **social media app** from the ground up, namely *UGM-Fezz*. Draw a Peter Chen ER Diagram for it based on the following business rules. Focus on capturing the conceptual logic of how users interact.

**Business Rules:**
* **Users** are identified by a `User_ID` and have a `Username` and `Email`.
* **Posts** are identified by a `Post_ID` and have a `Content` (text) and a `Timestamp`.
* A **User** can *create* multiple **Posts**, but each **Post** is created by exactly one **User**.
* **Communities** (Groups) are identified by a `Comm_ID` and have a `Description`.
* **Users** can *join* multiple **Communities**, and each **Community** can have many **Users**.
* We must record the `Join_Date` of when a User joined a specific Community.

**Requirements:**

* Use **Rectangles** for Entities and **Diamonds** for Relationships.
* Use **Ovals** for Attributes and underline the **Primary Keys**.
* Clearly label the **Cardinality** (e.g., `1:N`, `M:N`) on the relationship lines.

You are also free to add more data or entities if you think they are necessary.

## Part 2: Advanced Attributes & Relationships (30 Points)
Building on the social media model, apply the following conceptual constraints:

1. **Multivalued Attributes:** A **User** may have multiple `Social_Links` (e.g., links to their GitHub, LinkedIn, or Portfolio). Refer to your lecture notes on how to represent an attribute that can have multiple values.
2. **Composite Attributes:** The User's `Account_Settings` should be broken down into `Privacy_Level`, `Notification_Pref`, and `Theme_Color`.
3. **Derived Attributes:** A **Post** has a `Total_Likes` count. Since this number is calculated based on the likes relationship, represent it as a derived attribute. (Recall the specific dashed oval style for derived data.)

## Part 3: Identifying Existence Dependency (30 Points)
*The concept of "Weak Entities" is fundamental for handling data that cannot exist on its own (Existence Dependency).*

**Scenario:**
* **Post** is a Strong Entity with attributes `Post_ID` (PK) and `Content`.
* **Comment** is a Weak Entity with attributes `Comment_No` (discriminator), `Text`, and `Post_Time`.
* **Logic:** A Comment is "weak" because it belongs to a specific Post. You cannot have "Comment #5" floating in the database without knowing which Post it belongs to.

**Questions:**

1. **The Discriminator:** In this scenario, why is `Comment_No` called a "Partial Key" (Discriminator) instead of a Primary Key?
2. **Drawing (Chen Notation):** Draw the relationship between Post and Comment. Refer to **Slide 34** and ensure you use:
   * **Double Rectangles** for the Weak Entity (Comment).
   * **Double Diamonds** for the Identifying Relationship.
   * **Double Lines** to show Total Participation of the Comment in the relationship.

## Submission Instructions

* You may use tools like **Draw.io** (select the "Entity Relation" library) or draw clearly by hand and scan your work.
* Ensure all symbols follow the standard Peter Chen notation as shown in the lecture slides.
* Export/scan your diagram as a single PDF and submit it via **eLOK** (the course eLearning platform). Late submissions after the due date above will not be accepted through eLOK.
* Include your name and student ID on the first page of your PDF.
