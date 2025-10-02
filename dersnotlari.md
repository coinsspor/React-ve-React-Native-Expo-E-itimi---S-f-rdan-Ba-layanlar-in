# React ve React Native Expo Eğitimi - Sıfırdan Başlayanlar İçin

## 📚 İçindekiler
- [Giriş: Web Sayfası Nasıl Çalışır?](#giriş-web-sayfası-nasıl-çalışır)
- [Hafta 1: React Temelleri](#hafta-1-react-temelleri)
  - [Gün 1: React'e Giriş ve İlk Adımlar](#gün-1-reacte-giriş-ve-ilk-adımlar)
  - [Gün 2: Components ve Props](#gün-2-components-ve-props)
- [Hafta 2: State ve Etkileşim](#hafta-2-state-ve-etkileşim)
  - [Gün 1: State ile Dinamik Uygulamalar](#gün-1-state-ile-dinamik-uygulamalar)
  - [Gün 2: useEffect ve Dış Verilerle Çalışma](#gün-2-useeffect-ve-dış-verilerle-çalışma)

---

# Giriş: Web Sayfası Nasıl Çalışır?

React'i öğrenmeden önce, web sayfalarının nasıl çalıştığını kısaca hatırlayalım.

## HTML, CSS ve JavaScript Nedir?

Bir web sayfası 3 temel teknolojiden oluşur:

1. **HTML (İskelet)**: Sayfanın yapısını oluşturur
   - Başlıklar, paragraflar, resimler, butonlar
   
2. **CSS (Giysi)**: Sayfayı güzelleştirir
   - Renkler, boyutlar, konumlar
   
3. **JavaScript (Beyin)**: Sayfayı akıllı yapar
   - Tıklama olayları, hesaplamalar, değişiklikler

## HTML Etiketleri Hatırlatma

HTML'de her şey etiketlerle başlar:

```html
<!-- Bu bir yorum satırıdır, tarayıcıda görünmez -->

<!-- div etiketi: Bölüm/kutu oluşturur -->
<div>
  Ben bir kutuyum
</div>

<!-- h1 etiketi: En büyük başlık -->
<h1>Ana Başlık</h1>

<!-- p etiketi: Paragraf -->
<p>Bu bir paragraf metnidir.</p>

<!-- button etiketi: Buton -->
<button>Tıkla Bana</button>

<!-- input etiketi: Yazı girişi -->
<input type="text" placeholder="Adınızı yazın" />
```

## Neden React'e İhtiyacımız Var?

Normal HTML ile bir sayaç yapmaya çalışalım:

```html
<!-- Problem: HTML kendi başına değişemez! -->
<div>
  <h1>0</h1>  <!-- Bu sayı kendiliğinden değişmez -->
  <button>Arttır</button>  <!-- Bu buton çalışmaz -->
</div>
```

JavaScript eklersek:

```html
<div>
  <h1 id="sayi">0</h1>
  <button onclick="arttir()">Arttır</button>
</div>

<script>
  let deger = 0;
  
  function arttir() {
    deger = deger + 1;
    document.getElementById("sayi").innerHTML = deger;
  }
</script>
```

Bu çalışır ama karmaşık! React ile aynı şey çok daha basit olacak.

### 🚀 React ile Aynı Sayaç:

```jsx
import { useState } from 'react';

function Sayac() {
  const [sayi, setSayi] = useState(0);
  
  return (
    <div>
      <h1>{sayi}</h1>
      <button onClick={() => setSayi(sayi + 1)}>Arttır</button>
    </div>
  );
}
```

**İşte farklar:**
- JavaScript'te `getElementById` kullanmak zorundasın
- JavaScript'te `innerHTML` ile uğraşman gerekiyor
- React'te sadece `useState` ile hallediyor
- React'te sayı değişince otomatik güncelleniyor
- React kodu çok daha kısa ve anlaşılır!

---

# HAFTA 1: React Temelleri

## Gün 1: React'e Giriş ve İlk Adımlar

### 🎯 Bugün Ne Öğreneceğiz?

1. React nedir ve neden kullanılır?
2. İlk React projemizi nasıl oluştururuz?
3. JSX nedir ve nasıl kullanılır?
4. İlk component'imizi nasıl yazarız?

### 📖 React Nedir?

React, Facebook tarafından yapılmış bir JavaScript kütüphanesidir. Web sayfalarını daha kolay yapmamızı sağlar.

#### React'in Avantajları:

1. **Component Sistemi**: Lego gibi parçalar halinde çalışırız
2. **Otomatik Güncelleme**: Veri değişince sayfa otomatik güncellenir
3. **Daha Az Kod**: Aynı işi daha az kodla yaparız
4. **Hızlı**: Sadece değişen yerleri günceller

### 🛠️ Kurulum - Adım Adım

#### 1. Node.js Kurulumu

Node.js, bilgisayarımızda JavaScript çalıştırmamızı sağlar.

1. [nodejs.org](https://nodejs.org) sitesine girin
2. "LTS" yazan versiyonu indirin (daha kararlı)
3. İndirilen dosyayı açın ve "Next" diyerek kurun
4. Kurulum bittikten sonra bilgisayarı yeniden başlatın

#### 2. Kurulumu Kontrol Etme

Windows'ta:
- Başlat menüsünde "cmd" yazın ve Command Prompt'u açın

Mac'te:
- Terminal uygulamasını açın

Şu komutları yazın:

```bash
node --version
```

Eğer `v18.17.0` gibi bir sayı görüyorsanız, kurulum başarılı!

#### 3. İlk React Projemizi Oluşturalım

Terminal/CMD'de şu komutları sırayla yazın:

```bash
# Masaüstüne gidelim
cd Desktop

# React projesi oluştur (biraz zaman alabilir)
npx create-react-app ilk-projem

# Oluşan klasöre gir
cd ilk-projem

# Projeyi başlat
npm start
```

Tarayıcınız açılacak ve dönen React logosu göreceksiniz! 🎉

### 📁 Proje Yapısını Tanıyalım

Oluşan klasörde şu dosyalar var:

```
ilk-projem/
│
├── node_modules/        → Yardımcı kodlar (dokunmayın)
├── public/             
│   └── index.html       → Ana HTML dosyası
│
├── src/                 → Bizim kodlarımız burada!
│   ├── App.js          → Ana component
│   ├── App.css         → Stil dosyası
│   └── index.js        → Başlangıç dosyası
│
└── package.json         → Proje ayarları
```

### 🌟 İlk Değişikliğimiz

`src/App.js` dosyasını açın. İçinde şöyle bir kod göreceksiniz:

```jsx
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        ...
      </header>
    </div>
  );
}

export default App;
```

Hepsini silip şunu yazın:

```jsx
function App() {
  return (
    <div>
      <h1>Merhaba Dünya!</h1>
      <p>Ben React öğreniyorum!</p>
    </div>
  );
}

export default App;
```

Kaydedin (Ctrl+S veya Cmd+S) ve tarayıcıya bakın - otomatik değişti!

### 📝 JSX Nedir?

JSX, HTML'e benzeyen ama aslında JavaScript olan bir yazım şeklidir. React'te HTML ve JavaScript'i birlikte kullanmamızı sağlar.

## 🔴 DIV ve Alternatifleri - Detaylı Açıklama

### DIV Nedir?
`div` = "division" (bölüm) = **Genel amaçlı kutu**. HTML'de elementleri gruplamak için kullanılan, hiçbir özel anlamı olmayan bir konteyner/kutu elementidir.

```jsx
// div = Boş bir karton kutu gibi düşünün
function Ornek() {
  return (
    <div>  {/* Bu bir kutu */}
      <h1>Başlık</h1>  {/* Kutunun içindeki başlık */}
      <p>Paragraf</p>   {/* Kutunun içindeki yazı */}
    </div>  {/* Kutu kapandı */}
  );
}
```

**div kullanma sebepleri:**
1. Elementleri gruplamak için
2. Stil vermek için
3. Düzen oluşturmak için

```jsx
// div'siz - dağınık - ÇALIŞMAZ!
function Dagınik() {
  return (
    <h1>Başlık</h1>
    <p>Yazı</p>
    <button>Buton</button>
  );  // ❌ HATA! React'te böyle olmaz
}

// div'li - düzenli - ÇALIŞIR!
function Duzenli() {
  return (
    <div style={{backgroundColor: 'lightblue', padding: '20px'}}>
      <h1>Başlık</h1>
      <p>Yazı</p>
      <button>Buton</button>
    </div>  // ✅ Hepsi mavi kutunun içinde
  );
}
```

### 🎯 HTML5 Anlamlı Elementler (Semantic Elements)

Her birinin özel bir ANLAMI var:

```jsx
function WebSitesiOrnegi() {
  return (
    <>
      {/* HEADER - Sayfanın üst kısmı */}
      <header style={{backgroundColor: 'lightblue', padding: '20px'}}>
        <h1>Site Başlığı</h1>
        <p>Logo ve menü burada olur</p>
      </header>
      
      {/* NAV - Navigasyon/Menü */}
      <nav style={{backgroundColor: 'lightgray', padding: '10px'}}>
        <a href="#">Ana Sayfa</a> | 
        <a href="#">Hakkımızda</a> | 
        <a href="#">İletişim</a>
      </nav>
      
      {/* MAIN - Ana içerik */}
      <main style={{backgroundColor: 'white', padding: '20px'}}>
        <h2>Ana İçerik Burada</h2>
        
        {/* SECTION - Bölüm */}
        <section style={{border: '1px solid gray', padding: '10px', margin: '10px'}}>
          <h3>Haberler Bölümü</h3>
          
          {/* ARTICLE - Makale/Yazı */}
          <article style={{backgroundColor: '#f0f0f0', padding: '10px', margin: '5px'}}>
            <h4>Haber Başlığı</h4>
            <p>Haber içeriği...</p>
          </article>
        </section>
        
        {/* ASIDE - Yan içerik */}
        <aside style={{backgroundColor: 'lightyellow', padding: '10px'}}>
          <h3>Yan Bilgi</h3>
          <p>Reklam veya ek bilgiler</p>
        </aside>
      </main>
      
      {/* FOOTER - Alt kısım */}
      <footer style={{backgroundColor: 'darkgray', color: 'white', padding: '20px'}}>
        <p>© 2024 Telif Hakkı</p>
      </footer>
    </>
  );
}
```

### 📊 Ne Zaman Hangisini Kullanmalı?

| Element | Ne Zaman Kullan | Örnek |
|---------|----------------|--------|
| **div** | Sadece gruplama/stil için | Kartlar, kutular |
| **header** | Sayfa/bölüm başlığı | Logo, site başlığı |
| **nav** | Menü/navigasyon | Ana menü, yan menü |
| **main** | Ana içerik | Sayfanın asıl konusu |
| **section** | İlgili içerik grubu | Haberler, Ürünler |
| **article** | Bağımsız içerik | Blog yazısı, haber |
| **aside** | Yan/ek içerik | Reklam, ilgili linkler |
| **footer** | Alt bilgi | Copyright, iletişim |

### 🚫 Fragment Kullanımı (Görünmez Kapsayıcı)

Fragment, HTML'de görünmeyen bir kapsayıcıdır:

```jsx
// div kullanırsak - HTML'de görünür
function DivKullanimi() {
  return (
    <div>
      <h1>Başlık</h1>
      <p>Paragraf</p>
    </div>
  );
}
// HTML çıktısı:
// <div>  ← Bu görünür
//   <h1>Başlık</h1>
//   <p>Paragraf</p>
// </div>

// Fragment kullanırsak - HTML'de görünmez
function FragmentKullanimi() {
  return (
    <>
      <h1>Başlık</h1>
      <p>Paragraf</p>
    </>
  );
}
// HTML çıktısı:
// <h1>Başlık</h1>  ← div yok!
// <p>Paragraf</p>
```

## 📌 JSX'in 3 Temel Kuralı - Detaylı Anlatım

### **Kural 1: TEK BİR ANA ELEMENT OLMALI**

React'te return içinde sadece TEK bir ana element döndürebilirsiniz. Neden? Çünkü JavaScript fonksiyonları sadece tek bir değer döndürebilir.

```jsx
// ❌ YANLIŞ - İki element yan yana olamaz
function YanlisOrnek() {
  return (
    <h1>Başlık</h1>
    <p>Paragraf</p>  // HATA! İki element yan yana
  );
}

// ✅ DOĞRU - Tek bir div içinde
function DogruOrnek() {
  return (
    <div>  {/* Ana element */}
      <h1>Başlık</h1>
      <p>Paragraf</p>
    </div>
  );
}

// ✅ DOĞRU - Fragment kullanımı (görünmez kapsayıcı)
function FragmentOrnek() {
  return (
    <>  {/* Fragment - HTML'de görünmez */}
      <h1>Başlık</h1>
      <p>Paragraf</p>
    </>
  );
}

// GERÇEK HAYAT ÖRNEĞİ
function ProfilKarti() {
  // ❌ YANLIŞ
  return (
    <img src="foto.jpg" />
    <h2>Ali Yılmaz</h2>
    <p>Öğrenci</p>
  );
  
  // ✅ DOĞRU
  return (
    <div className="profil-karti">
      <img src="foto.jpg" />
      <h2>Ali Yılmaz</h2>
      <p>Öğrenci</p>
    </div>
  );
}
```

### **Kural 2: JAVASCRIPT KODUNU {} İÇİNE YAZARIZ**

JSX içinde JavaScript kullanmak için süslü parantez `{}` kullanırız.

```jsx
function JavaScriptOrnekleri() {
  // Değişkenler
  const isim = "Mehmet";
  const yas = 16;
  const notlar = [80, 90, 75];
  const ogrenciMi = true;
  
  return (
    <div>
      {/* 1. Değişken kullanımı */}
      <h1>Merhaba {isim}</h1>
      
      {/* 2. Matematiksel işlemler */}
      <p>Yaşın: {yas}</p>
      <p>5 yıl sonra: {yas + 5} yaşında olacaksın</p>
      <p>Doğum yılın: {2024 - yas}</p>
      
      {/* 3. String birleştirme */}
      <p>{"Merhaba " + isim + ", nasılsın?"}</p>
      <p>{`Selam ${isim}, yaşın ${yas}`}</p>
      
      {/* 4. Dizi işlemleri */}
      <p>Notların: {notlar.join(", ")}</p>
      <p>Not ortalaması: {notlar.reduce((a,b) => a+b) / notlar.length}</p>
      
      {/* 5. Koşullu ifadeler */}
      <p>{ogrenciMi ? "Öğrencisin" : "Öğrenci değilsin"}</p>
      <p>{yas >= 18 ? "Reşitsin" : "Reşit değilsin"}</p>
      
      {/* 6. Fonksiyon çağırma */}
      <p>Büyük harf: {isim.toUpperCase()}</p>
      <p>Harf sayısı: {isim.length}</p>
    </div>
  );
}

// DAHA FAZLA ÖRNEK
function HesapMakinesi() {
  const sayi1 = 10;
  const sayi2 = 5;
  
  return (
    <div>
      <h2>Hesap Makinesi</h2>
      <p>{sayi1} + {sayi2} = {sayi1 + sayi2}</p>
      <p>{sayi1} - {sayi2} = {sayi1 - sayi2}</p>
      <p>{sayi1} × {sayi2} = {sayi1 * sayi2}</p>
      <p>{sayi1} ÷ {sayi2} = {sayi1 / sayi2}</p>
      <p>{sayi1} üzeri 2 = {sayi1 ** 2}</p>
      <p>{sayi1} mod {sayi2} = {sayi1 % sayi2}</p>
    </div>
  );
}
```

### **Kural 3: HTML ATTRİBUTE'LARI FARKLI**

JSX'te bazı HTML özellikleri farklı yazılır:

```jsx
function AttributeOrnekleri() {
  return (
    <div>
      {/* class yerine className */}
      <div className="kutu">
        HTML'de: class="kutu"
        JSX'te: className="kutu"
      </div>
      
      {/* for yerine htmlFor */}
      <label htmlFor="isim">İsim:</label>
      <input id="isim" type="text" />
      
      {/* onclick yerine onClick (camelCase) */}
      <button onClick={() => alert('Tıklandı!')}>
        Tıkla
      </button>
      
      {/* style string değil, obje olmalı */}
      {/* HTML: style="color: red; font-size: 20px" */}
      {/* JSX: */}
      <p style={{color: 'red', fontSize: '20px'}}>
        Kırmızı yazı
      </p>
      
      {/* Diğer örnekler */}
      <input 
        onChange={() => {}}     // onchange değil
        onFocus={() => {}}      // onfocus değil
        onBlur={() => {}}       // onblur değil
        autoComplete="off"      // autocomplete değil
        autoFocus              // autofocus değil
      />
    </div>
  );
}
```

### 🎨 Style (Stil) Kullanımı - DETAYLI ANLATIM

React'te elementlere stil vermenin iki yolu var. Şimdi her birini detaylıca öğrenelim.

## 📐 Style Özellikleri ve Kullanımları

### PX Nedir?
**px = pixel** = Ekrandaki en küçük nokta birimi. Sabit boyut için kullanılır.

```jsx
function PixelOrnegi() {
  return (
    <div>
      <p style={{fontSize: '12px'}}>12 piksel boyutunda yazı (küçük)</p>
      <p style={{fontSize: '16px'}}>16 piksel boyutunda yazı (normal)</p>
      <p style={{fontSize: '24px'}}>24 piksel boyutunda yazı (büyük)</p>
      <p style={{fontSize: '48px'}}>48 piksel boyutunda yazı (çok büyük)</p>
    </div>
  );
}
```

### 1. backgroundColor (Arkaplan Rengi)

```jsx
function ArkaplanRengiOrnekleri() {
  return (
    <div>
      {/* İngilizce renk isimleri */}
      <div style={{backgroundColor: 'red', padding: '10px', color: 'white'}}>
        Kırmızı arkaplan (red)
      </div>
      
      <div style={{backgroundColor: 'blue', padding: '10px', color: 'white'}}>
        Mavi arkaplan (blue)
      </div>
      
      {/* Hex renk kodları (#RRGGBB) */}
      <div style={{backgroundColor: '#FF5733', padding: '10px'}}>
        Turuncu arkaplan (#FF5733)
      </div>
      
      {/* RGB renk değerleri */}
      <div style={{backgroundColor: 'rgb(0, 255, 0)', padding: '10px'}}>
        Yeşil arkaplan rgb(0, 255, 0)
      </div>
      
      {/* Saydamlıklı renkler (rgba) */}
      <div style={{backgroundColor: 'rgba(0, 0, 0, 0.5)', padding: '10px', color: 'white'}}>
        %50 saydam siyah arkaplan
      </div>
    </div>
  );
}
```

### 2. color (Yazı Rengi)

```jsx
function YaziRengiOrnekleri() {
  return (
    <div>
      <p style={{color: 'red'}}>Kırmızı yazı</p>
      <p style={{color: 'blue'}}>Mavi yazı</p>
      <p style={{color: '#FF6B6B'}}>Hex kod ile pembe yazı</p>
      <p style={{color: 'rgb(128, 0, 128)'}}>RGB ile mor yazı</p>
    </div>
  );
}
```

### 3. padding (İç Boşluk)

```jsx
function PaddingOrnekleri() {
  const kutuStili = {
    backgroundColor: 'lightblue',
    border: '2px solid blue',
    marginBottom: '10px'
  };
  
  return (
    <div>
      {/* Tek değer: Her taraftan aynı boşluk */}
      <div style={{...kutuStili, padding: '20px'}}>
        padding: '20px' - Her taraftan 20px boşluk
      </div>
      
      {/* İki değer: Üst-alt, sağ-sol */}
      <div style={{...kutuStili, padding: '10px 30px'}}>
        padding: '10px 30px' - Üst-alt 10px, sağ-sol 30px
      </div>
      
      {/* Dört değer: Üst, sağ, alt, sol (saat yönünde) */}
      <div style={{...kutuStili, padding: '5px 10px 15px 20px'}}>
        padding: '5px 10px 15px 20px' - Üst 5, sağ 10, alt 15, sol 20
      </div>
      
      {/* Tek tek yönler */}
      <div style={{
        ...kutuStili,
        paddingTop: '30px',
        paddingBottom: '30px',
        paddingLeft: '10px',
        paddingRight: '10px'
      }}>
        paddingTop ve paddingBottom: 30px
      </div>
    </div>
  );
}
```

### 4. margin (Dış Boşluk)

```jsx
function MarginOrnekleri() {
  const kutuStili = {
    backgroundColor: 'lightgreen',
    padding: '10px',
    border: '2px solid green'
  };
  
  return (
    <div style={{backgroundColor: '#f0f0f0', padding: '10px'}}>
      <div style={{...kutuStili, margin: '20px'}}>
        margin: '20px' - Her taraftan 20px dış boşluk
      </div>
      
      <div style={{...kutuStili, margin: '0 auto', width: '200px'}}>
        margin: '0 auto' - Ortalar (width gerekli)
      </div>
      
      <div style={{...kutuStili, marginTop: '50px'}}>
        marginTop: '50px' - Sadece üstten boşluk
      </div>
    </div>
  );
}
```

### 5. border (Çerçeve/Kenarlık)

```jsx
function BorderOrnekleri() {
  return (
    <div>
      {/* Basit çerçeve: kalınlık stil renk */}
      <div style={{
        border: '1px solid black',
        padding: '10px',
        margin: '5px'
      }}>
        1px kalınlığında düz siyah çerçeve
      </div>
      
      <div style={{
        border: '3px dashed red',
        padding: '10px',
        margin: '5px'
      }}>
        3px kalınlığında kesikli kırmızı çerçeve
      </div>
      
      <div style={{
        border: '5px dotted blue',
        padding: '10px',
        margin: '5px'
      }}>
        5px kalınlığında noktalı mavi çerçeve
      </div>
    </div>
  );
}
```

#### 📐 Border'ın 3 Parçası:

```
border: 'kalınlık stil renk'
         ↓        ↓    ↓
        2px    solid  blue
```

#### 2️⃣ Border Stil Değerleri (solid yerine ne kullanabiliriz):

```jsx
function BorderStilleri() {
  const kutustil = {
    padding: '10px',
    margin: '10px',
    backgroundColor: '#f0f0f0'
  };
  
  return (
    <div>
      {/* SOLID - Düz çizgi */}
      <div style={{...kutustil, border: '3px solid black'}}>
        solid - ━━━ Düz çizgi (en çok kullanılan)
      </div>
      
      {/* DASHED - Kesik çizgi */}
      <div style={{...kutustil, border: '3px dashed red'}}>
        dashed - - - - Kesik kesik çizgi
      </div>
      
      {/* DOTTED - Noktalı çizgi */}
      <div style={{...kutustil, border: '3px dotted blue'}}>
        dotted ••••• Noktalı çizgi
      </div>
      
      {/* DOUBLE - Çift çizgi */}
      <div style={{...kutustil, border: '5px double green'}}>
        double ═══ Çift çizgi (en az 3px olmalı)
      </div>
      
      {/* GROOVE - 3D oyuk efekti */}
      <div style={{...kutustil, border: '5px groove gray'}}>
        groove - 3D oyuk/içe çökük görünüm
      </div>
      
      {/* RIDGE - 3D çıkıntı efekti */}
      <div style={{...kutustil, border: '5px ridge gray'}}>
        ridge - 3D çıkıntı/kabartma görünüm
      </div>
      
      {/* INSET - İçe gömük */}
      <div style={{...kutustil, border: '5px inset gray'}}>
        inset - Kutu içe gömülmüş gibi görünür
      </div>
      
      {/* OUTSET - Dışa çıkık */}
      <div style={{...kutustil, border: '5px outset gray'}}>
        outset - Kutu dışa çıkmış gibi görünür
      </div>
      
      {/* NONE - Çerçeve yok */}
      <div style={{...kutustil, border: 'none'}}>
        none - Çerçeve yok (gizlemek için)
      </div>
    </div>
  );
}
```

### 6. borderRadius (Köşe Yuvarlaklığı)

```jsx
function BorderRadiusOrnekleri() {
  const temelStil = {
    backgroundColor: 'purple',
    color: 'white',
    padding: '20px',
    margin: '10px',
    textAlign: 'center'
  };
  
  return (
    <div>
      <div style={{...temelStil, borderRadius: '0px'}}>
        borderRadius: '0px' - Köşeli
      </div>
      
      <div style={{...temelStil, borderRadius: '5px'}}>
        borderRadius: '5px' - Hafif yuvarlak
      </div>
      
      <div style={{...temelStil, borderRadius: '15px'}}>
        borderRadius: '15px' - Orta yuvarlak
      </div>
      
      <div style={{...temelStil, borderRadius: '50%', width: '100px', height: '100px'}}>
        borderRadius: '50%' - Daire
      </div>
    </div>
  );
}
```

### 7. fontSize (Yazı Boyutu)

```jsx
function FontSizeOrnekleri() {
  return (
    <div>
      <p style={{fontSize: '10px'}}>10px - Çok küçük yazı</p>
      <p style={{fontSize: '14px'}}>14px - Küçük yazı</p>
      <p style={{fontSize: '16px'}}>16px - Normal yazı</p>
      <p style={{fontSize: '20px'}}>20px - Büyük yazı</p>
      <p style={{fontSize: '32px'}}>32px - Çok büyük yazı</p>
      
      {/* Em birimi (göreceli boyut) */}
      <p style={{fontSize: '1em'}}>1em - Normal boyut</p>
      <p style={{fontSize: '1.5em'}}>1.5em - 1.5 katı</p>
      <p style={{fontSize: '2em'}}>2em - 2 katı</p>
    </div>
  );
}
```

### 8. fontWeight (Yazı Kalınlığı)

```jsx
function FontWeightOrnekleri() {
  return (
    <div>
      <p style={{fontWeight: 'normal'}}>Normal kalınlık</p>
      <p style={{fontWeight: 'bold'}}>Kalın yazı (bold)</p>
      <p style={{fontWeight: '100'}}>100 - Çok ince</p>
      <p style={{fontWeight: '400'}}>400 - Normal</p>
      <p style={{fontWeight: '700'}}>700 - Kalın</p>
      <p style={{fontWeight: '900'}}>900 - Çok kalın</p>
    </div>
  );
}
```

### 9. textAlign (Yazı Hizalama)

```jsx
function TextAlignOrnekleri() {
  const kutuStil = {
    backgroundColor: 'lightyellow',
    padding: '10px',
    margin: '5px',
    border: '1px solid orange'
  };
  
  return (
    <div>
      <div style={{...kutuStil, textAlign: 'left'}}>
        textAlign: 'left' - Sola hizalı
      </div>
      
      <div style={{...kutuStil, textAlign: 'center'}}>
        textAlign: 'center' - Ortaya hizalı
      </div>
      
      <div style={{...kutuStil, textAlign: 'right'}}>
        textAlign: 'right' - Sağa hizalı
      </div>
    </div>
  );
}
```

### 10. width ve height (Genişlik ve Yükseklik)

```jsx
function BoyutOrnekleri() {
  const kutuStil = {
    backgroundColor: 'lightcoral',
    padding: '10px',
    margin: '5px',
    color: 'white'
  };
  
  return (
    <div>
      {/* Piksel ile boyut */}
      <div style={{...kutuStil, width: '200px', height: '100px'}}>
        200px genişlik, 100px yükseklik
      </div>
      
      {/* Yüzde ile boyut */}
      <div style={{...kutuStil, width: '50%', height: '80px'}}>
        %50 genişlik (kapsayıcının yarısı)
      </div>
      
      {/* Otomatik boyut */}
      <div style={{...kutuStil, width: 'auto'}}>
        width: 'auto' - İçeriğe göre genişlik
      </div>
    </div>
  );
}
```

## Teşikilat Şeması Örneği

```jsx
function TeskilatSemasi() {
  // Kart stili - Tekrar kullanmak için
  const kartStili = {
    padding: '15px',
    margin: '5px',
    borderRadius: '5px',
    textAlign: 'center',
    fontSize: '14px',
    fontWeight: 'bold',
    width: '32%',
    display: 'inline-block',
    verticalAlign: 'top'
  };

  // Satır stili - Kartları yan yana dizer
  const satirStili = {
    marginBottom: '10px',
    textAlign: 'center'
  };

  // Farklı renkler için stil objeleri
  const maviAcik = {
    ...kartStili,
    backgroundColor: '#B8E6E6',
    color: '#000'
  };

  const sari = {
    ...kartStili,
    backgroundColor: '#F9E79F',
    color: '#000'
  };

  const mor = {
    ...kartStili,
    backgroundColor: '#D7BDE2',
    color: '#000'
  };

  const yesil = {
    ...kartStili,
    backgroundColor: '#7FD8D8',
    color: '#000'
  };

  const pembe = {
    ...kartStili,
    backgroundColor: '#F5B7B1',
    color: '#000'
  };

  return (
    <>
      {/* NAV - Menü Çubuğu */}
      <nav style={{
        backgroundColor: '#C62828',
        padding: '15px 20px',
        textAlign: 'center'
      }}>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          🏠 Ana Sayfa
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Oluşturulmuş
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Alanlarınız
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Etkinliklerimiz
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Projelerimiz
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          İletişim
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Okul Aile Birliği
        </a>
        <a href="#" style={{
          color: 'white',
          textDecoration: 'none',
          margin: '0 15px',
          fontSize: '16px'
        }}>
          Yemekane Bilg.
        </a>
      </nav>

      {/* MAIN - Ana İçerik (Ortalanmış) */}
      <main style={{
        width: '1200px',
        margin: '0 auto',
        padding: '40px 20px',
        backgroundColor: '#f0f0f0'
      }}>
        {/* Başlık */}
        <h1 style={{
          textAlign: 'center',
          color: '#333',
          marginBottom: '30px',
          fontSize: '32px'
        }}>
          Teşkilat Şeması
        </h1>

        {/* Başkan - En üst - TEK KART */}
        <div style={satirStili}>
          <div style={{
            ...maviAcik,
            width: '100%'
          }}>
            <div>LEVENT KANDEMİR</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              OKUL MÜDÜRÜ
            </div>
          </div>
        </div>

        {/* Müdür Yardımcısı - TEK KART */}
        <div style={satirStili}>
          <div style={{
            ...sari,
            width: '100%'
          }}>
            <div>B. GÜLŞIN MUTLU</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR BAŞYARDIMCISI
            </div>
          </div>
        </div>

        {/* 3'lü satır - Mor - İLK 3 */}
        <div style={satirStili}>
          <div style={mor}>
            <div>SÜLEYMAN DALCI</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
          <div style={mor}>
            <div>EMRULLAH ARSLANTAŞ</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
          <div style={mor}>
            <div>ESTUĞRUL YAŞARPULAT</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
        </div>

        {/* 3'lü satır - Mor - SON 3 */}
        <div style={satirStili}>
          <div style={mor}>
            <div>HAYDAR DOĞAN</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
          <div style={mor}>
            <div>HİLAL AL SAEDİ</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
          <div style={mor}>
            <div>AHMET ŞENOL</div>
            <div style={{fontSize: '12px', fontWeight: 'normal'}}>
              MÜDÜR YARDIMCISI
            </div>
          </div>
        </div>

        {/* 3'lü satır - Açık Mavi - İLK 3 */}
        <div style={satirStili}>
          <div style={maviAcik}>
            <div>İSA ATALA</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Muhasebe ve İş Müdürü Tasvirosu Alan Şefi
            </div>
          </div>
          <div style={maviAcik}>
            <div>BÜLENT TOPALOĞLU</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Elektronik-Elektronik Alan Şefi
            </div>
          </div>
          <div style={maviAcik}>
            <div style={{fontSize: '13px'}}>**</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Tasarım Teknolojileri ve İçtihatlarına Alan Şefi
            </div>
          </div>
        </div>

        {/* 3'lü satır - Açık Mavi - SON 3 */}
        <div style={satirStili}>
          <div style={maviAcik}>
            <div>GÜNDAL KOPAN</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Bilişim Teknolojileri Alan Şefi
            </div>
          </div>
          <div style={maviAcik}>
            <div>ADEM ÇETİN</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Motorlu Araçlar Teknolojisi Alan Şefi
            </div>
          </div>
          <div style={maviAcik}>
            <div>DAVUT ÜNEŞİ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Metal Teknolojisi Alan Şefi
            </div>
          </div>
        </div>

        {/* 3'lü satır - Açık Mavi - Rehber */}
        <div style={satirStili}>
          <div style={maviAcik}>
            <div>OKTAY BOZKURT</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Rehber Öğretmeni
            </div>
          </div>
          <div style={maviAcik}>
            <div>BEDİYE VECİT AKBAŞ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Rehber Öğretmeni
            </div>
          </div>
          <div style={maviAcik}>
            <div>SEMA TEKÇE</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Rehber Öğretmeni
            </div>
          </div>
        </div>

        {/* 3'lü satır - Yeşil - Beden Eğitimi 3 */}
        <div style={satirStili}>
          <div style={yesil}>
            <div>HASAN KARATEKE</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Beden Eğitimi Öğretmeni
            </div>
          </div>
          <div style={yesil}>
            <div>ALTAY ŞEN</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Beden Eğitimi Öğretmeni
            </div>
          </div>
          <div style={yesil}>
            <div>UĞRAŞ YETKİN</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Beden Eğitimi Öğretmeni
            </div>
          </div>
        </div>

        {/* Tek kişi - Yeşil - Müzik */}
        <div style={satirStili}>
          <div style={yesil}>
            <div>TÜLAY AYDEMİR</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Müzik Öğretmeni
            </div>
          </div>
        </div>

        {/* 3'lü satır - Pembe */}
        <div style={satirStili}>
          <div style={pembe}>
            <div>SEBİN DENİZ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Resim-İş Öğretmeni
            </div>
          </div>
          <div style={pembe}>
            <div>ERCAN MERT</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Boyahçı Öğretmeni
            </div>
          </div>
          <div style={pembe}>
            <div>AYŞE ULUŞ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Plak Öğretmeni
            </div>
          </div>
        </div>

        {/* Tek kişi - Pembe */}
        <div style={satirStili}>
          <div style={pembe}>
            <div>ŞEVVAL YERLİ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Finki Öğretmeni
            </div>
          </div>
        </div>

        {/* 3'lü satır - Sarı - 2 kişi (3. boş) */}
        <div style={satirStili}>
          <div style={sari}>
            <div>ERDAL YERLİ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Coğrafya Öğretmeni
            </div>
          </div>
          <div style={sari}>
            <div>MEHMET YAKUPOĞLU</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Coğrafya Öğretmeni
            </div>
          </div>
        </div>

        {/* 3'lü satır - Mor - Tarih */}
        <div style={satirStili}>
          <div style={mor}>
            <div>ÖZLEM BEŞER</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Tarih Öğretmeni
            </div>
          </div>
          <div style={mor}>
            <div>KADRİ EFE</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Tarih Öğretmeni
            </div>
          </div>
          <div style={mor}>
            <div>DEMET KOCAKOÇ</div>
            <div style={{fontSize: '11px', fontWeight: 'normal'}}>
              Tarih Öğretmeni
            </div>
          </div>
        </div>
      </main>
    </>
  );
}

export default TeskilatSemasi;
```


## 💻 JavaScript Temelleri - React için Gerekli Bilgiler

React öğrenmeden önce JavaScript'in temellerini anlamamız gerekiyor. Şimdi adım adım öğrenelim.

### 📦 Değişkenler Nedir?

Değişken, bilgi saklamak için kullandığımız kutulardır. Bir kutuya isim veririz ve içine değer koyarız.

```jsx
// Değişken = Etiketli kutu gibi düşünün
const isim = "Ali";        // "isim" kutusuna "Ali" koyduk
const yas = 15;            // "yas" kutusuna 15 koyduk
const ogrenciMi = true;    // "ogrenciMi" kutusuna true koyduk
```

### const, let ve var Farkları

```jsx
function DegiskenTurleri() {
  // CONST - Sabit değişken (değiştirilemez)
  const isim = "Mehmet";
  // isim = "Ali";  // ❌ HATA! const değiştirilemez
  
  // LET - Değiştirilebilir değişken
  let yas = 15;
  yas = 16;  // ✅ Değiştirilebilir
  yas = yas + 1;  // ✅ 17 oldu
  
  // VAR - Eski yöntem (kullanmayın)
  var sehir = "İstanbul";  // Artık kullanılmıyor
  
  return (
    <div>
      <h2>Değişken Örnekleri</h2>
      <p>İsim (const): {isim}</p>
      <p>Yaş (let): {yas}</p>
      <p>Şehir (var): {sehir}</p>
    </div>
  );
}
```

### Ne Zaman const, Ne Zaman let?

```jsx
function NeZamanHangisi() {
  // CONST KULLANALIM - Değişmeyecek değerler için
  const dogumYili = 2008;        // Doğum yılı değişmez
  const tcKimlik = "12345678901"; // TC kimlik değişmez
  const PI = 3.14;                // Pi sayısı sabittir
  
  // LET KULLANALIM - Değişecek değerler için
  let puan = 0;         // Oyun puanı değişir
  let saat = "14:30";   // Saat değişir
  let havaDurumu = "güneşli"; // Hava durumu değişir
  
  // Örnek kullanım
  puan = puan + 10;  // Puan arttı
  saat = "15:00";     // Saat değişti
  havaDurumu = "yağmurlu"; // Hava değişti
  
  return (
    <div>
      <p>Doğum Yılı (const): {dogumYili}</p>
      <p>Güncel Puan (let): {puan}</p>
      <p>Şu anki saat (let): {saat}</p>
      <p>Hava durumu (let): {havaDurumu}</p>
    </div>
  );
}
```

### const ortalama = (vize * 0.4) + (final * 0.6) Neden const?

```jsx
function NotHesapla() {
  const vize = 70;
  const final = 85;
  
  // NEDEN CONST?
  // Çünkü ortalama BİR KERE hesaplanıyor ve sonra DEĞİŞMİYOR
  const ortalama = (vize * 0.4) + (final * 0.6);  // = 79
  
  // ortalama = 80;  // ❌ HATA! const değiştirilemez
  
  // EĞER LET KULLANSAYDIK?
  let ortalama2 = (vize * 0.4) + (final * 0.6);  // = 79
  // Çalışır ama gereksiz! Çünkü ortalamayı değiştirmeyeceğiz
  
  return (
    <div>
      <p>Vize: {vize}</p>
      <p>Final: {final}</p>
      <p>Ortalama: {ortalama}</p>
      <p>Not: Ortalama bir kere hesaplandı (79) ve bir daha değişmeyecek!</p>
    </div>
  );
}
```

### 🔢 Veri Tipleri

```jsx
function VeriTipleri() {
  // 1. STRING (Metin)
  const isim = "Ali";
  const soyisim = 'Yılmaz';  // Tek veya çift tırnak olabilir
  const cumle = "Merhaba, ben Ali";
  
  // 2. NUMBER (Sayı)
  const yas = 15;
  const boy = 1.75;  // Ondalıklı sayı
  const sicaklik = -5;  // Negatif sayı
  
  // 3. BOOLEAN (Doğru/Yanlış)
  const ogrenciMi = true;
  const mezunMu = false;
  
  // 4. ARRAY (Dizi/Liste)
  const notlar = [80, 90, 75, 85];
  const isimler = ["Ali", "Ayşe", "Mehmet"];
  const karisik = [15, "Ali", true, 3.14];  // Karışık tipler
  
  // 5. OBJECT (Nesne)
  const ogrenci = {
    isim: "Ali",
    yas: 15,
    sinif: "9-A",
    notlar: [80, 90, 75]
  };
  
  return (
    <div>
      <h2>Veri Tipleri</h2>
      <p>String: {isim}</p>
      <p>Number: {yas}</p>
      <p>Boolean: {ogrenciMi ? "Evet" : "Hayır"}</p>
      <p>Array: {notlar.join(", ")}</p>
      <p>Object: {ogrenci.isim} - {ogrenci.sinif}</p>
    </div>
  );
}
```

### 🔀 IF-ELSE Koşul Yapıları

```jsx
function KosulOrnekleri() {
  const yas = 16;
  const not = 75;
  const parola = "1234";
  
  // Basit if-else
  let mesaj1;
  if (yas >= 18) {
    mesaj1 = "Reşitsiniz";
  } else {
    mesaj1 = "Reşit değilsiniz";
  }
  
  // Çoklu koşullar
  let basari;
  if (not >= 90) {
    basari = "Pekiyi";
  } else if (not >= 80) {
    basari = "İyi";
  } else if (not >= 70) {
    basari = "Orta";
  } else if (not >= 50) {
    basari = "Geçer";
  } else {
    basari = "Kaldı";
  }
  
  // && (VE) operatörü - Her iki koşul da doğru olmalı
  const girisIzni = (yas >= 18 && parola === "1234");
  
  // || (VEYA) operatörü - En az bir koşul doğru olmalı
  const indirim = (yas < 18 || yas > 65);  // Çocuk veya yaşlı indirimi
  
  // Ternary operator (kısa if-else)
  const durum = not >= 50 ? "Geçti" : "Kaldı";
  
  return (
    <div>
      <h2>Koşul Örnekleri</h2>
      <p>Yaş: {yas} - {mesaj1}</p>
      <p>Not: {not} - {basari}</p>
      <p>Giriş izni: {girisIzni ? "Var" : "Yok"}</p>
      <p>İndirim: {indirim ? "Var" : "Yok"}</p>
      <p>Durum: {durum}</p>
    </div>
  );
}
```

### 🔁 Fonksiyonlar

Fonksiyon, tekrar kullanılabilir kod bloklarıdır. Bir işi yapan mini programlardır.

```jsx
// FONKSİYON TANIMLAMA
function selamVer() {
  return "Merhaba!";
}

// PARAMETRELİ FONKSİYON
function topla(a, b) {
  return a + b;
}

// ARROW FONKSİYON (Ok fonksiyonu)
const carp = (a, b) => {
  return a * b;
};

// KISA ARROW FONKSİYON
const kareAl = (x) => x * x;

// FONKSİYONLARI KULLANAN COMPONENT
function FonksiyonOrnekleri() {
  // Normal fonksiyon
  function buyukHarfYap(metin) {
    return metin.toUpperCase();
  }
  
  // Arrow fonksiyon
  const kucukHarfYap = (metin) => {
    return metin.toLowerCase();
  };
  
  // Hesaplama fonksiyonu
  const notHesapla = (vize, final) => {
    const ortalama = (vize * 0.4) + (final * 0.6);
    return ortalama;
  };
  
  // Koşullu fonksiyon
  const gectiMi = (not) => {
    if (not >= 50) {
      return "Geçti ✅";
    } else {
      return "Kaldı ❌";
    }
  };
  
  // Fonksiyonları kullanma
  const isim = "Mehmet Yılmaz";
  const vizeNotu = 70;
  const finalNotu = 85;
  const ortalama = notHesapla(vizeNotu, finalNotu);
  
  return (
    <div>
      <h2>Fonksiyon Örnekleri</h2>
      <p>Normal: {isim}</p>
      <p>Büyük Harf: {buyukHarfYap(isim)}</p>
      <p>Küçük Harf: {kucukHarfYap(isim)}</p>
      <p>Vize: {vizeNotu}, Final: {finalNotu}</p>
      <p>Ortalama: {ortalama}</p>
      <p>Sonuç: {gectiMi(ortalama)}</p>
    </div>
  );
}
```

if = "10-A";
  const numara = 256;
  
  // Stil objemiz
  const kartStili = {
    border: '2px solid blue',      // 2 piksel mavi çerçeve
    padding: '20px',                // İç boşluk
    margin: '20px',                 // Dış boşluk
    borderRadius: '10px',           // Yuvarlatılmış köşeler
    backgroundColor: '#f0f0f0',     // Açık gri arkaplan
    width: '300px'                  // 300 piksel genişlik
  };
  
  const baslikStili = {
    color: 'blue',
    fontSize: '24px',
    marginBottom: '10px'
  };
  
  return (
    <div style={kartStili}>
      <h2 style={baslikStili}>{ad} {soyad}</h2>
      <p>Sınıf: {sinif}</p>
      <p>Numara: {numara}</p>
      <p>Okul: Atatürk Lisesi</p>
    </div>
  );
}

// App component'inde kullanalım
function App() {
  return (
    <div>
      <h1>Öğrenci Bilgi Sistemi</h1>
      <OgrenciKarti />
    </div>
  );
}

export default App;
```

---

## Gün 2: Components ve Props

### 🎯 Bugün Ne Öğreneceğiz?

1. Component nedir, nasıl çalışır?
2. Props ile veri aktarımı
3. Tekrar kullanılabilir component'ler
4. Children props kullanımı

### 🧩 Component Nedir?

Component'leri LEGO parçaları gibi düşünün. Küçük parçaları birleştirerek büyük yapılar oluşturursunuz.

```jsx
// Bu bir component
function Buton() {
  return (
    <button>Tıkla</button>
  );
}

// Bu da bir component
function Sayfa() {
  return (
    <div>
      <h1>Başlık</h1>
      <Buton />  {/* Component'i kullanıyoruz */}
      <Buton />  {/* İstediğimiz kadar kullanabiliriz */}
    </div>
  );
}
```

### 📦 Props Nedir?

Props, component'lere bilgi göndermemizi sağlar. Fonksiyonlardaki parametreler gibidir.

#### Props Olmadan (Sorunlu):

```jsx
// Her öğrenci için ayrı component yazmak zorunda kalırız!
function Ogrenci1() {
  return <div>Ali</div>;
}

function Ogrenci2() {
  return <div>Ayşe</div>;
}

function Ogrenci3() {
  return <div>Mehmet</div>;
}
```

#### Props İle (Çözüm):

```jsx
// Tek component, farklı veriler!
function Ogrenci(props) {
  return (
    <div>
      <h3>{props.isim}</h3>
      <p>Yaş: {props.yas}</p>
    </div>
  );
}

// Kullanımı
function App() {
  return (
    <div>
      <Ogrenci isim="Ali" yas={15} />
      <Ogrenci isim="Ayşe" yas={16} />
      <Ogrenci isim="Mehmet" yas={15} />
    </div>
  );
}
```

### 🎯 Props Detaylı Açıklama

```jsx
// Component tanımlama
function UrunKarti(props) {
  // props bir objedir ve içinde gönderdiğimiz bilgiler var
  console.log(props); // {isim: "Laptop", fiyat: 5000}
  
  return (
    <div style={{
      border: '1px solid gray',
      padding: '15px',
      margin: '10px',
      borderRadius: '8px'
    }}>
      <h3>{props.isim}</h3>
      <p>Fiyat: {props.fiyat} TL</p>
      <button>Sepete Ekle</button>
    </div>
  );
}

// Component'i kullanma
function App() {
  return (
    <div>
      <h1>Ürünlerimiz</h1>
      
      {/* props gönderiyoruz */}
      <UrunKarti isim="Laptop" fiyat={5000} />
      <UrunKarti isim="Telefon" fiyat={3000} />
      <UrunKarti isim="Tablet" fiyat={2000} />
    </div>
  );
}
```

### 🔄 Props Türleri

Props olarak her türlü veri gönderebiliriz:

```jsx
function OrnekComponent(props) {
  return (
    <div>
      <p>String: {props.metin}</p>
      <p>Sayı: {props.sayi}</p>
      <p>Boolean: {props.dogruMu ? "Evet" : "Hayır"}</p>
      <p>Dizi: {props.liste.join(", ")}</p>
    </div>
  );
}

function App() {
  return (
    <OrnekComponent 
      metin="Merhaba"           // String
      sayi={42}                  // Number  
      dogruMu={true}             // Boolean
      liste={["a", "b", "c"]}    // Array
    />
  );
}
```

### 🎨 Örnek: Renkli Kart Component'i

```jsx
function RenkliKart(props) {
  // Props'tan gelen değerleri kullanalım
  const kartStili = {
    backgroundColor: props.renk,
    color: props.yaziRengi || 'white', // Varsayılan beyaz
    padding: '20px',
    margin: '10px',
    borderRadius: '10px',
    border: `2px solid ${props.renk}`
  };
  
  return (
    <div style={kartStili}>
      <h3>{props.baslik}</h3>
      <p>{props.icerik}</p>
    </div>
  );
}

function App() {
  return (
    <div>
      <h1>Renkli Kartlarım</h1>
      
      <RenkliKart 
        renk="blue"
        baslik="Mavi Kart"
        icerik="Bu mavi bir kart"
      />
      
      <RenkliKart 
        renk="red"
        baslik="Kırmızı Kart"
        icerik="Bu kırmızı bir kart"
      />
      
      <RenkliKart 
        renk="green"
        yaziRengi="yellow"
        baslik="Yeşil Kart"
        icerik="Bu yeşil bir kart, sarı yazılı"
      />
    </div>
  );
}
```

---

# HAFTA 2: State ve Etkileşim

## Gün 1: State ile Dinamik Uygulamalar

### 🎯 Bugün Ne Öğreneceğiz?

1. State nedir ve neden gereklidir?
2. useState Hook'u nasıl kullanılır?
3. Event (olay) yönetimi
4. Form elemanları ile çalışma

### 🧠 State Nedir?

State, component'in **hafızasıdır**. Değişebilen verileri saklar.

#### Props vs State

| Props | State |
|-------|-------|
| Parent'tan gelir | Component içinde tanımlanır |
| Değiştirilemez | Değiştirilebilir |
| Veri almak için | Veri saklamak için |

### 🎮 Basit Örnek: Sayaç

```jsx
import { useState } from 'react';

function Sayac() {
  // State tanımlama
  // [değişken, değiştirme fonksiyonu] = useState(başlangıç değeri)
  const [sayi, setSayi] = useState(0);
  
  // Fonksiyonlar
  const arttir = () => {
    setSayi(sayi + 1);
  };
  
  const azalt = () => {
    setSayi(sayi - 1);
  };
  
  const sifirla = () => {
    setSayi(0);
  };
  
  return (
    <div style={{
      textAlign: 'center',
      padding: '20px',
      backgroundColor: '#f0f0f0',
      borderRadius: '10px',
      margin: '20px'
    }}>
      <h1>Sayaç: {sayi}</h1>
      
      <button 
        onClick={arttir}
        style={{
          padding: '10px 20px',
          margin: '5px',
          fontSize: '16px',
          backgroundColor: '#2ecc71',
          color: 'white',
          border: 'none',
          borderRadius: '5px',
          cursor: 'pointer'
        }}
      >
        Arttır (+1)
      </button>
      
      <button 
        onClick={azalt}
        style={{
          padding: '10px 20px',
          margin: '5px',
          fontSize: '16px',
          backgroundColor: '#e74c3c',
          color: 'white',
          border: 'none',
          borderRadius: '5px',
          cursor: 'pointer'
        }}
      >
        Azalt (-1)
      </button>
      
      <button 
        onClick={sifirla}
        style={{
          padding: '10px 20px',
          margin: '5px',
          fontSize: '16px',
          backgroundColor: '#3498db',
          color: 'white',
          border: 'none',
          borderRadius: '5px',
          cursor: 'pointer'
        }}
      >
        Sıfırla
      </button>
    </div>
  );
}
```

### 📋 Todo List Uygulaması - DETAYLI ANLATIM

```jsx
import { useState } from 'react';

function TodoListDetayli() {
  // State'lerimiz
  const [gorevler, setGorevler] = useState([]);
  const [yeniGorev, setYeniGorev] = useState('');
  const [kategori, setKategori] = useState('genel');
  const [oncelik, setOncelik] = useState('normal');
  const [aramaTerimi, setAramaTerimi] = useState('');
  const [filtre, setFiltre] = useState('hepsi'); // hepsi, aktif, tamamlanan
  const [siralama, setSiralama] = useState('tarih'); // tarih, isim, oncelik
  
  // Kategori renkleri
  const kategoriRenkleri = {
    genel: '#3498db',
    is: '#e74c3c',
    kisisel: '#2ecc71',
    alisveris: '#f39c12',
    egitim: '#9b59b6'
  };
  
  // Öncelik seviyeleri
  const oncelikSeviyeleri = {
    dusuk: { renk: '#95a5a6', simge: '▽' },
    normal: { renk: '#3498db', simge: '◯' },
    yuksek: { renk: '#f39c12', simge: '△' },
    acil: { renk: '#e74c3c', simge: '⚠' }
  };
  
  // Görev ekleme fonksiyonu
  const gorevEkle = (e) => {
    e.preventDefault(); // Form gönderimini engelle
    
    // Boş görev kontrolü
    if (yeniGorev.trim() === '') {
      alert('Lütfen bir görev yazın!');
      return;
    }
    
    // Aynı görev var mı kontrolü
    const ayniGorevVarMi = gorevler.some(
      gorev => gorev.metin.toLowerCase() === yeniGorev.toLowerCase()
    );
    
    if (ayniGorevVarMi) {
      alert('Bu görev zaten listede var!');
      return;
    }
    
    // Yeni görev objesi oluştur
    const yeniGorevObjesi = {
      id: Date.now(), // Benzersiz ID
      metin: yeniGorev,
      kategori: kategori,
      oncelik: oncelik,
      tamamlandi: false,
      tarih: new Date().toISOString(),
      tamamlanmaTarihi: null
    };
    
    // Görevi listeye ekle
    setGorevler([...gorevler, yeniGorevObjesi]);
    
    // Formu temizle
    setYeniGorev('');
    setKategori('genel');
    setOncelik('normal');
    
    // Başarı mesajı (opsiyonel)
    console.log('Görev eklendi:', yeniGorevObjesi);
  };
  
  // Görev silme fonksiyonu
  const gorevSil = (id) => {
    // Onay al
    const gorev = gorevler.find(g => g.id === id);
    if (window.confirm(`"${gorev.metin}" görevini silmek istediğinize emin misiniz?`)) {
      setGorevler(gorevler.filter(gorev => gorev.id !== id));
    }
  };
  
  // Görev tamamlama fonksiyonu
  const gorevTamamla = (id) => {
    setGorevler(gorevler.map(gorev => {
      if (gorev.id === id) {
        return {
          ...gorev,
          tamamlandi: !gorev.tamamlandi,
          tamamlanmaTarihi: !gorev.tamamlandi ? new Date().toISOString() : null
        };
      }
      return gorev;
    }));
  };
  
  // Görev düzenleme fonksiyonu
  const gorevDuzenle = (id, yeniMetin) => {
    setGorevler(gorevler.map(gorev => {
      if (gorev.id === id) {
        return { ...gorev, metin: yeniMetin };
      }
      return gorev;
    }));
  };
  
  // Filtreleme fonksiyonu
  const filtrelenmisGorevler = gorevler
    .filter(gorev => {
      // Arama filtresi
      if (aramaTerimi && !gorev.metin.toLowerCase().includes(aramaTerimi.toLowerCase())) {
        return false;
      }
      
      // Durum filtresi
      if (filtre === 'aktif' && gorev.tamamlandi) return false;
      if (filtre === 'tamamlanan' && !gorev.tamamlandi) return false;
      
      return true;
    })
    .sort((a, b) => {
      // Sıralama
      if (siralama === 'tarih') {
        return new Date(b.tarih) - new Date(a.tarih);
      }
      if (siralama === 'isim') {
        return a.metin.localeCompare(b.metin);
      }
      if (siralama === 'oncelik') {
        const oncelikSirasi = { acil: 0, yuksek: 1, normal: 2, dusuk: 3 };
        return oncelikSirasi[a.oncelik] - oncelikSirasi[b.oncelik];
      }
      return 0;
    });
  
  // İstatistikler
  const istatistikler = {
    toplam: gorevler.length,
    tamamlanan: gorevler.filter(g => g.tamamlandi).length,
    aktif: gorevler.filter(g => !g.tamamlandi).length,
    acil: gorevler.filter(g => g.oncelik === 'acil' && !g.tamamlandi).length
  };
  
  // Tümünü temizle
  const tumunuTemizle = () => {
    if (window.confirm('Tüm görevler silinecek. Emin misiniz?')) {
      setGorevler([]);
    }
  };
  
  // Tamamlananları temizle
  const tamamlananlariTemizle = () => {
    setGorevler(gorevler.filter(g => !g.tamamlandi));
  };
  
  return (
    <div style={{
      maxWidth: '800px',
      margin: '20px auto',
      padding: '20px',
      backgroundColor: '#f8f9fa',
      borderRadius: '10px',
      fontFamily: 'Arial, sans-serif'
    }}>
      <h1 style={{
        textAlign: 'center',
        color: '#2c3e50',
        marginBottom: '30px'
      }}>
        📝 Gelişmiş Todo List Uygulaması
      </h1>
      
      {/* İstatistikler */}
      <div style={{
        display: 'grid',
        gridTemplateColumns: 'repeat(4, 1fr)',
        gap: '10px',
        marginBottom: '20px'
      }}>
        <div style={{
          backgroundColor: 'white',
          padding: '15px',
          borderRadius: '8px',
          textAlign: 'center',
          borderLeft: '4px solid #3498db'
        }}>
          <h3 style={{margin: '0', color: '#3498db'}}>{istatistikler.toplam}</h3>
          <small>Toplam</small>
        </div>
        
        <div style={{
          backgroundColor: 'white',
          padding: '15px',
          borderRadius: '8px',
          textAlign: 'center',
          borderLeft: '4px solid #e67e22'
        }}>
          <h3 style={{margin: '0', color: '#e67e22'}}>{istatistikler.aktif}</h3>
          <small>Aktif</small>
        </div>
        
        <div style={{
          backgroundColor: 'white',
          padding: '15px',
          borderRadius: '8px',
          textAlign: 'center',
          borderLeft: '4px solid #27ae60'
        }}>
          <h3 style={{margin: '0', color: '#27ae60'}}>{istatistikler.tamamlanan}</h3>
          <small>Tamamlanan</small>
        </div>
        
        <div style={{
          backgroundColor: 'white',
          padding: '15px',
          borderRadius: '8px',
          textAlign: 'center',
          borderLeft: '4px solid #e74c3c'
        }}>
          <h3 style={{margin: '0', color: '#e74c3c'}}>{istatistikler.acil}</h3>
          <small>Acil</small>
        </div>
      </div>
      
      {/* Görev Ekleme Formu */}
      <form onSubmit={gorevEkle} style={{
        backgroundColor: 'white',
        padding: '20px',
        borderRadius: '8px',
        marginBottom: '20px'
      }}>
        <div style={{
          display: 'flex',
          gap: '10px',
          marginBottom: '10px'
        }}>
          <input
            type="text"
            value={yeniGorev}
            onChange={(e) => setYeniGorev(e.target.value)}
            placeholder="Yeni görev ekle..."
            style={{
              flex: 1,
              padding: '10px',
              border: '2px solid #ddd',
              borderRadius: '5px',
              fontSize: '16px'
            }}
          />
          
          <select
            value={kategori}
            onChange={(e) => setKategori(e.target.value)}
            style={{
              padding: '10px',
              border: '2px solid #ddd',
              borderRadius: '5px'
            }}
          >
            <option value="genel">Genel</option>
            <option value="is">İş</option>
            <option value="kisisel">Kişisel</option>
            <option value="alisveris">Alışveriş</option>
            <option value="egitim">Eğitim</option>
          </select>
          
          <select
            value={oncelik}
            onChange={(e) => setOncelik(e.target.value)}
            style={{
              padding: '10px',
              border: '2px solid #ddd',
              borderRadius: '5px'
            }}
          >
            <option value="dusuk">Düşük</option>
            <option value="normal">Normal</option>
            <option value="yuksek">Yüksek</option>
            <option value="acil">Acil</option>
          </select>
          
          <button
            type="submit"
            style={{
              padding: '10px 20px',
              backgroundColor: '#3498db',
              color: 'white',
              border: 'none',
              borderRadius: '5px',
              fontSize: '16px',
              cursor: 'pointer'
            }}
          >
            Ekle
          </button>
        </div>
      </form>
      
      {/* Arama ve Filtreleme */}
      <div style={{
        backgroundColor: 'white',
        padding: '15px',
        borderRadius: '8px',
        marginBottom: '20px',
        display: 'flex',
        gap: '10px',
        alignItems: 'center'
      }}>
        <input
          type="text"
          value={aramaTerimi}
          onChange={(e) => setAramaTerimi(e.target.value)}
          placeholder="🔍 Görev ara..."
          style={{
            flex: 1,
            padding: '8px',
            border: '1px solid #ddd',
            borderRadius: '5px'
          }}
        />
        
        <select
          value={filtre}
          onChange={(e) => setFiltre(e.target.value)}
          style={{
            padding: '8px',
            border: '1px solid #ddd',
            borderRadius: '5px'
          }}
        >
          <option value="hepsi">Hepsi</option>
          <option value="aktif">Aktif</option>
          <option value="tamamlanan">Tamamlanan</option>
        </select>
        
        <select
          value={siralama}
          onChange={(e) => setSiralama(e.target.value)}
          style={{
            padding: '8px',
            border: '1px solid #ddd',
            borderRadius: '5px'
          }}
        >
          <option value="tarih">Tarihe Göre</option>
          <option value="isim">İsme Göre</option>
          <option value="oncelik">Önceliğe Göre</option>
        </select>
      </div>
      
      {/* Görev Listesi */}
      <div style={{
        backgroundColor: 'white',
        borderRadius: '8px',
        padding: '10px',
        minHeight: '200px'
      }}>
        {filtrelenmisGorevler.length === 0 ? (
          <div style={{
            textAlign: 'center',
            padding: '40px',
            color: '#95a5a6'
          }}>
            {aramaTerimi ? 'Arama sonucu bulunamadı' : 'Henüz görev eklenmedi'}
          </div>
        ) : (
          filtrelenmisGorevler.map(gorev => (
            <div
              key={gorev.id}
              style={{
                display: 'flex',
                alignItems: 'center',
                padding: '12px',
                marginBottom: '8px',
                backgroundColor: gorev.tamamlandi ? '#f8f9fa' : 'white',
                borderRadius: '8px',
                borderLeft: `4px solid ${kategoriRenkleri[gorev.kategori]}`,
                transition: 'all 0.3s'
              }}
            >
              {/* Checkbox */}
              <input
                type="checkbox"
                checked={gorev.tamamlandi}
                onChange={() => gorevTamamla(gorev.id)}
                style={{
                  width: '20px',
                  height: '20px',
                  marginRight: '10px',
                  cursor: 'pointer'
                }}
              />
              
              {/* Öncelik İkonu */}
              <span style={{
                color: oncelikSeviyeleri[gorev.oncelik].renk,
                fontSize: '20px',
                marginRight: '10px'
              }}>
                {oncelikSeviyeleri[gorev.oncelik].simge}
              </span>
              
              {/* Görev Metni */}
              <div style={{flex: 1}}>
                <p style={{
                  margin: '0',
                  textDecoration: gorev.tamamlandi ? 'line-through' : 'none',
                  color: gorev.tamamlandi ? '#95a5a6' : '#2c3e50',
                  fontSize: '16px'
                }}>
                  {gorev.metin}
                </p>
                <small style={{color: '#95a5a6'}}>
                  {gorev.kategori} • {new Date(gorev.tarih).toLocaleDateString('tr-TR')}
                  {gorev.tamamlandi && gorev.tamamlanmaTarihi && 
                    ` • Tamamlandı: ${new Date(gorev.tamamlanmaTarihi).toLocaleDateString('tr-TR')}`
                  }
                </small>
              </div>
              
              {/* Aksiyonlar */}
              <button
                onClick={() => {
                  const yeniMetin = prompt('Görevi düzenle:', gorev.metin);
                  if (yeniMetin && yeniMetin.trim()) {
                    gorevDuzenle(gorev.id, yeniMetin);
                  }
                }}
                style={{
                  padding: '5px 10px',
                  marginRight: '5px',
                  backgroundColor: '#f39c12',
                  color: 'white',
                  border: 'none',
                  borderRadius: '4px',
                  cursor: 'pointer'
                }}
              >
                Düzenle
              </button>
              
              <button
                onClick={() => gorevSil(gorev.id)}
                style={{
                  padding: '5px 10px',
                  backgroundColor: '#e74c3c',
                  color: 'white',
                  border: 'none',
                  borderRadius: '4px',
                  cursor: 'pointer'
                }}
              >
                Sil
              </button>
            </div>
          ))
        )}
      </div>
      
      {/* Alt Butonlar */}
      {gorevler.length > 0 && (
        <div style={{
          marginTop: '20px',
          display: 'flex',
          gap: '10px',
          justifyContent: 'center'
        }}>
          <button
            onClick={tamamlananlariTemizle}
            disabled={istatistikler.tamamlanan === 0}
            style={{
              padding: '10px 20px',
              backgroundColor: istatistikler.tamamlanan === 0 ? '#95a5a6' : '#e67e22',
              color: 'white',
              border: 'none',
              borderRadius: '5px',
              cursor: istatistikler.tamamlanan === 0 ? 'not-allowed' : 'pointer'
            }}
          >
            Tamamlananları Temizle ({istatistikler.tamamlanan})
          </button>
          
          <button
            onClick={tumunuTemizle}
            style={{
              padding: '10px 20px',
              backgroundColor: '#c0392b',
              color: 'white',
              border: 'none',
              borderRadius: '5px',
              cursor: 'pointer'
            }}
          >
            Tümünü Temizle
          </button>
        </div>
      )}
    </div>
  );
}
```

### 🎯 State ile İlgili Sık Sorulan Sorular ve Cevapları

#### Soru 1: Neden state'i direkt değiştiremiyoruz?

```jsx
function YanlisOrnek() {
  const [sayi, setSayi] = useState(0);
  
  // ❌ YANLIŞ - React değişikliği görmez
  const yanlis = () => {
    sayi = sayi + 1; // Hata verir!
  };
  
  // ✅ DOĞRU - React değişikliği görür
  const dogru = () => {
    setSayi(sayi + 1);
  };
}
```

**Cevap:** React, state değişikliklerini takip etmek için setter fonksiyonunu kullanır. Direkt değiştirirseniz, React değişikliği fark etmez ve ekranı güncellemez.

#### Soru 2: Birden fazla state mi yoksa tek obje mi kullanmalıyım?

```jsx
// Yöntem 1: Ayrı state'ler
function AyriStates() {
  const [isim, setIsim] = useState('');
  const [yas, setYas] = useState(0);
  const [sehir, setSehir] = useState('');
  
  // Kullanımı basit
  setIsim('Ali');
  setYas(20);
}

// Yöntem 2: Tek obje
function TekObje() {
  const [kullanici, setKullanici] = useState({
    isim: '',
    yas: 0,
    sehir: ''
  });
  
  // Güncelleme biraz daha karmaşık
  setKullanici({...kullanici, isim: 'Ali'});
}
```

**Cevap:** İlişkili veriler için tek obje, bağımsız veriler için ayrı state'ler kullanın.

#### Soru 3: State güncellemesi neden hemen olmuyor?

```jsx
function StateGuncellemesi() {
  const [sayi, setSayi] = useState(0);
  
  const guncelle = () => {
    setSayi(sayi + 1);
    console.log(sayi); // Hala 0 gösterir!
    
    // Doğru yöntem
    setSayi(prevSayi => {
      console.log('Yeni değer:', prevSayi + 1);
      return prevSayi + 1;
    });
  };
}
```

**Cevap:** State güncellemeleri asenkron (eşzamansız) çalışır. Güncelleme bir sonraki render'da gerçekleşir.</div>
          
          <button
            onClick={() => gorevSil(gorev.id)}
            style={{
              padding: '5px 10px',
              backgroundColor: '#e74c3c',
              color: 'white',
              border: 'none',
              borderRadius: '5px',
              cursor: 'pointer'
            }}
          >
            Sil
          </button>
        </div>
      ))}
    </div>
  );
}
```

---

## Gün 2: useEffect ve Dış Verilerle Çalışma

### 🎯 Bugün Ne Öğreneceğiz?

1. useEffect Hook'u nedir?
2. Component yaşam döngüsü
3. API'lerden veri çekme
4. Loading ve error durumları

### 🔄 useEffect Örnekleri - DETAYLI ANLATIM

#### useEffect'in 3 Farklı Kullanımı

```jsx
import { useState, useEffect } from 'react';

function UseEffectDetayli() {
  const [sayac, setSayac] = useState(0);
  const [isim, setIsim] = useState('');
  const [zaman, setZaman] = useState(new Date());
  const [veri, setVeri] = useState(null);
  
  // 1. SADECE İLK YÜKLEMEDE ÇALIŞIR
  useEffect(() => {
    console.log('Component yüklendi! (1 kere çalışır)');
    
    // Local Storage'dan veri oku
    const kayitliIsim = localStorage.getItem('kullaniciIsmi');
    if (kayitliIsim) {
      setIsim(kayitliIsim);
    }
    
    // API'den veri çek
    fetch('https://jsonplaceholder.typicode.com/users/1')
      .then(res => res.json())
      .then(data => setVeri(data));
    
    // Cleanup (temizleme) fonksiyonu
    return () => {
      console.log('Component kaldırıldı!');
    };
  }, []); // ← Boş array = sadece ilk yüklemede
  
  // 2. BELİRLİ BİR STATE DEĞİŞTİĞİNDE ÇALIŞIR
  useEffect(() => {
    console.log(`Sayaç değişti! Yeni değer: ${sayac}`);
    
    // Sayaç her değiştiğinde title'ı güncelle
    document.title = `Sayaç: ${sayac}`;
    
    // Sayaç 10'a ulaştığında uyarı
    if (sayac === 10) {
      alert('Tebrikler! 10\'a ulaştınız! 🎉');
    }
    
    // 5'in katlarında renk değiştir
    if (sayac % 5 === 0 && sayac !== 0) {
      document.body.style.backgroundColor = '#e8f5e9';
      setTimeout(() => {
        document.body.style.backgroundColor = 'white';
      }, 1000);
    }
  }, [sayac]); // ← sayac değiştiğinde çalış
  
  // 3. BİRDEN FAZLA BAĞIMLILIK
  useEffect(() => {
    console.log('İsim veya sayaç değişti!');
    
    // İsmi local storage'a kaydet
    if (isim) {
      localStorage.setItem('kullaniciIsmi', isim);
    }
  }, [isim, sayac]); // ← isim VEYA sayac değiştiğinde
  
  // 4. HER RENDER'DA ÇALIŞIR (dikkatli kullan!)
  useEffect(() => {
    console.log('Component render edildi');
    // Dependency array yok = her güncellenmede çalışır
  });
  
  // 5. ZAMANLAYICI ÖRNEĞİ
  useEffect(() => {
    const timer = setInterval(() => {
      setZaman(new Date());
    }, 1000);
    
    // CLEANUP çok önemli! Timer'ı durdur
    return () => {
      clearInterval(timer);
      console.log('Timer temizlendi');
    };
  }, []); // Sadece bir kez başlat
  
  return (
    <div style={{padding: '20px'}}>
      <h2>useEffect Örnekleri</h2>
      
      <div style={{marginBottom: '20px'}}>
        <h3>Sayaç: {sayac}</h3>
        <button onClick={() => setSayac(sayac + 1)}>Arttır</button>
        <button onClick={() => setSayac(0)}>Sıfırla</button>
      </div>
      
      <div style={{marginBottom: '20px'}}>
        <h3>İsim:</h3>
        <input
          value={isim}
          onChange={(e) => setIsim(e.target.value)}
          placeholder="İsminizi girin (kaydedilecek)"
        />
      </div>
      
      <div style={{marginBottom: '20px'}}>
        <h3>Saat: {zaman.toLocaleTimeString('tr-TR')}</h3>
      </div>
      
      <div>
        <h3>API'den Gelen Veri:</h3>
        {veri ? (
          <div>
            <p>İsim: {veri.name}</p>
            <p>Email: {veri.email}</p>
          </div>
        ) : (
          <p>Yükleniyor...</p>
        )}
      </div>
    </div>
  );
}
```

#### useEffect ile Gerçek Dünya Örneği: Otomatik Kayıt

```jsx
import { useState, useEffect } from 'react';

function OtomatikKayitFormu() {
  const [form, setForm] = useState({
    baslik: '',
    icerik: '',
    kategori: 'genel'
  });
  const [kayitDurumu, setKayitDurumu] = useState('');
  const [sonKayit, setSonKayit] = useState(null);
  
  // Form değişikliklerini otomatik kaydet
  useEffect(() => {
    // İlk yüklemede çalışmasın
    if (form.baslik === '' && form.icerik === '') {
      return;
    }
    
    // Kaydetme işlemini geciktir (debounce)
    const timer = setTimeout(() => {
      // Local Storage'a kaydet
      localStorage.setItem('taslak', JSON.stringify(form));
      setKayitDurumu('Otomatik kaydedildi ✓');
      setSonKayit(new Date().toLocaleTimeString('tr-TR'));
      
      // 2 saniye sonra mesajı kaldır
      setTimeout(() => {
        setKayitDurumu('');
      }, 2000);
    }, 1000); // 1 saniye bekle
    
    // Önceki timer'ı temizle
    return () => clearTimeout(timer);
  }, [form]); // Form değiştiğinde
  
  // Sayfa yüklendiğinde kayıtlı veriyi getir
  useEffect(() => {
    const kayitliVeri = localStorage.getItem('taslak');
    if (kayitliVeri) {
      const veri = JSON.parse(kayitliVeri);
      setForm(veri);
      setKayitDurumu('Önceki taslak yüklendi');
    }
  }, []); // Sadece ilk yüklemede
  
  const handleChange = (e) => {
    const { name, value } = e.target;
    setForm(prev => ({
      ...prev,
      [name]: value
    }));
    setKayitDurumu('Yazıyorsunuz...');
  };
  
  const temizle = () => {
    setForm({ baslik: '', icerik: '', kategori: 'genel' });
    localStorage.removeItem('taslak');
    setKayitDurumu('Temizlendi');
  };
  
  return (
    <div style={{
      maxWidth: '600px',
      margin: '20px auto',
      padding: '20px'
    }}>
      <h2>📝 Otomatik Kayıt Örneği</h2>
      
      <div style={{
        display: 'flex',
        justifyContent: 'space-between',
        marginBottom: '10px',
        fontSize: '14px',
        color: '#666'
      }}>
        <span>{kayitDurumu}</span>
        {sonKayit && <span>Son kayıt: {sonKayit}</span>}
      </div>
      
      <input
        name="baslik"
        value={form.baslik}
        onChange={handleChange}
        placeholder="Başlık..."
        style={{
          width: '100%',
          padding: '10px',
          marginBottom: '10px',
          border: '1px solid #ddd',
          borderRadius: '5px'
        }}
      />
      
      <textarea
        name="icerik"
        value={form.icerik}
        onChange={handleChange}
        placeholder="İçerik yazın... (Otomatik kaydedilecek)"
        style={{
          width: '100%',
          height: '200px',
          padding: '10px',
          border: '1px solid #ddd',
          borderRadius: '5px',
          resize: 'vertical'
        }}
      />
      
      <select
        name="kategori"
        value={form.kategori}
        onChange={handleChange}
        style={{
          width: '100%',
          padding: '10px',
          marginTop: '10px',
          border: '1px solid #ddd',
          borderRadius: '5px'
        }}
      >
        <option value="genel">Genel</option>
        <option value="is">İş</option>
        <option value="kisisel">Kişisel</option>
      </select>
      
      <button
        onClick={temizle}
        style={{
          marginTop: '10px',
          padding: '10px 20px',
          backgroundColor: '#e74c3c',
          color: 'white',
          border: 'none',
          borderRadius: '5px',
          cursor: 'pointer'
        }}
      >
        Temizle
      </button>
    </div>
  );
}
```

### 🌐 API Kullanımı - Detaylı Örnekler

#### Örnek 1: Basit Veri Çekme

```jsx
import { useState, useEffect } from 'react';

function BasitAPIOrnek() {
  const [veri, setVeri] = useState(null);
  const [yukleniyor, setYukleniyor] = useState(true);
  const [hata, setHata] = useState(null);
  
  useEffect(() => {
    // Veri çekme fonksiyonu
    const veriCek = async () => {
      try {
        // 1. Yükleniyor durumunu aç
        setYukleniyor(true);
        
        // 2. API'ye istek at
        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        
        // 3. Response kontrolü
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        // 4. JSON'a çevir
        const data = await response.json();
        
        // 5. Veriyi state'e kaydet
        setVeri(data);
      } catch (err) {
        // 6. Hata varsa yakala
        setHata(err.message);
      } finally {
        // 7. Yükleniyor durumunu kapat
        setYukleniyor(false);
      }
    };
    
    veriCek();
  }, []); // Sadece ilk yüklemede
  
  // Farklı durumlar için farklı görünümler
  if (yukleniyor) {
    return (
      <div style={{textAlign: 'center', padding: '50px'}}>
        <div style={{fontSize: '50px'}}>⏳</div>
        <p>Veriler yükleniyor...</p>
      </div>
    );
  }
  
  if (hata) {
    return (
      <div style={{
        textAlign: 'center',
        padding: '50px',
        color: 'red'
      }}>
        <div style={{fontSize: '50px'}}>❌</div>
        <p>Hata: {hata}</p>
        <button onClick={() => window.location.reload()}>
          Tekrar Dene
        </button>
      </div>
    );
  }
  
  return (
    <div style={{padding: '20px'}}>
      <h2>API'den Gelen Veri</h2>
      <div style={{
        backgroundColor: '#f0f0f0',
        padding: '15px',
        borderRadius: '5px'
      }}>
        <h3>{veri.title}</h3>
        <p>{veri.body}</p>
        <small>Post ID: {veri.id} | User ID: {veri.userId}</small>
      </div>
    </div>
  );
}
```

#### Örnek 2: Kullanıcı Listesi ve Detay

```jsx
import { useState, useEffect } from 'react';

function KullaniciYonetimi() {
  const [kullanicilar, setKullanicilar] = useState([]);
  const [secilenKullanici, setSecilenKullanici] = useState(null);
  const [kullaniciPostlari, setKullaniciPostlari] = useState([]);
  const [yukleniyor, setYukleniyor] = useState(false);
  const [aramaMetni, setAramaMetni] = useState('');
  
  // Kullanıcıları yükle
  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(res => res.json())
      .then(data => setKullanicilar(data))
      .catch(err => console.error('Hata:', err));
  }, []);
  
  // Seçilen kullanıcının postlarını yükle
  useEffect(() => {
    if (!secilenKullanici) return;
    
    setYukleniyor(true);
    fetch(`https://jsonplaceholder.typicode.com/posts?userId=${secilenKullanici.id}`)
      .then(res => res.json())
      .then(data => {
        setKullaniciPostlari(data);
        setYukleniyor(false);
      })
      .catch(err => {
        console.error('Hata:', err);
        setYukleniyor(false);
      });
  }, [secilenKullanici]);
  
  // Filtrelenmiş kullanıcılar
  const filtrelenmisKullanicilar = kullanicilar.filter(k =>
    k.name.toLowerCase().includes(aramaMetni.toLowerCase()) ||
    k.email.toLowerCase().includes(aramaMetni.toLowerCase())
  );
  
  return (
    <div style={{
      display: 'flex',
      gap: '20px',
      padding: '20px',
      height: '100vh'
    }}>
      {/* Sol Panel - Kullanıcı Listesi */}
      <div style={{
        width: '300px',
        borderRight: '1px solid #ddd',
        paddingRight: '20px',
        overflowY: 'auto'
      }}>
        <h2>👥 Kullanıcılar</h2>
        
        <input
          type="text"
          value={aramaMetni}
          onChange={(e) => setAramaMetni(e.target.value)}
          placeholder="Kullanıcı ara..."
          style={{
            width: '100%',
            padding: '8px',
            marginBottom: '15px',
            border: '1px solid #ddd',
            borderRadius: '5px'
          }}
        />
        
        {filtrelenmisKullanicilar.map(kullanici => (
          <div
            key={kullanici.id}
            onClick={() => setSecilenKullanici(kullanici)}
            style={{
              padding: '10px',
              marginBottom: '10px',
              backgroundColor: secilenKullanici?.id === kullanici.id ? '#e3f2fd' : '#f5f5f5',
              borderRadius: '5px',
              cursor: 'pointer',
              transition: 'all 0.3s'
            }}
          >
            <strong>{kullanici.name}</strong>
            <p style={{margin: '5px 0', fontSize: '14px', color: '#666'}}>
              {kullanici.email}
            </p>
            <p style={{margin: '0', fontSize: '12px', color: '#999'}}>
              {kullanici.company.name}
            </p>
          </div>
        ))}
      </div>
      
      {/* Sağ Panel - Kullanıcı Detayı */}
      <div style={{flex: 1, overflowY: 'auto'}}>
        {secilenKullanici ? (
          <>
            <div style={{
              backgroundColor: '#f0f0f0',
              padding: '20px',
              borderRadius: '10px',
              marginBottom: '20px'
            }}>
              <h2>{secilenKullanici.name}</h2>
              <p>📧 {secilenKullanici.email}</p>
              <p>📱 {secilenKullanici.phone}</p>
              <p>🌐 {secilenKullanici.website}</p>
              <p>🏢 {secilenKullanici.company.name}</p>
              <p>📍 {secilenKullanici.address.city}</p>
            </div>
            
            <h3>📝 Kullanıcının Yazıları ({kullaniciPostlari.length})</h3>
            
            {yukleniyor ? (
              <p>Yazılar yükleniyor...</p>
            ) : (
              <div>
                {kullaniciPostlari.map(post => (
                  <div
                    key={post.id}
                    style={{
                      padding: '15px',
                      marginBottom: '15px',
                      backgroundColor: 'white',
                      border: '1px solid #ddd',
                      borderRadius: '5px'
                    }}
                  >
                    <h4>{post.title}</h4>
                    <p>{post.body}</p>
                  </div>
                ))}
              </div>
            )}
          </>
        ) : (
          <div style={{
            display: 'flex',
            alignItems: 'center',
            justifyContent: 'center',
            height: '100%',
            color: '#999'
          }}>
            <p>Bir kullanıcı seçin</p>
          </div>
        )}
      </div>
    </div>
  );
}
```

#### Örnek 3: Infinite Scroll (Sonsuz Kaydırma)

```jsx
import { useState, useEffect, useCallback } from 'react';

function SonsuzKaydirma() {
  const [resimler, setResimler] = useState([]);
  const [sayfa, setSayfa] = useState(1);
  const [yukleniyor, setYukleniyor] = useState(false);
  const [dahaFazlaVar, setDahaFazlaVar] = useState(true);
  
  // Resimleri yükle
  const resimleriYukle = useCallback(async () => {
    if (yukleniyor || !dahaFazlaVar) return;
    
    setYukleniyor(true);
    try {
      // Picsum API'si kullanıyoruz
      const response = await fetch(
        `https://picsum.photos/v2/list?page=${sayfa}&limit=10`
      );
      const yeniResimler = await response.json();
      
      if (yeniResimler.length === 0) {
        setDahaFazlaVar(false);
      } else {
        setResimler(prev => [...prev, ...yeniResimler]);
        setSayfa(prev => prev + 1);
      }
    } catch (error) {
      console.error('Hata:', error);
    } finally {
      setYukleniyor(false);
    }
  }, [sayfa, yukleniyor, dahaFazlaVar]);
  
  // İlk yükleme
  useEffect(() => {
    resimleriYukle();
  }, []);
  
  // Scroll event listener
  useEffect(() => {
    const handleScroll = () => {
      // Sayfanın sonuna gelindi mi kontrolü
      if (window.innerHeight + document.documentElement.scrollTop 
          >= document.documentElement.offsetHeight - 100) {
        resimleriYukle();
      }
    };
    
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, [resimleriYukle]);
  
  return (
    <div style={{padding: '20px'}}>
      <h2>📷 Sonsuz Resim Galerisi</h2>
      <p style={{color: '#666'}}>
        Aşağı kaydırdıkça yeni resimler yüklenir
      </p>
      
      <div style={{
        display: 'grid',
        gridTemplateColumns: 'repeat(auto-fill, minmax(300px, 1fr))',
        gap: '20px',
        marginTop: '20px'
      }}>
        {resimler.map((resim, index) => (
          <div
            key={`${resim.id}-${index}`}
            style={{
              backgroundColor: '#f0f0f0',
              borderRadius: '10px',
              overflow: 'hidden',
              boxShadow: '0 2px 8px rgba(0,0,0,0.1)'
            }}
          >
            <img
              src={`https://picsum.photos/id/${resim.id}/300/200`}
              alt={resim.author}
              style={{
                width: '100%',
                height: '200px',
                objectFit: 'cover'
              }}
              loading="lazy"
            />
            <div style={{padding: '15px'}}>
              <p style={{margin: '0', fontWeight: 'bold'}}>
                Fotoğraf: {resim.author}
              </p>
              <a
                href={resim.url}
                target="_blank"
                rel="noopener noreferrer"
                style={{
                  color: '#3498db',
                  fontSize: '14px'
                }}
              >
                Orijinal →
              </a>
            </div>
          </div>
        ))}
      </div>
      
      {yukleniyor && (
        <div style={{
          textAlign: 'center',
          padding: '30px',
          fontSize: '20px'
        }}>
          ⏳ Daha fazla yükleniyor...
        </div>
      )}
      
      {!dahaFazlaVar && (
        <div style={{
          textAlign: 'center',
          padding: '30px',
          color: '#666'
        }}>
          Tüm resimler yüklendi! 🎉
        </div>
      )}
    </div>
  );
}
```

### 🎯 useEffect ile İlgili Sık Sorulan Sorular

#### Soru 1: useEffect ne zaman kullanmalıyım?

**Cevap:** 
- API'den veri çekerken
- Timer/Interval kullanırken
- DOM manipülasyonu yaparken
- Local Storage işlemlerinde
- Event listener eklerken

#### Soru 2: Cleanup fonksiyonu nedir?

```jsx
useEffect(() => {
  // Setup kodu
  const timer = setInterval(() => {
    console.log('Çalışıyor');
  }, 1000);
  
  // Cleanup fonksiyonu
  return () => {
    clearInterval(timer); // Timer'ı durdur
    console.log('Temizlendi');
  };
}, []);
```

**Cevap:** Component kaldırıldığında veya effect yeniden çalışmadan önce temizlik yapar. Memory leak'leri önler.

#### Soru 3: Dependency array'e ne koymalıyım?

```jsx
// ❌ YANLIŞ - Eksik dependency
useEffect(() => {
  console.log(sayi); // sayi kullanılıyor ama dependency'de yok
}, []); 

// ✅ DOĞRU
useEffect(() => {
  console.log(sayi);
}, [sayi]); // sayi dependency'de
```

**Cevap:** Effect içinde kullandığınız tüm state ve props'ları dependency array'e ekleyin.

#### Soru 4: Sonsuz döngüye nasıl girerim ve nasıl çözülür?

```jsx
// ❌ SONSUZ DÖNGÜ
useEffect(() => {
  setSayi(sayi + 1); // Her render'da sayi değişir
}); // Dependency yok = her render'da çalışır

// ✅ ÇÖZÜM 1: Dependency ekle
useEffect(() => {
  setSayi(sayi + 1);
}, []); // Sadece ilk yüklemede

// ✅ ÇÖZÜM 2: Koşul ekle
useEffect(() => {
  if (sayi < 10) {
    setSayi(sayi + 1);
  }
}, [sayi]);
```

---

## 🎓 2. Hafta Özeti ve Önemli Noktalar

### State Kullanımında Dikkat Edilecekler:
1. **State'i direkt değiştirmeyin** - Her zaman setter fonksiyonu kullanın
2. **State güncellemeleri asenkrondur** - Hemen güncellenmez
3. **Objeler ve dizilerde spread operator kullanın** - `{...obj}` veya `[...array]`
4. **Gereksiz state kullanmayın** - Hesaplanabilir değerler için state tutmayın

### useEffect Kullanımında Dikkat Edilecekler:
1. **Dependency array'i unutmayın** - Sonsuz döngüye girersiniz
2. **Cleanup fonksiyonlarını kullanın** - Memory leak'leri önleyin
3. **Async fonksiyonları direkt kullanmayın** - İçerde tanımlayın
4. **Race condition'lara dikkat edin** - Eski istekleri iptal edin

### API Kullanımında Best Practices:
1. **Loading state kullanın** - Kullanıcıya geri bildirim verin
2. **Error handling yapın** - Hataları yakalayın ve gösterin
3. **Try-catch kullanın** - Async/await ile birlikte
4. **AbortController kullanın** - İstekleri iptal edebilmek için

**Tebrikler! 2. Haftayı da tamamladınız! 🎉**
```

### ⏰ Dijital Saat Örneği

```jsx
import { useState, useEffect } from 'react';

function DijitalSaat() {
  const [saat, setSaat] = useState(new Date());
  
  useEffect(() => {
    // Her saniye saati güncelle
    const zamanlayici = setInterval(() => {
      setSaat(new Date());
    }, 1000);
    
    // Component kaldırıldığında zamanlayıcıyı temizle
    return () => {
      clearInterval(zamanlayici);
    };
  }, []); // Sadece bir kez başlat
  
  return (
    <div style={{
      display: 'flex',
      flexDirection: 'column',
      alignItems: 'center',
      justifyContent: 'center',
      height: '300px',
      backgroundColor: '#2c3e50',
      color: '#2ecc71',
      fontFamily: 'monospace',
      borderRadius: '15px',
      margin: '20px'
    }}>
      <div style={{ fontSize: '60px', fontWeight: 'bold' }}>
        {saat.toLocaleTimeString('tr-TR')}
      </div>
      <div style={{ fontSize: '24px', marginTop: '10px' }}>
        {saat.toLocaleDateString('tr-TR', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        })}
      </div>
    </div>
  );
}
```

### 🌐 API'den Veri Çekme

API (Application Programming Interface), farklı uygulamaların birbiriyle konuşmasını sağlar.

#### Fetch API ile Veri Çekme:

```jsx
import { useState, useEffect } from 'react';

function KullaniciListesi() {
  const [kullanicilar, setKullanicilar] = useState([]);
  const [yukleniyor, setYukleniyor] = useState(true);
  const [hata, setHata] = useState(null);
  
  useEffect(() => {
    // API'den veri çek
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        if (!response.ok) {
          throw new Error('Veri çekilemedi!');
        }
        return response.json();
      })
      .then(data => {
        setKullanicilar(data);
        setYukleniyor(false);
      })
      .catch(error => {
        setHata(error.message);
        setYukleniyor(false);
      });
  }, []);
  
  // Yükleniyor durumu
  if (yukleniyor) {
    return (
      <div style={{
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center',
        height: '100vh',
        fontSize: '24px'
      }}>
        ⏳ Yükleniyor...
      </div>
    );
  }
  
  // Hata durumu
  if (hata) {
    return (
      <div style={{
        color: 'red',
        textAlign: 'center',
        padding: '20px'
      }}>
        ❌ Hata: {hata}
      </div>
    );
  }
  
  // Başarılı durumu
  return (
    <div style={{padding: '20px'}}>
      <h2>👥 Kullanıcı Listesi</h2>
      <div style={{
        display: 'grid',
        gridTemplateColumns: 'repeat(auto-fill, minmax(300px, 1fr))',
        gap: '20px'
      }}>
        {kullanicilar.map(kullanici => (
          <div
            key={kullanici.id}
            style={{
              border: '1px solid #ddd',
              borderRadius: '10px',
              padding: '15px',
              backgroundColor: '#f9f9f9'
            }}
          >
            <h3>{kullanici.name}</h3>
            <p>📧 {kullanici.email}</p>
            <p>📱 {kullanici.phone}</p>
            <p>🌐 {kullanici.website}</p>
            <p>🏢 {kullanici.company.name}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
```

### 🔄 Async/Await Kullanımı

Modern JavaScript'te Promise'leri daha temiz kullanmak için async/await kullanırız:

```jsx
import { useState, useEffect } from 'react';

function PostListesi() {
  const [postlar, setPostlar] = useState([]);
  const [yukleniyor, setYukleniyor] = useState(true);
  const [hata, setHata] = useState(null);
  const [sayfa, setSayfa] = useState(1);
  
  useEffect(() => {
    // Async fonksiyon tanımla
    const verileriCek = async () => {
      try {
        setYukleniyor(true);
        
        // await ile response'u bekle
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/posts?_page=${sayfa}&_limit=10`
        );
        
        if (!response.ok) {
          throw new Error('Veriler yüklenemedi');
        }
        
        // JSON'a çevir
        const data = await response.json();
        setPostlar(data);
        
      } catch (err) {
        setHata(err.message);
      } finally {
        setYukleniyor(false);
      }
    };
    
    // Fonksiyonu çağır
    verileriCek();
  }, [sayfa]); // sayfa değişince yeniden çek
  
  if (yukleniyor) {
    return <div>Yükleniyor...</div>;
  }
  
  if (hata) {
    return <div>Hata: {hata}</div>;
  }
  
  return (
    <div>
      <h2>📝 Blog Yazıları</h2>
      
      {postlar.map(post => (
        <article
          key={post.id}
          style={{
            marginBottom: '20px',
            padding: '15px',
            border: '1px solid #ddd',
            borderRadius: '8px'
          }}
        >
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </article>
      ))}
      
      {/* Sayfalama */}
      <div style={{
        display: 'flex',
        justifyContent: 'center',
        gap: '10px',
        marginTop: '20px'
      }}>
        <button
          onClick={() => setSayfa(sayfa - 1)}
          disabled={sayfa === 1}
          style={{
            padding: '10px 20px',
            backgroundColor: sayfa === 1 ? '#95a5a6' : '#3498db',
            color: 'white',
            border: 'none',
            borderRadius: '5px',
            cursor: sayfa === 1 ? 'not-allowed' : 'pointer'
          }}
        >
          ← Önceki
        </button>
        
        <span style={{
          padding: '10px',
          fontSize: '18px'
        }}>
          Sayfa {sayfa}
        </span>
        
        <button
          onClick={() => setSayfa(sayfa + 1)}
          style={{
            padding: '10px 20px',
            backgroundColor: '#3498db',
            color: 'white',
            border: 'none',
            borderRadius: '5px',
            cursor: 'pointer'
          }}
        >
          Sonraki →
        </button>
      </div>
    </div>
  );
}
```

### ☀️ Mini Proje: Hava Durumu Uygulaması

OpenWeatherMap API kullanarak gerçek hava durumu verisi gösterelim:

```jsx
import { useState, useEffect } from 'react';

function HavaDurumu() {
  const [sehir, setSehir] = useState('Istanbul');
  const [aramaMetni, setAramaMetni] = useState('');
  const [havaDurumu, setHavaDurumu] = useState(null);
  const [yukleniyor, setYukleniyor] = useState(false);
  const [hata, setHata] = useState(null);
  
  // API Key (ücretsiz hesap açarak alabilirsiniz)
  // openweathermap.org adresinden
  const API_KEY = 'YOUR_API_KEY_HERE';
  const API_URL = `https://api.openweathermap.org/data/2.5/weather?q=${sehir}&appid=${API_KEY}&units=metric&lang=tr`;
  
  useEffect(() => {
    havaDurumuGetir();
  }, [sehir]);
  
  const havaDurumuGetir = async () => {
    try {
      setYukleniyor(true);
      setHata(null);
      
      const response = await fetch(API_URL);
      
      if (!response.ok) {
        if (response.status === 404) {
          throw new Error('Şehir bulunamadı');
        }
        throw new Error('Hava durumu alınamadı');
      }
      
      const data = await response.json();
      setHavaDurumu(data);
      
    } catch (err) {
      setHata(err.message);
      setHavaDurumu(null);
    } finally {
      setYukleniyor(false);
    }
  };
  
  const aramaYap = (e) => {
    e.preventDefault();
    if (aramaMetni.trim()) {
      setSehir(aramaMetni);
      setAramaMetni('');
    }
  };
  
  // Hava durumu ikonunu al
  const havaDurumuIkonu = (durum) => {
    const ikonlar = {
      'Clear': '☀️',
      'Clouds': '☁️',
      'Rain': '🌧️',
      'Drizzle': '🌦️',
      'Thunderstorm': '⛈️',
      'Snow': '❄️',
      'Mist': '🌫️',
      'Fog': '🌫️'
    };
    return ikonlar[durum] || '🌡️';
  };
  
  // Arkaplan rengini belirle
  const arkaplanRengi = () => {
    if (!havaDurumu) return '#3498db';
    const sicaklik = havaDurumu.main.temp;
    
    if (sicaklik < 0) return '#9b59b6';  // Mor - Çok soğuk
    if (sicaklik < 10) return '#3498db'; // Mavi - Soğuk
    if (sicaklik < 20) return '#2ecc71'; // Yeşil - Ilık
    if (sicaklik < 30) return '#f39c12'; // Turuncu - Sıcak
    return '#e74c3c'; // Kırmızı - Çok sıcak
  };
  
  return (
    <div style={{
      minHeight: '100vh',
      background: `linear-gradient(135deg, ${arkaplanRengi()} 0%, ${arkaplanRengi()}dd 100%)`,
      padding: '20px',
      color: 'white',
      fontFamily: 'Arial, sans-serif'
    }}>
      <div style={{
        maxWidth: '500px',
        margin: '0 auto'
      }}>
        <h1 style={{textAlign: 'center', marginBottom: '30px'}}>
          🌤️ Hava Durumu
        </h1>
        
        {/* Arama Formu */}
        <form onSubmit={aramaYap} style={{
          display: 'flex',
          gap: '10px',
          marginBottom: '30px'
        }}>
          <input
            type="text"
            value={aramaMetni}
            onChange={(e) => setAramaMetni(e.target.value)}
            placeholder="Şehir adı giriniz..."
            style={{
              flex: 1,
              padding: '12px',
              fontSize: '16px',
              border: 'none',
              borderRadius: '25px',
              backgroundColor: 'rgba(255,255,255,0.2)',
              color: 'white',
              backdropFilter: 'blur(10px)'
            }}
          />
          <button
            type="submit"
            style={{
              padding: '12px 24px',
              fontSize: '16px',
              border: 'none',
              borderRadius: '25px',
              backgroundColor: 'rgba(255,255,255,0.3)',
              color: 'white',
              cursor: 'pointer',
              backdropFilter: 'blur(10px)'
            }}
          >
            Ara
          </button>
        </form>
        
        {/* Yükleniyor */}
        {yukleniyor && (
          <div style={{
            textAlign: 'center',
            fontSize: '24px',
            padding: '50px'
          }}>
            ⏳ Yükleniyor...
          </div>
        )}
        
        {/* Hata */}
        {hata && (
          <div style={{
            backgroundColor: 'rgba(231, 76, 60, 0.2)',
            border: '2px solid #e74c3c',
            borderRadius: '10px',
            padding: '20px',
            textAlign: 'center'
          }}>
            ❌ {hata}
          </div>
        )}
        
        {/* Hava Durumu Kartı */}
        {havaDurumu && !yukleniyor && (
          <div style={{
            backgroundColor: 'rgba(255,255,255,0.1)',
            backdropFilter: 'blur(10px)',
            borderRadius: '20px',
            padding: '30px',
            textAlign: 'center'
          }}>
            {/* Şehir Adı */}
            <h2 style={{
              fontSize: '32px',
              marginBottom: '10px'
            }}>
              {havaDurumu.name}, {havaDurumu.sys.country}
            </h2>
            
            {/* Ana Sıcaklık */}
            <div style={{
              fontSize: '72px',
              margin: '20px 0'
            }}>
              {havaDurumuIkonu(havaDurumu.weather[0].main)}
            </div>
            
            <div style={{
              fontSize: '48px',
              fontWeight: 'bold',
              marginBottom: '10px'
            }}>
              {Math.round(havaDurumu.main.temp)}°C
            </div>
            
            {/* Hava Durumu Açıklaması */}
            <p style={{
              fontSize: '20px',
              textTransform: 'capitalize',
              marginBottom: '20px'
            }}>
              {havaDurumu.weather[0].description}
            </p>
            
            {/* Detaylı Bilgiler */}
            <div style={{
              display: 'grid',
              gridTemplateColumns: '1fr 1fr',
              gap: '15px',
              marginTop: '30px',
              fontSize: '16px'
            }}>
              <div style={{
                backgroundColor: 'rgba(255,255,255,0.1)',
                padding: '10px',
                borderRadius: '10px'
              }}>
                <p style={{margin: '0', opacity: '0.8'}}>Hissedilen</p>
                <p style={{margin: '0', fontSize: '20px', fontWeight: 'bold'}}>
                  {Math.round(havaDurumu.main.feels_like)}°C
                </p>
              </div>
              
              <div style={{
                backgroundColor: 'rgba(255,255,255,0.1)',
                padding: '10px',
                borderRadius: '10px'
              }}>
                <p style={{margin: '0', opacity: '0.8'}}>Nem</p>
                <p style={{margin: '0', fontSize: '20px', fontWeight: 'bold'}}>
                  %{havaDurumu.main.humidity}
                </p>
              </div>
              
              <div style={{
                backgroundColor: 'rgba(255,255,255,0.1)',
                padding: '10px',
                borderRadius: '10px'
              }}>
                <p style={{margin: '0', opacity: '0.8'}}>Rüzgar</p>
                <p style={{margin: '0', fontSize: '20px', fontWeight: 'bold'}}>
                  {havaDurumu.wind.speed} m/s
                </p>
              </div>
              
              <div style={{
                backgroundColor: 'rgba(255,255,255,0.1)',
                padding: '10px',
                borderRadius: '10px'
              }}>
                <p style={{margin: '0', opacity: '0.8'}}>Basınç</p>
                <p style={{margin: '0', fontSize: '20px', fontWeight: 'bold'}}>
                  {havaDurumu.main.pressure} hPa
                </p>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

export default HavaDurumu;
```

### 📚 Ödev: Film Arama Uygulaması

OMDB API kullanarak film arama uygulaması yapın:

```jsx
import { useState, useEffect } from 'react';

function FilmArama() {
  const [aramaMetni, setAramaMetni] = useState('');
  const [filmler, setFilmler] = useState([]);
  const [yukleniyor, setYukleniyor] = useState(false);
  const [hata, setHata] = useState(null);
  
  // OMDB API Key (ücretsiz hesap açın)
  const API_KEY = 'YOUR_API_KEY';
  
  const filmAra = async () => {
    if (!aramaMetni.trim()) {
      alert('Lütfen film adı girin!');
      return;
    }
    
    try {
      setYukleniyor(true);
      setHata(null);
      
      const response = await fetch(
        `http://www.omdbapi.com/?s=${aramaMetni}&apikey=${API_KEY}`
      );
      
      const data = await response.json();
      
      if (data.Response === 'True') {
        setFilmler(data.Search);
      } else {
        setHata('Film bulunamadı');
        setFilmler([]);
      }
    } catch (err) {
      setHata('Bir hata oluştu');
    } finally {
      setYukleniyor(false);
    }
  };
  
  return (
    <div style={{
      padding: '20px',
      backgroundColor: '#1a1a2e',
      minHeight: '100vh',
      color: 'white'
    }}>
      <h1 style={{textAlign: 'center'}}>🎬 Film Arama</h1>
      
      {/* Arama Formu */}
      <div style={{
        display: 'flex',
        gap: '10px',
        maxWidth: '500px',
        margin: '20px auto'
      }}>
        <input
          type="text"
          value={aramaMetni}
          onChange={(e) => setAramaMetni(e.target.value)}
          onKeyPress={(e) => e.key === 'Enter' && filmAra()}
          placeholder="Film adı yazın..."
          style={{
            flex: 1,
            padding: '10px',
            fontSize: '16px',
            borderRadius: '5px',
            border: 'none'
          }}
        />
        <button
          onClick={filmAra}
          style={{
            padding: '10px 20px',
            backgroundColor: '#e50914',
            color: 'white',
            border: 'none',
            borderRadius: '5px',
            cursor: 'pointer',
            fontSize: '16px'
          }}
        >
          Ara
        </button>
      </div>
      
      {/* Yükleniyor */}
      {yukleniyor && (
        <div style={{textAlign: 'center'}}>
          <p>Filmler aranıyor...</p>
        </div>
      )}
      
      {/* Hata */}
      {hata && (
        <div style={{
          textAlign: 'center',
          color: '#e50914'
        }}>
          <p>{hata}</p>
        </div>
      )}
      
      {/* Film Listesi */}
      <div style={{
        display: 'grid',
        gridTemplateColumns: 'repeat(auto-fill, minmax(200px, 1fr))',
        gap: '20px',
        marginTop: '30px'
      }}>
        {filmler.map(film => (
          <div
            key={film.imdbID}
            style={{
              backgroundColor: '#16213e',
              borderRadius: '10px',
              padding: '10px',
              textAlign: 'center'
            }}
          >
            <img
              src={film.Poster !== 'N/A' ? film.Poster : 'https://via.placeholder.com/200x300'}
              alt={film.Title}
              style={{
                width: '100%',
                height: '300px',
                objectFit: 'cover',
                borderRadius: '5px'
              }}
            />
            <h3 style={{
              fontSize: '16px',
              margin: '10px 0 5px 0'
            }}>
              {film.Title}
            </h3>
            <p style={{
              color: '#888',
              margin: '0'
            }}>
              {film.Year}
            </p>
          </div>
        ))}
      </div>
    </div>
  );
}

export default FilmArama;
```

---

## 🎓 Öğrendiklerimizin Özeti

### Hafta 1'de Öğrendiklerimiz:
- ✅ React nedir ve neden kullanılır
- ✅ İlk React projesi oluşturma
- ✅ JSX syntax ve kuralları
- ✅ DIV ve HTML5 semantic elementler
- ✅ Style/CSS kullanımı
- ✅ JavaScript temelleri (const, let, if-else, fonksiyonlar)
- ✅ Component oluşturma
- ✅ Props ile veri aktarımı

### Hafta 2'de Öğrendiklerimiz:
- ✅ State kavramı ve useState Hook'u
- ✅ Event handling (tıklama, form olayları)
- ✅ Controlled components
- ✅ Todo List uygulaması
- ✅ useEffect Hook'u
- ✅ API'lerden veri çekme
- ✅ Loading ve error durumları yönetimi
- ✅ Async/await kullanımı

### 🚀 Sonraki Adımlar:
1. Bu örnekleri kendi bilgisayarınızda deneyin
2. Kendi projelerinizi oluşturun
3. React Native'e geçiş yapın
4. Daha ileri seviye konular öğrenin (Context, Redux, Router)

---

## 📝 Notlar ve İpuçları

### React'te Sık Yapılan Hatalar:
1. **State'i direkt değiştirmeyin** - Her zaman setState kullanın
2. **Key prop'u unutmayın** - map kullanırken her element'e key verin
3. **useEffect dependency array'i unutmayın** - Sonsuz döngüye girer
4. **async/await'i try-catch ile kullanın** - Hataları yakalayın

### Faydalı Kaynaklar:
- React Resmi Dokümantasyon: reactjs.org
- MDN Web Docs: developer.mozilla.org
- W3Schools: w3schools.com
- YouTube eğitim videoları

---

**📌 SON NOT:** Bu rehber sürekli pratik yaparak öğrenmenizi sağlamak için hazırlandı. Her konuyu mutlaka kendi bilgisayarınızda deneyin ve farklı örnekler yapın. Kod yazarak öğrenmek en etkili yöntemdir!

**Başarılar! 🎉**
