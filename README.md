## Client-Server Application with GUI using JavaFX

This client application is designed to manage objects within a collection, utilizing a relational database management system (PostgreSQL) for data storage. The application implements the following features:

+ Database Integration: Organizes the storage of the collection in a PostgreSQL relational database. The collection is no longer stored in a file.
+ ID Generation: Utilizes the database's sequence feature for generating ID fields.
+ Memory Collection Update: Updates the collection's state in memory only upon successfully adding an object to the database.
+ User Registration and Authentication: Implements user registration and authentication functionality, allowing users to specify passwords. Passwords are hashed using the SHA-384 algorithm for storage.
+ Command Execution Restriction: Disallows execution of commands by unauthorized users.
+ User Information Preservation: Stores information about the user who created each object in the database.
+ Object Access Control: Users can view all objects in the collection but can only modify objects belonging to them.
+ User Identification: Sends the login and password with each request for user identification.

# Features
+ Client-Server Communication: Facilitates communication between multiple clients and a server.
+ Graphical User Interface (GUI): Provides an interface for users to interact with the application.
+ Real-Time Updates: Supports real-time updates and notifications for clients.
+ Data Management: Allows users to manage and manipulate data efficiently through the GUI.
+ Scalability: Designed to be scalable, accommodating a growing number of clients and data.

# The functionality of the client includes:

1. Authentication/Registration Window: Allows users to authenticate or register an account.
2. Display of Current User: Shows information about the currently logged-in user.
3. Table View: Displays all objects from the collection with the following features:
   + Each field of the object is represented in a separate column of the table.
   + Users can filter/sort rows of the table based on the values of any column. Sorting and filtering are implemented using the Streams API.
4. Visualization Area: Visualizes objects in the collection with the following features:
   + Objects are drawn using graphical primitives such as Graphics, Canvas, or similar graphics library tools.
   + Visualization includes object coordinates and sizes.
   + Objects from different users are drawn with different colors.
   + Clicking on an object displays information about that object.
   + When an object is added/removed/modified, it should automatically appear/disappear/change in the visualization area for both the owner and all other clients.
   + Consistent animation is applied during object rendering, as per the instructor's guidelines.
5. Editing Fields: Users can edit individual fields of any object belonging to them. Editing an object can be initiated from the table displaying the list of objects or from the visualization area.
6. Deletion of Objects: Users can delete selected objects, even if the remove command has not been executed previously.

# Responsibilities of the server application:

1. Managing a collection of objects.
2. Purpose of automatically generated fields of objects in the collection.
3. Waiting for connections and requests from the client.
4. Processing received requests (commands).
5. Saving the collection when the application is terminated.
6. Saving a collection to a file when executing a special command that is available only to the server (the client cannot send such a command).

# The server application consists of the following modules:

1. Connection receiving module.
2. Request reading module.
3. Module for processing received commands.
4. Module for sending responses to the client.
     
# Usage
  + Launch the server application.
  + Launch the client application.
  + Use the graphical interface to interact with the application, such as sending messages, requesting data from the server, etc.

# List of available commands:
+ `help`: display help on available commands
+ `info`: print information about the collection (type, initialization date, number of elements, etc.) to standard output
+ `show`: Print to standard output all the elements of the collection in string representation
+ `add {element}`: add a new element to the collection
+ `update id {element}` : update the value of a collection element whose id is equal to the given one
+ `remove_by_id {id}`: remove an element from a collection by its id
+ `clear`: clear the collection
+ `save`: save the collection to a file
+ `execute_script file_name`: Read and execute a script from the specified file. The script contains commands in the same form in which the user enters them interactively.
+ `exit`: exit the program (without saving to a file)
+ `remove_greater {element}` : remove from the collection all elements greater than the given one
+ `remove_lower {element}` : remove all elements from the collection that are smaller than the given one
+ `history`: print the last 5 commands (without their arguments)
