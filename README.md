# KİM YALAN SÖYLÜYOR? — Telegram Mini App

Mobil uyumlu, birinci şahıs kamera açılı, Three.js ile oluşturulmuş 3D masa ve karakterler içeren gerçek oyunculu sosyal çıkarım oyunu başlangıcı.

## Yerelde çalıştırma
1. Node.js 18+ kur.
2. Bu klasörde `npm install`
3. `npm start`
4. `http://localhost:3000` adresini en az 3 tarayıcı sekmesinde aç. Birinde oda oluştur, diğerlerinde oda koduyla katıl. Oda sahibi oyunu başlatabilir.

## Yayınlama mimarisi
**Önemli:** Netlify statik frontend barındırır; canlı çok oyunculu oyun için ayrıca sürekli çalışan Node.js sunucusu gerekir.

### 1. Oyun sunucusu (Render örneği)
- Projeyi GitHub deposuna yükle.
- Render → New → Web Service ile depoyu bağla.
- Build command: `npm install`
- Start command: `npm start`
- Yayınlandıktan sonra `https://SUNUCU-ADRESIN/health` aç; `{"ok":true}` görmelisin.

### 2. Frontend (Netlify)
- Netlify'de site oluştur, Publish directory olarak `public` seç.
- `public/game.js` içindeki `io({transports:["websocket","polling"]})` kısmını `io("https://SUNUCU-ADRESIN",{transports:["websocket","polling"]})` olarak değiştir. `SUNUCU-ADRESIN` yerine Render URL'sini yaz.
- Yeniden deploy et.
- BotFather Web App URL alanına gerçek Netlify HTTPS adresini gir.

## Dahil olanlar
- Birinci şahıs oturma kamerası, 3D masa, ışıklar, kollar ve oyuncu avatarları
- 3–8 kişilik oda kodları ve davet
- Sunucu tarafından gizli rol/ipuçları atama
- Masa sohbeti, oylama ve tur sonucu
- Oda sahibinin sonraki turu başlatması

## Üretim öncesi
Bu bir başlangıç prototipidir. Gerçek cihazlarda test et; yeniden bağlanma, hız sınırlama, sohbet moderasyonu, hile önleme, veri gizliliği ve sunucu dayanıklılığı ekle. Sohbet metin tabanlıdır; sesli sohbet içermez. Oda durumu sunucu belleğinde tutulduğu için sunucu yeniden başlarsa odalar sıfırlanır.
