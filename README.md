# Customer Segmentation in Excel

## 📊 Project Description
This project demonstrates how to classify customers in Excel using a **single nested IF formula**.  
Each customer receives a label (VIP, Gold, Premium, Exotic, etc.) based on purchase data and business rules.  

The goal of the project is to show how complex conditions can be combined into one formula for automated classification.

---

## 📁 Dataset
The file `Customer_Sales_Database.xlsx` contains the following columns:

- **CustomerID** – unique identifier  
- **Name** – customer name  
- **Product** – purchased product  
- **Quantity** – number of units  
- **UnitPrice** – price per unit  
- **Region** – customer region  
- **Age** – customer age  
- **Discount** – discount in %  
- **OrderDate** – order date  

---

## 🧮 Business Rules for Classification
- Product or Quantity empty → **Check Data**  
- (Quantity × UnitPrice) > 200 and Discount > 10% → **Gold**  
- (Product = Coffee and Region = North) OR (Quantity > 15) → **VIP**  
- Product = Chocolate and Age > 50 → **Sweet Lover**  
- (Quantity × UnitPrice) > 100 and ≤ 200 → **Premium**  
- Product = Tea and Region = East → **Exotic**  
- Discount = 0 and (Quantity × UnitPrice) < 50 → **Small**  
- Age < 30 and Quantity > 10 → **Young Active**  
- All others → **Regular**  

---

## 🔧 Final Formula
```excel
=IF(OR(C2="";D2="");"Check Data";
 IF(AND(D2*E2>200;H2>10);"Gold";
 IF(OR(AND(C2="Coffee";F2="North");D2>15);"VIP";
 IF(AND(C2="Chocolate";G2>50);"Sweet Lover";
 IF(AND(D2*E2>100;D2*E2<=200);"Premium";
 IF(AND(C2="Tea";F2="East");"Exotic";
 IF(AND(H2=0;D2*E2<50);"Small";
 IF(AND(G2<30;D2>10);"Young Active";
 "Regular"))))))))
