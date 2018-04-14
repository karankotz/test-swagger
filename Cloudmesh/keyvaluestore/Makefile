SWAGGERCODEGEN=java -jar swagger-codegen-cli-2.3.1.jar
YAML=keyval.yaml
EXECDIR=keyvaluestore/
OUTPUT=keyvaluestore/
REQDIR=keyvaluestore/server/flaskConnexion
RESTSERV=RESTServer

all: service start 
	
service: 
	mkdir $(EXECDIR)
	chmod 777 $(EXECDIR)
	wget https://www.dropbox.com/s/0730xoz8rboes7b/swagger-codegen-cli-2.3.1.jar
	$(SWAGGERCODEGEN) generate \
	-i $(YAML) \
	-l python-flask \
	-o $(OUTPUT) \
	-D supportPython2=true 

	sudo pip install virtualenv

	sudo virtualenv $(RESTSERV)

	sudo chmod 777 $(RESTSERV)

	sudo pip install requests==1.1.0 

	sudo pip install python-firebase

	cp -r *.py $(EXECDIR)/swagger_server/controllers

	cd $(EXECDIR) && sudo pip install -r requirements.txt

start: 
	cd $(EXECDIR) && python -m swagger_server

testGet: 
	curl http://0.0.0.0:8080/api/keyvaluestore 

testPost:
	curl -X POST http://0.0.0.0:8080/api/setkeyvalue?key=drive1

container:
	sudo docker build -t swagger:latest
	sudo docker run -d -p 8080:8080 swagger

clean: 
		sudo rm -rf $(OUTPUT)
		sudo rm *.jar
		sudo rm -rf $(RESTSERV)
