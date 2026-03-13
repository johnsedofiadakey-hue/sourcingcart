# Glasstech Fabrications — Sourcing Platform
## Deploy Instructions (Firebase Hosting + Firestore)

---

### What you're deploying
```
glasstech/
├── public/
│   ├── index.html          ← Admin dashboard (PIN: 5646)
│   └── client/
│       └── index.html      ← Client catalogue (themed per client)
├── firebase.json
├── firestore.rules
├── firestore.indexes.json
└── .firebaserc
```

**Admin URL:**   https://sourcingcart-84b93.web.app
**Client URLs:** https://sourcingcart-84b93.web.app/client/CLIENT_ID

---

### Step 1 — Open terminal in the glasstech folder

```bash
cd path/to/glasstech
```

---

### Step 2 — Log in to Firebase (first time only)

```bash
firebase login
```

A browser window opens — sign in with your Google account linked to Firebase.

---

### Step 3 — Deploy everything

```bash
firebase deploy
```

This deploys:
- Hosting (both HTML files)
- Firestore rules
- Firestore indexes

You'll see output like:
```
✔  Deploy complete!
Hosting URL: https://sourcingcart-84b93.web.app
```

---

### Step 4 — Open your admin dashboard

Go to: **https://sourcingcart-84b93.web.app**

PIN: **5646**

---

### How to use it

1. **Create a client** — enter their name, pick a theme colour, mode, font → click "Create Client"
2. **Copy their link** — e.g. `https://sourcingcart-84b93.web.app/client/abc123xyz`
3. **Add categories** for that client (Dining lights, Main doors, etc.)
4. **Add products** with photos, prices, descriptions
5. **Send the link** to your client via WhatsApp, email, or SMS
6. They browse, select, and send you a WhatsApp summary — straight to +233 59 845 5012

---

### Custom domain (optional)

To use `catalogue.glasstechfabrications.com`:

1. Firebase Console → Hosting → Add custom domain
2. Enter `catalogue.glasstechfabrications.com`
3. Add the DNS records they give you to your domain registrar
4. Wait ~24h for SSL to activate

---

### Re-deploying after changes

Any time you edit the HTML files, just run:
```bash
firebase deploy --only hosting
```

---

### Firestore indexes note

The first time you add products/categories, Firebase may show a link in the browser console to create indexes. Click it — it takes about 1 minute to build. After that, everything works instantly.

---

### PIN change

To change the admin PIN, open `public/index.html` and find:
```javascript
const PIN = '5646';
```
Change it to any 4-digit number, then redeploy.
