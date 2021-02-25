# lab7-1: Configuring Permissions
## <img align="left" src="../images/ConstructionSign.png">Sorry, this lab has not been reviewed recently and may contain:
  - outdated technical informatiom
  - spelling errors, grammar errors, and poor markdown formatting

## OBJECTIVE

In this lab, you will practice creating users, creating groups, and granting
permissions to both.

## SETUP

There are no special setup steps for this lab.

## STEPS

On server1, create the following groups and grant them ownership to the
documents as described below:

 1.  Create the groups "sales" and "acct"
 2.  Make users "patrick" and "percilla" members of the sales group
 3.  Make "paul" a member of the acct group
 4.  Create directories /data/sales and /data/acct, both owned by root
 5.  Make the sales group owner of /data/sales and the acct group the owner of
     /data/acct
 6.  Make sure only members of the sales group can create files in /data/sales
 7.  Make sure only members of the acct group can create files in /data/acct
 8.  Make sure members of either group can read files created in the other
     group's directory
 9.  Make sure only the creator of a file in either of these directories can
     delete it
10.  Make sure nobody outside of either of these groups, besides root, has any
     access to the directories
11.  Ensure newly created files are owned by the group owning the directory
     they are in
12.  Create files in both directories to test your work
