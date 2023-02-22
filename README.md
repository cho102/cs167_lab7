# Lab 7

## Student information

* Full name: Cindy Ho
* E-mail: cho102@ucr.edu
* UCR NetID: cho102
* Student ID: 862151318

## Answers

* (Q1) What is your command to import the `contact.json` file?

    ```shell
    # Replace here
    mongoimport --collection=contacts --jsonArray contacts.json
    ```

* (Q2) What is the output of the import command?

    ```text
    # Replace here
    2023-02-22T00:03:37.082+0000	connected to: mongodb://localhost/
    2023-02-22T00:03:37.230+0000	1000 document(s) imported successfully. 0 document(s) failed to import.
    ```

* (Q3) What is your command to retrieve all users sorted by Name in ascending order?

    ```javascript
    // Replace here
    db.contacts.find().sort({Name:1})
    ```

* (Q4) What is your command to retrieve only the `_id` and `Name` sorted in reverse order by `Name`?

    ```javascript
    // Replace here
    db.contacts.find({_id:1},{Name:1}).sort({Name:-1})
    ```

* (Q5) Is the comparison of the attribute `Name` case-sensitive?


* (Q6) Explain how you answered (Q5). Show the commands that you ran and how would the output tell you if MongoDB applied case-sensitive or case-insensitive.


* (Q7) What is the command that retrieves the results in sorted order but without the `_id` field?

    ```javascript
    ```


* (Q8) What is the command to insert the sample document? What is the result of running the command?

    Command:
    ```javascript
    // Replace here
    ```

    Result:
    ```json
    ```

* (Q9) Does MongoDB accept this document while the `Name` field has a different type than other records?



* (Q10) What is your command to insert the record `{Name: ["Yuan", "Zhang"]}`?

    ```javascript
    // Replace here
    ```


* (Q11) Where did the two new records appear in the sort order?


* (Q12) Why did they appear at these specific locations?


* (Q13) Where did the two records appear in the ascending sort order? Explain your observation.


* (Q14) Is MongoDB able to build the index on that field with the different value types stored in the `Name` field?


* (Q15) What is your command for building the index?

    ```javascript
    // Replace here
    ```


* (Q16) What is the output of the create index command?

    ```text
    ```
