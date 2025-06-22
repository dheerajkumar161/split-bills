# Split Bills

Split Bills is a modern, full-stack web application designed to simplify expense tracking and bill splitting among friends, family, and groups. It features an intuitive user interface and a powerful AI assistant that allows users to add expenses using natural language commands.

## ✨ Key Features

- **User Authentication**: Secure sign-up and sign-in functionality using Clerk.
- **Group Management**: Create and manage groups to track shared expenses.
- **Expense Tracking**: Add, view, and manage expenses with detailed information.
- **AI-Powered Expense Creation**: Use natural language to quickly add expenses (e.g., "I paid $50 for dinner with Alex and Bob").
- **Real-time Balance Summary**: A dashboard that provides a clear overview of who owes whom.
- **Debt Settlement**: Easily record and track settlements between users.
- **Background Job Processing**: Uses Inngest for asynchronous tasks like sending notifications.
- **Email Notifications**: Integration with Resend for sending emails.

## 🚀 Tech Stack

- **Framework**: [Next.js](https://nextjs.org/)
- **Backend & Database**: [Convex](https://www.convex.dev/)
- **Authentication**: [Clerk](https://clerk.com/)
- **AI**: [Ollama](https://ollama.com/) with the Mistral model for natural language processing.
- **UI**:
  - [React](https://react.dev/)
  - [Tailwind CSS](https://tailwindcss.com/)
  - [shadcn/ui](https://ui.shadcn.com/) for UI components.
  - [Recharts](https://recharts.org/) for data visualization.
- **Background Jobs**: [Inngest](https://www.inngest.com/)
- **Email Service**: [Resend](https://resend.com/)
- **Form Management**: [React Hook Form](https://react-hook-form.com/) & [Zod](https://zod.dev/)

## 🏁 Getting Started

Follow these instructions to set up and run the project locally.

### Prerequisites

- [Node.js](https://nodejs.org/en) (v18 or later)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)
- [Ollama](https://ollama.com/) installed and running on your local machine.

### 1. Clone the Repository

```bash
git clone <repository-url>
cd split-bills
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up Environment Variables

Create a `.env.local` file in the root of the project and add the following environment variables.

```
# Convex
CONVEX_DEPLOYMENT=
NEXT_PUBLIC_CONVEX_URL=

# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=

# Email (Resend)
RESEND_API_KEY=

# Google Gemini
GEMINI_API_KEY=
```

- **Convex**:
  1. Sign up for a [Convex](https://www.convex.dev/) account.
  2. Create a new project.
  3. Find your project's credentials in the Convex dashboard settings and add them to the `.env.local` file.

- **Clerk**:
  1. Sign up for a [Clerk](https://clerk.com/) account.
  2. Create a new application.
  3. Find your API keys in the Clerk dashboard and add them to the `.env.local` file.
  4. In the Clerk dashboard, navigate to **JWT Templates**, create a new template based on Convex, and make it the primary template.

- **Resend**:
  1. Sign up for a [Resend](https://resend.com/) account.
  2. Create an API key and add it to the `.env.local` file.

### 4. Set Up Convex Backend

Run the following command to deploy your backend schema and functions to Convex. It will also sync your environment variables from the Convex dashboard.

```bash
npx convex dev
```

Keep this process running in a separate terminal.

### 5. Set Up Local AI Model (Ollama)

This project uses a local AI model via Ollama to parse expense commands.

1.  **Download and Install Ollama**: Follow the instructions on the [Ollama website](https://ollama.com/).
2.  **Pull the Mistral Model**: Open your terminal and run the following command:
    ```bash
    ollama pull mistral
    ```
3.  **Ensure Ollama is running**: The application expects the Ollama API server to be available at `http://localhost:11434`.

### 6. Run the Development Server

Once the setup is complete, you can run the Next.js development server.

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## 📂 Project Structure

- `app/`: The Next.js 13 App Router directory structure.
  - `(auth)/`: Routes for authentication (sign-in, sign-up).
  - `(main)/`: Core application routes after authentication.
  - `api/`: API routes, including the endpoint for processing AI commands.
- `components/`: Shared UI components used across the application.
- `convex/`: Contains all backend code, including database schema, query functions, and mutations.
- `lib/`: Utility functions and third-party library configurations.
  - `ai-command-parser.js`: Logic for calling the local AI model to parse expense commands.
- `public/`: Static assets like images and logos.
- `hooks/`: Custom React hooks.

---

Happy splitting!
