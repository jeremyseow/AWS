# Versioning

- Versioning is a means of keeping multiple variants of an object in the same bucket

- With versioning, you can easily recover from both unintended user actions and application failures
	- Protection from accidental deletion
	- Recovering an earlier version
	- Retrieving deleted objects

- Versioning is turned off by default

- When you turn on versioning, Amazon S3 will create new versions of your object every time you overwrite a particular object key
	- You can have ==two objects with the same key, but different version IDs==
	- You can retrieve any of the particular objects that you need using `GET` on the object key name and the particular version

![[S3 Versioning.png]]

- When a delete request is issued against a versioned bucket on a particular object, ==S3 still retains the data, but it removes access for users to retrieve that data==
	- S3 places a delete marker on top of that object, which means that if you perform a `GET` on it, you will receive an error as if the object does not exist
	- However, an administrator, or anyone else with the necessary permissions, could remove the delete marker and access the data


#### Pricing
- When calculating cost for your bucket, you must calculate as though every version is a completely separate object that takes up the same space as the object itself