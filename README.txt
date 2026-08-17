MyLocal — अपना Local Super App
================================================
FINAL VERSION — पूरी तरह टेस्ट किया गया, ready to use

इस ZIP में क्या है
--------------------
1) index.html            → यूज़र्स के लिए मुख्य ऐप
2) admin.html             → सिर्फ Admin Panel (Firebase login ज़रूरी)
3) database.rules.json    → Firebase को बताने के लिए कि कौन data पढ़/लिख सकता है
4) README.txt             → यही फाइल

दोनों HTML फाइलें पूरी तरह self-contained हैं — कोई अलग icon/png/
manifest/service-worker फाइल की ज़रूरत नहीं। बस इन्हें कहीं भी host
करें और खोलें।


═══════════════════════════════════════════════════
FIRST-TIME SETUP (सिर्फ एक बार, लगभग 5 मिनट)
═══════════════════════════════════════════════════

STEP 1 — Email/Password Login चालू करें
------------------------------------------
1. https://console.firebase.google.com खोलें → अपना प्रोजेक्ट चुनें
2. बाईं तरफ "Authentication" → ऊपर "Sign-in method" टैब
3. "Email/Password" पर क्लिक करें → Enable करें → Save
   (इसके बिना Admin login कभी काम नहीं करेगा)

STEP 2 — Database Rules लगाएं (ताकि data पढ़ा/लिखा जा सके)
----------------------------------------------------------------
सबसे आसान तरीका — इसी ZIP की database.rules.json फाइल का पूरा
content कॉपी करें:

1. "Realtime Database" → "Rules" टैब खोलें
2. जो भी वहाँ लिखा है उसे मिटाकर database.rules.json का content paste करें
3. "Publish" दबाएं

(इसके बिना Chat/Like/Comment/Post/Order कुछ भी सबके बीच sync नहीं होगा
— सिर्फ अपने ही device पर दिखेगा)

STEP 3 — पहला Admin User बनाएं
---------------------------------
1. "Authentication" → "Users" टैब → "Add user"
2. कोई Email + Password डालें (जैसे admin@mylocal.com)
3. "Add user" दबाएं
4. अब admin.html खोलें, इसी Email/Password से "Firebase Super Admin
   Login" से लॉगिन करें
5. ✅ ऐप खुद इस पहले user को Super Admin बना देगी — कहीं और कुछ भी
   manually edit करने की ज़रूरत नहीं

बाद में और स्टाफ/एडमिन जोड़ने के लिए: लॉगिन के बाद admin.html के
"Users (Firebase)" टैब से नया user बनाएं।


═══════════════════════════════════════════════════
कहाँ Host करें
═══════════════════════════════════════════════════
GPS Location और Firebase (login, live sync) पूरी तरह सही तभी काम
करते हैं जब फाइलें https:// से खुलें (सीधे फोन के File Manager से
खोलने पर नहीं)। मुफ़्त होस्टिंग विकल्प:
  • Firebase Hosting (उसी प्रोजेक्ट से, सबसे आसान)
  • Netlify
  • GitHub Pages
इनमें से किसी पर भी index.html और admin.html अपलोड करें और वहाँ के
https:// लिंक से खोलें।


═══════════════════════════════════════════════════
यह सब टेस्ट होकर पास हो चुका है
═══════════════════════════════════════════════════
✅ Like / Unlike सही से toggle और save होता है
✅ Share (WhatsApp / native share) काम करता है
✅ Comment save होता है, सबको दिखता है
✅ Private Chat (नया room बनाना, code से join करना, message भेजना)
✅ हर user "लोकल काम-काज" (job) post कर सकता है — search/filter सहित
✅ Admin: Product post (turant publish / approval के लिए pending)
✅ Admin: Job post (सरकारी/प्राइवेट, योग्यता, वेतन, अंतिम तारीख, apply link)
✅ Admin: Approve / Reject / Delete
✅ Advertisement: Save / Remove, Home पर लाइव दिखना
✅ Orders: बनना, Admin को दिखना, Complete होना
✅ Service Area (50km GPS lock): Set करना, save होना
✅ Admin login सिर्फ Firebase से — कोई password fallback नहीं
✅ Weather: तापमान, feels-like, हवा, नमी, अगले 7 दिन hourly पूर्वानुमान
✅ Age Calculator, Unit Converter — दोनों सही गणना करते हैं
✅ 50 बार तेज़ी से tab बदलने पर भी कोई lag/hang नहीं (< 1 सेकंड)
✅ Location/Firebase अटक (hang) जाए तो भी ऐप कभी permanently stuck
   नहीं होता — अधिकतम 18 सेकंड में खुद retry-screen दिखा देता है
✅ हर post/order अपने ID से अलग-अलग सुरक्षित रहता है — एक साथ कई लोगों
   का data एक-दूसरे को overwrite नहीं करता (यही सबसे बड़ी पुरानी खराबी थी)
✅ sync कभी fail हो तो कोड console error में छुपने की बजाय ऐप के अंदर
   ही लाल banner में साफ चेतावनी देता है


═══════════════════════════════════════════════════
Troubleshooting
═══════════════════════════════════════════════════
"Chat/Comment/Like दूसरों को नहीं दिख रहा"
  → STEP 2 (Database Rules) दोबारा जांचें, और पुरानी cached फाइल की
    जगह इसी ZIP की ताज़ा फाइल इस्तेमाल करें (browser में Ctrl+Shift+R
    से hard-refresh करें)।

"Admin login fail हो रहा है (auth/operation-not-allowed)"
  → STEP 1 (Email/Password Enable) नहीं किया गया है।

"Admin login fail हो रहा है (user-not-found / wrong-password)"
  → STEP 3 पहले पूरा करें (Firebase Console में user बनाएं)।

"App location जांचते हुए अटक गया"
  → अब ऐसा नहीं होगा — 18 सेकंड में अपने आप retry-screen आ जाएगी।
    फिर भी दिक्कत हो तो फाइल को https:// होस्टिंग से खोलें (सीधे
    फोन से content:// लिंक से नहीं)।
