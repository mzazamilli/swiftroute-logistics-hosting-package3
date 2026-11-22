# SwiftRoute Logistics
A small full-stack logistics portal with:
Admin sign-in
Package registration and automatically generated tracking IDs
Public tracking lookup and shipment event timeline
Printable shipping receipt (browser Print → Save as PDF)
SQLite persistence
Important branding note
This is an independent logistics template using its own name and visual identity. It is not an official DHL website and does not use DHL's logo or claim DHL affiliation. Only use DHL trademarks/branding if your business has written authorization.
Run locally
Install Node.js 20 or newer.
Copy .env.example to .env.
Set ADMIN_PASSWORD to a unique password of at least 12 characters and replace SESSION_SECRET with a long random secret.
Run npm install, then npm start.
Open http://localhost:3000.
The app creates its SQLite database under data/ by default. The first admin is created from ADMIN_USERNAME and ADMIN_PASSWORD when the database is empty.
Deploy to Render
Create a private Git repository and upload these project files.
In Render, choose New → Blueprint, connect the repository, and apply render.yaml.
Enter ADMIN_USERNAME, a strong ADMIN_PASSWORD, and your real company contact details when prompted.
Wait for the deploy to finish, then open the Render URL.
Test admin sign-in, register a test parcel, print its receipt, and track its generated code in a private/incognito browser window.
The Render blueprint mounts a persistent disk at /var/data; this is important because the SQLite database and session store must survive redeploys. Persistent disks may require a paid Render plan. Do not remove the disk or set the database path to an ephemeral filesystem in production.
Before accepting real shipments
Change all sample company details and admin credentials.
Use HTTPS (Render provides it on its hosted domain).
Add a custom domain in Render if desired.
Back up the SQLite database regularly.
Limit administrator access and use a unique password.
Test restore procedures and operational workflows.
This starter has one administrator account and does not include customer accounts, online payments, carrier integrations, SMS/email notifications, barcode labels, or live GPS. Tracking updates are entered manually by staff.
Do not enter payment card details or sensitive identity documents into this starter app.
Main routes
/ — public site
/api/track/:tracking — public tracking data
/api/login — admin sign-in
/api/packages — admin package registration/list
/api/packages/:id/status — admin status update
/api/receipt/:tracking — admin receipt data swiftroute-logistics-hosting-package3