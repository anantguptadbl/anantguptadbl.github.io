---
layout: post
title:  "Quickly Setting up MongoDB"
date:   2019-06-14 
categories: 
---

## MongoDB
MongoDB is a very actively used No-SQL database. An advantage of using this is the extensive community that is using it which helps one resolve issues quickly

### Installation
We will be installing MongoDB Community Edition on a Windows machine. The steps are similar for a Linux installation as well

#### Downloading the installer

##### Step 1
Go to the link https://www.mongodb.com/download-center/community?jmp=docs
and click on the download link

<img src="../images/mongoDBPage.png" style="float: left; margin-right: 10px;" />

##### Step 2
Once the installation is complete, make the following directory 
C:\data\db

##### Step 3
Traverse to the following path
C:\Program Files\MongoDB\Server\4.0\bin

##### Step 4
Run the following command
mongod

We will see a screen that looks something like this
<img src="images/mongod.png" style="float: left; margin-right: 10px;" />

##### Step 5
Run the following command
mongo

We will see a command prompt from where we can run all the mongo DB commands
<img src="images/mongo.png" style="float: left; margin-right: 10px;" />

``` python
# This is a simple repeated data set
data=np.array([0,1,0,-1,-1,0,1,0,-1,-1,0,1,0,-1,-1,0,1,0,-1,-1])
data=np.array(list(data)*100)
```
