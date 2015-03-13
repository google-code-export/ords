# Introduction #

One of the initial user requirements of the ORDS was that users should be able to make their whole database open to the public. Somehow this objective got lost somewhere along the way, but we have early adopters with this requirement, so it does need to be implemented sooner rather than later.

# Requirements #

  * Public should be able to view all data in a publicly-accessible database
  * Public should be able to download a copy of a publicly-accessible database
  * Public should be able to query a publicly-accessible database within the ORDS
  * Public should not have to register or log in to the ORDS in order to access public databases
  * It should be clear how to cite a database held in ORDS


# Details #

Might be worth approaching this in stages.

Please add suggestions for technical solutions here...

David suggests adding a new class of user - 'public'

Most sensible way to enable public access to projects would probably be to turn a project title in the 'search project' list into a clickable URL that take the user to a limited project page showing:
  * Name of Project
  * Other project metadata
  * 'Contact' button for project (as on the project list)
  * NOT the list of project members - probably best to keep that private
  * Clickable list of (accessible) databases in that Project

Clicking on a database should take the user to the database page, from which they should be able to view, but not edit, the database schema, go to the tables list, or go to the list of saved (publicly accessible) datasets. Also download databases

The tables list should work as it usually does - can go to data viewing interface (but not add, edit, or delete records) and to data querying interfaces.


We should enable a project to come up with a preferred format for citation by adding an additional editable metadata field for each database. This will allow them to specify exactly who should be given credit for what.