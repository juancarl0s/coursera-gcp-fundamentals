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

## Move data
gsutil which is the cloud storage command from this cloud SDK.
You can also move data in with a drag and drop in the GCP console,
if you use the Google Chrome browser.
But what if you have to upload terabytes or even petabytes of data?
Google Cloud platform offers
the online storage transfer service and the offline transfer appliance to help.
The storage transfer service lets you schedule
and manage batch transfers to cloud storage from
another cloud provider from a different cloud storage region or from an HTTPS endpoint.
The transfer appliance is a rackable,
high-capacity storage server that you lease from Google Cloud.
You simply connect it to your network, load it with data,
and then ship it to an upload facility where the data is uploaded to cloud storage.
This service enables you to securely
transfer up to a petabyte of data on a single appliance

mport and export tables from and to BigQuery as well as Cloud SQL.
You can also store App Engine logs,
cloud data store backups,
and objects used by App Engine applications like images.
Cloud storage can also store instant startup scripts,
Compute Engine images, and objects used by Compute Engine applications.
In short, cloud storage is often the ingestion point for data being
moved into the cloud and is frequently the long-term storage location for data.
