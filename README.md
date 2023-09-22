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

### GETリクエスト
 &emsp;ターミナルとPostmanを活用して個人アクセストークンを使ってプライベートな情報を取得<br>
 &emsp;下記のように表示結果は一致した。<br>


 
 　
