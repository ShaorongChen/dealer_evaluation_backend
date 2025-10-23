# Product List Microservice

## Overview
This microservice provides an API for retrieving a list of products and their associated dealers.

## Features
- Get list of products
- Get dealers for specific product
- CORS support for cross-origin requests

## Endpoints
- `GET /products` - Returns list of all products
- `GET /getdealers/<product>` - Returns dealers for specified product

## Usage
To build and run using IBM Cloud CE:
```bash
ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source .
```

Other Command
```bash
# Get Deployed Instances
ibmcloud ce app get --name prodlist -q
# Update set min. Instances
ibmcloud ce app update --name prodlist --min 2
# To delete the application
ibmcloud ce application delete --name prodlist
```

## Requirements
- Python 3.13
- Flask
- Flask-CORS

## File Structure
```
.
├── app.py              # Main application file
├── Dockerfile          # Docker build file
└── products.json       # Product data file
```

---

# Dealer Evaluation Backend

## 🚀 Overview
This is a microservice backend that provides price information for products across different dealers.

## 🔧 Features
- **Price Lookup**: Get the price of a specific product from a dealer
- **All Prices**: Get all prices for a product across all dealers

## 📦 Installation
```bash
npm install
```

## Usage
To build and run using IBM Cloud CE:
```bash
ibmcloud ce application create --name dealerdetails --image us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source .
```

Other Command
```bash
# Get Deployed Instances
ibmcloud ce app get --name dealerdetails -q
# Update set min. Instances
ibmcloud ce app update --name dealerdetails --min 2
# To delete the application
ibmcloud ce application delete --name dealerdetails
```

## 🛠️ Usage
### Price Lookup
```
GET /price/:dealer/:product
```
Example: `GET /price/Binglee/Headphones`

### All Prices
```
GET /allprice/:product
```
Example: `GET /allprice/Printer`

## 📝 Notes
- The server listens on port 8080 by default
- Dockerfile is provided for containerization

## 🚨 Important
- This service uses CORS middleware to allow cross-origin requests
- The JSON file contains dealer information with product prices
- The server will return a message if a product or dealer is not found

## 📚 References
- [Express.js Documentation](https://expressjs.com/)
- [CORS Middleware](https://www.npmjs.com/package/cors)