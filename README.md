# Introduction to Application

### What it does:
Improves the Sprout Creak Farm e-commerence website through the new suite of retail APIs courtesy of IBM. 
The repository the contains the node.js app codebase can be found [here](https://github.com/dtt-projects/retail-app). 
This repository includes the files to containizerize that node.js app. 

### How it helps:
From a developer perspective, the application built on node,js tests out IBM’s suite of APIs. In addition, by 		containerizing the application, it allows the application to be easily shuttled between environments. From a consumer
perspective, the new and improved application allows a better user-experience at the retail-portion of the website.

### Dependencies:	
This [repository](https://github.com/dtt-projects/retail-app) is a node.js template repository that IBM created to assist Marist students redesign a retail website.
The repository allows developers to use bootstrap to build a small, but scalable node.js server from existing code.
IBM provides a suite of open-source tools and libraries such as the “express-generator”, which quickly creates an
application skeleton, to eliminate tedious work so that developers can spend more on time on the application. IBM gave
Marist students permission to actively change and clone the repository as developers saw fit. Refer to this repository
to learn more about the repository's structure the application dependencies. 


# How to Deploy Your Application

## Deploying the Application Locally

NOTE: Having access to a bash-based shell that can use Git is important for this project. If you are on Windows, it is suggested to either install the Linux subsystem for Windows, which gives you access to a true Linux-based Bash shell, or Git Bash for a simulated Bash shell on Windows.

### To install this project, you must first have the following items installed:

1. Node.js and the Node Package Manager (NPM). Please select the LTS version, NOT the latest version.
2. Git SCM (Note: Mac users may have to install XCode first)
3. Docker 

### Commands to verify installations:

	```
	npm -v
	node -v
	git --version 
	docker ps
	```
### Starting a Server
	
	```
	cd retail app
	npm install nodemon
	npm run start
	```
You should see the following output:

```
[nodemon] 1.19.1
[nodemon] to restart at any time, enter `rs`
[nodemon] watching: *.*
[nodemon] starting `node ./bin/www`
Begin server deployment Node.js script...
Free port captured: 3000. Normalizing for 'Express' object use.
Port successfully set to  3000
Server instance created.
Server successfully started on port  3000
Website active on: http://localhost:3000
From here, you can copy and paste the website link to your browser to view the website! In this particular example, you'd navigate to http://localhost:3000. When running in development mode, the port is always 3000.
```

### Running the Application

	```
	0.0.0.:30000
	```

To kill a development server, simply type CTRL+c on your keyboard in the terminal running the node process. This will kill the server immediately

### Containerizing Cloned Application on your Local Environment 

1. Enter into the etail-app repository

	```
	cd retail-app
	```

2. Create empty file called Dockerfile

	```
	touch Dockerfile
	```

3. Copy and paste contents within the file from the Dockerfile found in this repository 
	- Save and quit by Esc, and entering :wq!

4. Create empty file called .dockerignore

	```
	touch .dockerignore
	```

5. Copy and paste contents within the file from the .dockerignore found in this repository 
	- Save and quit by Esc, and entering :wq!

6. Build the image

	```
	docker build -t fedbrunp/node-web-app .
	```

7. Verify docker image has been created
	
	```
	docker images 
	```

8. Run the image 

	```
	docker run -p 49160:3000 -d fedbrunp/node-web-app
	```

9. Test the site by entering into your browser

	```
	0.0.0.0:49160
	```

### Running the Applicaiton via the VM instance on Google Cloud Platform 
Accessing the VM instance on Google Cloud Environment through the terminal on your device:

Must be on Marist’s network to connect to the VM. If not, VPN into the Marist Network using Cisco Any Connect, which you can download [here](https://v1.marist.edu/+CSCOE+/logon.html#form_title_text). Note: After entering your Marist credentials, select 'Tunnel-All'.

Open either Terminal or Command Prompt depending on if you are using an Apple product or Windows product and SSH into the VM instance on Google Cloud Platform

	ssh root@35.245.170.116
	Password: Maristcap2019

Once inside the VM, run the following commands to start the application:

	sudo systemctl start docker
	cd retail-app
	docker run -p 49160:3000 -d fedbrunp/node-web

Enter in your browswer:

	35.245.170.116:30000 or 35.245.170.116:49160 

# Node.js Container Architecture Diagram

![nodejscontainer](https://technology.amis.nl/wp-content/uploads/2017/05/image-56-702x336.png)
	

# IBM API REST SERVICES 

### GET/ Credit 
1. Description 
	- Get all credit cards in the table for the customer 
	- We know the customer based on the customerid associated with the cards
2. Security 
	- Client secret key apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- CustomerID 
		- Query credit cards based on customerid 
		- Type = Integer 
4. Preferred 
	- Query-based on credit card entry for a customerid 
	
### POST/ Credit 
1. Description  
	- Create new entries in the credit card table 
2. Security 
	- Client secret key apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- Creditcard
		- Contains details about the credit card to be added 

### PUT/ Credit/{CreditID} 
1. Description  
	- Updates existing credit cards 
2. Security 
	- Client secret key apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- CreditID 
		- Id for credit card information 

### DELETE /Credit/{CreditID} 
1. Description 
	- Remove an existing entry from the credit card table 
2. Security 
	- Client secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- CreditID
		- A lot of credit cards in the credit card table 
	- Accept 
		- Application / JSON and optional 

### GET /Customer 
1. Description 
	- Retrieve all entries stored in the customer table 
2. Security 
	- Client secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters
	- None 

### POST /Customer 
1. Description 
	- Creates a new entry in the customer table with details about the entry specified in the request body 
2. Security 
	- Client secret apiKey located in the header 
	- ClientId apiKey located in the header 
3. Parameters 
	- Creditcard 
		- Contains details about the customer entry to be created 

### GET /Customer/{CustomerID}
1. Description 
	- Get details about a specific entry in the customer table 
2. Security 
	- Client secret apiKey located in the header 
	- ClientID apiKey located in the header 
	- CustomerID 
		- The ID of a customer in the customer table 

### PUT /Customer/{CustomerID}
1. Description 
	- Updates an existing entry in the customer table with details about the entry specified in the request body 
2. Security 
-	 Client secret apiKey located in the header 
-	 ClientID apiKey located in the header  
3. Parameters 
	- CustomerID 
		- The ID of a customer in the customer table 
	- Customer
		- Contains details about the customer entry to be updated   

### DELETE /Customer/{CustomerID}
1. Description 
	- Removes an existing entry in the customer table 
2. Security 
	- Client secret apiKey located in the header.
	- ClientID apiKey located in the header 
	- CustomerID
		- Id of a customer in the customer table 

### GET /Inventory 
1. Description 
	- Retrieves all items in the inventory table.  Optionally, querying by merchantID or itemcat or itemdesc is permitted 
2. Security 
	- Client secret apiKey located in the header 
	- ClinetID apiKey located in the header 
3. Parameters 
	- MerchantID 
		- Query inventory items by merchantID 
	- Itemcat
		- Query inventory items by items category 
	- Itemdesc 
		- Query inventory items by item description 

### POST /Inventory 
1. Description 
	- Creates a new item in the inventory table with details about the item specified in the request body 
2. Security 
	- Client secret apiKey located in the header 
	- ClientId apiKey located in the header 
3. Parameters 
	- InventoryItem 
		- Contains details about the inventory item to be created 

### GET /Inventory/{InventoryID}
1. Description 
	- Retrieves details about a specific item identified by the itemID specified in the URL path 
2. Security 
	- Client secret apiKey located in the header 
	- ClientId apiKey located in the header 
3. Parameters 
	- InventoryID 
		- Id of an inventory item in the inventory table 

### PUT /Inventory/{InventoryID} 
1. Description 
	- Updates an existing item in the inventory table with details about the item specified in the request body. 
2. Security 
	- Client secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- InventoryID 
		- Id of an inventory item in the inventory table 
	- InventoryItem 
		- Contains details about the inventory item to be updated 

### DELETE /Inventory/{InventoryId} 
1. Description 
	- Removes an existing item in the inventory table 
2. Security 
	- Client secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- InventoryID 
		- Id of an inventory item in the inventory table

### GET /Merchant 
1. Description 
	- Retrieves every entry stored in the merchant’s table 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 

### POST /Merchant 
1. Description 
	- Creates a new entry in the merchant’s table with details about the entry specified in the request body 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- Merchant 
		- Contains details about the merchant entry to be created 
		- Contains details about the merchant entry to be created 

### PUT /Merchant/{MerchantID} 
1. Description 
	- Updates an existing entry in the merchant’s table with details about the entry specified in the request body 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
	- MerchantID 
		- Id of a merchant entry in the merchant’s table 

### DELETE /Merchant/{MerchantID} 
1. Description 
	- Removes an existing entry in the merchant’s table 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- MerchantID 
		- The ID of a merchant entry in the merchant’s table 

### GET /Shipper 
1. Description 
	- Retrieves every entry stored in the shipper’s table 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 

### POST /Shipper 
1. Description 
	- Creates a new entry in the shipper table with details about the entry specified in the request body 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientId located in the header 
	- Shipper 
		- Contains details about the shipper entry to be created 

### GET /Shipper/{ShipperID} 
1. Description 
	- Retrievs details about a specific entry identified by the shipperID specified in the URL path 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- ShipperID 
		- Id of a shipper entry in the shipper’s table 
	- Shipper 
		- Contains details about the shipper to be updated 

### DELETE /Shipper/{ShipperID} 
1. Description 
	- Removes an existing entry in the shipper’s table 
2. Security 
	- Client secret apiKey located in the header 
	- ClientId apiKey located in the header 
3. Parameters 
	- ShipperID 
		- Id of a shipper entry in the shipper’s table 

### GET /Order 
1. Description 
	- Retrieves all orders in the order tables
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters
	- TrackingID and CustomerNumber 
	- Optional 

### GET /Order/{OrderNum}
1. Description 
	- Retrieve a specific order identified by the OrderNum in the provided URL 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- OrderNum

### DELETE /Order/{OrderNum} 
1. Description 
	- Removes an existing entry in the orders table 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- OrderNum 

### POST /PlaceOrder 
1. Description 
	- Places an order for an item in the inventory channel. This service will check to make sure that the customer specified by the customerNumber has enough credit to place an order for the item (and quantity) specified. If allowed, the service will also verify that there is enough inventory remaining in order to fulfill the request 
2. Security 
	- Client Secret apiKey located in the header 
	- ClientID apiKey located in the header 
3. Parameters 
	- None
