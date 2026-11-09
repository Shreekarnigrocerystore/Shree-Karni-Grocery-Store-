SHREE KARNI GROCERY STORE — VERSION 2 (SEPARATE ADMIN PANEL)

FILES
- index.html: customer shopping website
- admin.html: separate owner/admin login and dashboard
- firebase-config.js: Firebase web app config (same file used by both pages)
- firestore.rules: Firestore security rules

IMPORTANT
This version is cloud-database ready, but it will NOT work online until Firebase is configured and the files are hosted. Firebase free Spark plan is generally enough for a small pilot, subject to quotas and current terms. Product/order data will then sync across customer and admin devices.

SETUP CHECKLIST
1. Open https://console.firebase.google.com and create a project named Shree Karni Grocery Store.
2. In Project settings > General > Your apps, add a Web app and copy its Firebase config into firebase-config.js, replacing every YOUR_* value.
3. In Build > Firestore Database, create a database (production mode).
4. Open Firestore Rules and publish the contents of firestore.rules after replacing REPLACE_WITH_YOUR_ADMIN_EMAIL with the exact email you will use for admin login.
5. In Build > Authentication > Sign-in method, enable Email/Password.
6. In Authentication > Users, add your own admin email and a strong password.
7. Create a products collection and add product documents with fields:
   name (string), category (string), price (number), stock (number), emoji (string), image (string), active (boolean true).
   You can also add products later from admin.html.
8. Upload all four files to a static host such as Firebase Hosting. For Firebase Hosting, install Firebase CLI on a computer and run `firebase init hosting`, choose the project, set public directory to the folder containing these files, then `firebase deploy`.
9. Customer website is the hosting URL. Admin panel is the same URL followed by /admin.html.

SECURITY / OPERATION NOTES
- Admin email is checked in Firestore rules. Replace the placeholder with your actual admin email before publishing rules.
- Keep the admin password private and strong. Do not share admin.html login credentials.
- Do not make Firestore rules public. The supplied rules let visitors create orders but only the admin account can read or manage orders and products.
- This is a starter store. Validate stock, delivery coverage, final price and order details with the customer before fulfilling. Online UPI/card collection is not integrated.
- Customer orders are shared in Firestore and visible in the separate admin panel after setup.
- Add your WhatsApp number later; WhatsApp notification handoff is not enabled in this cloud version yet.
