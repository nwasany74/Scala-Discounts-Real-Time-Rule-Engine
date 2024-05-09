# Scala Discounts Real-Time Rule Engine
A simple Scala Real-Time Rule Engine project that applies different discount rules to real-time transaction data and writes the results to a MySQL database. It also keeps tracking the logs data, and backups all data into CSV files.

## Problem Statement:
A large retail store wants a rule engine that qualifies order transactions for discounts based on a set of qualifying rules.

They need the system to be up and running for 24 hours. Raw transactions’ files will be pushed to the following machine (IP: X.X.X.X) on the following path (……/raw_data). They need the calculations to be done automatically once the file is pushed.

## Project Details:
Scala Real-Time Rule Engine processes the data CSV files once they are pushed to the directory that is being watched. It applies different discount rules on data based on some predefined calculation rules. Then, it writes the result into MySQL database tables. It also keeps tracking the log data and storing it in the MySQL database tables. Finally, it backs up all data into CSV files for any unexpected errors.

### Discount Rules:
The following discount rules are applied to the transactions data:

1. **Expiration Date Discount**:
   - If the number of days remaining between the purchasing date and the expiration date is less than 30 days, a discount of (30 - (days between)) is applied. Otherwise, no discount is applied.
     - For example:
       - If 29 days remain -> 1% discount.
       - If 28 days remain -> 2% discount.
       - If 27 days remain -> 3% discount. etc …

2. **Product Category Discount**:
   - If the product category is "Cheese", a discount of 10% is applied. If the product category is "Wine", a discount of 5% is applied. Otherwise, no discount is applied.

3. **Specific Day of Month Discount**:
   - If the purchasing date is March 23, a special discount of 50% is applied. Otherwise, no discount is applied.

4. **Quantity Discount**:
   - If the quantity of products purchased is more than 5 of the same product, a discount will be applied.
     - If the quantity is between 6 and 9, a discount of 5% is applied.
     - If the quantity of products purchased is between 10 and 14, a discount of 7% is applied.
     - If the quantity of products purchased is 15 or more, a discount of 10% is applied. Otherwise, no discount is applied.

5. **Purchasing Channel Discount**:
   - Sales that are made through the "App" will have a special discount. A discount of the quantity rounded up to the nearest multiple of 5 is applied.

6. **Payment Method Discount**:
   - If the payment method is "Visa", a discount of 5% is applied. Otherwise, no discount is applied.

### Main Rules:
- Transactions that didn't qualify for any discount will have a 0% discount.
- Transactions that qualified for more than one discount will get the top 2 and get their average.
- After ingesting the raw data and calculating the discount, the final price will be calculated and loaded into the output files.
- The raw data needs to be removed from the source directory after successfully processing and writing it in the database.
- It is required to log the engine’s events in a log file.

## Project Technicality:
- The project is written using Scala programming language, in a purely functional manner.
- It follows the Functional Programming approach, by using pure, immutable, and predictable behavior functions and data structures.
- No loops and no Null values are used.
- All functions are documented.

  # Detailed Solution Overview

## PostgreSQL Implementation

### Approach
- **Database Configuration**: Set up PostgreSQL database with the provided connection details.
- **Code Structure**: Utilized Scala to implement the rule engine logic, database interactions, and logging.
- **Functional Programming**: Ensured the core logic adheres to functional programming principles with immutable data structures, no vars, and pure functions.
- **Qualifying Rules and Calculation Rules**: Implemented the specified rules for qualifying transactions and calculating discounts.
- **Database Interaction**: Loaded the calculated discounts into the PostgreSQL database.
- **Logging**: Recorded engine events in a log file (`rules_engine.log`).

### Solution Review
- **Code Review**: Each component of the solution was reviewed for clarity, correctness, and adherence to functional programming principles.
- **Testing**: Conducted thorough testing to ensure that the discount calculation, database interactions, and logging functionalities work as expected.
- **Refinement**: Made necessary adjustments based on code review feedback and testing results to improve code quality and performance.
- **Documentation**: Documented the PostgreSQL implementation, including setup instructions, code structure, and usage guidelines.

  

https://github.com/nwasany74/Scala-Discounts-Real-Time-Rule-Engine/assets/155104546/21332cc7-135c-46a8-9449-ab2dc5cbe226



## MySQL Implementation

### Approach
- **Database Configuration**: Configured MySQL database with the provided connection details.
- **Code Reusability**: Leveraged the existing Scala codebase and adapted it to work with MySQL database by updating the database connection details.
- **Functional Equivalence**: Ensured that the MySQL implementation mirrors the functionality and structure of the PostgreSQL implementation.
- **Compatibility Testing**: Tested the solution with MySQL to ensure compatibility and correct functionality.

### Solution Review
- **Cross-Validation**: Verified that the MySQL implementation produces the same results as the PostgreSQL implementation for identical input data.
- **Performance Optimization**: Optimized database queries and interactions to enhance performance and efficiency.
- **Code Consistency**: Ensured consistency in coding style, comments, and documentation with the PostgreSQL implementation.
- **Error Handling**: Implemented robust error handling mechanisms to handle database errors and exceptions gracefully.



https://github.com/nwasany74/Scala-Discounts-Real-Time-Rule-Engine/assets/155104546/94e1966c-e99d-4de0-9049-3160838be855




## Oracle Implementation

### Approach
- **Database Configuration**: Set up Oracle database with the provided connection details.
- **Code Adaptation**: Modified the existing Scala codebase to support Oracle database by updating the JDBC URL, username, and password.
- **Compatibility Testing**: Tested the solution with Oracle database to ensure compatibility and correct functionality.
- **Oracle-specific Considerations**: Addressed any Oracle-specific requirements or differences in database interaction.

### Solution Review
- **Integration Testing**: Conducted comprehensive integration testing with Oracle database to verify functionality and performance.
- **Compatibility Verification**: Ensured that the Oracle implementation produces consistent results with the PostgreSQL and MySQL implementations.
- **Code Documentation**: Documented the Oracle implementation, including any specific considerations or configurations required for Oracle database.

  

https://github.com/nwasany74/Scala-Discounts-Real-Time-Rule-Engine/assets/155104546/7f211324-a9f8-4b0f-bc4d-a270ee3afd30



## Overall Solution Review
- **Functional Completeness**: Ensured that the solution meets all the functional requirements specified in the project brief.
- **Code Quality**: Reviewed and refined the codebase to maintain high code quality, readability, and maintainability.
- **Documentation**: Documented the overall solution architecture, implementation details, setup instructions, and usage guidelines in the README file.
- **Version Control**: Utilized version control (e.g., Git) to manage code changes, branches, and collaboration among team members.

