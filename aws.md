Cloud computing
- AWS
- Google Cloud
- Microsoft Azure

Spot Instance
- Cheaper
- If a big job comes in, they will kick you off.

Storage
- Up to 30GiB for free.
- It's harder to increase later on.

Tags
-

Preferences
- Get emails to tell you how much it's costing you.

- IP Addresses
  - Create one
  - Associate to the Instance

### Add user
`sudo adduser jtirtanata`
- in home, you can see all of the user folders.
- you can delete the user with `userdel`
- User privileges
  - sudo visudo : give us all of the privileges
    - Edit permissions here
    - root ALL=(ALL:ALL)ALL

- Set up user account
- switch user `su`


# Postgres Set Up
```bash
sudo su -postgres # Switch user to Postgres
vim /etc/postgresql/9.5/main/postgresql.conf
```
- Change `listen_addresses = * `
  - Allows everyone to connect to the psql
- Switch back to your user to restart
```bash
vim /etc/postgresql/9.5/main/pg_hba.conf
```
- This allows you to connect to the postgres from Metis

- Next, make a rule in security group in AWS to complete this.
