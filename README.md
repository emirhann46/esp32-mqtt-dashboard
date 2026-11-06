# MQTT Web Dashboard

ESP32 tabanlı IoT cihazlarını yönetmek için web tabanlı kontrol paneli.

## Özellikler

- 🌐 Web tabanlı kullanıcı arayüzü
- 🔒 Kullanıcı kimlik doğrulama sistemi
- 📧 E-posta ile şifre sıfırlama
- 📊 Gerçek zamanlı sensör veri takibi
- 💡 LED kontrolü
- 🔄 MQTT protokolü ile cihaz iletişimi
- 📱 Responsive tasarım

## Teknolojiler

- **Backend**: Node.js, Express.js
- **Database**: MongoDB, Mongoose
- **Real-time**: Socket.IO
- **MQTT**: MQTT.js
- **Email**: Nodemailer
- **Frontend**: HTML, CSS, JavaScript

## Kurulum

### Gereksinimler

- Node.js (v14 veya üzeri)
- MongoDB
- MQTT Broker

### Adımlar

1. Projeyi klonlayın:
```bash
git clone https://github.com/emirhann46/esp32-mqtt-dashboard.git
cd esp32-mqtt-dashboard
```

2. Bağımlılıkları yükleyin:
```bash
npm install
```

3. `.env` dosyasını yapılandırın:
```env
# MQTT Broker Configuration
MQTT_BROKER=mqtt://your-mqtt-broker-ip

# Server Configuration
PORT=3000

# Email Configuration (Gmail örneği)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# MongoDB Configuration
MONGODB_URI=mongodb://localhost:27017/mqtt_dashboard
```

4. MongoDB'yi başlatın

5. Uygulamayı çalıştırın:
```bash
npm start
```

## E-posta Konfigürasyonu

Şifre sıfırlama özelliği için e-posta konfigürasyonu gereklidir.

### Gmail için Kurulum

1. Gmail hesabınızda 2-factor authentication'ı aktifleştirin
2. App Password oluşturun:
   - Google Account ayarlarına gidin
   - Security → 2-Step Verification → App passwords
   - Yeni bir app password oluşturun
3. `.env` dosyasında EMAIL_USER ve EMAIL_PASS değerlerini güncelleyin

Detaylı bilgi için `EMAIL_SETUP.md` dosyasına bakın.

## Kullanım

### Varsayılan Admin Hesabı
- Kullanıcı adı: `admin`
- Şifre: `1234`

### Web Arayüzü

1. Tarayıcınızda `http://localhost:3000` adresine gidin
2. Login sayfasından giriş yapın
3. Dashboard'dan cihazlarınızı yönetin

### Desteklenen Cihazlar

- ESP32 LED modülleri
- Sensör modülleri (sıcaklık, basınç, rüzgar)

## API Endpoints

### Kimlik Doğrulama
- `POST /api/login` - Kullanıcı girişi
- `POST /api/register` - Kullanıcı kaydı
- `POST /api/forgot-password` - Şifre sıfırlama talebi
- `POST /api/reset-password` - Şifre sıfırlama

### Cihaz Yönetimi
- `GET /api/devices` - Tüm cihazları listele
- `GET /api/device/:id` - Belirli cihazı getir
- `GET /api/leds` - LED durumlarını getir

### Sensör Verileri
- `POST /api/sensor` - Sensör verisi kaydet
- `GET /api/sensor/:device` - Son sensör verisini getir

## MQTT Topics

- `esp32/led/12/status` - LED 12 durumu
- `esp32/led/27/status` - LED 27 durumu

## Klasör Yapısı

```
esp32-mqtt-dashboard/
├── models/                 # MongoDB modelleri
│   ├── User.js
│   ├── SensorData.js
│   └── deviceTitle.js
├── public/                 # Frontend dosyaları
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── device.html
│   ├── style.css
│   └── *.js
├── server.js              # Ana sunucu dosyası
├── package.json
├── .env                   # Çevre değişkenleri
└── README.md
```

## Lisans

MIT License

## Katkıda Bulunma

1. Fork yapın
2. Feature branch oluşturun (`git checkout -b feature/amazing-feature`)
3. Değişikliklerinizi commit edin (`git commit -m 'Add amazing feature'`)
4. Branch'i push edin (`git push origin feature/amazing-feature`)
5. Pull Request oluşturun

## İletişim

Sorularınız için issue oluşturabilirsiniz.
