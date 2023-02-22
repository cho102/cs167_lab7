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
    db.contacts.find({},{_id:true ,Name:true}).sort({Name:-1})
    ```

* (Q5) Is the comparison of the attribute `Name` case-sensitive?
<br/>Yes, the attribute `Name` is case sensitive. 

* (Q6) Explain how you answered (Q5). Show the commands that you ran and how would the output tell you if MongoDB applied case-sensitive or case-insensitive.
<br/>I ran two commands:
    ```javascript
    db.contacts.find({},{_id:true ,Name:true}).sort({Name:-1})
    db.contacts.find({},{_id:true ,Name:true}).sort({name:-1})
    ```
And the first command returned the array with the name in reverse order but in the second command, the file was not sorted. 


* (Q7) What is the command that retrieves the results in sorted order but without the `_id` field?

    ```javascript
    db.contacts.find({},{_id:false, Name: true}).sort({Name:1})
    ```


* (Q8) What is the command to insert the sample document? What is the result of running the command?

    Command:
    ```javascript
    // Replace here
    db.contacts.insertOne({Name: {First: "Yuan", Last: "Zhang"}})
    ```

    Result:
    ```json
    {
	"acknowledged" : true,
	"insertedId" : ObjectId("63f5658f6fc599026c9b7886")
    }
    ```

* (Q9) Does MongoDB accept this document while the `Name` field has a different type than other records?
<br/>Yes, MongoDB accepted it.


* (Q10) What is your command to insert the record `{Name: ["Yuan", "Zhang"]}`?

    ```javascript
    // Replace here
    db.contacts.insertOne({Name: ["Yuan", "Zhang"]})
    ```


* (Q11) Where did the two new records appear in the sort order? <br/>
`{Name: {First: "Yuan", Last: "Zhang"}}` appear first in the output whereas `{Name: ["Yuan", "Zhang"]}` appeared between "Zoey Freeman" and "Yuna Williamson."

    ```text
    { "_id" : ObjectId("63f5658f6fc599026c9b7886"), "Name" : { "First" : "Yuan", "Last" : "Zhang" } }
    { "_id" : ObjectId("63f55bd9e505213f0889e232"), "Name" : "Zoey Stevens" }
    ...
    { "_id" : ObjectId("63f55f7d176bc8dc8479bb9c"), "Name" : "Zoey Freeman" }
    { "_id" : ObjectId("63f566036fc599026c9b7887"), "Name" : [ "Yuan", "Zhang" ] }
    { "_id" : ObjectId("63f55bd9e505213f0889e472"), "Name" : "Yuna Williamson" }
    ```

* (Q12) Why did they appear at these specific locations? <br/>

`{First: "Yuan", Last: "Zhang"}` is an object whereas `["Yuan", "Zhang"]` is an array. Therefore when comparing BSON types, objects have the highest order, 


* (Q13) Where did the two records appear in the ascending sort order? Explain your observation.

`{First: "Yuan", Last: "Zhang"}` appear at the very end whereas `["Yuan", "Zhang"]` appeared between "Victoria Woods" and "Yuka Allen."

* (Q14) Is MongoDB able to build the index on that field with the different value types stored in the `Name` field?
Yes, MongoDB was able to build the index on that field. 

* (Q15) What is your command for building the index?

    ```javascript
    // Replace here
    db.contacts.createIndex({Name: 1})
    ```


* (Q16) What is the output of the create index command?

    ```text
    {
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
    }
    ```
