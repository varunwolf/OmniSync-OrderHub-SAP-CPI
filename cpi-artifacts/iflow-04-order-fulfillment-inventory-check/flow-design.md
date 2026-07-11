# iFlow 04 - Order Fulfillment Inventory Check

## Purpose

This integration flow reads validated order files from the AWS EC2 SFTP processed folder, extracts product SKU and quantity, calls the Inventory API, and routes the order based on stock availability.

This is the fourth working integration flow of the OmniSync OrderHub project.

## Business Scenario

After an order is validated, the next business step is to check whether the ordered product is available in inventory.

If stock is available, the order is sent to the fulfillment folder.

If stock is not available, the order is sent to the backorder folder.

## Flow Design

AWS EC2 SFTP processed folder  
→ SAP CPI SFTP Sender  
→ Groovy Script - Prepare Inventory Request  
→ Request Reply  
→ HTTP Receiver - Inventory API  
→ Groovy Script - Prepare Fulfillment Result  
→ Router - Check Inventory Status  
→ Available_Stock branch  
→ SFTP Receiver - fulfillment folder  

Out_Of_Stock branch  
→ SFTP Receiver - backorder folder

## iFlow Details

Name: Order Fulfillment Inventory Check

ID: Order_Fulfillment_Inventory_Check

Runtime Profile: Cloud Integration

Sender: AWS_EC2_SFTP

Receivers:
- Inventory_API
- AWS_EC2_SFTP
- AWS_EC2_SFTP_Backorder

## Source Folder

processed

Resolved EC2 path:

/home/cpiuser/processed

## Target Folders

Available stock orders:

/home/cpiuser/fulfillment

Out-of-stock orders:

/home/cpiuser/backorder

## Archive Folder

/home/cpiuser/processed_archive

This folder is intended to store files already picked by iFlow 04 and avoid duplicate processing.

## Inventory API Endpoint

http://13.51.163.250:3000/inventory/check

## Inventory API Request Format

```json
{
  "sku": "P1001",
  "qty": 2
}
