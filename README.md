# Loan & Finance Website — 5 pages (HTML, CSS, vanilla JS)

## File guide
| File | Purpose |
|---|---|
| `index.html`, `services.html`, `eligibility.html`, `about.html`, `contact.html` | The five pages |
| `styles.css` | Whole design system (cream and white theme, tokens in `:root`) |
| `js/config.js` | **Edit this first**: company name, phone, email, WhatsApp, address, hours, loan categories |
| `js/app.js` | Nav, modals, service cards, filters, toasts, validators, WhatsApp |
| `js/emi-calculator.js` | EMI calculator (reducing-balance formula) |
| `js/enquiry-form.js` | 3-step enquiry form on the Eligibility page |
| `js/contact-form.js` | Contact form + WhatsApp enquiry |
| `firebase-config.js` | Firebase client setup (ES module) |
| `firestore.rules` | Security rules: public create-only, no public reads |

## 1. Set company details
Open `js/config.js` and fill the empty values. Anything left empty shows a placeholder like `[Business phone]` and the matching link stays inactive. Phone and WhatsApp: digits with country code, e.g. `919876543210`.
Also replace `https://your-domain.com` (canonical and Open Graph URLs) in the five HTML files, and replace the placeholder Privacy and Terms text in `js/app.js` (`LEGAL`) with text approved by the owner.

## 2. Firebase setup
1. Create a project at console.firebase.google.com and add a **Web app**.
2. Paste its config into `firebase-config.js` (these web values are not secrets).
3. Build → Firestore Database → Create database.
4. Firestore → Rules → paste `firestore.rules` → Publish.
5. Enquiries appear in the `enquiries` and `contactMessages` collections. View them in the Firebase Console (public reads are blocked on purpose).
6. Recommended: enable **App Check** (reCAPTCHA) in Firebase for abuse and rate protection. Rules alone cannot rate-limit. A hidden honeypot field is already included.
Until configured, forms show "Online enquiry submission is temporarily unavailable" and never fake a success.

## 3. Run locally
Use a local server (ES modules do not load from `file://`): `npx serve .` or VS Code Live Server.

## 4. Deploy: GitHub + Vercel
1. `git init && git add . && git commit -m "Initial site"`
2. Create a GitHub repo, then `git remote add origin <url> && git push -u origin main`
3. On vercel.com → Add New → Project → import the repo. Framework: **Other**, no build command, output directory `.` → Deploy.
4. Add the custom domain under Project → Settings → Domains.

## Notes
- Add `assets/images/og-image.jpg` and an `og:image` meta tag when you have a verified brand image.
- Add structured data (Organization/LocalBusiness) only after company details are verified.
- Do not claim RBI registration, lender partnerships or ratings unless the owner confirms them.
