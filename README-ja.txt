# マイクラみんなの地図（Webアプリ試作）

## できること
- 日本語UI、スマホ対応
- 座標・種類・メモの登録、編集、削除
- オーバーワールド／ネザー／エンドの切り替え
- 座標グリッド表示、地図タップでX/Z入力
- ネザー座標変換、検索、JSON/CSVの入出力
- Firebase設定後、ルームコードを使ったリアルタイム共同編集

## オンライン共同編集を有効にする
1. https://console.firebase.google.com/ でFirebaseプロジェクトを作成
2. プロジェクト設定からWebアプリを追加し、`apiKey`, `authDomain`, `projectId`, `appId`を取得
3. Authentication > Sign-in method で **Anonymous（匿名）** を有効化
4. Firestore Databaseを作成
5. FirestoreのRulesに `firestore.rules` の内容を設定して公開
6. `index.html` をHTTPSでホスト（Firebase Hosting、GitHub Pages等）
7. サイトの「接続設定」に4つの値を入力して保存
8. 「新しい共有ルームを作る」を押し、表示されたルームコードを友達に共有
9. 友達も同じサイトを開き、ルームコードで参加

## セキュリティ上の注意
- これはプロトタイプです。付属のルールは、匿名ログイン済みなら任意のルームパスにアクセスできる簡易設定です。ルームコードは長くランダムですが、コードを知る人は編集可能です。公開・本格運用前には、ルームごとのメンバー管理とFirestore Security Rulesを強化してください。
- FirebaseのWeb設定値はブラウザに見える公開設定です。FirebaseのAPIキーだけを秘密にする設計ではありませんが、認証とSecurity Rulesを必ず設定してください。
- Minecraft/Microsoftのログイン情報は要求しません。
- このアプリは地形を自動生成するものではなく、座標グリッド上に登録地点を表示します。
- ローカルデータとオンラインルームは別管理です。既存のローカルデータを共有したい場合はJSONを書き出し、共有ルームに入ってからJSONを読み込んでください。
