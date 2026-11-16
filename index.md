# Gizlilik Politikası ve KVKK Aydınlatma Metni — Amel

**Yürürlük tarihi:** 16 Kasım 2026
**Uygulama:** Amel — İslami Yaşam Asistanı (iOS ve Android)
**Veri sorumlusu / geliştirici:** Emir Güngör (bireysel geliştirici)
**İletişim:** application.amel@gmail.com

Bu metin, Amel uygulamasının iOS ve Android sürümleri için ortaktır. 6698 sayılı Kişisel
Verilerin Korunması Kanunu ("KVKK") madde 10 kapsamındaki aydınlatma yükümlülüğünü de
karşılamak üzere hazırlanmıştır (bkz. Bölüm 9).

---

## Kısa özet

- **İbadet ve kişisel kayıtlarınız cihazınızda kalır.** Namaz işaretlemeleri, alışkanlıklar,
  zikir sayıları, günlük notlarınız, ilaç ve sağlık kayıtlarınız, favorileriniz sunucularımıza
  gönderilmez.
- **Uygulama içinde reklam gösterilmez.** Ancak uygulama; kullanım istatistiği (Google
  Firebase Analytics) ve reklam kampanyalarımızın ölçümü (Meta ve TikTok SDK'ları) için
  bazı kullanım olaylarını ve cihaz tanımlayıcılarını bu hizmetlere iletir.
- **Abonelik** işlemleri App Store / Google Play üzerinden yapılır; abonelik durumu
  RevenueCat ile doğrulanır.
- **Amel Rehberi'ne** (yapay zeka) yazdığınız mesajlar, yanıt üretilmesi için
  sunucumuz üzerinden yapay zeka sağlayıcısı Anthropic'e iletilir. Mesaj içerikleri
  sunucumuzda saklanmaz.
- Kayıt/hesap açmanız gerekmez; ad-soyad, e-posta veya telefon numaranızı istemeyiz.

## 1. Yalnızca cihazınızda saklanan veriler

Aşağıdaki veriler cihazınızdaki yerel veritabanında (`niyet.db`, SQLite) ve uygulamanın
yerel ayar deposunda tutulur; geliştiriciye veya üçüncü taraflara **gönderilmez**, buluta
yedeklenmez:

- Tanışma adımlarında girdiğiniz ad (isteğe bağlı), seçtiğiniz hedefler ve ilgi alanları
- Namaz işaretlemeleri, kaza namazı sayıları, nafile namaz kayıtları
- Alışkanlıklar, alışkanlık zincirleri, mazeret günleri, hatırlatma saatleri, rozetler
- Zikir (tesbihat) sayaçları
- Günlük (journal) notları ve ruh hâli kayıtları
- Sağlık bölümündeki ilaçlar, ilaç saatleri ve geçmişi; kalori/besin ve egzersiz kayıtları
- Beğendiğiniz ve kaydettiğiniz ayet, hadis ve Esmâ-ül Hüsnâ içerikleri
- Uygulama tercihleriniz (dil, tema, hesaplama yöntemi vb.)
- Rehber sohbet geçmişi (ekranda tutulur, kalıcı olarak kaydedilmez)

Uygulamayı sildiğinizde bu verilerin tamamı cihazınızdan silinir. Uygulama içinde veya
sunucuda bu verilerin bir kopyası bulunmadığından, bunları biz de göremeyiz ve geri
getiremeyiz. (Not: Cihazınızın kendi yedekleme özelliği — iCloud/Google yedeklemesi —
açıksa, işletim sistemi uygulama verisini kendi yedeğine dahil edebilir; bu yedekler sizin
hesabınızda tutulur ve bize ulaşmaz.)

## 2. Konum

Namaz vakitlerini ve kıble yönünü hesaplamak için konum izni istenir.

- Vakit ve kıble hesabı **cihazınızda** yapılır (açık kaynak Adhan kütüphanesi).
- Konum koordinatlarınız geliştiriciye veya analitik/reklam hizmetlerine **gönderilmez**.
- Bulunduğunuz şehrin adını göstermek için koordinatlar, işletim sisteminin yerleşik adres
  çözümleme hizmetine (iOS'ta Apple, Android'de Google/cihaz üreticisi hizmeti) iletilir.
  Bu işlem işletim sistemi tarafından yürütülür.
- İzin vermezseniz şehri elle seçebilirsiniz.

## 3. Bildirimler

Namaz, ayet/hadis, alışkanlık hatırlatmaları, akşam özeti ve ilaç hatırlatmaları
cihazınızda **yerel olarak** planlanır. Bildirim sunucusu (push) kullanılmaz.

## 4. Üçüncü taraf hizmetler ve SDK'lar

Uygulama aşağıdaki hizmetleri kullanır. Bu hizmetlerin her biri kendi gizlilik politikasına
tabidir.

| Hizmet | Ne için | Hangi veriler | Nerede işlenir |
|---|---|---|---|
| **Google Firebase Analytics** | Uygulama kullanım istatistiği; Google Ads kampanya ölçümü | Uygulama içi olaylar (ör. ekran/adım görüntüleme, abonelik satın alma olayı, alışkanlık işaretleme olayı — içerik değil), uygulama örneği kimliği, rastgele üretilmiş kurulum kimliği, cihaz modeli, işletim sistemi, dil, yaklaşık ülke/bölge (IP'den), Android'de reklam kimliği | Google LLC, ABD ve diğer ülkeler |
| **Google Firebase Remote Config** | Uygulama ayarlarını uzaktan yönetmek | Firebase kurulum kimliği, uygulama sürümü, cihaz dili/ülkesi | Google LLC |
| **Google Firebase Authentication (anonim)** | Rehber'e gelen isteklerin kötüye kullanımını önlemek ve kullanım sınırını uygulamak | Rastgele anonim kullanıcı kimliği (uid) ve kimlik doğrulama jetonu. Ad, e-posta, telefon **alınmaz**. | Google LLC |
| **Google Cloud Functions + Firestore** (sunucumuz) | Rehber mesajlarını yapay zekaya iletmek; kullanım sınırı sayacı | Rehber mesajlarınız (yalnız aktarım sırasında), anonim uid, günlük/aylık soru **sayısı**, teknik kayıtlar (uid, zaman, işlenen metin uzunluğu — mesaj içeriği değil) | Google Cloud, `europe-west1` bölgesi (Belçika) |
| **Anthropic (Claude API)** | Amel Rehberi'nin yanıtlarını üretmek | Rehber'e yazdığınız mesajlar ve aynı sohbetteki önceki mesajlar | Anthropic PBC, ABD |
| **RevenueCat** | Abonelik durumunu doğrulamak, satın almaları geri yüklemek | Anonim RevenueCat kullanıcı kimliği, satın alma/abonelik kayıtları (ürün, tarih, fiyat, ülke), kurulum kimliği ve Firebase uygulama örneği kimliği (eşleştirme için), cihaz/işletim sistemi bilgisi | RevenueCat Inc., ABD |
| **Meta (Facebook) SDK** | Meta reklam kampanyalarımızın sonuçlarını ölçmek (reklam atfı) | Uygulama kurulumu/açılışı olayları, abonelik satın alma olayı (tutar, para birimi, paket), cihaz bilgisi; Android'de reklam kimliği; iOS'ta reklam kimliği (IDFA) **yalnızca** "Takip izni"ni verirseniz | Meta Platforms, ABD/İrlanda |
| **TikTok Business SDK** | TikTok reklam kampanyalarımızın sonuçlarını ölçmek (reklam atfı) | Kurulum/açılış olayları, tanışma adımlarını tamamlama ve abonelik satın alma olayı (tutar, para birimi, paket), cihaz bilgisi; Android'de reklam kimliği; iOS'ta IDFA yalnızca izin verirseniz | TikTok Pte. Ltd. / TikTok Inc. ve bağlı şirketleri |
| **App Store / Google Play** | Ödeme ve abonelik yönetimi | Ödeme bilgileriniz yalnız Apple/Google tarafından işlenir; bize ulaşmaz | Apple / Google |
| **jsDelivr CDN** | Kur'an tilaveti ses dosyalarını indirmek (Yâsîn, Fetih, Felak, Nâs) | Standart ağ isteği (IP adresi). Kişisel veri gönderilmez. | jsDelivr (Cloudflare/Fastly) |

Uygulamada **hata/çökme raporlama aracı (crash reporting) bulunmaz.**
Uygulama içinde **reklam gösterilmez** ve verileriniz **satılmaz**.

Gizlilik politikaları:
Google/Firebase https://policies.google.com/privacy ·
Anthropic https://www.anthropic.com/legal/privacy ·
RevenueCat https://www.revenuecat.com/privacy ·
Meta https://www.facebook.com/privacy/policy ·
TikTok https://www.tiktok.com/legal/privacy-policy

### iOS'ta "Takip" izni (ATT)

iOS'ta tanışma adımlarından sonra "Uygulamanın sizi takip etmesine izin verilsin mi?"
sorusu gösterilir. İzin vermezseniz reklam kimliğiniz (IDFA) Meta/TikTok'a **iletilmez**;
kurulum ve satın alma olayları Apple'ın gizlilik korumalı ölçüm altyapısı (SKAdNetwork)
üzerinden, reklam kimliği olmadan iletilmeye devam eder.

### Android'de reklam kimliği

Android'de reklam kimliği (AD_ID) Meta, TikTok ve Firebase tarafından ölçüm amacıyla
okunabilir. Cihazınızın **Ayarlar → Google → Reklamlar** bölümünden reklam kimliğinizi
silebilir veya kişiselleştirilmiş reklamları kapatabilirsiniz.

## 5. Amel Rehberi (yapay zeka)

- Rehber'e bir soru yazdığınızda, mesajınız ve aynı sohbetteki önceki mesajlar şifreli
  bağlantı (HTTPS) ile sunucumuza (Google Cloud Functions) gönderilir ve oradan yanıt
  üretilmesi için **Anthropic**'in Claude modeline iletilir. Yanıtın sizin dilinizde
  gelmesi için uygulama dilinin kodu (ör. `tr`, `de`) da gönderilir.
- Sunucumuz mesaj **içeriğini kaydetmez**; yalnızca anonim kullanıcı kimliğiniz için
  günlük/aylık soru sayısını ve teknik kayıtları (işlenen metin uzunluğu, hata bilgisi)
  tutar.
- Anthropic, API üzerinden gelen girdi ve çıktıları kendi koşulları gereği 30 gün içinde
  siler; kullanım politikası ihlali olarak işaretlenen içerikleri daha uzun (en fazla 2 yıl)
  saklayabilir. Anthropic bu verileri model eğitiminde kullanmaz.
- Rehber'deki hazır konu düğmeleri cevabı cihazdaki içerikten verir; bu durumda sunucuya
  istek gitmez.
- Lütfen Rehber'e sağlık durumunuz, kimlik numaranız gibi hassas kişisel bilgiler yazmayın.
- Rehber fetva vermez, bir âlimin yerini tutmaz; yanıtlar hata içerebilir.

## 6. Dini içerik kaynakları

- Kur'an-ı Kerim Arapça metni: Tanzil.net
- İngilizce meal: Saheeh International · Azerbaycanca meal: Əlixan Musayev (QuranEnc)
- Almanca, Fransızca, Felemenkçe, Arnavutça ve Boşnakça mealler: QuranEnc.com (Kur'an-ı
  Kerim Tercümeleri Ansiklopedisi) · Arapça tefsir: et-Tefsîru'l-Müyesser
- Hadislerin Almanca/Fransızca/Felemenkçe/Arnavutça/Boşnakça/Arapça metinleri: yalnızca
  lafzı birebir eşleşenler HadeethEnc.com'dan; eşleşmeyenler İngilizce gösterilir.
- Hadisler: 17 konuda 175 hadis; her hadis kaynağıyla birlikte verilir (Buhârî, Müslim,
  Tirmizî, Ebû Dâvûd, Nesâî, İbn Mâce, Ahmed ve diğerleri).

Bu metinler uygulamayla birlikte gelir; internetten çekilmez.

## 7. Saklama süreleri

- Cihazdaki veriler: uygulamayı silene kadar cihazınızda.
- Rehber kullanım sayacı (anonim uid, gün/ay sayısı): son kullanımınızdan 12 ay sonra otomatik olarak silinir.
- Sunucu teknik kayıtları (Google Cloud Logging): 30 gün.
- Firebase Analytics olay verisi: Google Analytics saklama ayarına göre en fazla 14 ay.
- RevenueCat abonelik kayıtları: abonelik ilişkisi ve yasal yükümlülükler süresince.
- Meta/TikTok: ilgili şirketin politikalarına göre.

## 8. Çocuklar

Amel 13 yaşından küçük çocuklara yönelik değildir ve bilerek çocuklardan kişisel veri
toplamaz.

## 9. KVKK Aydınlatma Metni

**Veri sorumlusu:** Emir Güngör (application.amel@gmail.com)

**İşlenen kişisel veri kategorileri:** İşlem güvenliği (anonim kullanıcı kimliği, kurulum
kimliği, cihaz/uygulama tanımlayıcıları, reklam kimliği, IP adresi), müşteri işlem
(abonelik ve satın alma kayıtları), pazarlama (reklam atfı olayları), kullanım verisi
(uygulama içi olaylar), Rehber'e yazdığınız mesaj içerikleri.
Cihazınızda kalan veriler (Bölüm 1), tarafımızca işlenmediği için bu kapsama girmez.
Sağlık bölümündeki kayıtlar özel nitelikli veri olabilir; bu kayıtlar yalnızca
cihazınızda tutulur ve tarafımıza aktarılmaz.

**İşleme amaçları ve hukuki sebepler (KVKK md. 5):**
- Aboneliğin sağlanması ve doğrulanması, Rehber hizmetinin sunulması — bir sözleşmenin
  kurulması veya ifasıyla doğrudan ilgili olması (md. 5/2-c).
- Kötüye kullanımın önlenmesi, kullanım sınırı, hizmet güvenliği — veri sorumlusunun meşru
  menfaati (md. 5/2-f).
- Kullanım istatistiği ve reklam kampanyalarının ölçümü — veri sorumlusunun meşru menfaati (md. 5/2-f); kullanıcı, uygulamayı indirmeden önce mağaza sayfasındaki gizlilik beyanı ve bu politika ile bilgilendirilir. iOS'ta reklam kimliği (IDFA) yalnızca uygulama izleme izni verirseniz kullanılır.

**Toplama yöntemi:** Uygulama ve içindeki SDK'lar aracılığıyla, elektronik ortamda,
otomatik yollarla.

**Aktarım:** Veriler, yukarıdaki amaçlarla sınırlı olarak Bölüm 4'te sayılan hizmet
sağlayıcılara aktarılır. Bu sağlayıcıların sunucuları çoğunlukla Türkiye dışında (ABD, AB ve
diğer ülkeler) bulunduğundan veriler **yurt dışına aktarılmaktadır**. Yurt dışı aktarımın
KVKK md. 9'da öngörülen uygun güvencelerdir; aktarım, hizmet sağlayıcıların standart veri
işleme sözleşmeleri ve standart sözleşme hükümleri çerçevesinde yapılır.

**Haklarınız (KVKK md. 11):** Kişisel verinizin işlenip işlenmediğini öğrenme; işlenmişse
bilgi talep etme; işleme amacını ve amacına uygun kullanılıp kullanılmadığını öğrenme;
yurt içinde/yurt dışında aktarıldığı üçüncü kişileri bilme; eksik veya yanlış işlenmişse
düzeltilmesini isteme; KVKK md. 7 çerçevesinde silinmesini veya yok edilmesini isteme;
düzeltme/silme işlemlerinin aktarılan üçüncü kişilere bildirilmesini isteme; münhasıran
otomatik sistemlerle analiz edilmesi sonucu aleyhinize bir sonuç çıkmasına itiraz etme;
kanuna aykırı işleme nedeniyle zarara uğramanız hâlinde zararın giderilmesini talep etme.

**Başvuru:** Taleplerinizi application.amel@gmail.com adresine e-posta ile
iletebilirsiniz. Başvurunuzda kimliğinizi
doğrulayabilmemiz ve ilgili kayıtları bulabilmemiz için hangi platformu (iOS/Android)
kullandığınızı belirtin; hesap olmadığından sizi yalnızca cihazdaki anonim kimliklerle
eşleştirebiliriz. Başvurular en geç **30 gün** içinde ücretsiz olarak yanıtlanır (Veri
Sorumlusuna Başvuru Usul ve Esasları Hakkında Tebliğ). Yanıttan memnun kalmazsanız
Kişisel Verileri Koruma Kurulu'na şikâyette bulunabilirsiniz.

## 10. Verilerinizi silme

- **Cihazdaki veriler:** Uygulamayı silmeniz yeterlidir (Android'de ayrıca Ayarlar →
  Uygulamalar → Amel → Depolama → Verileri temizle).
- **Sunucudaki ve hizmet sağlayıcılardaki veriler** (Rehber kullanım sayacı, analitik
  veriler): application.amel@gmail.com adresine silme talebi gönderebilirsiniz.
- **Abonelik:** Uygulamayı silmek aboneliği iptal etmez. İptal için iOS'ta Ayarlar →
  Apple Kimliği → Abonelikler, Android'de Google Play → Ödemeler ve abonelikler.

## 11. Güvenlik

Uygulama ile sunucular ve hizmet sağlayıcılar arasındaki tüm iletişim şifreli (HTTPS/TLS)
bağlantı ile yapılır. Yapay zeka anahtarları uygulamada bulunmaz, yalnızca sunucuda
güvenli şekilde saklanır.

## 12. Değişiklikler

Bu politika değişirse yürürlük tarihi güncellenir; önemli değişiklikler uygulama içinden
duyurulur.

## 13. İletişim

- **E-posta:** application.amel@gmail.com
- **Veri sorumlusu:** Emir Güngör (application.amel@gmail.com)

---

# Privacy Policy — Amel (English)

**Effective date:** November 16, 2026
**Application:** Amel — Islamic Life Assistant (iOS and Android)
**Data controller / developer:** Emir Güngör (independent developer)
**Contact:** application.amel@gmail.com

If the Turkish and English versions differ, the Turkish version prevails.

## Summary

- **Your worship and personal records stay on your device.** Prayer check-ins, habits,
  dhikr counts, journal entries, medication and health records and favorites are never
  sent to our servers.
- **No ads are shown in the app.** The app does send certain usage events and device
  identifiers to Google Firebase Analytics (usage statistics) and to the Meta and TikTok
  SDKs (measuring our ad campaigns).
- **Subscriptions** are processed by the App Store / Google Play; subscription status is
  verified through RevenueCat.
- **Messages you write to Amel Guide** (AI) are relayed through our server to the AI
  provider Anthropic to generate a reply. Message content is not stored on our server.
- No account is required; we do not ask for your name, email or phone number.

## 1. Data stored only on your device

Stored in the app's local database (`niyet.db`, SQLite) and local preferences; never sent
to the developer or third parties, never synced to our cloud: the optional name you enter
during onboarding, goals and interests; prayer check-ins, qada counts, voluntary prayer
logs; habits, habit chains, excused days, reminder times, badges; dhikr counts; journal
notes and mood; medications, schedules and history, calorie/food and exercise logs;
liked and saved verses, hadith and Names of Allah; app preferences; the Guide chat
(kept on screen, not persisted). Deleting the app deletes all of it. Your device's own
backup (iCloud/Google) may include app data in your personal backup; that never reaches us.

## 2. Location

Used to calculate prayer times and the qibla direction, **on your device** (Adhan
library). Coordinates are not sent to the developer or to analytics/ad services. To show
your city name, coordinates are passed to the operating system's built-in geocoder (Apple
on iOS; Google/device vendor on Android). Without permission you can pick a city manually.

## 3. Notifications

All notifications (prayer, verse/hadith, habit reminders, evening summary, medication)
are scheduled **locally**. No push server is used.

## 4. Third-party services and SDKs

| Service | Purpose | Data | Where |
|---|---|---|---|
| **Google Firebase Analytics** | Usage statistics; Google Ads measurement | In-app events (e.g. screen/step views, purchase event, habit check-in event — not content), app instance ID, random install ID, device model, OS, language, approximate country (from IP), advertising ID on Android | Google LLC, USA and other countries |
| **Google Firebase Remote Config** | Remote app configuration | Firebase installation ID, app version, device language/country | Google LLC |
| **Google Firebase Authentication (anonymous)** | Abuse prevention and usage limits for the Guide | Random anonymous user ID and auth token. No name/email/phone. | Google LLC |
| **Google Cloud Functions + Firestore** (our server) | Relaying Guide messages to the AI; usage counter | Your Guide messages (in transit only), anonymous uid, daily/monthly question **count**, technical logs (uid, time, text length — not content) | Google Cloud `europe-west1` (Belgium) |
| **Anthropic (Claude API)** | Generating Amel Guide replies | Messages you write in the Guide and earlier messages of the same chat | Anthropic PBC, USA |
| **RevenueCat** | Verifying and restoring subscriptions | Anonymous RevenueCat user ID, purchase/subscription records (product, date, price, country), install ID and Firebase app instance ID (for matching), device/OS info | RevenueCat Inc., USA |
| **Meta (Facebook) SDK** | Measuring our Meta ad campaigns (attribution) | Install/open events, subscription purchase event (amount, currency, package), device info; advertising ID on Android; on iOS the IDFA **only** if you allow tracking | Meta Platforms, USA/Ireland |
| **TikTok Business SDK** | Measuring our TikTok ad campaigns (attribution) | Install/open events, onboarding-complete and purchase events (amount, currency, package), device info; advertising ID on Android; IDFA on iOS only with permission | TikTok Pte. Ltd. / TikTok Inc. and affiliates |
| **App Store / Google Play** | Payment and subscription management | Payment details are handled only by Apple/Google | Apple / Google |
| **jsDelivr CDN** | Downloading Qur'an recitation audio (Yasin, Al-Fath, Al-Falaq, An-Nas) | Standard network request (IP address) | jsDelivr |

There is **no crash-reporting SDK**. **No ads** are shown in the app and your data is
**not sold**.

**iOS tracking permission (ATT):** if you decline, your IDFA is not passed to Meta/TikTok;
install and purchase events still flow without it via Apple's privacy-preserving
SKAdNetwork. **Android advertising ID:** you can reset or delete it in
Settings → Google → Ads.

## 5. Amel Guide (AI)

Your message and the earlier messages of the same chat are sent over HTTPS to our server
(Google Cloud Functions) and forwarded to **Anthropic**'s Claude model to generate a reply,
together with the app's language code (e.g. `en`, `de`) so the reply comes in your language.
Our server does **not store message content**; it keeps only a daily/monthly question
count per anonymous ID and technical logs. Under its terms, Anthropic deletes API inputs
and outputs within 30 days (content flagged for usage-policy violations may be kept up to
2 years) and does not use them for model training.
Quick-topic buttons are answered from on-device content without any server call. Please
do not share sensitive personal information in the Guide. The Guide does not issue fatwas
and may make mistakes.

## 6. Religious content sources

Arabic Qur'an text: Tanzil.net · English:
Saheeh International · Azerbaijani: Alikhan Musayev (QuranEnc) · German, French, Dutch,
Albanian and Bosnian: QuranEnc.com · Arabic tafsir: al-Tafsir al-Muyassar · Hadith: 175
hadith in 17 topics, each with its source; translations in other languages only where
HadeethEnc.com has the exact same wording, otherwise English. Bundled with the app, not
downloaded.

## 7. Retention

On-device data: until you delete the app. Guide usage counter: deleted automatically 12 months after your last use.
Server logs: 30 days. Firebase Analytics: up to 14 months, per the Google Analytics retention setting.
RevenueCat: for the subscription relationship and legal obligations. Meta/TikTok: per
their policies.

## 8. Children

Amel is not directed to children under 13 and does not knowingly collect their data.

## 9. Your rights and requests

Under KVKK (Turkey) and, where applicable, GDPR, you may request access, correction,
deletion, information about recipients and transfers, and object to processing. Send
requests to application.amel@gmail.com; please state your platform (iOS/Android). We reply within
30 days, free of charge. Data is transferred outside Turkey to the providers listed above
(USA, EU and other countries). Legal basis for analytics/attribution:
legitimate interest (KVKK art. 5/2-f); users are informed before download via the store privacy disclosure and this policy. On iOS the advertising identifier (IDFA) is used only if you allow app tracking. Legal basis for international transfer: appropriate safeguards under KVKK art. 9 — the providers' standard data processing agreements and standard contractual clauses.

## 10. Deleting your data

On-device: delete the app (Android: also Settings → Apps → Amel → Storage → Clear data).
Server/provider data: email application.amel@gmail.com. Deleting the app does not cancel your
subscription — manage it in Apple ID → Subscriptions or Google Play → Payments &
subscriptions.

## 11. Security

All traffic between the app, our server and providers is encrypted (HTTPS/TLS). AI keys
are never shipped in the app.

## 12. Changes and contact

If this policy changes, the effective date is updated; significant changes are announced
in the app. Contact: application.amel@gmail.com · Emir Güngör
