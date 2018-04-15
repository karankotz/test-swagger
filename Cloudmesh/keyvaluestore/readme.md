# ASSIGNMENT TO BUILD A SWAGGER REST API IN ORDER TO ACCESS THE KEYVALUESTORE AND POST THE VALUES TO THE KEYVALUESTORE, THE FIRESTORE IS USED IN THE BACKEND TO SAVE THE KEYS AND VALUES THAT THE SWAGGER API CONNECTS WITH (FIREBASE - DATABASE IS USED).

## REST API END POINTS AND THE SERVICES 

* Firebase in the google cloud platform that provides the space to store in a NO-SQL database that can accessed via cloud or other API's

* This swagger API fetches the simple keyvaluestore that is added in the firebase database 

* The post and the get methods are implemented with the below end points

	* /api/keyvaluestore

	* /api/setkeyvalue

## Options for the Make file 

* Build and run the docker container and start the service with the following command.

	make docker-all 

* To only build the docker container with the following command 
	
	make docker-build

* To only run the container after the build 

	make docker-run

* To pull the docker container locally 

	make docker-pull

*

## Instructions to run the docker container
	
	* The docker pull can be used to run the container 
	* docker pull karan/swagger 

## Clone the Project into a folder and navigate to the directory swagger/Cloudmesh/keyvaluestore
	
	make docker-run 

## Testing the dockerized swagger API 

## Get

### Get the keyvaluestore

curl -X GET http://0.0.0.0:8080/api/keyvaluestore

Example result of the above call:

	{
	  "KeyValueStore": {
	    "File": {
	      "Size ": "100 GB",
	      "Time Created": "January 4th 2018"
	    },
	    "Memory": {
	      "RAM Size": "16 GB"
	    },
	    "Ram": {
	      "-L4xGK_uvGZP30zLzz8R": "Dynamic"
	    },
	    "Drive2": {
	      "-L5_GRJ5JDqaz1dJuH8q": "None"
	    },
	    "Motherboard": {
	      "-L5_YK_sbqh6oiq3ptxe": "None"
	    }
	  }
	}

   
# POST

### Posting the Key value to the database 

* The curl call for the post method is as below 

	curl -X POST http://0.0.0.0:8080/api/setkeyvalue?key=drive9

where the drive9 is key and the default value of the key is set to null.

* Return value is "Post Successfull" if it is successfully 	   inserted into the firestore.

Example result of the above call:

	{
	  "KeyValueStore": "Post Successfull"
	}


## The container id at the runtime can be found with the following command 
 	
	sudo docker ps

### Example of the container ID 
	CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
	536dccdec049        swag3               "python -m swagger_s…"   5 seconds ago       Up 4 seconds        0.0.0.0:8080->8080/tcp   hungry_mahavira


### References and acknowledgements 
I have referred the repositories hid-sp18-405 and hid-sp18-409 in order to create the Makefile with respect to the swagger service that I have implemented.


