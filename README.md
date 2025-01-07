# Migrate-database-from-MongoDB-Atlas-to-self-hosted-MongoDB

## Description
Migrating a database from MongoDB Atlas to a self-hosted MongoDB instance involves exporting the data from Atlas and importing it into your self-hosted MongoDB. Below is a step-by-step guide to achieve this migration smoothly.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Export-Data-from-MongoDB-Atlas](#export-data-from-mongodb-atlas)
- [Import-Data-into-Self-Hosted-MongoDB](#import-data-into-self-Hosted-mongodb)
- [Verify-the-Migration](#verify-the-migration)
- [Step-by-Step Migration Guide](#step-by-step-migration-guide)

## 1. Prerequisites
Before starting the migration, ensure the following:

1. **MongoDB Installed on Self-Hosted Server**: 
   - Install MongoDB on your self-hosted server. You can follow the official MongoDB installation guide for your operating system.

2. **MongoDB Tools Installed**: 
   - Install the MongoDB Database Tools (`mongodump` and `mongorestore`) on your local machine or server.

For **Ubuntu**:
   ```bash
   sudo apt install mongodb-database-tools
   ```
For **MacOS**:
   ```bash
   brew install mongodb-database-tools
   ```

3. **Access to MongoDB Atlas**: 
   - Please ensure you have the connection string for your MongoDB Atlas cluster.

4. **Network Configuration**: 
   - Ensure your self-hosted MongoDB instance is accessible (e.g., open the necessary ports like `27017`).

## 2. Export Data from MongoDB Atlas
You can use the `mongodump` tool to export data from MongoDB Atlas.

### Step 1: Get the MongoDB Atlas Connection String

1. Log in to your MongoDB Atlas account.
2. Navigate to your project and select your cluster.
3. Click **Connect** and choose **Connect Your Application**.
4. Copy the connection string. It should look something like this:
   `mongodb+srv://<username>:<password>@cluster0.mongodb.net/mydatabase`

### Step 2: Run mongodump

Use the `mongodump` command to export the data from MongoDB Atlas.

```bash
mongodump --uri="mongodb+srv://<username>:<password>@cluster0.mongodb.net/<database_name>" --out=/path/to/backup
```

**Example**:
  ```bash
   mongodump --uri="mongodb+srv://admin:password@cluster0.mongodb.net/mydatabase" --out=/backups/mongodb
   ```

This will create a backup of the `mydatabase` database in the `/backups/mongodb` directory.

## 3. Import Data into Self-Hosted MongoDB

Once you have exported the data, you can use the `mongorestore` tool to import it into your self-hosted MongoDB instance.

### Step 1: Ensure MongoDB is Running

Make sure your self-hosted MongoDB instance is running

```bash
sudo systemctl start mongod
```

### Step 2: Run mongorestore

Use the `mongorestore` command to restore the data into your self-hosted MongoDB instance:

```bash
mongorestore --host localhost --port 27017 --db <database_name> /path/to/backup/<database_name>
```

**Example**

```bash
mongorestore --host localhost --port 27017 --db mydatabase /backups/mongodb/mydatabase
```

This will restore the `mydatabase` database into your self-hosted MongoDB instance.

## 4. Verify the Migration

After restoring the data, verify that the migration was successful.

### Step 1: Connect to Self-Hosted MongoDB

Use the `mongosh` shell to connect to your self-hosted MongoDB instance:

```bash
mongosh
```

### Step 2: Check Databases

List all databases to ensure your database is present:
```bash
show dbs
```

### Step 3: Check Collections

Switch to your database and list its collections:
```bash
use mydatabase
show collections
```

### Step 4: Check if the Collection Has Data

```bash
db.collection_name.countDocuments()
```

By following this step-by-step guide, you can successfully migrate your MongoDB database from MongoDB Atlas to a self-hosted MongoDB instance.
