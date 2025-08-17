# Power Query Project - Data Levarage

## 📌 Project Overview
This project integrates **Sales Data (Jan–Mar)** with **Employee Data**, and enriches it with a **CountryRegion reference table imported from the web**, using Power Query in Excel/Power BI.  
The final merged dataset allows analysis of sales performance alongside employee information.

---

## 📂 Sources Used
- **All_Sales_Raw** → Combined data from Sales_Jan.xlsx, Sales_Feb.xlsx, Sales_Mar.xlsx  
- **Employees_Raw** → Employee master data (EmployeeID, Name, Department, Region, Join Date, Birthdate)  
- **CountryRegion** → Imported from **web source** (reference table for mapping countries and regions)  
- **Sales_With_Employees** → Final merged dataset (Sales + Employee attributes)

---

## 🔄 Transformations Applied
1. **Sales Data**
   - Removed blank rows/columns  
   - Promoted first row as headers  
   - Renamed columns (`Order ID`, `Customer Name`, `Region`, `Cost`, `Profit`, `Year`)  
   - Ensured correct data types (`Cost`, `Profit` as Decimal, `Year` as Whole Number)  

2. **Employee Data**
   - Removed blanks/nulls  
   - Promoted first row to headers  
   - Renamed columns (`EmployeeID`, `Name`, `Department`, `Region`, `Join Date`, `Birthdate`)  
   - Added calculated column `Birth Year` from `Birthdate`  

3. **CountryRegion Data**
   - Imported directly from **web**  
   - Cleaned and structured into two columns: `Country`, `Region`  
   - Used for validation and region mapping  

4. **Merging**
   - Merged **All_Sales_Raw** with **Employees_Raw**  
   - Join column: `Region`  
   - Join type: **Left Outer (all Sales, matching Employees)**  
   - Expanded fields from Employees: `Name`, `Department`, `Join Date`, `Birthdate`  
   - Renamed final table → **Sales_With_Employees**  

---

## ⚡ Challenges & Solutions
- **Issue:** Parameters like `FiscalStartMonth` blocked deletion  
  - **Solution:** Removed parameter references in dependent queries before deleting  
- **Issue:** Duplicate or unnecessary queries created (e.g., Sample File, Helper Queries)  
  - **Solution:** Kept only required queries (`All_Sales_Raw`, `Employees_Raw`, `CountryRegion`, `Sales_With_Employees`)  
- **Issue:** Data type mismatches (`Year` imported as text)  
  - **Solution:** Converted to correct types (whole numbers, decimals, dates)  
- **Issue:** CountryRegion web import sometimes had extra formatting  
  - **Solution:** Cleaned unnecessary rows/columns before using  

---

## ✅ Final Queries in Project
- `All_Sales_Raw`  (folder)
- `Employees_Raw`  
- `CountryRegion` (from web)  
- `Sales_With_Employees`  

---

## 📄 Output
The final merged dataset (`Sales_With_Employees`) is ready for reporting and visualization in Excel/Power BI.
