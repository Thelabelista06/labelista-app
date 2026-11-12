# The Labelista — FREE APK (PWA + APK, Play Store baad mein)

**Date:** 12 November 2026
**Store:** https://www.thelabelista.com/ (Shopify, 46 products, COD Pakistan)
**App name:** The Labelista
**Package name:** `com.thelabelista.app` — yehi naam baad mein Play Store par bhi use hoga, is liye isay change mat karna.
**Cost so far:** Rs 0 / $0. Koi Play Console account nahi banaya, koi paisa nahi diya, kuch publish nahi kiya.

---

## 1. Ye kya hai — aur kyun Bubblewrap/TWA chuna

Ye app tumhari website ka **Trusted Web Activity (TWA)** wrapper hai, jo Google ke **Bubblewrap** tool se banta hai. Matlab: app khulti hai to andar asal mein `thelabelista.com` hi chalta hai — products, cart, checkout, COD, WhatsApp — sab website wala hi hai. Koi doosra catalog maintain nahi karna.

**Capacitor (native WebView app) kyun nahi chuna?**

- Capacitor mein poora Android project, WebView settings, back-button, checkout aur file handling khud sambhalna parta hai — zyada code, zyada maintenance.
- Bubblewrap/TWA Google ka official tareeqa hai, is mein ye sab pehle se bana hua hai, aur **yehi project baad mein Play Store wala AAB bhi bana deta hai** — dobara app banane ki zaroorat nahi.
- Dono mein checkout website se hi chalta, is liye TWA simpler aur zyada reliable hai.

**Kya milega / kya nahi milega:**

| Cheez | Free route mein |
|---|---|
| App install ho jati hai, icon ke saath | ✅ Haan — APK se |
| Products / prices / COD / checkout | ✅ Website wale hi, auto-sync |
| Play Store par listing, search, ratings | ❌ Nahi — is ke liye $25 wala Play account chahiye (baad mein) |
| Auto-update (Play jaisa) | ❌ Nahi — naya version banao, dobara share karo, user dobara install kare |
| Push notifications | ❌ v1 mein nahi |

---

## 2. Is folder mein kya hai

| File | Kaam |
|---|---|
| `README.md` | Ye file — poora plan |
| `manifest.webmanifest` | PWA manifest — “Add to Home Screen” ke liye (neeche §6 dekho) |
| `twa-manifest.json` | Bubblewrap ki source of truth — package, naam, rang, version |
| `package.json` | Bubblewrap version pin (`@bubblewrap/cli@1.24.1`) aur build scripts |
| `assets/icon-512.png` (512×512) | App icon |
| `assets/icon-192.png` (192×192) | Chhota icon |
| `.github/workflows/build-apk.yml` | GitHub Actions workflow — free mein APK banata hai |
| `.gitignore` | Keystore / APK / generated Android project ko git se bahar rakhta hai |

Parent folder `workspace/labelista-app/` mein Play Store wala pack pehle se hai (`README.md`, `play-store-listing.md`, `play-store-checklist.md`, `assetlinks.json`, `twa-manifest.json`) — wo baad mein kaam aayega.

---

## 3. Step-by-step — GitHub se free APK banana

Sirf ek free GitHub account chahiye. Koi Android Studio, koi JDK apne computer par install karne ki zaroorat nahi — sab GitHub ke computer par hota hai.

### Step 1 — Free GitHub account banao
1. https://github.com/ par jao, **Sign up** karo (free).
2. Email verify karo.

### Step 2 — Naya repo banao
1. GitHub par **New repository** dabao.
2. Naam rakho: `labelista-app`
3. **Public** chuno (public repo par GitHub Actions free hai; private repo par bhi free minutes milte hain, lekin public sab se safe hai).
4. **Create repository** dabao.

### Step 3 — Ye folder upload karo
1. Repo ke page par **“uploading an existing file”** / **Add file → Upload files** dabao.
2. Apne computer se is poori `free-apk` folder ka content upload karo — **lekin dhyaan rakho:** `.github` wala folder bhi upload hona chahiye. GitHub ki website se hidden folder upload karna mushkil ho sakta hai; agar `.github/workflows/build-apk.yml` upload na ho, to repo mein manually folder banao: **Add file → Create new file**, naam likho `.github/workflows/build-apk.yml`, aur us file ka content paste kar do.
3. Saath mein `manifest.webmanifest`, `twa-manifest.json`, `package.json`, `assets/` (dono icons) zaroor upload karo.
4. **Commit** dabao.

> Asaan tareeqa (agar GitHub Desktop / git aata hai): repo clone karo, `free-apk` ka content repo ki root mein copy karo, phir `git add .`, `git commit -m "Labelista free APK"`, `git push`.

### Step 4 — Workflow chalao
1. Repo mein **Actions** tab kholo.
2. Left side mein **“Build Labelista APK (free)”** dikhega — us par click karo.
3. **Run workflow** dabao, phir green **Run workflow** button.
4. 5–10 minute wait karo. Pehli dafa Android SDK download hota hai, is liye thoda time lagta hai.

### Step 5 — APK download karo
1. Jab run green tick (✅) ho jaye, us run par click karo.
2. Neeche **Artifacts** mein `labelista-debug-apk` dikhega — download karo.
3. Andar `app-debug.apk` milega. Yehi file customers ko deni hai.

Agar run red (❌) ho jaye to ghabrao mat — **Actions → us run → failed step** par click kar ke error dekho, aur neeche §7 (Troubleshooting) dekho.

---

## 4. APK customers tak kaise pohonchayen

1. **Website se:** `thelabelista.com` par ek button / banner lagao — “Download Our App (Android)” — jo APK file ka link de. (APK ko pehle Google Drive ya apni site par upload karna parega; Drive link bhi chal jata hai.)
2. **WhatsApp se:** Apne customers / WhatsApp status par APK bhej do, ya Drive link share kar do. Store ka WhatsApp: 0370 8399725.
3. **Direct:** Kisi ke phone mein APK file bhej kar install karwa do.

### Customer ke phone par install kaise hoga
1. APK par tap kare → **Install** dabaye.
2. Phone poochhega **“Allow install from this source / unknown apps?”** — **Allow** karna parega, kyunke ye Play Store se nahi aaya. Ye normal hai.
3. **Play Protect warning** aa sakta hai: “This app is from an unknown developer” — is ka matlab ye nahi ke app mein virus hai; is ka matlab hai Google ne is developer ko verify nahi kiya. Customer **“Install anyway”** dabaye.
4. App khulegi, icon home screen par aa jayega.

> **Important:** Debug APK sirf testing ke liye hai. 2–3 doston / apne phone par pehle test karo — khol kar dekho ke products khul rahe hain, checkout / COD tak ja raha hai, WhatsApp button kaam kar raha hai. Sab theek ho to hi zyada logon ko bhejo.

---

## 5. Debug APK vs Release APK — ye farq samajhna zaroori hai

- **Debug APK** (jo workflow bina kisi secret ke banata hai): GitHub ke auto-generated debug key se sign hota hai. Testing ke liye theek hai.
- **Release APK** (asal app): Tumhare **apne keystore** se sign hota hai. Ye keystore ek dafa banega aur **hamesha wohi use hoga** — agar ye kho gaya ya badal gaya, to purane users ko naya version install karne ke liye pehle purani app uninstall karni paregi.

**Is liye: APK zyada logon ko bhejne se PEHLE release keystore bana lo, aur usi se release APK banao. Debug APK ko “official” app mat banao.**

### Release keystore kaise banayen (ek dafa, apne computer par)
1. Apne computer par JDK install karo, phir terminal mein:
   ```bash
   keytool -genkeypair -v \
     -keystore labelista-release.keystore \
     -alias upload \
     -keyalg RSA -keysize 2048 -validity 10000
   ```
   Ye tum se passwords aur naam poochhega — passwords kahin safe likh lo (password manager mein).
2. Keystore ko base64 mein badlo:
   ```bash
   base64 -w0 labelista-release.keystore > labelista-release.keystore.base64
   # macOS par: base64 -i labelista-release.keystore -o labelista-release.keystore.base64
   ```
3. GitHub repo mein jao: **Settings → Secrets and variables → Actions → New repository secret**, aur ye 4 secrets banao:
   - `ANDROID_KEYSTORE_BASE64` — base64 file ka poora content
   - `ANDROID_KEYSTORE_PASSWORD` — keystore ka password
   - `ANDROID_KEY_ALIAS` — `upload`
   - `ANDROID_KEY_PASSWORD` — key ka password
4. Phir workflow dobara chalao — is dafa `labelista-release` artifact bhi banega, jis mein hoga:
   - `app-release-signed.apk` — **yehi customers ko do**
   - `app-release-bundle.aab` — **ye Play Store ke liye sambhal kar rakho, abhi upload mat karo**

**Keystore ko kabhi git mein commit mat karo, kabhi WhatsApp / email par mat bhejo, aur us ki copy 2 safe jagah par rakho (e.g. encrypted USB + password manager).** Workflow keystore ko build ke baad delete kar deta hai; GitHub secrets mein wo encrypted rehta hai.

---

## 6. PWA — “Add to Home Screen” (bina APK ke bhi app jaisi)

`manifest.webmanifest` is liye hai ke koi bhi customer Chrome mein `thelabelista.com` khol kar **“Add to Home Screen” / “Install app”** dabaye to site app jaisi install ho jaye — bina APK download kiye. Is ke liye manifest aur icons site par live hone chahiye:

- `https://www.thelabelista.com/manifest.webmanifest`
- `https://www.thelabelista.com/icon-512.png`
- `https://www.thelabelista.com/icon-192.png`

**Owner ka step (Muse nahi kar sakta):** Shopify ki **Files** upload se ye files root path par nahi aati — wo `/cdn/shop/files/…` wala link deti hai, jo manifest ke liye kaam nahi karta. Is liye store owner / Shopify developer ko Shopify support se confirm karna hoga ke root files (`/manifest.webmanifest`, `/icon-512.png`) kaise serve hongi (theme file, Shopify app, ya store ke aage CDN/proxy). **Jab tak ye live na ho, tab tak PWA install aur TWA ki full-screen verification dono pending rahenge — APK phir bhi kaam karega, lekin pehli dafa URL bar dikh sakta hai.** Yehi limitation `assetlinks.json` ke liye bhi hai (dekho parent folder ki README §5).

Workflow mein is ka workaround hai: build ke waqt icons ko locally serve kar ke Android project generate kiya jata hai, is liye APK build manifest ke live hone ka wait nahi karta.

---

## 7. Updates kaise hongi (free route mein)

Play Store jaisa auto-update **nahi** hai. Har update ka tareeqa ye hai:

1. `twa-manifest.json` mein version barhao:
   - `appVersion`: `1.0.0` → `1.0.1`
   - `appVersionCode`: `1` → `2` (har dafa +1, kabhi peeche nahi)
2. GitHub par commit / push karo (ya workflow dobara chalao).
3. Naya APK download karo, purani jagah (Drive / website) par replace karo, customers ko bata do ke naya version install kar lein.
4. **Website par price ya product change ho to APK dobara banane ki zaroorat nahi** — wo website se khud update ho jata hai. Sirf app ka naam, icon, rang ya version badle to naya APK chahiye.

---

## 8. Baad mein Play Store par kaise jayenge ($25 de kar)

Jab tum tayyar ho, to yehi project Play Store wala AAB bana dega — dobara app banane ki zaroorat nahi:

1. Google Play Console account banao, $25 one-time fee do, CNIC/passport se identity verify karo.
2. Isi workflow se bana hua `app-release-bundle.aab` (release secrets ke saath) Play Console par upload karo. **AAB wahi keystore se sign hona chahiye jo §5 mein banaya tha** — warna Play purana version update nahi karne dega.
3. Parent folder `workspace/labelista-app/` ka pack use karo: `play-store-listing.md` (listing ka text), `play-store-checklist.md` (checklist), aur `assetlinks.json` (full-screen TWA ke liye, §6 wali Shopify limitation ke saath).
4. Naye personal account ke liye 12 testers ke saath 14 din ki closed testing hogi, phir production access milega — ye Google ki requirement hai, isay chhota nahi kiya ja sakta.

---

## 9. Troubleshooting (pehli run fail ho to)

| Masla | Kya karein |
|---|---|
| Workflow red, “Bubblewrap … JDK / SDK” error | Check karo ke `actions/setup-java` (JDK 17) aur `android-actions/setup-android` steps pass hue. Bubblewrap ko JDK 17 hi chahiye — 8 ya 21 nahi. |
| “manifest.webmanifest not found” / icon download fail | Ye expected hai jab tak §6 wala manifest live na ho. Workflow mein local icon server ka workaround hai; agar phir bhi fail ho to failed step ka log dekho — icon URL ya `bubblewrap update` wali line mein masla hoga. |
| “keystore / signing” error, release step fail | Sirf tab hota hai jab secrets set hon aur galat hon. Pehle debug APK se kaam chalao, phir secrets dobara check karo (§5). |
| APK install nahi ho raha / “App not installed” | Purana version (debug vs release, alag key) pehle se installed ho to pehle uninstall karo, phir install karo. |
| App khulti hai lekin URL bar dikh raha hai | `assetlinks.json` abhi live nahi hai — ye TWA verification ka masla hai, app ka nahi. App phir bhi kaam karegi; full-screen ke liye §6 / parent README §5 dekho. |

---

## 10. Kya verify nahi hua (honest note)

- **Ye workflow yahan end-to-end run nahi hua.** Is VM mein JDK / Android SDK nahi tha, aur koi GitHub account nahi banaya gaya. YAML syntax aur JSON files validate kar li gayi hain, lekin pehli GitHub run par 1–2 chhoti fixes lag sakti hain (sab se zyada chance Bubblewrap ke icon fetch / interactive prompt wale hisse mein hai).
- **Shopify par root files serve karna verify nahi hua** — `manifest.webmanifest`, icons aur `assetlinks.json` ke liye Shopify support / developer se confirm karna baqi hai.
- **Store facts dobara live fetch nahi kiye** — 46 products, Rs 1,299–4,000, COD, free delivery over Rs 5,000, WhatsApp 0370 8399725 — ye 12 Nov 2026 ko verify hue the; submit karne se pehle live site par dobara check kar lena.
- Koi account nahi banaya, koi paisa nahi diya, kuch publish nahi kiya.
