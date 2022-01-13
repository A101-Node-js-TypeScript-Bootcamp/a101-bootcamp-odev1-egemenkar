# 2. Ödev - Node.js ile Sunucu Ayağa Kaldırma

Node.js ile sunucu ayağa kaldırabilmek için öncelikle bilgisayarımızda **Node.js** yüklü olması gerekiyor.

## İçindekiler
1. [NodeJs Kurulumu](#nodejs-kurulumu)
2. [NodeJs Sunucu Kurulumu](#nodejs-sunucu-kurulumu)
3. [ExpressJs ile Sunucu Kurulumu](#expressjs-ile-sunucu-kurulumu)
4. [Kaynaklar](#kaynaklar)

## NodeJs Kurulumu

Aşağıdaki adımları izlemeliyiz.

-  [Bu adrese](https://nodejs.org/en/) gidin.
-  LTS versiyonunu tıklayın ve indirin.
-  İnen paketi çift tıklayark kurulumu tamamlayın.

Bu adımları tamamladıktan sonra **Node.js** ve **NPM**'in kurulumunu hatasız bir şekilde yapmış mıyız anlayabilmek için terminal/command açın ve aşağıdaki komutları yazın.

```
  > node -v
  v17.3.0
```
```
  > npm -v
  8.3.0
```
## NodeJs Sunucu Kurulumu

Ek bir paket yüklemeden yalnızca Node.js kullarak aşağıdaki şekilde bir sunucu ayağa kaldırabiliriz.

Bu kodu oluşturduğunuz bir **index.js** dosyasına yapıştırın.

```
//HTTP modülünü yükler
const http = require("http");
const hostname = '127.0.0.1';
const port = 3000;

//Bir HTTP sunucusu yaratır ve 3000 portunda istekleri takip eder
const server = http.createServer((req, res) => {

  //İstek sonarası sunucu tarafından verilecek cevap ve durumu gösterir
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

//3000 portunda sunucunun çalıştığını gösteren fonksiyon
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

Daha sonra terminal/command'a gelin ve kodunuzu çalıştırın.

```
  >node index.js
  Server running at http://127.0.0.1:3000/
```
Eğer her şey yolunda gittiyse yukarıdaki adresi tarayıcınızda açtığınızda "Hello World" yazısını göreceksiniz.

## ExpressJs ile Sunucu Kurulumu

[Express.js](https://expressjs.com/) paketi, **Node.js** tabanlı bir web uygulama sunucu çatısıdır. Express.js’nin sunduğu sınırsız HTTP yardımcı araçları ve katmanlar sayesinde oldukça hızlı ve kolaydır şekilde sunucu kurabiliriz.

Öncelikle **package.json** dosyasını oluşturmamız gerekiyor. Bunu aşağıdaki komutu çalıştırarak yapıyoruz. 

```
  >npm init
```

Komutu girdikten sonra size uygulamanın adı, versiyonu gibi bir takım sorular soruluyor. Daha sonra verdiğiniz bilgilere göre aşağıda yer alan **package.json** dosyası oluşturuluyor.

```
{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

Şimdi NPM ile express.js paketini yükleyeceğiz.

```
  >npm install express
```

Bu komut sonrasında package.json dosyasına baktığınızda **dependencies** eklendiğini göreceksiniz. Yüklediğimiz tüm paketler bu başlık altında package.json dosyamız içerisinde gösterilir.

```
{
  "name": "myapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.2"
  }
}
```

Yukarıda HTTP ile yaptığımız işlemin bir benzerini, express ile aşağıdaki şekilde yapabiliriz.

```
const express = require('express')
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!')
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`)
});
```

Sunucunuzu aşağıdaki komutu girerek başlatabilirsiniz.

```
  >node index.js
  Example app listening on port 3000
```

Hatasız bir şekilde kurulum yapmayı başardınız ise [http://127.0.0.1:3000/](http://127.0.0.1:3000/) adresini tarayıcınızda açtığınızda "Hello World" yazısını göreceksiniz.

## Kaynaklar

#### 1

[https://nodejs.org/en/](https://nodejs.org/en/)

#### 2

[https://expressjs.com/](https://expressjs.com/)

#### 3

[https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/development_environment](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/development_environment)