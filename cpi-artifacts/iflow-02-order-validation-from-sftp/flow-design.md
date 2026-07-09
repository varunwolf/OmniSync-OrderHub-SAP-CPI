# iFlow 02 - Order Validation from SFTP

## Purpose

This integration flow reads staged order JSON files from the AWS EC2 SFTP inbox directory, validates mandatory order fields, and routes the files into separate folders based on validation result.

This is the second working integration flow of the OmniSync OrderHub project.

## Sender

AWS_EC2_SFTP

## Receiver

AWS_EC2_SFTP

## Adapters Used

- SFTP Sender Adapter
- SFTP Receiver Adapter

## Source Folder

inbox

Resolved EC2 Path:

/home/cpiuser/inbox

## Target Folders

Valid orders:

/home/cpiuser/processed

Invalid orders:

/home/cpiuser/error

## Flow Steps

AWS_EC2_SFTP  
→ SFTP Sender Adapter  
→ Start  
→ Groovy Script - Validate Order Payload  
→ Router - Check Order Validity  
→ Valid_Order branch  
→ SFTP Receiver - processed folder  

Invalid_Order branch  
→ SFTP Receiver - error folder

## Business Meaning

After raw order files are staged in the SFTP inbox by iFlow 01, this iFlow performs basic business validation before downstream ERP or inventory processing.

Valid order files are moved to the processed folder. Invalid or incomplete order files are moved to the error folder for review.

## Test Result

The iFlow successfully picked order JSON files from the inbox folder and routed them based on validation result.

Valid files created:

/home/cpiuser/processed/valid_order_20260709_230126.json  
/home/cpiuser/processed/valid_order_20260709_230123.json

Invalid file created:

/home/cpiuser/error/invalid_order_20260709_230128.json

## Status

Completed and tested successfully.
