CampusLend

A secure P2P micro-lending platform for students, built with React and Firebase.

🚀 Live Demo

View the live project here: [PASTE_YOUR_DEPLOYED_PROJECT_LINK_HERE]

📖 The Problem

Students frequently face short-term "cash crunches"—small, urgent financial needs for textbooks, project supplies, or even a meal. Traditional banks are inaccessible for such small, fast loans, and borrowing from friends is often awkward, informal, and difficult to track.

✨ The Solution

CampusLend is a web application that creates a closed-loop, trusted economy for a college campus. By verifying users with their official student email (e.g., .edu, .siu.edu.in), we ensure a secure, student-only community.

Every new member is given 1000 free "CampusTokens" to instantly kickstart the economy.

A Borrower can post a request for a small loan (e.g., "Need 50 tokens for project materials").

A Lender can browse a real-time marketplace of these requests and choose to fund one with a single click.

The platform securely handles the entire transaction, moving the tokens instantly and providing a full transaction history for every user.

🌟 Key Features

Secure Student-Only Auth: Sign-up is restricted to users with a valid student email domain.

Community Rules Pop-up: A one-time modal for new users to agree to the platform's rules before entering.

Virtual Token Economy: Every user starts with 1000 tokens, eliminating real-money risk and creating an instantly active user base.

Real-Time Loan Marketplace: A "Marketplace" tab that shows all pending loan requests from other students, updating in real-time.

One-Click Loan Funding: Securely fund any open request with your available token balance.

Personal Dashboard: A "Home" tab showing a user's own active debts, with amounts due and "Repay" buttons.

Request Money Form: A dedicated tab for users to post their own loan requests.

Transaction History: A "History" tab showing a complete log of all paid and completed transactions (both borrowed and lent).

🛠️ How it Works: The Tech Stack

This project is a perfect example of a modern serverless architecture. The frontend (React) is completely decoupled from the backend (Firebase).

1. React (The Frontend)

Built with Vite: Provides a lightning-fast development experience.

Component-Based UI: The entire application is built as a set of React components (e.g., Header, NavButton, LoanMarketplace).

State Management: Uses React.Context (AuthContext) to store and share the logged-in user's data (like their auth status and token balance) across the entire app.

Real-time Updates: Uses Firebase's onSnapshot listener to subscribe to database changes. When a loan is funded, the database updates, and the UI reacts and re-renders automatically without a page refresh.

2. Firebase (The Backend)

Firebase Authentication: Securely handles all user sign-up and login, verifying student email domains.

Firestore Database: A NoSQL database that stores all our data.

users collection: Stores user data (e.g., displayName, email, balance).

loans collection: Stores all loan objects (e.g., amount, purpose, status: 'pending').

Secure Transactions: All token transfers (funding a loan, repaying a loan) are handled using Firebase writeBatch transactions. This ensures that the operation is atomic—either all steps (e.g., subtract from lender, add to borrower, update loan status) complete successfully, or none of them do. This prevents errors like "lost" tokens.

Architecture Diagram

This diagram shows how the frontend and backend communicate.

graph TD
    User[User Interface (React App)]
    FBAuth[Firebase Authentication]
    FS[Firestore Database (Serverless)]

    User -- 1. Login/Signup with email --> FBAuth
    FBAuth -- 2. Confirms User Identity --> User
    User -- 3. Clicks 'Fund Loan' --> FS(4. Runs Secure Transaction)
    FS -- 5. Data Changes (e.g., new balance) --> User(6. UI Updates in Real-Time via onSnapshot)


☁️ How to Deploy

This project uses a "JAMstack" (JavaScript, APIs, Markup) model, which is incredibly easy to deploy.

Part 1: Deploying the Backend (Firebase)

This is the best part: you already did it.

Firebase is serverless. The moment you created the project in the Firebase console, your database and auth systems were "deployed" and live on the internet.

Your only step is to go to the Firebase Console -> Authentication -> Settings -> Authorized Domains and add the URL of your deployed frontend (e.g., campuslend.vercel.app) to the list.

Part 2: Deploying the Frontend (React)

The easiest way to deploy a Vite + React app is with Vercel or Netlify.

Push to GitHub: Create a new repository on GitHub and push your campuslend project folder.

Sign up for Vercel (with your GitHub account).

Import Project: On your Vercel dashboard, click "Add New... > Project" and select your new GitHub repository.

Deploy: Vercel automatically detects it's a Vite project and handles all the build steps. You just need to click Deploy.

In 60 seconds, your project will be live on the internet with a link like campuslend.vercel.app.

📈 Future Roadmap & Market Potential

This hackathon project is a proof-of-concept for a much larger, scalable application.

Future Features

Payment Gateway Integration (Razorpay/Stripe): Allow users to "Top Up" their token balance with real money (e.g., ₹100 = 1000 tokens), turning the virtual economy into a real one.

Trust Score & Reputation: Build a reputation system based on repayment history. Lenders can choose to only fund loans for users with a high trust score.

Automated Due Dates & Penalties: Implement automated due dates (e.g., 7 days) and small token penalties for late repayments.

Market & Growth Potential

The "market cap" of a P2P lending app is based on its Total Transaction Volume. The growth model is based on expanding the trusted community.

graph TD
    A[Phase 1: Single Campus (e.g., SIT Nagpur)]
    B[Phase 2: Intra-University (All SIU Campuses)]
    C[Phase 3: National Inter-College Network (e.g., All IITs, All NITs)]
    D[Phase 4: Global Student Market (India, US, UK, etc.)]
    
    A --> B
    B --> C
    C --> D


Phase 1 (Our MVP): Prove the model within a single, high-trust community (SIT Nagpur).

Phase 2: Expand to other colleges within the same university system (Symbiosis International University).

Phase 3: Create a national network, allowing students from different trusted universities (e.g., IITs, NITs) to lend to each other.

Phase 4: Expand to the global student market, becoming the default "Venmo for Student Loans."

💻 How to Run This Project Locally

Clone the repository:

git clone [https://github.com/](https://github.com/)[YOUR_USERNAME]/[YOUR_REPO_NAME].git


Navigate to the project folder:

cd campuslend


Install dependencies (this project uses npm):

npm install
npm install lucide-react


Run the project:

npm run dev


Your app will be running at https://campuslend-b3c8f.web.app/

(Note: The firebaseConfig is hard-coded in src/App.jsx. You can replace it with your own Firebase project keys.)

📄 License

This project is licensed under the MIT License.
