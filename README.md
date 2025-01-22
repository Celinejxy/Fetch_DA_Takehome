After investigating the data quality and trends, I’ve identified a few key points and would appreciate your input to move forward. 

**Data Source: [Fetch Commerce Data](Raw Data)**

> **Data Quality Issue:**
1. **Inappropriate Data Types**
    - The data types of columns in all three tables (User, Product, and Transaction) were incorrectly defined upon initial reading, requiring adjustments to match their logical meanings (e.g., dates, integers, and floats).

2. **Duplicate and Missing Data**, where rows with identical values across all columns were identified as erroneous duplicates and those with missing value on User ID/ Barcode in the User/Product table would be dropped.
    - Product Table:
        - 215 duplicate rows across all columns were dropped.
        - 4,022 duplicate rows based on BARCODE were identified, with rows containing missing barcode information dropped first.A further 54 duplicate rows based on BARCODE remained, which were cleaned by retaining rows with fewer missing values.
    - Transaction Table:
        - 171 duplicate rows were identified and dropped. Duplicates were defined as rows where SCAN_DATE, RECEIPT_ID, USER_ID, and BARCODE values were identical, which is not valid for unique transactions.

3. **Inconsistent Labeling**
    - User Table: Issues with inconsistent gender labeling.
    - Product Table:
        - Brands were associated with multiple manufacturers.
        - Barcodes were labeled with multiple brand values.
    - Transaction Table: Quantity values were labeled as 'zero' instead of 0.0.

4. **Weak Common Keys for Mapping Across Tables**, the overlap between tables was unexpectedly low:
    - User Table and Transaction Table: Only 130 of 24,795 USER_ID values were common.
    - Product Table: 51.60% of rows had missing information, reducing the ability to map across tables effectively.

> **Interesting Trend:**

One trend that stood out is the Dips & Salsa category's brand performance. After aggregating the data, I found that the leading brand in terms of sales in this category has far outpaced its competitors, highlighting strong customer preference for Tostitos. However, we also need to ensure that the brand labeling is consistent across all products to avoid discrepancies.

> **Data Insight**

- Power Users: I identified users who have both frequent transactions and high spending, which could inform targeted marketing strategies. These users tend to purchase across multiple categories, indicating they are engaged with a broad range of products. This group represents a valuable customer base.

> **Request for Action:**

1. **Help with Standardization:** It would be great if you could clarify the standard labels for Gender and Brand fields, as this will help us clean and structure the data more effectively.
2. **More Data on Missing Fields:** We also need additional context on how we should handle missing category information in the Product table (e.g., how to deal with products that are missing CATEGORY_2 and CATEGORY_3).
3. **Confirmation on Key Metrics**: Please confirm if total sales and transaction frequency are the correct metrics to use when identifying power users or if there are other metrics you would prefer to focus on.
