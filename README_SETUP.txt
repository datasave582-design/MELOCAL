MyLocal FINAL — local-9a38c

Files:
- index.html
- admin.html
- firebase-rules.json
- manifest.webmanifest
- sw.js
- icon-192.png
- icon-512.png

Firebase Project: local-9a38c
Authorized domain: datasave582-design.github.io

Authentication:
- Google = Enabled
- Email/Password = Enabled
- Admin authorization: admins/ADMIN_UID = true

Deployment:
1. Replace GitHub index.html and admin.html.
2. Upload manifest.webmanifest, sw.js, icon-192.png, icon-512.png.
3. Realtime Database -> Rules: replace ALL old rules with firebase-rules.json and Publish.
4. Do not mix old rules with these rules.
5. Hard refresh Ctrl+Shift+R. Uninstall old PWA before reinstalling if the old icon/cache remains.

Realtime:
- Posts, likes, comments and shares update without page refresh.
- Private room chat uses rooms/{roomCode}/messages.
- Seller chat uses productRooms/{productId}/messages.
- Admin uses admins/{UID}=true and authorization is continuously monitored.
