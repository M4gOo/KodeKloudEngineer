
Amazon S3 is an object storage service with scalability, data availability, security, performance, and (11 9s) of data durability. 
The most durable storage cannot protect against human error or software bugs that could cause your applications to become corrupted or to accidentally delete data. 
With ransomware (Ransomware is a malware designed to deny a user or organization access to files on their computer) events on the rise, 
customers of all sizes are evaluating additional protection options against malicious tampering with their critical data in Amazon S3.

As with any data, it is best practice to have a backup and to put safeguards in place against malicious or accidental deletion.

### best practices with 

* Amazon S3 Versioning - which allows you to preserve, retrieve, and restore every version of every object stored in an Amazon S3 bucket.
 
* Amazon S3 Object Lock - can then be added on top of S3 Versioning to prevent data from being deleted or overwritten for a fixed amount of time, or indefinitely.
Object Lock - Store objects using a write-once-read-many (WORM) model
After you enable this feature, anyone with the appropriate permissions can put immutable objects in the bucket. You might be blocked from deleting the objects and the bucket.
 
* Amazon S3 Replication - for creating additional copies of your data in another AWS Region for multi-Region protection (works with both S3 Versioning and S3 Object Lock) to automatically copy objects across AWS Regions 
and separate AWS accounts.

* Amazon S3 Storage Lens - bring visibility of your current data protection levels and the usage of these features all together into a single dashboard.


### Lets create our LAB


Bucket names are globally unique across all AWS accounts.


We recommend that you disable ACLs (access control lists) except in unusual circumstances where you need to control access for each object individually. 
With Object Ownership, you can disable ACLs and rely on policies for access control.


Enable versioning


Enable default encryption for the bucket SSE-S3. These settings will apply to any objects uploaded to the bucket where you have not defined at-rest encryption details during the upload process. 


Advanced settings section, under Object Lock, select Enable


### UPLOAD SOME FILES


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/f8b8f2f0-903d-4092-bc9c-5b674ea07ab1)


With S3 Versioning enabled, only the owner of an Amazon S3 bucket can permanently delete a version
Keeping noncurrent versions of objects can increase your storage costs. You can use lifecycle rules to manage the lifetime and the cost of storing multiple versions of your objects. 


When versioning is enabled, a simple DELETE cannot permanently delete an object. Instead, Amazon S3 inserts a delete marker in the bucket, and that marker becomes the current version of the object with a new ID. 

#

Lests delete the new version (V2), turn off theshow versions

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/95ad03ab-2731-4f2e-89cc-2943f5383c39)


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/19732637-aa8e-4238-824a-93a8e126afa1)



Then, on the Objects tab, you will see the object appears to have been deleted.
Turn on Show versions. Notice that the top-level object is now listed as a Delete marker under the Type column, but both versions of the object are still available.

