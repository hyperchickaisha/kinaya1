[GITHUB_HANDOFF.md](https://github.com/user-attachments/files/33336740/GITHUB_HANDOFF.md)

# kinaya1# KINAYA GitHub Handoff

This archive contains the verified KINAYA launch website at checkpoint `f770e98`.

## Local setup

```bash
corepack enable
corepack prepare pnpm@10.18.0 --activate
pnpm install --frozen-lockfile
cp .env.example .env
# Fill DATABASE_URL and any runtime values required by your deployment.
pnpm db:migrate
pnpm dev
```

Open `http://localhost:3000`.

## Checks and production build

```bash
pnpm check
pnpm test
pnpm build
pnpm start
```

## Add this source to a new GitHub repository

```bash
git init
git add .
git commit -m "Add KINAYA launch website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

The archive does not contain `node_modules`, `dist`, `.git`, private environment values, or Manus session logs. The waitlist form and WhatsApp analytics require a reachable MySQL `DATABASE_URL`; the table names are `waitlistSignups` and `analyticsEvents`.

The included `Dockerfile` builds the Express/Vite application on port 3000. Configure your GitHub deployment platform with the environment variables from `.env.example` and run the checked-in Drizzle migrations before using the form.
