---
layout: page
title: User Guide
---

<p align="center">
    <img src="images/tracko_logo_docs.png" width="70%"/>
</p>

Track-O is a **desktop app for private tutors to manage their tutees**, optimized for use via a Command Line Interface (CLI) while still having the benefits of a Graphical User Interface (GUI). Track-O lets you track an assortment of data, from grades to home addresses to lesson timings. You can easily access the many functions of Track-O using simple commands, such as add and get. Hop over to our Quick Start section to get started.

* Table of Contents
{:toc}

--------------------------------------------------------------------------------------------------------------------

## Quick start

1. Ensure you have Java `11` or above installed in your Computer. You can download it [here](https://www.oracle.com/java/technologies/downloads/#java11).
 
2. Download the latest `tracko.jar` from [here](https://github.com/AY2122S1-CS2103T-F12-3/tp/releases/download/v1.4/tracko.jar).

3. Copy the file to the folder you want to use as the _home folder_ to run Track-O.

4. Double-click the file to start the app. The GUI should appear in a few seconds as shown in the image below. Note how the app contains some sample data.<br>

    <p align="center">
        <img src="sample_ug.png" width="95%"/>
    </p>

5. Refer to [Setting up your first tutee](#setting-up-your-first-tutee) to get started using Track-O.

If you need help with the start up process, visit our [Troubleshooting](#troubleshooting) section.



--------------------------------------------------------------------------------------------------------------------

## About

This section explains the terms used in the user guide.

If you are an intermediate user, you can hop over to the [Features](#features) section for the details of each command.

If you are an advanced user, you can see all the commands at a glance at the [Command Summary](#command-summary) section.

### Glossary

Terms | Explanation
--------|------------------
command | The text that you enter in the command box. Different commands have different formats.
prefix | A word or letter that ends with `/`. It is a short-handed notation that is used to specify the fields involved in a command. e.g. `n/` indicates that a name is involved.
parameter | A value that is defined based on your input and is immediately preceded by a prefix. e.g. Given a `p/` prefix which represents a phone number, followed by a `PHONE` parameter; if you input `98765432` in place of the `PHONE` parameter, the phone number holds a value of `98765432`.
alphanumeric characters | Words that consist of only English alphabets and/or numbers. Characters such as `@`, `?` and `%` are not alphanumeric. e.g. `2km`
integer | A number that has strictly no decimal places.
level | Refers to the education level of a student in the context of Singapore's education system.

### Application layout

![gui_layout.png](gui_layout.png)

The GUI of Track-O is divided mainly into 4 sections:
- `Menu Bar`: Navigation buttons that you can click to exit Track-O or open up a window containing a link to this User Guide. 
- `Tutee list`: A scrollable panel that shows a numbered list of your tutees.
  - The index number of the tutee list is the number that is assigned to each tutee in the numbered list.
- `Command box`: A text box where you can type in commands and hit `enter` to execute them.
- `Result panel`: A scrollable panel that shows the result of the command that you have just executed.
  - Note that some commands such as `get` will show a particular tutee's lessons in the form of a numbered list. Similar to the tutee list, the index number of a tutee's lesson refers to the number assigned to each lesson in the numbered list.

--------------------------------------------------------------------------------------------------------------------

## Setting up your first tutee

This section provides a quick guide to adding your first tutee and carrying out your first lesson. For more information
on each command, it can found under the [Features](#Features) section of our guide. To run a command, simply type the command in the command box and hit the Enter key on your keyboard.

### Before your lesson
1. Let's clear the existing sample data first. Run `clear` to remove the existing tutees.
2. To add in a new tutee, run `add n/John Tan l/p5 a/246 Hougang Ave sch/Rosyth School p/84567890`.
This will add in a tutee with the name `John Tan`, a `Primary 5` student from `Rosyth School`, living in `246 Hougang Ave` who can be contacted at `84567890`.
3. To add a lesson for this tutee, run `addlesson 1 subject/English d/7 s/14:00 e/16:00 rate/30`.
This will add an `English` lesson from `Sunday 2pm to 4pm` with the rate of `$30` per hour for John.
4. To state a date to receive payment by, run `payment 1 by/05-01-2022`. This means that you expect to collect the fees on
the 5th of January 2022.
5. Now run `get 1`. If you performed all the steps correctly, the application should look like this.

<img src="john_ug.png" width="95%"/>

### After your lesson
1. To add in the fees of this lesson, run `payment 1 lesson/1`. This will add in the total fees of the first lesson. Since
the rate was `$30` per hour over 2 hours, the final fees adds up to `$60.00`.
2. To add in any remarks for the lesson, run `remark 1 r/Good Progress!` and this set the comments `Good Progress!`
under the remarks for John.
3. If you have collected the fees for this lesson, run `payment 1 receive/` and this resets the payment value to `0.00`,
the pay-by date used in step 4 under [Before your lesson](#before-your-lesson), and updates John's last paid date to today's date.
4. Now run `get 1`. If you performed all the steps correctly, the application should look like this.

<img src="john_2_ug.png" width="95%"/>

### Managing your payments
1. To view the payment details of John, run `payment 1`. This shows us the existing payment details of John. 
2. To manually overwrite the payment amount John owes, run `payment 1 amount/100`. This sets the amount owed by John to
`$100.00`.
3. To receive the payment and set the next date to pay by in the same command, run `payment 1 receive/05-02-2022`.
This resets the value owed by John to `0` and sets the next date to pay by to `05-02-2022`.

### Managing your lessons
1. To view your schedule for the week, run `schedule` and this displays your upcoming lessons for the week.
2. To add in a new lesson to John, run `addlesson 1 subject/Math d/6 s/10:00 e/12:00 rate/40`. This will add a `Math` lesson from `Saturday 10am to 12pm` with the rate of `$40` per hour for John.  
3. To delete the first lesson from John, run `deletelesson 1 lesson/2`. This will delete the second lesson of John which was the `Math` lesson previously added. 

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…` after them can be used multiple times.<br>
e.g. `[t/TAG]…` tags are optional can be added multiple times: `t/friend`, `t/friend t/family` etc.<br>
e.g. `[subject/SUBJECT…]` subject keywords are optional and allows multiple keyword search: `subject/English Math Science`

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `p/12341234 p/56785678`, only `p/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `schedule`, `exit` and `clear`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### Viewing help : `help`

Shows a message explaining how to access the help page.

<p align="center">
    <img src="help_ug.png" width="85%"/>
</p>

Format: `help`

### Managing tutee's information

#### Adding a tutee: `add`

Adds a tutee to the existing list of tutees.

<img src="add_ug.png" width="95%"/>

Format: `add n/NAME p/PHONE sch/SCHOOL l/LEVEL a/ADDRESS [t/TAG]…`
* `n/NAME` and `[t/TAG]` can only take in alphanumeric characters and spaces.
* `p/PHONE` should only take in 8-digit phone numbers.
* `l/LEVEL` should only take in `p1` to `p6`, `s1` to `s5`, `j1` to `j2`.
* All entries should **not be blank**.

Examples:
* `add n/John Doe p/93456789 sch/Temasek Jc l/j2 a/135 Rivervale Link`
* `add n/Betsy Crowe l/p5 a/246 Hougang Ave 6 sch/Rosyth p/84567890 t/Northeast region`

#### Deleting a tutee : `delete`

Deletes the specified tutee from our list of tutees.

![](delete_ug.png)

Format: `delete INDEX`

* Deletes the tutee at the specified `INDEX`.
* The index refers to the index number tagged to each tutee in the tutee list.
* The index must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …

Examples:
* `delete 2` deletes the 2nd tutee in the tutee list.

#### Editing a tutee :  `edit`

Edits an existing tutee in the tutee list.

<img src="edit_ug.png" width="95%"/>

Format: `edit INDEX [n/NAME] [p/PHONE] [sch/SCHOOL] [l/LEVEL] [a/ADDRESS] [t/TAG]…`

* Edits the person at the specified `INDEX`.
* The index refers to the index number shown in the tutee list and **must be a positive integer** 1, 2, 3, …
* At least one of the optional fields must be provided.
* `n/NAME` and `[t/TAG]` can only take in alphanumeric characters and spaces.
* `p/PHONE` should only take in 8-digit phone numbers.
* `l/LEVEL` should only take in `p1` to `p6`, `s1` to `s5`, `j1` to `j2`.
* Existing values will be updated to the input values while all other values without input values remains unchanged.
* When editing tags, the existing tags of the tutee will be removed i.e adding of tags is not cumulative.
* You can remove all the tutee’s tags by typing `t/` without specifying any tags after it.
* All entries should **not be blank**.

Examples:
* `edit 1 p/91234567 a/345 Bedok North Ave 3` Edits the phone number and address of the 1st tutee to be `91234567` and `345 Bedok North Ave 3` respectively.
* `edit 2 n/Betty Chan t/` Edits the name of the 2nd tutee to be `Betty Chan` and clears all existing tags.

#### Finding tutee by fields : `find`

Filters the tutee list to display matches according to keywords.

<img src="find_ug.png" width="95%"/>

Format: `find [n/NAME…] [subject/SUBJECT…] [l/LEVEL] [overdue/OVERDUE_STATUS]`

* At least one of the optional filters must be provided.
* Keywords are case-insensitive.
* The returned tutee list contains matches that fulfills **all** the filters. If the filter has multiple keywords,
only tutees which fulfills **all** keywords will be returned.
* `name` filter can take **multiple keywords** to be matched and can only be alphanumeric characters.
* `subject` filter can take **multiple keywords** to be matched and can only be alphanumeric characters.
* `level` filter can only take **1 keyword** in the form of abbreviation.<br>
  e.g. `p5` for Primary 5, `s2` for Secondary 2
* `overdue` filter can only take **1 keyword**, either `yes` or `no`.

Example:
* Find all tutees with name containing `David` in the tutee list: `find n/david`.
* Find all tutees with name containing `David` and  `Lee` in the tutee list: `find n/david lee`.
* Find all tutees of level `Secondary 4`: `find l/s4`.
* Find all tutees taking `math` and `physics` classes: `find subject/math physics`.
* Find all tutees taking `math` classes with fees overdue: `find subject/math overdue/yes`.


#### Listing all tutees : `list`

Shows the full list of tutees stored.

Format: `list`

#### Get tutee's information : `get`

Gets the details of a specified tutee from the tutee list.

![](get_ug.png)

Format: `get INDEX`

* Gets the tutee at the specified `INDEX` in the format `Name: John Doe Level: P5`
* The index refers to the index number tagged to each tutee in the tutee list.
* The index must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …

<img src="clear_ug.png" width="95%"/>

Format: `clear`
Examples:
* `list` followed by `get 2` shows the 2nd tutee in the tutee list.

### Managing Remarks

#### Adding a remark to a tutee: `remark`

Adds a remark to the specified tutee with the provided `TEXT` input. New remarks will be appended to existing ones on 
a new line and will not overwrite them.

<img src="remark_ug.png" width="95%"/>

Format: `remark INDEX r/TEXT`

* Adds the desired `TEXT` to the tutee specified at the specified `INDEX`.
* The index refers to the index number tagged to each tutee in the tutee list.
* The index must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …

Examples:
* `remark 1 r/Went through Organic Chemistry`

#### Clearing all remarks of a tutee: `clearremark`

Clears all remarks of the specified tutee.

<img src="clearremark_ug.png" width="95%"/>

Format: `clearremark INDEX`

* Clears all remarks of the tutee specified at the specified `INDEX`.
* The index refers to the index number tagged to each tutee in the tutee list.
* The index must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …

Examples:
* `clearremark 1`

### Managing Lessons

#### Adding a lesson to a tutee : `addlesson`

Adds a lesson to the specified tutee from our list of tutees and to the user's schedule.

<img src="addlesson_ug.png" width="95%"/>

Format: `addlesson INDEX subject/SUBJECT d/DAY_OF_WEEK s/START_TIME e/END_TIME rate/HOURLY_RATE`

* Adds a lesson to the tutee at the specified `INDEX`.
* The index refers to the index number tagged to each tutee in the tutee list.
* The index must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …
* The lesson occurs on the specified `DAY_OF_WEEK`, from the specified `START_TIME` to the specified `END_TIME`, costing `HOURLY_RATE` dollars per hour.
* `DAY_OF_WEEK` **must be an integer in the range [1, 7]** where `1` to `7` corresponds to Monday to Sunday.
* `START_TIME` and `END_TIME` must be specified in an `HH:MM` format.
* The supported duration for a lesson is **30 min — 23 h 59 min**
* `HOURLY_RATE` **must be a positive number** expressed in either zero decimal places or two decimal places with the last decimal place (i.e. last digit) being `0` or `5`.
* If the lesson that is being added conflicts with an existing lesson belonging to any tutee, Track-O feedbacks that there is a schedule conflict,
and re-displays the information of the lesson that the user inputs.

Examples:
* `addlesson 1 subject/Biology d/4 s/11:30 e/13:30 rate/40.50`
* `addlesson 2 subject/Math d/5 s/19:30 e/21:30 rate/40.75`
* `addlesson 3 subject/Chemistry d/7 s/08:30 e/09:45 rate/40`

#### Deleting a lesson to a tutee : `deletelesson`

Deletes an existing lesson from the specific tutee's lesson list and user's schedule.

<img src="deletelesson_ug.png" width="95%"/>

Format: `deletelesson TUTEE_INDEX lesson/LESSON_INDEX`

* The tutee's index is the number displayed beside tutee's name in the filtered tutee's list.
* The lesson index is the number displayed beside the subject name after using `get` command on the tutee.
* `TUTEE_INDEX` and `LESSON_INDEX` are compulsory fields, an error message is produced if either one is missing.

Examples:
* Deleting **lesson 2** from **tutee 3**:
  `deletelesson 3 lesson/2`
* Deleting **lesson 3** from **tutee 1**:
  `deletelesson 1 lesson/3`

#### Tracking lesson schedule : `schedule`

Retrieves the user's schedule of lessons.

<img src="schedule_ug.png" width="95%"/>

Format: `schedule`

### Tracking Payments

Entering `payment` shows you all the payment-related commands available.<br>
Note that Track-O keeps track of fees up to $100,000, any payment command that results in the fees exceeding the amount will return an error.

#### To retrieve a specified tutee's payment details:

Format: `payment INDEX`

<img src="payment_ug.png" width="95%"/>

* Retrieves the payment details of the tutee at the specified `INDEX`.
* `INDEX` refers to the index number tagged to each tutee in the tutee list.
* `INDEX` must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …

Examples:
* `payment 1`

#### To add a specified lesson's fees to a specified tutee:

Format: `payment INDEX lesson/LESSON_INDEX`

<img src="payment_lesson_ug.png" width="95%"/>

* Adds the fees of the specified lesson at `LESSON_INDEX` to the specified tutee's payment details at `INDEX`.
* `INDEX` refers to the index number tagged to each tutee in the tutee list.
* `INDEX` must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …
* `LESSON_INDEX` must be within the size of the tutee's lesson list and **must be a positive integer** 1, 2, 3, …
* If the payment amount exceeds $100,000 after adding the lesson fees, Track-O returns and error message.
Examples:
* `payment 1 lesson/1`
* `payment 1 lesson/2`

#### To edit a specified tutee's payment amount:

Format: `payment INDEX amount/AMOUNT`

<img src="payment_amount_ug.png" width="95%"/>

* Changes the payment amount due by the specified tutee at `INDEX` to `AMOUNT`.
* `INDEX` refers to the index number tagged to each tutee in the tutee list.
* `INDEX` must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …
* `AMOUNT` **must be from 0 to 100,000** expressed in either zero decimal places or two decimal places with the last decimal place (i.e. last digit) being `0` or `5`.

Examples:
* `payment 1 amount/0`
* `payment 1 amount/80.50`
* `payment 2 amount/100`

#### To set a specified tutee's payment due date:

Format: `payment INDEX by/DUE_DATE`

<img src="payment_due_ug.png" width="95%"/>

* Changes the payment due date of the specified tutee at `INDEX` to `DUE_DATE`.
* `INDEX` refers to the index number tagged to each tutee in the tutee list.
* `INDEX` must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …
* `DUE_DATE` **must be later than or on the current date** expressed in the `dd-MM-YYYY` format.

Examples:
* `payment 1 by/25-12-2021`
* `payment 2 by/01-01-2022`

#### To receive a tutee's payment (and set a next payment due date):

Format: `payment INDEX receive/[DUE_DATE]`

<img src="payment_receive_ug.png" width="95%"/>

* Resets the payment amount due of the specified tutee to `0`.
* Resets the payment due date of the specified tutee at `INDEX` to `-`, or `DUE_DATE` if specified.
* Updates the specified tutee's last paid date in their payment details to the current date.
* `INDEX` refers to the index number tagged to each tutee in the tutee list.
* `INDEX` must be within the size of the tutee list and **must be a positive integer** 1, 2, 3, …
* `DUE_DATE` **must be later than or on the current date** expressed in the `dd-MM-YYYY` format, if specified.

Examples:
* `payment 1 receive/`
* `payment 2 receive/01-01-2022`

### Clearing all entries : `clear`

Clears the tutee list and the user's schedule.

Format: `clear`

### Exiting application : `exit`

Exits from the application.

Format: `exit`

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous Track-O home folder.

**Q**: Why does my application look slightly different?<br>
**A**: The screenshots in this User Guide are from an application running on macOS. If you are using Windows, your application would look something like this instead:

<img src="windows_ug.png" width="85%"/>

It is just a visual difference. Both applications have the same functionalities otherwise.

**Q**: Why doesn't pressing `F1` open the Help menu on my Mac?<br>
**A**: Try pressing `Fn` + `F1` (The Function and the F1 key together) instead. This is due to how macOS handles function keys.


--------------------------------------------------------------------------------------------------------------------

## Troubleshooting

### Installing Java 11

If you do not have Java 11 installed and are unsure of which version to download, refer to the follow steps:
1. Visit the Oracle website [here](https://www.oracle.com/java/technologies/downloads/#java11).
2. Scroll down until you see **Java SE Development Kit 11.0.13**. You should see something similar to the image below.

    <img src="download_java.png" width="130%"/>

3. Click on **Java 11**.
4. Select your own Operating System. If you are using a Mac or a MacBook, your Operating System is macOS. Otherwise, your Operating System is likely Windows. You may check your computer's [System Information](https://kb.wisc.edu/helpdesk/page.php?id=8208) to verify this.
5. Download the respective file. (You may need to register for an Oracle account) 
   1. For macOS users, download the file that ends with **.dmg**.
   2. For Windows users, download the file that ends with **.exe**.
   3. For Linux users, follow the instructions [here](https://docs.oracle.com/en/java/javase/11/install/installation-jdk-linux-platforms.html#GUID-4907E1A6-7B4B-4E98-9DA5-BF2A4D01AA57)
   to download Java 11.
6. For macOS and Windows users, once the **.dmg** or **.exe** file has been installed, double-click the file and follow the instructions provided to complete the installation.

### Installing Track-O (macOS)

For macOS users, you may receive an error similar to the one below when double-clicking **tracko.jar** for the first time.

<p align="center">
    <img src="download_1.png" width="35%"/>
</p>
 
Refer to the following steps to get started using Track-O:
1. Click on the "OK" to close the pop-up window.
2. Run **Spotlight** by pressing the Command key and Space Bar at the same time.
3. Type "Security & Privacy" and hit Enter. You should see a window similar to the one below:

    <p align="center">
        <img src="download_2.png" width="70%"/>
    </p>

5. Click on "Open Anyway" and a new window similar to the one below will pop up. 

    <p align="center">
        <img src="download_3.png" width="35%"/>
    </p>

6. Click on "Open" and Track-O will start.


--------------------------------------------------------------------------------------------------------------------


## Command summary

Action | Format, Examples
--------|------------------
**Help** | `help`
**Add tutee** | `add n/NAME p/PHONE sch/SCHOOL l/LEVEL a/ADDRESS [t/TAG]…` <br> e.g. `add n/James Ho p/87652345 sch/Anderson sec l/s4 a/200 Yio Chu Kang Road`
**Delete tutee** | `delete INDEX`<br> e.g. `delete 3`
**Edit tutee** | `edit INDEX [n/NAME] [p/PHONE] [sch/SCHOOL] [l/LEVEL] [a/ADDRESS] [t/TAG]…` <br> e.g. `edit 2 sch/Victoria Jc l/j1`
**Find tutee** | `find [n/NAME…] [l/LEVEL] [subject/SUBJECT…] [overdue/OVERDUE]`<br> e.g `find n/david subject/math`
**List all tutees** | `list`
**Get tutee information** | `get INDEX`<br> e.g. `get 2`
**Add remark** | `remark INDEX r/TEXT` <br> e.g `remark 1 r/Good progress.`
**Clear remarks** | `clearremark INDEX` <br> e.g `clearremark 1`
**View schedule** | `schedule`
**Add lesson to tutee** | `addlesson INDEX subject/SUBJECT d/DAY_OF_WEEK s/START_TIME e/END_TIME rate/HOURLY_RATE` <br> e.g `addlesson 1 subject/Biology d/4 s/11:30 e/13:30 rate/40.50`
**Delete Lesson from tutee** | `deletelesson TUTEE_INDEX lesson/LESSON_INDEX`<br> e.g `deletelesson 2 lesson/1`
**View payment details** | `payment INDEX` <br> e.g `payment 1`
**Add payment due** | `payment INDEX lesson/LESSON_INDEX` <br> e.g `payment 1 lesson/1`
**Edit payment due** | `payment INDEX amount/AMOUNT` <br> e.g `payment 1 amount/80.50`
**Set payment date** | `payment INDEX by/DUE_DATE` <br> e.g `payment 1 by/01-01-2022`
**Receive payment** | `payment INDEX receive/[DUE_DATE]` <br> e.g `payment 1 receive/01-02-2022`
**Clear** | `clear`
**Exit** | `exit`
