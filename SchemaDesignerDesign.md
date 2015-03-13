# Introduction #

The current Schema designer works like this:
  1. Load schema from XML
  1. User edits schema and saves
  1. Updated XML sent to server
  1. New schema created based on new XML
  1. Data copied from old schema to new schema
  1. If 5 is successful, old schema is deleted and new schema is renamed in its place

This provides an all-or-nothing approach which has various problems, for example:
  * It can't tell the different between a table being renamed, or a table being deleted and a new one created (and therefore assumes the latter)
  * Saving changes to a large database takes a long time, since all data must be selected from the old tables and inserted into the new ones.
  * If an invalid schema is created, it's hard to tell the change that caused the problem since several may have been made
  * If data is copied to the new schema in the wrong order, it may fail due to foreign key dependencies not being met

# Proposal #

The proposed changes involve keeping the same interface, but changing the background workflow to speed things up, and make changes more atomic.
  1. Clone existing database using a command such as those detailed [here](http://stackoverflow.com/questions/876522/creating-a-copy-of-a-database-in-postgres) (this is a lot faster than SELECT/INSERTing each table)
  1. Load schema from XML
  1. As each edit is made, send appropriate CREATE/ALTER/DELETE TABLE statements to the server, editing the clone's schema, waiting for each command to be processed before another change can be made.
  1. If step 3 fails, a useful error message about the operation that just took place is displayed
  1. When save is clicked, the saved XML is updated to represent the new schema, the original database is deleted, and the clone is renamed to replace it.