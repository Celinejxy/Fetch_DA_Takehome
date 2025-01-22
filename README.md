> **Data Quality Issue:**
1. <h6>Inappropriate Data Types</h6>
    <h6> - The data types in all three tables (User, Product, and Transaction) were incorrectly defined upon initial import, requiring adjustments to align with their logical meanings (e.g., converting dates to proper datetime formats, integers to numeric types, and correcting floating-point values)</h6>

2. <h6> Duplicate and Missing Data, where rows with identical values across all columns were identified as erroneous duplicates and those with missing values on User ID/ Barcode in the User/Product table would be dropped since their role as primary key in the respective table.</h6>
    <h6> - Product Table: 215 duplicate rows across all columns were dropped. Additionally, 4,022 duplicate rows based on the BARCODE field were identified. Rows with missing BARCODE values were dropped. After further cleaning, 54 duplicate rows remained and were resolved manually using domain knowledge.</h6>
    <h6> - Transaction Table: 171 duplicate rows were identified and dropped. Additional duplicates were defined as rows with identical SCAN_DATE, RECEIPT_ID, USER_ID, and BARCODE values, which is invalid for unique transactions. This revealed 49,829 duplicate rows, representing 99.6% of the data, which were cleaned by retaining records with fewer missing values. </h6>

3. <h6>Inconsistent Labeling</h6>
    <h6> - User Table: Gender labels were inconsistent (e.g., "prefer_not_to_say" vs. "Prefer not to say"), requiring standardization.</h6>
    <h6> - Product Table: 3 brands were associated with multiple manufacturers, which were corrected by retaining the most frequent pairing. 11 barcodes were linked to multiple brand values, resolved through manual review.</h6>
    <h6> - Transaction Table: Quantity values were inconsistently labeled as "zero" instead of 0.0, requiring correction for numeric operations.</h6>

4. <h6>Weak Common Keys for Mapping Across Tables, the overlap between tables was unexpectedly low:</h6>
    <h6> - User Table and Transaction Table: Only 130 of 24,795 USER_ID values were common, meaning 0.5% of the records in Transaction table could merge with additional user data. </h6>
    <h6> - Product Table: 51.60% of records in Transaction table failed to found a matching BARCODE in the Product table, reducing the ability to map across tables effectively.</h6>

****
> **Interesting Trend:**

<h6>One notable trend emerged in the Dips & Salsa category: After analyzing sales data, Tostitos consistently outperformed its competitors, establishing itself as the leading brand by a significant margin,indicating a strong customer preference in this product category.</h6>

<h6>However, this insight is contingent on accurate and consistent brand labeling across the dataset. During the analysis, we identified some discrepancies in product labeling, such as barcodes linked to multiple brands or missing brand information. Addressing these inconsistencies is crucial to ensuring the reliability of this finding.</h6>

****
> **Data Insight**

<h6>Power Users: I identified power users—customers with both frequent transactions and high spending. These users also tend to purchase across multiple product categories, indicating strong engagement with the full range of offerings. This group represents a highly valuable customer base and could serve as a key focus for targeted marketing campaigns to drive retention and further spending.</h6>

****
> **Request for Action:**
<h6> 1. Help with Standardization: Assistance from the cross-functional team is needed to clarify and standardize labels in the User and Product tables to ensure consistency across datasets (e.g., gender labels, brand associations, manufacturer details).</h6>
<h6> 2. Guidance on Missing Fields: Additional context is required on how to handle missing category information in the Product table, particularly for fields like CATEGORY_2 and CATEGORY_3. Should these rows be excluded, or should placeholder values be used? Any source for cross-referencing? </h6>
<h6> 3. Validation of Taxonomy: Please verify the taxonomy for USER_ID and BARCODE fields, as these will be used to define unique rows and as key identifiers for merging tables.</h6>
<h6> 4. Confirmation on Key Metrics: Kindly confirm if total sales and transaction frequency are the preferred metrics for identifying power users. If there are additional metrics or a different framework you’d like us to prioritize, let us know to align with business goals.</h6>
