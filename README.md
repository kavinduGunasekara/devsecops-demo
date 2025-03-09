# DevSecOps Pipeline Implementation for Tic Tac Toe Game

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

The build artifacts will be stored in the `dist/` directory.


## Start DevSecOps pipeline



