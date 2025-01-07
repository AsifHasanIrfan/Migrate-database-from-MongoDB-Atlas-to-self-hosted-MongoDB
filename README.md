# Migrate-database-from-MongoDB-Atlas-to-self-hosted-MongoDB

## Description
Migrating a database from MongoDB Atlas to a self-hosted MongoDB instance involves exporting the data from Atlas and importing it into your self-hosted MongoDB. Below is a step-by-step guide to achieve this migration smoothly.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Export-Data-from-MongoDB-Atlas](#export-data-from-mongodb-atlas)
- [Step-by-Step Migration Guide](#step-by-step-migration-guide)

## Prerequisites
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

## Export Data from MongoDB Atlas
You can use the `mongodump` tool to export data from MongoDB Atlas.

### Step 1: Get the MongoDB Atlas Connection String
