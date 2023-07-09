# RIDS - Remote ID Spoofer (リモートIDスプーファー)

こちらはESP8266/NodeMCUを用いたドローンリモートIDスプーファー(なりすまし)システムです。
[sxjack](https://github.com/sxjack/uav_electronic_ids) および [SpacehuhnTech](https://github.com/SpacehuhnTech/esp8266_deauther) の研究を基に作成されました。
我々は巨人の肩の上に立っています。(我々は先人の偉業に基づいて活動しています。)

このシステムは、16機の異なる偽のドローンの情報を生成し、すべて特定のGPS位置情報の周りにランダムな方向へ飛んでいるようリモートID情報を発報します。

ドローンを検出するために使用するデバイスが、空中からのパケットを十分速く収集できることを確認してください。
App StoreまたはPlay Storeで入手可能なOpenDroneIDを使用する場合は、お使いのデバイスのWi-Fi スキャン スロットリングを無効にし、16機すべてのドローンが実際に【空中】に表示される前に、アプリを5～10分間程度、事前に実行する必要があります。

<img src="./images/proof.jpg"  width="600">

## インストール方法

1. [Arduino IDE](https://www.arduino.cc/en/software) が必要です。事前にインストールしてください。
2. `RemoteIDSpoofer/RemoteIDSpoofer.ino` ファイルを開きます。
3. Arduino IDEで `File` ⇒ `Preferences` を選択し、このURLを `Additional Boards Manager URLs` に追加します：
	- https://raw.githubusercontent.com/SpacehuhnTech/arduino/main/package_spacehuhn_index.json
4. `Tools` ⇒ `Boards` ⇒ `Boards Manager` で `deauther` を検索し `Deauther ESP8266 Boards` をインストールします。
5. `Tools` ⇒ `Board` ⇒ で利用ボードを選択します。`Deauther ESP8266 Boards` であることを確認してください。( `ESP8266 Modules` ではありません) 
6. NodeMCU v2を用い `Tools` ⇒ `Port` でCOMポートを選択します。
7. `upload` をクリックするか、もしくはCtrl+Uを使います。
8. これでデバイスは、ランダムに出現する機体として生成されたリモートIDパケットの発報を開始します。

## 利用方法

1. インストールが完了したら、スマートフォン等の端末で無線アクセスポイント【ESP_RIDS】へ、パスワード【makkauhijau】を用いて接続します。
2. そこで自分の指定したいGPS座標を入力します。
3. スプーフィングの開始！

> もし起動後2分以内にGPS座標が入力されなかった場合、デバイスは自動的にスプーフィングモードになり、電源再起動をしなければ座標を変更できなくなりますのでご注意ください。

## 免責事項

このリポジトリとそのコードは、あくまで技術探求、教育・研究活動のみを目的としています。
ESP8266やそれらSDKは、本来このような詐称目的のために作られたものではありません。
重大なバグがある可能性がありますので、利用等には十分ご注意ください！

ADS-Bパケットのなりすましが違法であるのと同様に、公共の空域で偽のリモートIDパケットを発報することは違法行為となります。
つきましては掲載されている情報やシステムについて、慎重にご検討のうえ、自己責任においてご利用ください。
