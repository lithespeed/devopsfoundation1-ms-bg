# devopsfoundation1-ms-bg
Node microservice illustrating BG deployment

node-docker-mircroservice

Learn Docker by building a Microservice!

Demonstrating key concepts of Docker using a Node.js microservice as an example.

Pre-requisites

You must have Docker installed for this code to work! Check the Installation Guide if you haven't got it installed.

Coding

To start or stop the test database, build the test-database image and run it:

cd ./test-database
docker build -t test-database .
docker run -it -p 3306:3306 test-database
Some commands for working with the test server:

cd ./users-service
npm install         # setup everything
npm test            # unit test - no need for a test database running
npm start           # run the server - you must have a test database running
npm run debug       # run the server in debug mode, opens a browser with the inspector
npm run lint        # check to see if the code is beautiful
You can also run the test server in its own container:

docker build -t users-service .
docker run -it -p 8123:8123 --link db:db -e DATABASE_HOST=DB users-service
Integration Testing

To test the entire stack, run:

docker-compose build
docker-compose -d up
sleep 10 # give the database server enough time to start!
cd integration-test && npm start && cd ..
docker-compose -d down


Thanks to  dwmkerr.com for this.
