## Task 1: Install Docker

### Instructions

1. Follow the instructions on the Docker website: [Docker Installation Guide](https://docs.docker.com/get-started/) to install Docker on your machine.

2. Verify the installation by running the following command:

`docker --version`

Example of successful `docker --version`


<img width="472" alt="image" src="https://github.com/RevoU-FSSE-2/week-6-audiprevio/assets/126348614/44dc76e9-421d-4e4e-8ddb-50400afbac98">


## Task 3: Dockerize the Node.js project

### Instructions

1. Clone the Node.js project from GitHub: `https://gist.github.com/berdoezt/e51718982926f0caa3fcd8ed45111430`
2. Create a `Dockerfile` in the project directory with the following content:

```Dockerfile
# This Dockerfile will create a Docker image that can be used to run the Node.js project
# from GitHub.

FROM node:16-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the package.json file to the working directory
COPY package.json .

# Install the dependencies
RUN npm install

# Copy the rest of the project files to the working directory
COPY . .

# Set the command to start the application
CMD ["npm", "start"]
```

3. Build the Docker image:
Copy code
`docker build -t node-app .`

4. Run the Docker container:
Copy code
`docker run -it node-app`

## Dockerfile with Comment Explanation

```Dockerfile
# This Dockerfile will create a Docker image that can be used to run the Node.js project
# from GitHub.

FROM node:16-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the package.json file to the working directory

## Dockerfile with Comment Explanation

```Dockerfile
# This Dockerfile will create a Docker image that can be used to run the Node.js project
# from GitHub.

FROM node:16-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the package.json file to the working directory
COPY package.json .

# Install the dependencies
RUN npm install

# Copy the rest of the project files to the working directory
COPY . .

# Expose the port on which the Node.js app will run
EXPOSE 3001

# Set the command to start the application
CMD ["npm", "start"]
```

# Explanation:

The `FROM` command specifies the base image that the Docker image will be built on. In this case, we are using the node:16-alpine image, which is a lightweight version of the Node.js image.

The `WORKDIR` command sets the working directory for the Docker image. This is the directory where the application will be run.

The `COPY` commands copy the package.json file and the rest of the project files to the working directory.

The `RUN` command runs the npm install command to install the dependencies for the application.

The `CMD` command specifies the command that will be run when the Docker container starts. In this case, we are running the npm start command, which will start the Node.js application.

# Guide to Create package.json for Node.js Project in Visual Studio Code
In case you have no package.json in your working directory yet, you need to create one. Else, you cannot run node.Js through dockerized container

### Step 1: Open Visual Studio Code
Launch Visual Studio Code and open the folder where you want to create your Node.js project.

### Step 2: Create a New File
Create a new file in the root of your project folder and name it package.json. You can do this by right-clicking on the folder in the Explorer panel, selecting "New File," and then typing package.json as the filename.

### Step 3: Add package.json Content
In the newly created package.json file, add the basic structure of the package.json manually. Here's an example of a simple package.json:
```
{
    "name": "nodejs-docker-app",
    "version": "1.0.0",
    "description": "A simple Node.js app for Dockerization",
    "main": "app.js",
    "dependencies": {
        "http": "^0.0.1-security"
    },
    "scripts": {
        "start": "node.app.js"
    }
}
```

You can customize the fields as per your project's requirements. For example, you can add dependencies under the "dependencies" section or devDependencies under the "devDependencies" section.

### Step 4: Save the File
Save the package.json file once you have added the desired content.

### Step 5: Install Dependencies
To install the dependencies specified in your package.json, open the integrated terminal in Visual Studio Code and run:
`npm install`
This will install all the dependencies mentioned in the "dependencies" section.

### Step 6: Commit (Optional)
If your project is version-controlled with Git, you can commit the package.json file to your repository.


# Improving and Running the app.js through a Dockerized Node.JS
Save the changes to the Dockerfile, and then rebuild the Docker image using the docker build command:

Run the App.js through dockerized NodeJs by using
`docker build -t nodejs-app .`


To rebuild the node.js incase you make any changes to the package.json
`docker run -p 3001:3001 nodejs-app`
