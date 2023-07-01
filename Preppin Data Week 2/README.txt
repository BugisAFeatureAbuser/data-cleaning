6/18/23
1.0 Checked raw data for inconsistencies.
	1.1. Transactions Table
		1.1.1. Fixed C11 from number value to text value.
		1.1.2. Made nested if function. =IF(TYPE(A2) = 1, "Number", IF(TYPE(A2) = 2, "Text", IF(TYPE(A2) = 4, "Boolean", "Others")))
	1.2. Swift Codes
		1.2.1. Checked if data types are consistent per column, cleared formatting and alighted values in cells for uniformity.
			1.2.1.1. Converted Check Digits to text due to datatype inconsistencies.

2.0 Problem Solution
	2.1. Generated Account Number from Transactions by calling its values (=Transactions!B2) then filling 101 rows because account numbers was unique (=COUNTNIQUE(B2:B101) | 100)
	2.2. Generated Sort Code from Transactions by calling its values (=Transactions!C2) then filling 101 rows because account numbers was unique (=COUNTNIQUE(C2:C101) | 100)
	2.3 Nested vlookups to:
		2.3.1. generated coresponding bank from Transactions Table by account number (VLOOKUP(E2, Transactions!$B$2:$D$101,3, false))
		2.3.2. get coresponding bank code from Switf_Code table using 2.3.1 as search key. (=VLOOKUP(VLOOKUP(E2, Transactions!$B$2:$D$101,3, false), Swift_Codes!$A$2:$C$8, 2, false))
		2.3.3. copied function from c2 but changed index for outer vlookup to get check digits. =VLOOKUP(VLOOKUP(E2, Transactions!$B$2:$D$101,3, false), Swift_Codes!$A$2:$C$8, 3, false)
		2.3.4. Entered GB to all 100 rows because as stated, all transactions was done in england(GB).
	2.4. To generate IBANs, Concatenated from a2 to e2. (=CONCATENATE(A2:E2))