# Chatbot UI

A clean, open-source AI chat interface built with modern web technologies. Customizable, self-hostable, and extensible.

<img src="./public/readme/screenshot.png" alt="Chatbot UI Screenshot" width="600">

---

## Demo

Try the latest demo [here](https://chatbotui.com).

---

## Project Status

This project is actively being improved with upcoming features such as:

- Simplified deployment
- Enhanced backend support
- Improved mobile layout

---

## Hosted Version

Prefer not to self-host?  
Try the hosted version at: [https://chatbotui.com](https://chatbotui.com)

---

## Community & Support

Have questions or feedback? Use the **Discussions** tab in the repository to:

- Ask setup or usage questions
- Share ideas
- Connect with other users

---

## Issues

Please only use the **Issues** tab for reporting actual bugs or problems with the codebase.

For general help or feature ideas, use the **Discussions** section.

---

## Legacy Version

The previous version of the project (v1) is available on the `legacy` branch.

---

## Updating

To update your local instance:

```bash
npm run update
```

If you're running a hosted instance, also run:

```bash
npm run db-push
```

---

## Local Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/chatbot-ui.git
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Install Supabase Locally

#### Requirements

- [Docker](https://docs.docker.com/get-docker)
- Supabase CLI

**macOS/Linux:**

```bash
brew install supabase/tap/supabase
```

**Windows:**

```bash
scoop bucket add supabase https://github.com/supabase/scoop-bucket.git
scoop install supabase
```

#### Start Supabase

```bash
supabase start
```

---

### 4. Configure Environment Variables

Copy the template file:

```bash
cp .env.local.example .env.local
```

Get values by running:

```bash
supabase status
```

Update `.env.local` accordingly.

In `supabase/migrations/20240108234540_setup.sql`, update:

- `project_url`: Typically `http://supabase_kong_chatbotui:8000`
- `service_role_key`: From `supabase status`

---

### 5. Optional: Install Ollama (for Local Models)

Follow setup instructions at: [https://github.com/jmorganca/ollama](https://github.com/jmorganca/ollama)

---

### 6. Run the App

```bash
npm run chat
```

App should be available at: [http://localhost:3000](http://localhost:3000)

---

## Cloud Hosting

### 1. Complete Local Setup First

Follow steps 1–4 from the local setup.

Push your code to a new repository.

---

### 2. Set Up Supabase Backend

- Create a new project at [https://supabase.com](https://supabase.com)
- Collect the following values:

  - `Project Ref`
  - `Project URL`
  - `Anon Key`
  - `Service Role Key`

- Enable the "Email" provider under **Authentication > Providers**

Update the SQL file `supabase/migrations/20240108234540_setup.sql` with the collected values.

Then run the following:

```bash
supabase login
supabase link --project-ref <project-id>
supabase db push
```

---

### 3. Deploy Frontend with Hosting Platform

You can deploy with any service that supports Next.js, such as Vercel or Netlify.

Set the following environment variables:

```
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY
OPENAI_API_KEY (optional)
AZURE_OPENAI_API_KEY (optional)
```

Deploy the app using the hosting platform's instructions.

---

## Contributing

Contributions are welcome. Please fork the repository and submit a pull request.

---

## License

This project is open-sourced under the MIT license.

---

## Contact

Please use the repository’s Discussions section to ask questions or share ideas.
