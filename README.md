# Database Security Lab 03 (dbsec-lab03)

This project demonstrates the implementation of Public Key Cryptography (RSA) and Hashing (SHA1) within Microsoft SQL Server, as part of the Database Security curriculum.

## Overview

The database schema `QLSVNhom` manages students and academic staff while ensuring sensitive data remains secure. 

Key security implementations include:
- **Hashing**: Staff and student passwords (`MATKHAU`) are hashed using the `SHA1` algorithm.
- **Asymmetric Encryption**: Staff salaries (`LUONG`) are encrypted using `RSA_512` asymmetric keys protected by the Database Master Key (DMK).

## Project Structure

- `lab03.md`: The original laboratory assignment requirements.
- `lab03.sql`: The T-SQL script containing the database schema, constraints, and Master Key setup.

## Setup Instructions

1. Connect to your SQL Server instance via SSMS or Azure Data Studio.
2. Execute the `lab03.sql` script to generate the database, tables, and security keys.
3. Verify the creation of the `QLSVNhom` database.
