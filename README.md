

#                                                                                                              AURA
                                                                                                       Elevate Your Fashion

## **Overview**

This repository contains the architectural design and implementation for a scalable and efficient eCommerce platform using **Next.js**, **Sanity CMS**, and third-party API integrations. The solution focuses on creating a seamless user experience, efficient product management, order processing, and shipment tracking.

---

## **Technologies Used**

- **Frontend**:  
  - **Next.js**: React-based framework for building a fast, SEO-friendly, and scalable frontend.
  
- **Backend**:  
  - **Sanity CMS**: Headless content management system (CMS) for managing products, user data, and orders.
  
- **Third-Party APIs**:
  - **Stripe**: For secure payment gateway integration.
  - **ShipEngine**: For real-time shipment tracking and order delivery updates.

---

## **Architecture Flow**

The system architecture consists of several components working together to create a cohesive workflow. Here is an overview of the key components:

1. **Frontend (Next.js)**:
   - Handles the user interface for browsing products, adding to the cart, and proceeding to checkout.
   - Communicates with the backend to fetch product data and manage orders.

2. **Sanity CMS (Backend)**:
   - Manages and stores product details, user data, and orders.
   - Provides APIs to fetch product data and manage orders dynamically.

3. **Payment Gateway (Stripe)**:
   - Securely processes payments and updates the order status once payment is confirmed.

4. **Shipment Tracking API (ShipEngine)**:
   - Provides real-time updates on shipment status, ensuring users are informed about their delivery.

5. **Real-Time Data API**:
   - Updates stock levels, wishlist items, and user data in real-time.

---

## **Key Features**

- **User-Friendly Interface**:  
  - Product browsing with categorization, filtering, and sorting.
  - Smooth checkout process and easy order management.
  
- **Dynamic Content**:  
  - The frontend dynamically fetches product data from **Sanity CMS** based on user interactions.

- **Secure Payment**:  
  - Payment transactions are securely processed via **Stripe**, and payment status is updated in the backend.

- **Real-Time Shipment Tracking**:  
  - Shipment details are fetched in real-time via **ShipEngine**, and users can track their orders on the frontend.

- **Inventory Management**:  
  - Real-time stock updates fetched from **Sanity CMS** ensure accurate product availability.

---

## **API Endpoints**

The system uses various API endpoints to facilitate communication between the frontend and backend:

| **Endpoint**             | **Method** | **Purpose**                         | **Response Example**  |
|--------------------------|------------|-------------------------------------|-----------------------|
| `/products`              | GET        | Fetch all product details           | `{ "name": "Product", "slug": "product-slug", "price": 100 }` |
| `/order`                 | POST       | Submit new order details            | `{ "orderId": 123, "status": "success" }` |
| `/shipment-tracking`     | GET        | Fetch real-time tracking updates    | `{ "trackingId": "AB123", "status": "In Transit" }` |
| `/delivery-status`       | GET        | Fetch express delivery tracking     | `{ "orderId": 456, "deliveryTime": "30 mins" }` |
| `/inventory`             | GET        | Fetch real-time stock levels        | `{ "productId": 789, "stock": 50 }` |
| `/cart`                  | POST       | Add product to cart                 | `{ "cartId": 101, "items": [...] }` |
| `/wishlist`              | POST       | Add product to wishlist             | `{ "wishlistId": 202, "items": [...] }` |

---

## **High-Level System Architecture**

The system's architecture involves the following high-level flow:

```
+------------------------+               +-----------------------+
|   Frontend (Next.js)    | ------------> |      Sanity CMS        |
|  (User Interaction)     |   Fetches Product Data   +-----------------------+
|                        | <------------+ Product Data API    |   
|                        |               +-----------------------+  
+------------------------+                      |
            |                                    |
            v                                    v
+------------------------+               +-----------------------+   
|     Order Data         | <--------->  |      Sanity CMS        |
|  (Order Details)       |               |   (Stores Order Info)  |
+------------------------+               +-----------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+ 
| Payment Gateway API    | <--------->  |  Sanity CMS            |  
|   (Stripe API)         |               |  (Stores Payment Info) |  
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Shipment Tracking    | <--------->  |   ShipEngine API       |
|    (Tracking Updates)  |               |   (Real-Time Tracking) |
+------------------------+               +------------------------+ 
            |                                    |
            v                                    v
+------------------------+               +------------------------+
| Third-Party API        | <--------->  |     Real-Time Data     |
|  (External Integrations) |             |    (Stock, Wishlist)   |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|      Inventory API     | <--------->  |  Sanity CMS            |
| (Fetch Real-Time Stock)|               |   (Inventory Management)|
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Cart API             | <--------->  |  Sanity CMS            |
| (Manage Cart Items)    |               | (Manage Cart Data)     |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Wishlist API         | <--------->  |   Sanity CMS           |
| (Manage Wishlist Items)|               | (Manage Wishlist Data) |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
| Order Confirmation     |  <---------> |  Sanity CMS            |
|   (Order ID, Summary)  |               | (Confirm Order)        |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Shipment Dispatch    |  <---------> |   ShipEngine API       |
|  (Shipping Label)      |               | (Generate Tracking)    |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Delivery Tracking    |  <---------> |   ShipEngine API       |
|  (Track Delivery)      |               | (Real-Time Delivery)   |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   Order Delivered      | <----------- |   Sanity CMS           |
| (Final Confirmation)   |               | (Update Order Status)  |
+------------------------+               +------------------------+
            |                                    |
            v                                    v
+------------------------+               +------------------------+
|   User Notification    | <--------->  |   Sanity CMS           |
| (Email/SMS Notification)|              | (Send Delivery Status) |
+------------------------+               +------------------------+
```


---

### **Contributions**

Feel free to open issues or pull requests to suggest improvements or report bugs. Contributions are welcome!

