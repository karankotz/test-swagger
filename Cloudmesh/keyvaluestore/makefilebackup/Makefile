SWAGGERCODEGEN=java -jar /home/sai/Desktop/Swagger/Swag/swagger-codegen-cli-2.3.1.jar
YAMLFILE=keyval.yaml 
DESTDIR=server/keyvalstore/flaskconnexion
CREATED=server
KEYVALDIR=keyvalstore

all: service1 start
		@echo "DONE"

dest:
		mkdir -p $(DESTDIR)

service1: dest 
		  $(SWAGGERCODEGEN) generate \
		  -i /home/sai/Desktop/TestRepo/Cloudmesh/keyvaluestore/keyval.yaml \
		  -l python-flask \
		  -o /home/sai/Desktop/TestRepo/Cloudmesh/keyvalstore/server/keyvaluestore/flaskConnexion \
		  -D supportPython2=true


service: dest 
		 wget https://www.dropbox.com/s/0730xoz8rboes7b/swagger-codegen-cli-2.3.1.jar?dl=1
		 $(SWAGGERCODEGEN) generate \
		 -i $(YAMLFILE) \
		 -l python-flask \
		 -o $(DESTDIR) \
		 -D supportPython2=true

		 cp -r *.py $(DESTDIR)/swagger_server/controllers

start: 
		cd $(DESTDIR) && python -m swagger_server

test:   
		curl http://0.0.0.0:8080/api/keyvaluestore 
stop:
	 ps | grep swagger |grep -v "grep" | awk '{print $$1}' | xargs kill -9

clean: 
		rm -rf $(CREATED)
		rm *.jar








