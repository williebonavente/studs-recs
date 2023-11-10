# GRADING SYSTEM: PASS OR FAILED?

## Instruction

*Note*: Use the identifiers that are enclosed in parenthesis `(VAR)` as your **variable** names! Disregard the headings at the output file.

## Given: A file of STUDENT `INFILE`

|`STUD-NO`|`STUD-NAME`|`SUBJECT`|`GRADE`|
|-----|---|---|---|
|`(SNO-IN)`|`(SNAME-IN)`|`(SUBJ)`|`(GRD)`|

### Input Record

*Note*: There is one record per subject.  A student may have several subjects or records. The file is sorted by student number.

#### `INFILE`

|||||
|-----|---|---|---|
|`001`| RACHEL| `ICT211`| $1.75$|
|`001`| RACHEL| `ICT212`| $1.25$|
|`001`| RACHEL | `ICT213`| $1.50$|
|`002`| MJ | `ICT211`| $1.00$|
|`002`| MJ | `ICT211`| $1.00$|
|`002`| MJ | `ICT213`| $1.00$|
|`003`| RC | `ICT211`| $3.00$|
|`003`| RC | `ICT211`| $5.00$|
|`003`| RC | `ICT213`| $5.00$|

## OUTPUT LAYOUT:

**WRITE** `ACCNO`, `ACCNAME`, and `BALANCE`. At end of File, **WRITE** the total depositors and the total accumulated balances.

*Note:* Records are arranged according to `ACCNO`.

## `OUTFILE`: Output Layout

```
                 Polytechnic University of the Philippines
                            Sta. Mesa Manila

                             Students' Report

	Student 			Student 		        Average
	Number		  	     Name			         Grade
    (SNO-OUT)	       (SNAME-OUT)		       (AVE-OUT)

	001				    Rachel				      1.50
	002				    MJ				          1.00
	003				    SC				          4.00

	Total Passed:		2 (PCTR-OUT) 	 
	Total Failed:		1 (FCTR-OUT)	
	Total Students:	    3 (SCTR-OUT)       

```

### Variable Documentation Proper

*Note*: Disregard the **headings** at the output file.


#### INPUTS

> `INFILE` - ****INPUT FILE**.

> `REC-IN` - **RECORD INPUT**, hierarchial status, we read the file per rows or record.

> `SNO-IN` - **STUDENT NUMBER**, given input.
> 
> `SNAME-IN` - **STUDENT NAME**, given input.

> `SUBJ` - **SUBJECT CODE** of the student.

> `GRD` - **GRADE OF THE STUDENT PER SUBJECT**.


#### OUTPUTS

> `OUTFILE` - The output file were all processed records will be stored.

<!-- DEBATE MODE: ON, NEED FOR CLARIFICATION, EXPLANATION, AND CORROBORATION. -->
> `REC-IN` - It is storage for processed data inputs.

> `OUTREC` - Temporary variable for storing data for writing, it is writer variable.

> `SNO-OUT` - Output of  `SNO-IN`, needs to be written in the `OUTFILE`.

> `SNAME-OUT` - Output of  `SNAME-IN`, needs to be written in the `OUTFILE`.

> `AVE-OUT` - It is the output average of the sum of the grade divided by total numbers subjects taken by the individual student.

> `PCTR-OUT` - It is the total number of the passed students which will be written in the file.

> `FCTR-OUT` - It is the total number of the failed students which written in the file.

> `SCTR-OUT` - It is the number of the students which written in the file.

### Counter, Flagging, Temporary, Arithmetic, Accumulator, and Constant or  Formatter Variables

> `SCTR` - stands for **STUDENT NAME COUNTER**, at the end of file we need to write the total number of students.

> `PCTR` - counter for the  number of passed students.

> `FCTR` - counter for  the total number of failed students.

> `SUBJ-CTR` - stands for **SUBJECT COUNTER**, we need this variable because we want to count the number subjects taken.
For example `ICT211`, `ICT212`, then the value in this case will be $2$.

*Note*: For efficiency matter
<!---Take note also the efficiency of the logic that is being implemented  -->
*Note*: It is unnecessary to declare `SUM` since in COBOL we have the keyword `COMPUTE` which can be used for basic arithmetic operations.

> `AVE-ACCUM` - stands for **AVERAGE ACCUMULATOR**, for example (we read the record that has a grade of 1.5 then we will have `1.5 + AVE-ACCUM`)

> `TSNO` - stands for **TEMPORARY STUDENT NUMBER**.

> `TSNAME` - stands for **TEMPORARY STUDENT NAME**.

> `TEMP-AVE` - It will be used to reset the grade back to 0 so it will not count the previous average of the student.

> `EOFSW` - flagging for the main process.

> `STR-P = 'Total Passed: '` - text based string, it is only used for formatter.

> `STR-F = 'Total Failed: '` - text based string, it is only used for formatter.

> `STR-TSTD = 'Total Students: '` - text based string, it is only used for formatter.


### SUBPROCESS ROUTINE

> `MAIN-RTN` - main process.

> `INITIAL-RTN` - this is where input, output, accumulator, counter, constant string was declared.

> `PROCESS-RTN` - Process routine whether deposit or withdraw - to add or to subtract to the current balance.

> `SBREAK-RTN` - value reset function.

> `FINISH-RTN` - to terminate the program.
>

### FUNCTIONS

> `READ` reading by row.

> `WRITE` displaying the output, to `OUTFILE`. 


#### *Note*: Ignore all the files except `README.md`, `index.html` and `diagram.drawio`