# Project Overview

## Project Name

OmniSync OrderHub

## Full Project Title

OmniSync OrderHub: Order, Inventory and Fulfillment Integration using SAP Integration Suite and AWS-hosted Services

## Business Context

OmniSync OrderHub is designed for a retail order-to-fulfillment integration scenario where customer orders are received from an external digital sales channel and processed through backend enterprise services.

In a typical retail landscape, customer orders may originate from an e-commerce storefront, marketplace, mobile application, or partner portal. These orders must be validated, checked against inventory availability, created in the ERP system, and forwarded to the logistics or shipment system for fulfillment.

SAP Integration Suite - Cloud Integration is used as the middleware layer to orchestrate this process between the external sales channel and backend systems.

## Business Problem

Retail organizations often operate with multiple disconnected systems for order capture, inventory management, ERP processing, shipment handling, and customer communication.

Without integration, the process may require manual data entry, repeated status checks, delayed order confirmation, and separate follow-up with warehouse or logistics teams. This can lead to processing delays, incorrect order creation, stock mismatch, and poor customer visibility.

OmniSync OrderHub addresses this problem by creating a centralized integration layer that connects order intake, inventory validation, ERP order creation, shipment initiation, and exception handling.

## Objective

The objective of this project is to design an enterprise-style integration package using SAP Integration Suite - Cloud Integration for real-time order processing.

The solution focuses on:

- Receiving order data from an external storefront or API client

- Validating mandatory business fields

- Routing valid and invalid orders separately

- Checking product availability with an inventory service

- Reserving stock before ERP order creation

- Creating sales order records in an ERP mock service

- Triggering shipment processing

- Capturing technical and business errors

- Supporting retry and monitoring for failed transactions

## System Landscape

The project uses the following systems:

- External Storefront / Postman Client

- SAP Integration Suite - Cloud Integration

- Inventory Service

- SAP S/4HANA Mock ERP Service

- Shipment Service

- Mail Notification Service

- SQL Database for mock backend records

- GitHub for documentation and version control

## Integration Scope

The current project scope covers the order-to-fulfillment process from order intake to shipment initiation.

The integration package includes:

1. Order Intake and Validation

2. Inventory Availability Check

3. Stock Reservation

4. ERP Sales Order Creation

5. Shipment Trigger

6. Exception Handling and Retry Design

7. Monitoring and Testing Documentation

## Out of Scope

The following items are not part of the initial project scope:

- Real payment gateway integration

- Real SAP S/4HANA tenant connection

- Production warehouse management system

- Customer-facing frontend UI

- Advanced tax calculation

- Real carrier tracking API

For this implementation, SAP S/4HANA and downstream services are represented using mock REST APIs so that the integration logic can be developed and tested in a controlled environment.

## Expected Business Value

The solution improves order processing by reducing manual work, standardizing data exchange between systems, improving transaction visibility, and enabling controlled error handling for failed messages.

It also provides a reusable integration design that can be extended to connect real SAP S/4HANA, warehouse, shipment, and notification systems in the future.
