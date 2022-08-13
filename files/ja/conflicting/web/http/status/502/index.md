---
title: '502'
slug: conflicting/Web/HTTP/Status/502
tags:
  - '502'
  - HTTP エラー
  - Infrastructure
  - Navigation
  - 用語集
translation_of: Glossary/502
original_slug: Glossary/502
---
<p>{{Glossary("HTTP")}} のエラーコードで "Bad Gateway" という意味です。</p>

<p>{{Glossary("Server", "サーバー")}}はクライアント（ブラウザーなど）ともう一方、上流のサーバーとの間でゲートウェイまたはプロキシとしてふるまうことがあります。 {{Glossary("URL")}} へアクセスをリクエストしたとき、ゲートウェイサーバーはリクエストを上流のサーバーに中継することがあります。 "502" は上流のサーバーが無効なレスポンスを返したことを意味します。</p>

<p>通常、上流のサーバーは落ちていません（つまり、ゲートウェイ／プロキシへのレスポンスは提供しています）が、単にゲートウェイ／プロキシが同じデータ交換プロトコルを理解できないことを表します。インターネットの{{Glossary("Protocol", "プロトコル")}}はとても明確なので、502はふつう一方または両方のコンピューターが不正または不完全にプログラミングされているという意味です。</p>

<h2 id="関連情報">関連情報</h2>

<ul>
 <li><a href="/ja/docs/Web/HTTP/Response_codes">HTTP レスポンスコードの一覧</a></li>
</ul>