# TechzoneでTest環境を設定する流れ

### Techzoneでの環境の予約

[IBM Technology Zone](https://techzone.ibm.com/decisionpoints)にアクセスします。

<img width="1920" alt="スクリーンショット 2022-10-19 20 08 43" src="https://user-images.githubusercontent.com/108312056/196681159-b95f1d1f-b3c3-4abe-8526-591069f487fa.png">

検索バーに　***Red Hat OpenShift on IBM Cloud basics lab」　を入力します。

<img width="1920" alt="スクリーンショット 2022-10-19 20 08 54" src="https://user-images.githubusercontent.com/108312056/196681184-538db214-a622-4f89-b7c4-d9e50c52eebc.png">

`Red Hat OpenShift on IBM Cloud basics lab`をクリックします。

<img width="1920" alt="スクリーンショット 2022-10-19 20 09 35" src="https://user-images.githubusercontent.com/108312056/196681212-35c3166d-b560-4d07-bf1a-761ecdd0a148.png">

`Basic Lab`タブをクリックし、`Red Hat OpenShift on IBM Cloud basics lab - Environmonet`の予約を行います。

<img width="1920" alt="スクリーンショット 2022-10-19 20 09 48" src="https://user-images.githubusercontent.com/108312056/196681265-cf976c24-d946-4183-b0cc-540969da7e28.png">

予約画面で `Reserve now`　をクリックします。

<img width="1920" alt="スクリーンショット 2022-10-19 20 10 27" src="https://user-images.githubusercontent.com/108312056/196681298-c58264fb-9207-4ae7-b131-ccdf3522a090.png">

画面が切り替わり環境情報を入力する画面が出たら、環境情報に関するフィールドに以下の情報を入力します。
- Name:`Red Hat OpenShift on IBM Cloud basics lab - Environment` 
- Purpose : `Practice - Self Education`
- Purpose description : `New hire training`
- Preferred Geography (required) : `ワシントンDC 04`
- ***終了日***　と　***終了時刻***　を指定します。　　（このラボの所要時間は約90分ですが、それより長い時間予約することをお勧めします。）

項目を全て入力したら、下の`Submit`をクリックします。

<img width="1920" alt="スクリーンショット 2022-10-19 20 32 43" src="https://user-images.githubusercontent.com/108312056/196681344-bbef845d-d193-4eca-946e-a6e23b7ee147.png">

以下の画面が表示されたら、予約の準備が終わります。

<img width="1920" alt="スクリーンショット 2022-10-19 20 12 04" src="https://user-images.githubusercontent.com/108312056/196687906-925ac8ce-e375-4718-90e2-3d93671090de.png">

### Openshift環境にアクセス

予約してからまもなく予約した環境のデプロイ完了メールが届きます。
***IBM Cloud (no-reply@cloud.ibm.com)*** から　***Account: You are invited to join an account in IBM Cloud*** のタイトルで届いたメールを開き、`Join now`　をクリックします。

<img width="599" alt="スクリーンショット 2022-10-19 20 12 25" src="https://user-images.githubusercontent.com/108312056/196687012-34b1f6cf-e71d-419e-b060-ce27bcb5cbb1.png">

以下のような画面が表示されますが、`ログイン`をクリックし、IBM Cloudコンソールにアクセスします。

<img width="1440" alt="スクリーンショット 2022-10-19 20 49 54" src="https://user-images.githubusercontent.com/108312056/196687051-d300fbbd-446b-4468-9977-0598dc59cc54.png">

コンソールのIBM Cloud アカウントから lab アカウントに変更します: `2435442 - ITZ - Satellite`

<img width="1919" alt="スクリーンショット 2022-10-19 20 14 39" src="https://user-images.githubusercontent.com/108312056/196687243-e3ee2cc1-e2f9-4210-a434-fa365af592e2.png">

アカウントが切り替わったら、ナビゲーション・メニューにて `OpenShift` → `クラスター` をクリックします。

<img width="1920" alt="スクリーンショット 2022-10-19 20 15 08" src="https://user-images.githubusercontent.com/108312056/196687470-0c11da4e-d90d-4718-9971-bfa25f1723ad.png">

クラスターの中で、`NH-Training-cluster-NA`をクリックします。

<img width="1920" alt="スクリーンショット 2022-10-19 21 04 30" src="https://user-images.githubusercontent.com/108312056/196688076-5c8a1c62-f843-4484-a064-b11622fe776b.png">

***NH-Training-cluster-NA***　の環境は正常にデプロイされていることがわかります。`OpenShift Web コンソール` をクリックしてアクセスしましょう。
（もし環境予約時間の設定などによりエラーが発生している場合があります。その場合は再度正しい時間で予約を行なってください。）

<img width="1920" alt="スクリーンショット 2022-10-19 21 04 41" src="https://user-images.githubusercontent.com/108312056/196688119-c5d393da-9901-4c96-8353-d2854c6adcda.png">

これでIBM Cloud コンソールでの操作は終了です。


__________


# OpenShiftでSampleリソースを使ってデプロイする流れ（Githubリポジトリー）

### OpenShiftコンソール画面

OpenShiftには運用画面（`Administrator`）と開発画面(`Developer`)に分かれています。今回は`Developer`画面で操作をします。

<img width="1920" alt="スクリーンショット 2022-10-14 16 09 02" src="https://user-images.githubusercontent.com/108312056/195797790-cffa5aa5-5ae1-432f-933e-16669c2d4d8f.png">
<img width="260" alt="スクリーンショット 2022-10-14 16 09 19" src="https://user-images.githubusercontent.com/108312056/195797853-a8701ae7-b698-4bb0-add7-29dc7929aa1c.png">

現在のトポロジーには何も入っていないので、新しく追加をしていきましょう。`+追加`ボタンをクリックします。
この追加画面ではさまざまなリソースを用いてOpenShift上にデプロイできる手段が揃っています。今回のSampleリソースはGithubリポジトリーを使ってデプロイしていきます。
Gitからインポートをクッリクします。

<img width="1920" alt="スクリーンショット 2022-10-14 16 09 31" src="https://user-images.githubusercontent.com/108312056/195797918-9f606716-5f47-428a-a919-16624320a7dd.png">

### Gitリポジトリー入力

Gitリポジトリーを引っ張ってくるためのURL入力欄がありますね。
今回使ったSample URLは ***https://github.com/IBM/ibm-dte-openlab-samples*** を使っていますので、こちらをCopy・入力ください。
Gitのリソースが利用可能かどうかをOpenShift側で自動に検証してくれます。
’Builder Image 件、検出されました。ビルダーイメージが推奨されます。’と表示されることがわかります。
>Builder Image 件、検出されました。ビルダーイメージが推奨されます。

<img width="1920" alt="スクリーンショット 2022-10-14 16 18 09" src="https://user-images.githubusercontent.com/108312056/195798037-3dca0ad1-c976-420d-b828-f757936d7839.png">

その次に'詳細の Git オプションの非表示'をクリックし、詳細を設定していきます。コンテキストディレクトリーに ***Red Hat OpenShift on IBM Cloud/node-s2i-openshift-master/*** を入力ください。注意点として前方に予め記載されているスラッシュ（/）を消さないようにしてください。コンテキストディレクトリーはスラッシュ（/）から始まるように構成されています。

<img width="849" alt="スクリーンショット 2022-10-14 16 18 27" src="https://user-images.githubusercontent.com/108312056/195798612-f5fc17c8-96e0-4481-9e44-0d5b73ca18d8.png">
<img width="836" alt="スクリーンショット 2022-10-14 17 21 50" src="https://user-images.githubusercontent.com/108312056/195798928-c2f0f8aa-7b98-436f-afa2-3f3ea59d0b4b.png">

次にはビルドイメージを選択しましょう。Sampleリソースであるため、自動にNode.jsに選択されていると思いますが、万が一選択されていない、あるいは他のビルドイメージが自動選択されている場合には`インポートストラテジーを編集`をクリックし、`Node.js`を選択してください。

<img width="1621" alt="スクリーンショット 2022-10-14 16 18 55" src="https://user-images.githubusercontent.com/108312056/195799005-3e26d1d0-885b-4416-a195-5e1a6d397cd1.png">

下の一般設定の画面にスクロールし、アプリケーション名と名前を変えましょう。アプリケーションは新たに作成し***openshift-test***と名付け、名前も***openshift-sample-test***に設定しました。
こちらは自由に設定してください。

<img width="844" alt="スクリーンショット 2022-10-14 17 09 07" src="https://user-images.githubusercontent.com/108312056/195799462-34e8689a-d52c-45c9-978c-ba67df48c521.png">

設定が終わったら下までスクロールし、`作成`をクリックしましょう。

<img width="845" alt="スクリーンショット 2022-10-14 17 11 00" src="https://user-images.githubusercontent.com/108312056/195799565-40dce18d-7589-46f9-843d-78d4e1a0a755.png">

作成をクリックすると、空白であったトポロジー空間にアプリケーションがデプロイ中であることがわかります。
細かいですが、アプリケーションの右下に矢印が回っているような表示がありますが、これは’デプロイ中’との意味となります。
アプリケーションをクリックすると、詳細を確認することもできます。

<img width="1920" alt="スクリーンショット 2022-10-14 17 11 18" src="https://user-images.githubusercontent.com/108312056/195801661-195dad03-40d9-44a2-a618-9fcfec52463d.png">
<img width="863" alt="スクリーンショット 2022-10-14 17 11 32" src="https://user-images.githubusercontent.com/108312056/195801760-20e95948-e72f-472b-b51d-b069c5001405.png">

少し時間が経つと右下の矢印が緑のチェックマークに変わるデプロイ完了できたとの表示となります。

<img width="332" alt="スクリーンショット 2022-10-14 17 36 05" src="https://user-images.githubusercontent.com/108312056/195802647-9ce57d5d-42d9-4c87-9958-3c59f00a5718.png">

アプリケーションをクリックしリソース欄を確認すると`Running`表示されています。デプロイが確実にされたことがわかります。

<img width="482" alt="スクリーンショット 2022-10-14 17 36 31" src="https://user-images.githubusercontent.com/108312056/195802743-11f40f4d-3365-492f-93e1-3685de3e654b.png">

アプリケーションに戻って`右上のURLを開く`をクリックして実際デプロイされたアプリケーションを確認しましょう。

<img width="415" alt="スクリーンショット 2022-10-14 17 37 02" src="https://user-images.githubusercontent.com/108312056/195803146-62d8d151-a95c-4543-8ee9-507eca0f19d0.png">

デプロイされたサイトが表示されます。IDとPasswordを入力する欄が出ますが、ここは任意の文字あるいは数字を入力してください。
（* Chromeなど使っている場合は、Passwordが簡単すぎるとセキュリティー警告が出る場合があります。）

<img width="1920" alt="スクリーンショット 2022-10-14 17 37 52" src="https://user-images.githubusercontent.com/108312056/195803214-e7dd0238-4bcc-408e-a8ef-2dcabd44e927.png">

ログインすると以下の画面が表示されます。病院のカルテのようなアプリケーションですね。
Sampleリソースなのでそこまでの機能はついていないですが、地図を動かすぐらいは可能になっています。

<img width="1920" alt="スクリーンショット 2022-10-14 17 38 07" src="https://user-images.githubusercontent.com/108312056/195803920-e9bb65ef-c3ef-4291-b225-f08c7e36629a.png">
<img width="1920" alt="スクリーンショット 2022-10-14 17 38 16" src="https://user-images.githubusercontent.com/108312056/195803939-1dcaee6d-8ab0-4823-9265-81ed1b3e2a13.png">

OpenShift上でGitリソースを使って簡単にデプロイする流れは以上となります。


