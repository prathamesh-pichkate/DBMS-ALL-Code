# SQL Code for Storing and Calculating Circle Radius and Area

This document outlines the steps involved in creating a table to store the radius and area of circles, calculating the area for specific radius values, and displaying the results.

## Step 1: Create the Circle Table

The first step is to create a table named `circle` to store the radius and the corresponding area.

```sql
-- Create the table for storing radius and area
CREATE TABLE circle (
    Radius NUMBER,
    Area NUMBER
);

-- Declare variables for radius and area
DECLARE
    rad NUMBER;
    area NUMBER;
BEGIN
    -- Loop through the radius values from 5 to 9
    FOR rad IN 5..9 LOOP
        -- Calculate the area using the formula
        area := 3.14 * POWER(rad, 2);

        -- Insert radius and area into the table
        INSERT INTO circle (Radius, Area)
        VALUES (rad, area);
    END LOOP;

    -- Commit the transaction to save the data
    COMMIT;

    -- Output the header
    DBMS_OUTPUT.PUT_LINE('RADIUS | AREA');
    DBMS_OUTPUT.PUT_LINE('_____________');

    -- Loop through the data in the circle table and output it
    FOR shu IN (SELECT Radius, Area FROM circle) LOOP
        DBMS_OUTPUT.PUT_LINE(shu.Radius || '   |   ' || shu.Area);
    END LOOP;
END;

```

now to see the solution: select \* from circle;
