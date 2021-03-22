
# myRetail RESTful service

myRetail is a rapidly growing company with HQ in Richmond, VA and over 200 stores across the east coast. myRetail wants to make its internal data available to any number of client devices, from myRetail.com to native mobile apps.

## Description

This is a Proof Of Concept (PoC) for products API that aggregates product data from multiple sources and returns it as JSON to the consumer.

This application performs the following actions: 
 *	Responds to an HTTP GET request at /products/{id} and delivers product data as JSON (where {id} will be a number. 
Example product IDs: 13860428, 54456119, 13264003, 12954218) 
 *	Example response: {"id":13860428,"name":"The Big Lebowski (Blu-ray) (Widescreen)","current_price":{"value": 13.49,"currency_code":"USD"}}
 *	Performs an HTTP GET to retrieve the product name from an external API. (For this exercise the data will come from redsky.target.com, but let’s just pretend this is an internal resource hosted by myRetail)  
 *	Example: http://redsky.target.com/v2/pdp/tcin/13860428?excludes=taxonomy,price,promotion,bulk_ship,rating_and_review_reviews,rating_and_review_statistics,question_answer_statistics
 *	Reads pricing information from a NoSQL data store and combines it with the product id and name from the HTTP request into a single response.
 *	Accepts an HTTP PUT request at the same path (/products/{id}), containing a JSON request body similar to the GET response, and updates the product’s price in the data store.


## API URL structure
```
GET Products - /products/prices

GET Product Name - products/{id}/name

GET Product Price - products/{id}/price

GET Product Details - /products/{id}

PUT Product Price - /products/{id}/price

GET All Product Prices - /products/prices
```

### API Examples
```
GET Product Name - localhost:8080/products/13860428/name

GET Product Details - localhost:8080/products/13860428

GET Product Price - localhost:8080/products/13860428/price

```

### Development Environment

* IDE - IDEA Intelli
* Version Control - Git
* Dependency Management - Maven 3.3.9
* Database - MongoDb NoSql
* RESTful Application framework - Spring Boot
* Programming language - Java 1.8
* Unit Testing library - JUnit, Mockito
* API Integration Testing - PostMan
* Operating System - Windows

## Installing and Running mongoDB
Below are the steps-

* Download the installer.
Download the MongoDB Community .msi installer
* Run the MongoDB installer
From Windows Explorer/File Explorer, go to C:\Program Files\MongoDB\Server\4.*\bin\ directory and double-click on mongo.exe.
* Create the data directory where MongoDB stores data. MongoDB’s default data directory path is the absolute path \data\db on the drive from which you start MongoDB.
To start MongoDB, run mongod.exe.
"C:\Program Files\MongoDB\Server\4.4\bin\mongod.exe" --dbpath="c:\data\db" 


## Running the application

```
java -jar target/myretail-0.0.1-SNAPSHOT.jar com.target.myretail.service.myRetailApplication
```
OR from the project root---> you can run 

```
mvn spring-boot:run
```
 
## Testing

Unit tests -- All cases covered are passed and tested for below files 

 * com.target.myretail.service.ProductServiceImplTest.java
 * com.target.myretail.utils.JsonUtilsTest.java

For End to end testing

PostMan Collection Link
https://www.postman.com/collections/2f51d6cb48e2163cea07

## Authors

* **Divya Gadi**
[GitHub](https://github.com/divyagadi/restfulApp)
