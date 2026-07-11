# OmniSync OrderHub - SAP CPI Integration Project

## Project Overview

OmniSync OrderHub is an end-to-end SAP Integration Suite project that demonstrates order intake, SFTP staging, order validation, inventory checking, and fulfillment routing using SAP Cloud Integration, AWS EC2 SFTP, and a Node.js Inventory API.

This project simulates a real-world order management integration scenario where external order data is received, validated, checked against inventory, and routed for fulfillment or backorder processing.

---

## Architecture Summary

External Client / Postman  
→ SAP CPI HTTPS Sender  
→ AWS EC2 SFTP inbox  
→ SAP CPI SFTP Sender  
→ Groovy Validation  
→ Router  
→ Processed / Error folders  
→ Inventory API Check  
→ Fulfillment / Backorder folders

---

## Technologies Used

- SAP Integration Suite
- SAP Cloud Integration / CPI
- HTTPS Sender Adapter
- SFTP Sender and Receiver Adapter
- HTTP Receiver Adapter
- Request Reply Pattern
- Groovy Script
- AWS EC2 Ubuntu Server
- OpenSSH SFTP Server
- Node.js
- Express.js
- PM2 Process Manager
- Postman
- Git and GitHub

---

## Completed Integration Flows

### iFlow 01 - Order Intake to SFTP Staging

Receives order JSON from Postman or an external client through HTTPS sender and stores the raw order file in AWS EC2 SFTP inbox folder.

Status: Completed and tested successfully.

### iFlow 02 - Order Validation from SFTP

Reads order files from SFTP inbox, validates mandatory fields using Groovy script, and routes valid orders to processed folder and invalid orders to error folder.

Status: Completed and tested successfully.

### iFlow 03 - Order Inventory Check

Receives SKU and quantity from Postman, calls the AWS EC2 Inventory API, and returns stock availability response.

Status: Completed and tested successfully.

### iFlow 04 - Order Fulfillment Inventory Check

Reads validated order files from processed folder, extracts SKU and quantity, calls the Inventory API, and routes orders to fulfillment or backorder based on inventory status.

Status: Completed and tested successfully.

---

## AWS EC2 Folder Structure

```text
/home/cpiuser/inbox
/home/cpiuser/processed
/home/cpiuser/error
/home/cpiuser/fulfillment
/home/cpiuser/backorder
/home/cpiuser/processed_archive# OmniSync OrderHub

## Smart Order, Inventory and Fulfillment Integration using SAP Integration Suite and AWS EC2

OmniSync OrderHub is an end-to-end SAP Cloud Integration project that simulates a real-world retail order-to-fulfillment integration scenario.

## Business Scenario

A retail company receives customer orders from an online storefront hosted on AWS EC2. The order data is validated, checked against inventory, sent to ERP for sales order creation, and then passed to a shipment system for delivery processing.

## Technologies Used

- SAP Integration Suite - Cloud Integration
- SAP CPI Integration Flows
- AWS EC2
- REST APIs
- HTTPS Adapter
- Content Modifier
- Router
- Groovy Script
- Message Mapping
- Exception Subprocess
- Data Store / JMS Retry Design
- Postman
- SQL Database Schema

## Main Features

- Customer order intake through HTTPS endpoint
- Order payload validation
- Content-based routing
- Inventory availability check



