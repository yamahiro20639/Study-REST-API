# REST API
 ## 概要
 &emsp;ハンズを参考にREST APIの操作方法を学びました。


  ### GETリクエスト
 &emsp;ターミナルとPostmanを活用して個人アクセストークンを使ってプライベートな情報を取得<br>
 &emsp;下記のように表示結果は一致した。<br>
 ```
〜ターミナル〜
HTTP/2 200 
server: GitHub.com
date: Fri, 22 Sep 2023 12:53:45 GMT
content-type: application/json; charset=utf-8
~
"login": "yamahiro20639",
  "id": 144509349,
  "node_id": "U_kgDOCJ0JpQ",
  "avatar_url": "https://avatars.githubusercontent.com/u/144509349?v=4",
  "gravatar_id": "",
  "url": "https://api.github.com/users/yamahiro20639",
  "html_url": "https://github.com/yamahiro20639",
  "followers_url": "https://api.github.com/users/yamahiro20639/followers",
  "following_url": "https://api.github.com/users/yamahiro20639/following{/other_user}",
  "gists_url": "https://api.github.com/users/yamahiro20639/gists{/gist_id}",
  "starred_url": "https://api.github.com/users/yamahiro20639/starred{/owner}{/repo}",
  "subscriptions_url": "https://api.github.com/users/yamahiro20639/subscriptions",
  "organizations_url": "https://api.github.com/users/yamahiro20639/orgs",
  "repos_url": "https://api.github.com/users/yamahiro20639/repos",
  "events_url": "https://api.github.com/users/yamahiro20639/events{/privacy}",
  "received_events_url": "https://api.github.com/users/yamahiro20639/received_events",
  "type": "User",
  "site_admin": false,
  "name": null,
  "company": null,
  "blog": "",
  "location": null,
  "email": null,
  "hireable": null,
  "bio": null,
  "twitter_username": null,
  "public_repos": 9,
  "public_gists": 0,
  "followers": 0,
  "following": 0,
  "created_at": "2023-09-09T04:15:02Z",
  "updated_at": "2023-09-13T13:25:14Z"
```
〜Postman〜
<img width="1007" alt="スクリーンショット 2023-09-22 23 11 38" src="https://github.com/yamahiro20639/Study-REST-API/assets/144509349/1a942f96-7e14-4d7f-beba-e16edcf7ace7">


### POSTリクエスト
&emsp;下記コマンドでリポジトリの登録を実施。<br>
```
% curl -i -X POST \
    -H "Authorization: token 個人アクセストークン" \
    -d '{
        "name": "blog",
        "auto_init": true,
        "private": true,
        "gitignore_template": "Nanoc"
      }' \

```
&emsp;結果、下記の通りになりました。<br>
&emsp;&emsp;・ステータスラインがHTTP/2 201<br>
&emsp;&emsp;・レスポンスヘッダーのlocationの値のリンクがblogリポジトリになっている。<br>
&emsp;&emsp;・created_at（作成日時）、updated_at（更新日時）がリクエストしたときの日時になっている。<br>
&emsp;&emsp;・visibilityの値がprivate、privateの値がtrueになっている。<br>
&emsp;&emsp;・レスポンスボディのhtml_urlの値のリンク先にアクセスするとblogリポジトリが表示される。<br>
```
HTTP/2 201
...
location: https://api.github.com/repos/yamahiro20639/blog
{
...
"name": "blog",
...
"private": true,
...
"html_url": "https://github.com/yamahiro20639/blog",
...
"created_at": "2023-09-24T06:26:50Z",
"updated_at": "2023-09-24T06:26:51Z",
...
 "visibility": "private",
...

```
<img width="1434" alt="スクリーンショット 2023-09-24 15 47 28" src="https://github.com/yamahiro20639/Study-REST-API/assets/144509349/b7c90653-398e-4448-84a3-035d72a3f26c">

&emsp;下記Postmanでもリポジトリの登録を実施。<br>
&emsp;結果、リポジトリの登録完了。
<img width="1433" alt="スクリーンショット 2023-09-24 16 02 59" src="https://github.com/yamahiro20639/Study-REST-API/assets/144509349/380ba783-7538-42a0-9971-7decf1800c7d">


### PATCHリクエスト
&emsp;下記コマンドでリポジトリの内容変更を実施。<br>
&emsp;&emsp;・リポジトリ名をblogからhello-world-blogに変更する<br>
&emsp;&emsp;・privateをpublicに変更<br>
&emsp;&emsp;・Aboutを"This is your blog repository"に変更<br>
&emsp;&emsp;・ホームページに"https://github.com" を設定<br>
```
% curl -i -X PATCH \
  -H "Accept: application/vnd.github.v3+json" \
  -H "Authorization: token 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" \
  https://api.github.com/repos/your_username/repository_name \
  -d '{
    "name":"hello-world-blog",
    "description":"This is your blog repository",
    "homepage":"https://github.com",
    "private":false
  }'
```
&emsp;実行結果は下記の通りになりました。GitHubでも変更確認できました。<br>
```
HTTP/2 200
server: GitHub.com
...

{
  ...
  "name": "hello-world-blog",
  ...
  "private": false,
  ...
  "html_url": "https://github.com/yamahiro20639/hello-world-blog",
  "description": "This is your blog repository",
  ...
  "created_at": "2023-09-24T06:26:50Z",
  "updated_at": "2023-09-24T08:26:42Z",
  ...
  "homepage": "https://github.com",
  ...
  "visibility": "public",
  ...
```
<img width="1116" alt="スクリーンショット 2023-09-24 17 32 28（2）" src="https://github.com/yamahiro20639/Study-REST-API/assets/144509349/21604a0c-58af-4994-bc0e-cde836ad241d">


&emsp;下記Postmanでもリポジトリ(blog2)の内容変更を実施。<br>
&emsp;結果は下記の通り、ステータスコード２００で変更できました。<br>
<img width="1436" alt="スクリーンショット 2023-09-24 17 55 27" src="https://github.com/yamahiro20639/Study-REST-API/assets/144509349/9e92a3ab-1a65-4d73-8c8b-69e402e70477">



 
 　
