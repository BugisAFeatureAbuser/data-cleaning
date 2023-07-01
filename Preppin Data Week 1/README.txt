Problem 1
1. SPLIT the Transaction Code by "-".
2. Copied the first values from Bank Code (DTB, DS, DSB) and pasted on the left side of the raw data for later puposes.
3.(See label @ H1 for Problem 1) Created heading Bank and Value
4. Used =UNIQUE at column A to generate unique Banks and copy, pasted as values to avoid potential error (Column I2:I4).
5. Used =SUMIF to get total values of every bank.
(=SUMIF(A:A, I2, C:C))

------------------------------------------------------------------------

Problem 2
1. Created table with Bank, Online or In_person, Transaction Day and Value.
2. Copied Bank column from col.A.
3. Used =IF to make values of col.E from 1,2 to Online, In-Person respectively. 
(=IF(E2 = 1, "Online", "In-Person"))
4. Transaction Day by Day Name
	4.1. Split data from col.F by " ". (=SPLIT(F2, " "))
	4.2. Copied dd/mm/yyyy, deleted the results of 4.1 and pasted copied values as value only.
	4.3. Split dd/mm/yyyy by "/" then concatenated result into format mm/dd/yyyy.
	4.4. Converted concatenated values into Text.
	(=Text(mm/dd/yyyy, dddd))
5. Copy, paste value column from raw data.
6.Generate Output
	6.1. To make comprehensible result, since there is 3 types of banks that operates online and in-person and 7 days a week, created 14 rows to accomodate 2 operations type and 14 total days per each unique bank.
	6.2. To generate banks value per day per operation, used SUMIF 		(=SUMIFS(P:P, M:M, R2, N:N,S2,O:O,T2))

------------------------------------------------------------------------

Problem 3: Bank, Customer Code, Value
1. Copied bank from col.A
2.1. Used unique to generate unique customer code.
2.2. Since there is 3 unique banks, customer code will in every bank to measure value. (33 rows).
3. Used SUMIF to compute total value per customer code per bank. =SUMIFS(C:C,A:A,X2,D:D,Y2)


TL;DR
	Most data that was generated from a function was copy and pasted as values only to avoid errors when used to another function.