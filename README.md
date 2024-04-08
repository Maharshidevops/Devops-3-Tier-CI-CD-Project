# Devops-3-Tier-CI-CD-Project

Welcome to the DevOps 3-Tier Project Deployment Guide! This guide will walk you through the steps to deploy and set up your project environment.

Overview
This project involves deploying a 3-tier application consisting of a frontend, backend, and MongoDB database. Below are the main components and steps involved:

-Cloning the Project: Clone the project repository to your local machine.
-Installing Node.js with NVM: Install Node.js using Node Version Manager (NVM).
-Setting up MongoDB Database: Install and configure MongoDB for your project.
-Navigating to Backend Directory: Move to the backend directory to install dependencies and start the backend server.
-Installing Required Dependencies: Install necessary dependencies for the backend.
-Importing Sample Data: Populate the MongoDB database with sample data.
-Starting the Backend Server: Start the backend server.
-Setting up the Frontend: Move to the frontend directory, install dependencies, configure environment variables, and launch the frontend development server.
-Allowing Necessary Ports: Configure inbound traffic rules on AWS to allow necessary ports.

Installation Instructions
Follow these step-by-step instructions to deploy the DevOps 3-Tier Project:

1. Clone the project repository: https://github.com/LondheShubham153/wanderlust.git
2. Install Node.js using NVM:

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
nvm install 21

3. Set up MongoDB Database:

sudo apt-get install gnupg curl
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org
sudo systemctl start mongod
Navigate to the backend directory and install dependencies:

4. cd backend
   npm i

5. Set up your MongoDB Database

Open MongoDB Compass and connect MongoDB locally at mongodb://localhost:27017.
Import sample data

To populate the database with sample posts, you can copy the content from the backend/data/sample_posts.json file and insert it as a document in the wanderlust/posts collection in your local MongoDB database using either MongoDB Compass or mongoimport.

mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray

6. Start the backend server:

npm start
Configure frontend environment variables:

7. cd frontend
cp .env.sample .env.local
Install frontend dependencies and launch the development server:

8. npm i
npm run dev

9. Allow nesseceroy port in inbound traffic rule on AWS

add your ipaddress and edit file .env.sample

cp .env.sapmle .env.local

frontend background start use nohup npm run dev -- --host &

10. Allow necessary ports in inbound traffic rules on AWS.
