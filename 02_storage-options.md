# Cloud Storage

- High performance, internet-scale
- Simple administration
  - Doesn't need capacity managment

object storage?
It's not the same as file storage,
in which you manage your data as a hierarchy of folders.
It's not the same as block storage,
in which your operating system manages your data as chunks of disk.
Instead, object storage means you save to your storage here,
you keep this arbitrary bunch of bytes I give
you and the storage lets you address it with a unique key (often in the form of URLs).
fully managed scalable service.

Cloud Storage is not a file system
because each of your objects in Cloud Storage has a URL

he storage objects are immutable,
which means that you do not edit them in place but instead you create new versions

Cloud Storage always encrypts your data on
the server side before it is written to disk 

are organized into buckets.
When you create a bucket, you give it a globally unique name.
You specify a geographic location where the bucket and
its contents are stored and you choose a default storage class


there are several ways to control access to your objects and buckets.
For most purposes, Cloud IAM is sufficient.
Roles are inherited from project to bucket to object.
If you need finer control,
you can create access control lists - ACLs - that offer finer control

Each ACL consists of two pieces of information,
a scope which defines who can perform the specified actions, for example,
a specific user or group of users and a
permission which defines what actions can be performed.

Cloud Storage objects are immutable.
You can turn on object versioning on your buckets if you want.
If you do, Cloud Storage keeps a history of modifications. That is,
it overrides or deletes all of the objects in the bucket.

If you don't turn on object versioning,
new always overrides old.

Cloud Storage also offers lifecycle management policies

## Classes

![](images/cloud-storage-classes.png?raw=true)
