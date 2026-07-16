# Azure Queue Storage

1. What is it?

Azure Queue Storage is a **message queue service** used to **temporarily store tasks or messages until another application or service is ready to process them**. It allows one service to continue its work immediately while another service processes the task later in the background      (asynchronously).

Example: When a user uploads a PDF, the application places a message in the queue. A background worker later reads the message, processes the PDF, and creates embeddings without making the user wait.

2. When to use it?

Use Azure Queue Storage when you need to:

* Process background tasks
* Handle asynchronous operations
* Enable communication between different services

3. Equivalent service in AWS

**Amazon Simple Queue Service (SQS)**


1. `Azure Example`

    Suppose you have an e-commerce website.

    When a customer places an order:

    Customer
        │
        ▼
    Website

    Instead of immediately:

    Sending an email
    Updating inventory
    Generating an invoice
    Notifying the shipping system

    the website simply writes a message to Azure Queue Storage.

    Customer
        │
        ▼
    Website
        │
        ▼
    Azure Queue Storage
        │
        ├── Order #1001
        ├── Order #1002
        └── Order #1003

    Now background services process these messages one by one at there feasible time.

    Azure Queue Storage
            │
            ├────────► Email Service
            ├────────► Inventory Service
            ├────────► Invoice Service
            └────────► Shipping Service

    All this services are connected to Azure Queue storage

    The website responds to the customer immediately:

    ✅ "Your order has been placed."

    while the background services continue working independently.