---
title:  "Firebase Realtime Database"
date:   2017-06-24
author: Ashutosh Singh
categories:
- blog
tags:
- android
---


Realtime Database is one of the most important features of App development nowadays. It is required to handle data synchronization between client and server. It's much challenging to create a mobile app that allows user to access data from any device. We need to create API or web services to handle this. All of these challenges can fulfill by using `Firebase Realtime Database`.

### Firebase Realtime Database

`Firebase Realtime Database` is cloud hosted NoSQL(Non-Relational) database. It stores data in JSON form(not in tabular form). Its called Realtime due to synchronizing in realtime to all connected devices. All platforms app share one database instance and automatically receives updates with latest data. `Firebase Realtime Database` allows nesting data up to 32 levels deep. Developer can allow automatically database backup also.

### Key Feature of Firebase Realtime Database

* Realtime: Despite of typical HTTP requests, the `Firebase Realtime Database` uses data synchronization—every time data changes, all connected device receives that update within milliseconds.

* Offline: Firebase apps remain responsive even when offline because the Firebase Realtime Database SDK persists your data to disk. Once connectivity is reestablished, the client device receives any changes it missed.

* Accessible from Client Devices: Firebase Database can access directly from any client device. There is no need for any server.

### Rules

 The Realtime Database API is designed to only allow operations that can be executed quickly. Firebase Database Rules defines which user can read or write to the database. These rules are automatically applied to all query automatically. By default, rules are set to allow only authenticated users full read and write access to the database. There is four rule type for firebase.
 1. read: allow the user to read.
 2. write: allow the user to write.
 3. validate: allows you to apply validation logic using the same expressions used for .read and .write rules.
 4. indexOn: to specify ordering and querying data.

### Enable Offline Capabilties

Firebase app automatically handles the temrory network issue. Firebase used to cached data for user better experience. It persist user data to disk. Cached data is available while offline.
Ddeveloper can enable disk persistence with just one line of code.
```
FirebaseDatabase.getInstance().setPersistenceEnabled(true);
```

### Performaning Firebase Realtime Database Operations

This is my firebase database structure.
<img src="/static/firebase_database.png" alt="Drawing" style="width: 600px;"/>

To perform any operations on database we need developer need to get the reference of database

```
private DatabaseReference mDatabase;
mDatabase = FirebaseDatabase.getInstance().getReference();
```
It return the reference of top node. If developer need the reference of a perticular node then developer have to pass the node . The below code will return the reference of  `chat` node.
```
mDatabase = FirebaseDatabase.getInstance().getReference("chat");
```

#### Write Data to Firebase

We will store the chat object to database. For this first we have to create a chat model class.
```
public class ChatDTO {

    private String id;
    private String userName;
    private String message;

    public ChatDTO() {
    }

    public ChatDTO(String id, String userName, String message) {
        this.id = id;
        this.userName = userName;
        this.message = message;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getUserName() {
        return userName;
    }

    public void setUserName(String userName) {
        this.userName = userName;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }
}
```

As every chat needs a unique Id, you can generate one by calling push() method which creates an empty node with unique key. Then get the reference to `chat` node using child() method. Then use `setValue()` method to
store the chat data. By the below code a new chat object is stored with unique key value.

```
String id = mDatabaseReference.push().getKey();
ChatDTO chatDTO = new ChatDTO(id, name, message);
mDatabaseReference.child(id).setValue(chatDTO);
```

#### Read Data from Firebase

To read the data, you need to attach the `ValueEventListener()` to the database reference. This event will be triggered whenever there is a change in data in realtime. In `onDataChange()` you can perform the desired operations onto new data.

```
mDatabaseReference.addValueEventListener(valueEventListener);
ValueEventListener valueEventListener = new ValueEventListener() {
        @Override
        public void onDataChange(DataSnapshot dataSnapshot) {
          mChatDTOs.clear();
          Iterable<DataSnapshot> children =  dataSnapshot.getChildren();
            for (DataSnapshot snapShot : children){
                ChatDTO chatDTO =  snapShot.getValue(ChatDTO.class);
            }
        }

        @Override
        public void onCancelled(DatabaseError databaseError) {
            Log.e("error", databaseError.getMessage());
        }
    };
```
