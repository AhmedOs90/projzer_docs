
# API Documentation

## Overview
This document provides information about the API endpoints for the project. All endpoints return JSON responses.

---

## Base URL
```
http://35.234.96.134:3000
```

---

## Endpoints

### 1. **Filter Products**
- **URL**: `/products/filter`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "abv": "number",
    "abvOperator": "string",
    "vegan": "boolean",
    "glutenfree": "boolean"
  }
  ```
- **Response**:
  - **Success** (200):
    ```json
    [
      {
        "id": 4,
        "name": "Product A",
        "producerId": 1,
        "productCategoryId": 2,
        "abv": "5.00",
        "source_url": "http://example.com/productA",
        "description": "This is Product A",
        "vegan": 1,
        "glutenfree": 0,
        "sugar_per_100ml": "10.50",
        "kcal_per_100ml": "50.00",
        "images": "http://example.com/imageA.jpg",
        "enabled": 1,
        "created_at": "2024-09-25T22:50:22.000Z"
      }
    ]
    ```

---

## 2. Filter Producers

- **URL**: `/producers/filter`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "ownedBy": "Company Name",
    "brand": "Brand Name"
    }
  ```
- **Response**:
  - **Success** (200):
    ```json
    [
        {
            "id": 1,
            "name": "Producer One",
            "brand": "Brand One",
            "ownedBy": "Company A",
            "countryId": 1,
            "url": "http://producerone.com",
            "created_at": "2024-09-28T20:57:23.000Z"
        },
        {
            "id": 2,
            "name": "Producer Two",
            "brand": "Brand Two",
            "ownedBy": "Company B",
            "countryId": 2,
            "url": "http://producertwo.com",
            "created_at": "2024-09-28T20:57:23.000Z"
        }
    ]
    ```
---

## 3. Filter Availability

- **URL**: `/availability/filter`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "productId": 1,
    "resellerId": 2,
    "countryId": 3,
    "price": 19.99
    }
  ```
- **Response**:
  - **Success** (200):
    ```json
    [
        {
            "id": 1,
            "productId": 1,
            "resellerId": 2,
            "countryId": 3,
            "price": 19.99,
            "last_seen": "2024-09-25T22:50:22.000Z"
        },
        {
            "id": 2,
            "productId": 1,
            "resellerId": 3,
            "countryId": 3,
            "price": 20.50,
            "last_seen": "2024-09-26T10:00:00.000Z"
        }
    ]

    ```
---

## 4. Filter Reseller

- **URL**: `/resellers/filter`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "countryId": 1
    }
  ```
- **Response**:
  - **Success** (200):
    ```json
       [
        {
            "id": 1,
            "name": "Reseller A",
            "online": true,
            "address": "123 Main St, City",
            "url": "http://example.com/resellerA",
            "countryId": 1
        },
        {
            "id": 2,
            "name": "Reseller B",
            "online": false,
            "address": "456 Elm St, City",
            "url": "http://example.com/resellerB",
            "countryId": 1
        }
    ]
    ```
---
## 5. Product Category

- **URL**: `/categories`
- **Method**: `GET`
- **Request Body**:
  ```json
  {
    "category_name": "Beverages"
    }
  ```
- **Response**:
  - **Success** (200):
    ```json
        [
            {
                "id": 1,
                "category_name": "Beverages"
            },
            {
                "id": 2,
                "category_name": "Snacks"
            }
        ]
    ```
---
## 6. Countries

- **URL**: `/countries`
- **Method**: `GET`
- **Request Body**:
  No input parameters required.

- **Response**:
  - **Success** (200):
    ```json
        [
            {
                "countryid": 1,
                "name": "United States"
            },
            {
                "countryid": 2,
                "name": "Canada"
            }
        ]
    ```
---
## 7. States

- **URL**: `/states`
- **Method**: `GET`
- **Request Body**:
```json
      {
            "countryid": 1
        }
  ```
- **Response**:
  - **Success** (200):
    ```json
       [
            {
                "stateid": 1,
                "name": "California",
                "countryid": 1
            },
            {
                "stateid": 2,
                "name": "Ontario",
                "countryid": 2
            }
        ]
    ```
---
## 8. Currencies

- **URL**: `/currencies`
- **Method**: `GET`
- **Request Body**:
  No input parameters required.

- **Response**:
  - **Success** (200):
    ```json
        [
            {
                "currencyid": 1,
                "name": "US Dollar",
                "usd_rate": 1.0000
            },
            {
                "currencyid": 2,
                "name": "Euro",
                "usd_rate": 1.2000
            }
        ]
    ```
---
## 9. Source_sites

- **URL**: `/source_sites`
- **Method**: `GET`
- **Request Body**:
  No input parameters required.

- **Response**:
  - **Success** (200):
    ```json
        [
            {
                "id": 1,
                "name": "Example Source",
                "url": "http://example.com",
                "type": "Online"
            },
            {
                "id": 2,
                "name": "Another Source",
                "url": "http://anothersource.com",
                "type": "Retail"
            }
        ]
    ```
---
## Error Handling
- **400 Bad Request**: Invalid request format or parameters.
- **404 Not Found**: The requested resource does not exist.
- **500 Internal Server Error**: An error occurred on the server.

---

