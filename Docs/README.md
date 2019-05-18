                                       EVENT MANAGEMENT APPLICATION (EM-app)



**Brief description:**

This is an simple Event Managment application on private Sawtooth network that creates a distributed ledger with a decentralized platform. 

The advantages of this application include an immutable ledger, improved traceability, more efficiency, faster transactions, and cost-efficient.

EM-app (Event Managment Application) is a Simple application designed in such a way that an Event can be registered by giving the specific details by a user who has an authorized private key.
This application aims to demonstrate the working of a sawtooth network and how an application can be build on top of a hyperledger sawtooth network.

Here in this application in the beginning when the docker containers are turned up,a pair of publickey and private key named ("registration") is produced in the validator bash and can be used for acessing the application. Also by giving the
permissioning commands given below can be used to restrict the application from any other user and can be acessed only by the registration key.In this way we can set a certain number of keys permissioned to acess the application. This is done just to demonstrate the permissioning in sawtooth.

Note: if the permissioning commands is not given, application can be accessed by any private key. 

**System requirements:**

1. Operating system: Ubuntu 16.04
2. System RAM: 4 GB or above (recommended 8 GB)
3. Free System storage: 4 GB on /home


**Installation prerequisites:**

1. Docker must be installed in the system
2. docker compose must be installed


3. Ensure that NodeJS (version 8.15 ideally) is installed in the system. For more information about NodeJS, go to https://nodejs.org. To check if installed, open a terminal window: and give the command
   (-) node -v
4. If NodeJS is not installed, go to https://nodejs.org and download the compatible version (version 8.15) based on system OS, or in a terminal window: and give the command
   (-) sudo apt-get install -y nodejs
5. Ensure that Docker is installed. Docker is a platform for developers and system administrators to develop, ship, and run applications. For more information, go to https://www.docker.com/resources/what-container. To check if installed, in the terminal window: give the command
   (-) sudo docker --version
6. If Docker is not installed, in the terminal window:
   SET UP THE REPOSITORY
   Update the apt package index:
   (-) sudo apt-get update
   Install packages to allow apt to use a repository over HTTPS:
   (-) sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
   Add Docker’s official GPG key:
   (-) curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   Use the following command to set up the stable repository.
   (-) sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   (-)(lsb_release -cs) \
   stable"
   INSTALL DOCKER CE
   Update the apt package index.
   (-) sudo apt-get update
   Install the latest version of Docker CE.
   (-) sudo apt-get install docker-ce
   Verify that Docker CE is installed correctly by running the hello-world image.
   (-) sudo docker run hello-world
   This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.
7. Ensure that Docker Compose is installed. Compose is a tool for defining and running multi-container Docker applications. To check if installed, in the terminal window:
   (-) sudo docker-compose --version
8. If Docker Compose is not installed, in the terminal window:
   (-) sudo apt-get update
   (-) sudo apt-get install docker-compose


**Instructions for Installation of Application:**

1. Download the folder "EM-app"
2. Open terminal from the folder "EM-app" and give the command 
3. (-) sudo docker-compose up
4. This will turn up the Application and you can give permissioning if required by following the steps in permissioning or you can skip that and directly access the application by going to   http://localhost:3000


**Permissioning commands**
----------------------------------------------------------------------------------------------

5.  After running all the containers, Open another terminal from the same folder "EM-app" and give the command 

6. (-) sudo docker exec -it validator bash

7. This will open the validator bash and we have to set the permissions in this validator bash by giving the commands below

8. (-) sawset proposal create --key  ~/.sawtooth/keys/my_key.priv  sawtooth.identity.allowed_keys=$(cat ~/.sawtooth/keys/my_key.pub) --url http://rest-api:8008

9. (-) sawtooth identity policy create --key /root/.sawtooth/keys/my_key.priv policy_1 "PERMIT_KEY $(cat /root/.sawtooth/keys/my_key.pub)" "PERMIT_KEY $(cat /root/.sawtooth/keys/registration.pub)" --url http://rest-api:800​8 

10. Now set the role as transaction signer for Family name "Event_Managment_App" for the keys under the policy file name policy_1

(-) sawtooth identity role create --key ~/.sawtooth/keys/my_key.priv transactor.transaction_signer.Event_Managment_App policy_1 --url http://rest-api:8008 

11. Now give the below commands to view the keys of each department. Using these private keys we can access the UI

 cat ~/.sawtooth/keys/registration.priv


------------------------------------------------------------------------------------------

12. Now go to the browser and go to http://localhost:3000
13. Now you can access the application using the corresponding departments private key
14. To terminate the app execution, go to the terminal window (where docker-compose is running) and give CTRL+C
15. Wait for docker-compose to gracefully shutdown. Then: give the command
    (-) sudo docker-compose down








