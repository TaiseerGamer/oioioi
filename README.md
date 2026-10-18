# Tycoon Control Room

A live dashboard for your game. Only you can edit. Everyone else sees a clean, read-only version that updates the moment you save.

Tabs: Players, Network, Stores, Customers, Shops (furniture and decor, blueprints), Leaderboard, Daily quests.

Files:

- `index.html` is the whole site.
- `firebase-config.js` holds your Firebase settings (you fill this in).
- `firestore.rules` holds the database rules that make it owner-only (you paste this into Firebase).

## Setup (about 10 minutes, free)

### 1. Create the Firebase project

1. Go to https://console.firebase.google.com and click **Add project**. Analytics can be off.
2. In the left menu open **Build > Firestore Database > Create database**. Choose any region. Start in **production mode**.
3. Open **Build > Authentication > Get started > Sign-in method > Google**. Turn it on and pick a support email.

### 2. Register the web app

1. Open **Project settings** (gear icon) > **General** > **Your apps** > click the web icon `</>`.
2. Give it any name and register it (hosting is not needed).
3. Copy the `firebaseConfig` values it shows into `firebase-config.js`.

### 3. Lock editing to your account

1. Open **Firestore Database > Rules**.
2. Paste the contents of `firestore.rules`.
3. Replace `YOUR_EMAIL_HERE@gmail.com` with the Google account you will sign in with.
4. Click **Publish**.

### 4. Put it on GitHub Pages

1. Create a new GitHub repository and upload `index.html`, `firebase-config.js`, `firestore.rules` and this README.
2. Open the repo **Settings > Pages**. Under **Build and deployment** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then Save.
3. After a minute the site is live at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.

### 5. Allow sign-in on your GitHub address

1. In Firebase open **Authentication > Settings > Authorized domains**.
2. Click **Add domain** and enter `YOUR-USERNAME.github.io`.

### 6. First run

1. Open your site and click **Owner sign in** at the very bottom of the page.
2. Sign in with the Google account from step 3.
3. The admin panel appears. Click **Load sample data** to see how it looks, or start adding your own players, stores and shop items.
4. Share the plain site link with everyone else. They never need an account.

## Notes

- The site must be opened over `https://` (GitHub Pages does this). Opening `index.html` straight from your disk will not load the Firebase code.
- The first time you sign in, the site writes a tiny `owner-check` entry to confirm the database accepts your account. It is harmless.
- Daily quests roll to four new ones the first time you open the site each day. You can also roll them by hand, or press **Start new day** to reset store earnings and customers too.
- The free Firebase plan allows around 50,000 reads a day. Every visitor reading the dashboard uses some, so keep an eye on usage if your community is large.
- If someone else signs in with a different Google account they will see "This account is not allowed to edit this site" and nothing changes.
