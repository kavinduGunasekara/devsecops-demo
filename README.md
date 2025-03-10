![5 run projectlocaaly](https://github.com/user-attachments/assets/4088a0ca-09d1-42b9-80cc-e2f863e35e38)# DevSecOps Pipeline Implementation for Tic Tac Toe Game

![Screenshot 2025-03-04 at 7 16 48 PM](https://github.com/user-attachments/assets/7ed79f9c-9144-4870-accd-500085a15592)

![image](https://github.com/user-attachments/assets/5b2813a5-f493-4665-8964-77359b5be93a)

##Learn 
1. What is DevSecOps?
2. Why is DevSecOps

1. What is DevSecOps?
DevSecOps is essentially DevOps with a security mindset. While DevOps focuses on development and operations, DevSecOps integrates security at every step of the process. It’s not just about securing CI/CD pipelines but includes any task where security concerns are addressed during DevOps processes, such as:

** Infrastructure as Code (IaC): Ensuring security within your Terraform, Ansible, and Kubernetes configurations.
  using tf to automate AWS If you are working on this task and if you make sure the sensitive 
  information in the TF files is put in Valut because Terrform intergrated with vault
and you take care of files with remote backend , then this is also considered as devsecops
Ansible : when you woking with ansible within your ansible playbook file if you ensure there 
are no sensitive things like API token or there is nothing sensitive in your playbook and you 
will put all of that in vault and integrate that with ansible it is also devsecops

k8s sensitive info put in secret you make sure that your API server is protected
  etcd is encrypted all of this also comes under Dev secops
  
   DevSecOps is not only securing CI/CD pipelines but includes any task where security concerns are addressed during DevOps processes.

**2. Why is DevSecOps Gaining Significance?**
DevSecOps has gained traction due to two primary reasons:

a. Growing Use of AI Assistance
Many developers use AI assistants to write code. However, AI might generate code that:

Hardcodes secrets like API tokens.

Uses old versions of packages that may contain critical vulnerabilities.

Integrates vulnerable packages, opening up security risks.(allowing hackers to your applicatiom)

Without DevSecOps, these risks can go undetected. DevSecOps pipelines catch these issues by 
checking for hardcoded secrets or outdated packages an d packages with critical vulnerabilities.

b. Cybersecurity Risks
Developers sometimes use outdated versions of packages (like Log4j) without considering known 
vulnerabilities(id this vulnerable not caouch by the ci cd then this log4j applicatiom
invites the Bad actors to gain access to your application.
. Additionally, developers might hardcode sensitive information, like API tokens,then this not 
affect for the running of the application so it moved from  the dev to stage to production
environment with in prod if this hardcoded API token or any  sensitive information is logged in 
the application then your API token then every body can see the api token and access it 
which can later be exposed if not properly managed. With DevSecOps, security measures such as 
scanning for vulnerabilities, auditing code for secrets, and other security checks are added to 
CI/CD pipelines.

when you work on ci cd for applcation do not directly jump to write ci cd pipeline
need to better idea about the applciation

   **See our Typescript  application**
## Features

- 🎮 Fully functional Tic Tac Toe game
- 📊 Score tracking for X, O, and draws
- 📜 Game history with timestamps
- 🏆 Highlights winning combinations
- 🔄 Reset game and statistics
- 📱 Responsive design for all devices

## Technologies Used

- React 18
- TypeScript
- Tailwind CSS
- Lucide React for icons

## Project Structure

```
src/
├── components/
│   ├── Board.tsx       # Game board component
│   ├── Square.tsx      # Individual square component
│   ├── ScoreBoard.tsx  # Score tracking component
│   └── GameHistory.tsx # Game history component
├── utils/
│   └── gameLogic.ts    # Game logic utilities
├── App.tsx             # Main application component
└── main.tsx           # Entry point
```

## Game Logic

The game implements the following rules:

1. X goes first, followed by O
2. The first player to get 3 of their marks in a row (horizontally, vertically, or diagonally) wins
3. If all 9 squares are filled and no player has 3 marks in a row, the game is a draw
4. Winning combinations are highlighted
5. Game statistics are tracked and displayed

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/devsecops-demo.git
   cd devsecops-demo
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn
   ```

3. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. Open your browser and navigate to `http://localhost:5173`
   

## Building for Production

To create a production build:

```bash
npm run build
# or
yarn build
```
![3do build](https://github.com/user-attachments/assets/94c4924f-28db-4c31-9be5-f22a3eb0be43)

The build artifacts will be stored in the `dist/` directory.

Acess the project locally

![5 run projectlocaaly](https://github.com/user-attachments/assets/d775811c-db69-408c-b8ee-e21a5451f544)

## Start DevSecOps pipeline
Before devsecops you need to learn continerize
learn how to write docker file and how to build the docker image locally after go to devsecops 

How to write Dockerfile
You can write docker file in three simple step 
 you did it locally
 
1. download dependencies
2. build application
3. once you build the application you get the disc folder
4. copy disck folder on the **Nginx** (it will be webserver it can be nginx or what ever)


If you have these in your docker file  docker image also work

How do we do it it's always best practice to use multistage docker files or Docker build
previous what we will do
**First Stage**
1. dowonload dep
2. build
3. create the artifact

**Second Stage**
1.Just install nginx
2.run nginx server
3.put disk artifact in to the nginx HTML location or the location from where nginx can server 
the static content.
what happen because of that the docker image size will shrink drastically in the first you have
the dependencies which are Huge and youhave all the other things related to npm.
ypu can avoid the by coping only the disc folder to the nginx image.

**Let's Do it**


  FROM node -20:alpine as build
  workdir /app   ##if thes folder does not exit in the docker image it will be created
  ## then we do not completly copy the source code
  ## first copy package.json on to the docker image
  copy package.json .
  ## the run to the install the dependencies that are in the package.json
  ## download the dependencies from the package.json
  RUN npm ci
  copy . .   ## this copy every thing in your folder to the  docker image working directory
  **first . is current directory every thing in current directory of your application
will be coppied to the current directory of docker image which is /app 
  Run npm run dev ## whatever is provieded by the developer so that the artifacts are push to t
the disk folder, whrer it wil be push it will bepushed to the /app/disk in the perticular case
becasue /app is working directory , it will not be pushed to SL dis directory It will be pushed
to do /app/disk

**Now that we have the disk directory what we will do we will go to the second stage**

FROM nginx
 ## what we will do is from the first stage 




