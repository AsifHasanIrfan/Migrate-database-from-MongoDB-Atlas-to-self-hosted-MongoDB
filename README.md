# Migrate-database-from-MongoDB-Atlas-to-self-hosted-MongoDB

## Description
Migrating a database from MongoDB Atlas to a self-hosted MongoDB instance involves exporting the data from Atlas and importing it into your self-hosted MongoDB. Below is a step-by-step guide to achieve this migration smoothly.

## Table of Contents
- [Prerequisites](#prerequisites)
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
