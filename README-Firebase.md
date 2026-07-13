# Deploying `formulary` to Firebase Hosting

This folder contains your static site. Follow the steps below to enable CI deploy via GitHub Actions.

1) Create a Google Cloud service account and JSON key
- Go to Google Cloud Console → IAM & Admin → Service accounts
- Create a service account (e.g. `github-action`) in project `formulary-3a4ab`
- Grant roles: `Firebase Hosting Admin` (or `Editor` for broader permissions)
- Create a JSON key and download it

2) Add the key to your GitHub repository secrets
- In your GitHub repo go to Settings → Secrets and variables → Actions → New repository secret
- Name: `FIREBASE_SERVICE_ACCOUNT`
- Value: paste the entire JSON key contents

3) Ensure your site files are in the repository under the `public/` directory
- Copy `formulary.html` into `public/index.html` if not already present

4) Commit and push to `main`
- The workflow `.github/workflows/firebase-hosting.yml` will run on push to `main` and deploy to Firebase Hosting

Notes
- For local deployment you can still use the Firebase CLI: `npm install -g firebase-tools` then `firebase login` and `firebase deploy --only hosting --project=formulary-3a4ab`.
- Secure your service account and restrict IAM roles where possible.
