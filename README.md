# OpenShiftでSampleリソースを使ってデプロイする流れ（Githubリポジトリー）

## OpenShiftコンソール画面

OpenShiftには運用画面（`Administrator`）と開発画面(`Developer`)に分かれています。今回は`Developer`画面で操作をします。

<img width="1920" alt="スクリーンショット 2022-10-14 16 09 02" src="https://user-images.githubusercontent.com/108312056/195797790-cffa5aa5-5ae1-432f-933e-16669c2d4d8f.png">
<img width="260" alt="スクリーンショット 2022-10-14 16 09 19" src="https://user-images.githubusercontent.com/108312056/195797853-a8701ae7-b698-4bb0-add7-29dc7929aa1c.png">

現在のトポロジーには何も入っていないので、新しく追加をしていきましょう。'+追加'ボタンをクリックします。
この追加画面ではさまざまなリソースを用いてOpenShift上にデプロイできる手段が揃っています。今回のSampleリソースはGithubリポジトリーを使ってデプロイしていきます。
Gitからインポートをクッリクします。

<img width="1920" alt="スクリーンショット 2022-10-14 16 09 31" src="https://user-images.githubusercontent.com/108312056/195797918-9f606716-5f47-428a-a919-16624320a7dd.png">

## Gitリポジトリー入力

Gitリポジトリーを引っ張ってくるためのURL入力欄がありますね。今回使ったSample URLは ***https://github.com/IBM/ibm-dte-openlab-samples*** を使っていますので、こちらをCopy・入力ください。
Gitのリソースが利用可能かどうかをOpenShift側で自動に検証してくれます。’Builder Image 件、検出されました。ビルダーイメージが推奨されます。’と表示されることがわかります。
>Builder Image 件、検出されました。ビルダーイメージが推奨されます。

<img width="1920" alt="スクリーンショット 2022-10-14 16 18 09" src="https://user-images.githubusercontent.com/108312056/195798037-3dca0ad1-c976-420d-b828-f757936d7839.png">

その次に'詳細の Git オプションの非表示'をクリックし、詳細を設定していきます。コンテキストディレクトリーに ***Red Hat OpenShift on IBM Cloud/node-s2i-openshift-master/*** を入力ください。注意点として前方に予め記載されているスラッシュ（/）を消さないようにしてください。コンテキストディレクトリーはスラッシュ（/）から始まるように構成されています。

<img width="849" alt="スクリーンショット 2022-10-14 16 18 27" src="https://user-images.githubusercontent.com/108312056/195798612-f5fc17c8-96e0-4481-9e44-0d5b73ca18d8.png">
<img width="836" alt="スクリーンショット 2022-10-14 17 21 50" src="https://user-images.githubusercontent.com/108312056/195798928-c2f0f8aa-7b98-436f-afa2-3f3ea59d0b4b.png">

次にはビルドイメージを選択しましょう。Sampleリソースであるため、自動にNode.jsに選択されていると思いますが、万が一選択されていない、あるいは他のビルドイメージが自動選択されている場合には`インポートストラテジーを編集`をクリックし、Node.jsを選択してください。

<img width="1621" alt="スクリーンショット 2022-10-14 16 18 55" src="https://user-images.githubusercontent.com/108312056/195799005-3e26d1d0-885b-4416-a195-5e1a6d397cd1.png">

下の一般設定の画面にスクロールし、アプリケーション名と名前を変えましょう。アプリケーションは新たに作成し***openshift-test***と名付け、名前も***openshift-sample-test***に設定しました。
こちらは自由に設定してください。

<img width="844" alt="スクリーンショット 2022-10-14 17 09 07" src="https://user-images.githubusercontent.com/108312056/195799462-34e8689a-d52c-45c9-978c-ba67df48c521.png">

設定が終わったら下までスクロールし、`作成`をクリックしましょう。

<img width="845" alt="スクリーンショット 2022-10-14 17 11 00" src="https://user-images.githubusercontent.com/108312056/195799565-40dce18d-7589-46f9-843d-78d4e1a0a755.png">

