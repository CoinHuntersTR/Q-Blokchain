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
#### 1. Ödüllüerin %50'si ile Validatorlar kurmak ve ağda topluluk kurmak için stake edilebilecektir.
#### 2. Kalan %50'si ile başka Validatorlere stake edilebilir.
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
apt install screen
```

```
sudo apt-get update && sudo apt install jq && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```


### Gerekli olan portları açıyoruz.
> Portları sırasıyla giriyoruz.

```
sudo ufw allow 4133/tcp
sudo ufw allow 3033/tcp
```

### Node için gerekli olan kurulumları yapıyoruz.
> Kodları sırasıyla giriyoruz.
```
tmux
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS
./build_ubuntu.sh
cargo install --path .
```
### Cüzdan oluşturuyoruz

```
snarkos account new
```

> Cüzdanı kurulumunu yaptığınızda size verilen bilgileri kayıt etmeyi unutmayın.

Buradaki gibi çıktı alacaksınız;
```
Private Key    APrivateKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me And Use In The Next Step
     View Key  AViewKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me
      Address  aleo1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me 
```
## Node Başlatıyoruz
> Aşağıdaki kodu girdiğinizde çıkan ekranda sizden cüzdanınızın Private Key'ini girmenizi istiyor.
```
./run-prover.sh
```
Bu adımda private keyimizi girdiğimizde çalışmaya başlıyor. Sonrasında blokda ödül kazanıp kazanmadığımıza explorer üzerinden cüzdan adresimizle bakabiliriz.

# Explorer
### https://www.aleo.network/
### https://aleo123.io/
### https://explorer.hamp.app/

# Aleo Sosyal Medya Bağlantıları
### [Discord](https://discord.gg/aleohq)
### [Twitter](https://twitter.com/AleoHQ)
