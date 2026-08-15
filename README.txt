MyLocal — अपना Local Super App
================================

इस ZIP में 2 फाइलें हैं, दोनों पूरी तरह self-contained हैं
(कोई अलग icon/png/manifest/service-worker फाइल की ज़रूरत नहीं):

1) index.html   → यूज़र्स के लिए मुख्य ऐप (Market, Private Chat, Weather, Jobs, Tools आदि)
2) admin.html   → सिर्फ Admin के लिए (Product/Job post, Approval, Advertisement,
                   Orders, Service-Area 50km Lock वगैरह)

कैसे इस्तेमाल करें
------------------
सबसे अच्छा तरीका: दोनों फाइलों को किसी वेब होस्टिंग पर डालें
(जैसे Netlify, GitHub Pages, Firebase Hosting — सब फ्री हैं) और वहाँ से
https:// लिंक से खोलें। इससे GPS location और Firebase (login, live data
sync) हमेशा सही तरीके से काम करेंगे।

फोन के File Manager से सीधे खोलने पर (content:// या file://) कुछ फीचर
जैसे Location या Firebase ठीक से काम नहीं करते — यह ब्राउज़र की अपनी
सुरक्षा नीति की वजह से है, ऐप की गलती नहीं।

Admin पासवर्ड (डिफ़ॉल्ट)
-------------------------
admin123   (admin.html खोलकर बदला जा सकता है / Firebase login भी उपलब्ध है)

चैट के बारे में
----------------
अब कोई पब्लिक/कम्युनिटी चैट नहीं है — सिर्फ Private Chat (code से)
और Seller Chat (किसी product के बारे में) उपलब्ध हैं।

मौसम के बारे में
-----------------
अब मौसम में तापमान, feels-like, हवा की स्पीड व दिशा, नमी (humidity),
बारिश की संभावना, सूर्योदय/सूर्यास्त, और अगले 7 दिनों का घंटे-दर-घंटे
(hourly) पूर्वानुमान — सब शामिल है।

महत्वपूर्ण
----------
- दोनों फाइलें एक ही Firebase प्रोजेक्ट से जुड़ी हैं, इसलिए admin.html से
  जो भी products/jobs/ads/orders डालेंगे, वो index.html में अपने आप
  (लाइव) दिख जाएंगे।
- Service Area Lock (50km): admin.html के "सेवा क्षेत्र" टैब से एक बार
  क्षेत्र सेट कर दें तो index.html सिर्फ उसी 50km दायरे में काम करेगा।
  अगर कोई क्षेत्र सेट नहीं किया गया है, तो ऐप सभी जगह बिना किसी रोक के
  काम करता है।
