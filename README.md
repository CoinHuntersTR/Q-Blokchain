# Q Blokchain Node Testnet Kurulum Rehberi

![aleotestneti](https://miro.medium.com/max/4800/1*FAK4WvLprmUDh_t3gthrYQ.webp)


### Önerilen Sistem Gereksinimleri;

|CPU | RAM  | Disk  | 
|----|------|----------|
|  3| 2GB  | 128GB    |

 # Daha önce Node kurulumu yapmadıysanız buradan sırasıyla adımları takip ederek tüm süreci öğrenebilirsiniz.
  ## Yeni Başladım Rehberi; [Coin Hunters Testnet](https://www.pusulafinans.com/category/testnet/)
  ### 1. [Testnet ve Node test kurulum rehberi Bölüm-1](https://www.pusulafinans.com/testnet-ve-node-kurulum-rehberi/)
  ### 2. [Yeni Chrome Tarayıcı nasıl açarım?](https://www.pusulafinans.com/yeni-chrome-tarayici-nasil-acarim/)
  ### 3. [Ücretsiz Sunucu Kiralama](https://www.pusulafinans.com/nasil-ucretsiz-sunucu-kiralarim/)
  ### 4. [Digital Ocean Nasıl Kayıt olurum?](https://www.pusulafinans.com/digital-oceana-nasil-kayit-olabilirim/)
  ### 5. [MobaXTerm Terminal Kurulumu](https://www.pusulafinans.com/mobaxterm-terminal-kurulumu/)
  
## UYARI

![aleotestneti](https://miro.medium.com/max/4800/1*ESh0wU_KRa7cUxeXNv2aMg.webp)

> Ödülü dağıtım periyodu ve Node çalıştırma süreleri yukarıdaki görselde belirtilmiştir. 31 Aralık 2022 kadar kurulum ve kayıt işlemleri (bu sırada node çalışıyor olacak, 31 Mart 2023 yılında da Node testi biteceği belirtilmiş.) 
> Ödül Dağılım;
### Kazanılan ödüller dağıtım tarihinden itibaren 3 AY KİLİTLİ kalacaktır.
#### 1. Ödüllüerin %50'si ile Validator kurmak ve ağda topluluk oluşturmak için stake edilebilecektir.
#### 2. Kalan %50'si ile başka Validatore stake edilebilir.
#### 3. Kazanılan tokenlerin %100'ü ile tüm oylamalarda oy hakkında sahip olunacaktır.
#### [Detaylı Anlatım için Projenin yayınladığı makale](https://medium.com/q-blockchain/q-blockchain-validator-onboarding-program-part-1-validator-incentivized-testnet-567ef6e4002e)

> Projenin Discord Kanalına; [Buradan](https://discord.gg/aHdWbAh2R7) ulaşabilirsiniz.
> Bu repoyu forklayıp yıldız vermeyi ve Github'da bizi takip etmeyi unutmayın.

### Değişkenleri Ayarlayalım

```
PASSWORD=Kendinbelirlediğinşifre
```

```
echo "export PASSWORD=SIFRENIYAZ" $HOME/.bash_profile
source $HOME/.bash_profile
```
>SIFRENIYAZ bölümünde belirlediğin şifreyi ekliyoruz.

### Sistem Güncellemeleri

```
sudo apt update
```
```
sudo apt upgrade
```
```
apt install docker-compose
```

```
apt install npm
```


```
apt install screen
```

```
sudo apt-get update && sudo apt install jq && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```


### Binary ve pwd oluşturalım:
> Kodları sırasıyla girelim.
> SIFRE kısmını değiştirmeyi unutmayın.

```
git clone https://gitlab.com/q-dev/testnet-public-tools.git
cd testnet-public-tools/testnet-validator/
mkdir keystore
cd keystore/
echo "SIFRE" >> pwd.txt
```

### Cüzdan oluşturup bilgileri kaydedliyoruz.
> Oluşan cüzdan için token alıyoruz. [Faucet](https://faucet.qtestnet.org/)
```
cd ..
docker run --entrypoint="" --rm -v $PWD:/data -it qblockchain/q-client:testnet geth account new --datadir=/data --password=/data/keystore/pwd.txt
```
### Yapılandırma dosyasını düzenleyelim
> Oluşturduğunuz adresin 0x'li olan kısmın dışında kalan bölümü alıyoruz.
> CRTL X ve Y Enter ile kayıt ediyoruz.

```
cp .env.example .env
nano .env
```

### Aynı işlemi Şifre içinde yapıyoruz.
> Adres ve password kısmını düzenliyoruz.
> Adres kısmında 0x'siz, adresinizin başındaki kısım olmadan giriş yapıyoruz.
> CTRL X ve Y enter ile kayıt ediyoruz.

```
nano config.json
```

### Faucetten aldığımız tokenleri stake ediyoruz.
> Bu komut çalışmazsa yukarda yapılandırma dosyaları olan  .env ve config.json eksik yapılmıştır. Üst kısımdan kontrol edin.

```
docker run --rm -v $PWD:/data -v $PWD/config.json:/build/config.json qblockchain/js-interface:testnet validators.js
```
### Private Key ile özel anahtarımızı oluşturalım:
> Komutları sırasıyla girin.

```
cd
cd testnet-public-tools
chmod +x run-js-tools-in-docker.sh
./run-js-tools-in-docker.sh
npm install
```
> Uyarı: Bu bölümde koddaki Ox'li cüzdan adresiniz ve belirlediğiniz SIFRE'yi girmeyi unutmayın.
> Bu işlemden sonra PK adında bir klasör oluşur.
> İşlemler bittikten sonra CTRL A+D ile çıkın!

```
chmod +x extract-geth-private-key.js
node extract-geth-private-key 0XLİCUZDAN ../testnet-validator/ SIFRE
```
### WINSCP ve MobaXTerm ile sunucunuz dosyalar bölümüne bağlanıp;
> Private key dosyanız  /root/testnet-public-tools/js-tools içinde olacak
> Dosyanın içini açtığınızda size bir key verecek onu bilgisayarınıza indirip kayıt etmeyi unutmayın.

![qchain](https://user-images.githubusercontent.com/111747226/206897008-14ea93cb-9b2d-458c-8a00-44dbadfddf1a.png)

### Bir tane metamask cüzdan gerekli
> Mecvut kullandığınız cüzdanınızın içine de bu cüzdanı aktarabilirsiniz, 
> İsterseniz yeni bir metamask kurabilirsiniz, size kalmış.

![meta1](https://user-images.githubusercontent.com/111747226/206897293-48d69c7b-1aaf-4f34-9add-7ed4a7d0f8c3.png)
> Sağ üsteki simgeye basıyoruz,
> İçe aktar sekmesine basıyoruz.

![meta2](https://user-images.githubusercontent.com/111747226/206897331-81c019b0-1b05-4288-9931-e5318a24f900.png)
> Özel Anahtar altındaki boşluğa yukarıdaki MobaxTerm ve WinSCP ile aldığınız txt dosyası içerisindeki özel anahtarı yapıştırıp cüzdanınız metamaska kurabilirsiniz.



