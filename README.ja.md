# NLWebとは

NLWebは、ウェブサイト向けの会話型インターフェースを簡単に構築するためのオープンプロトコルとツールのコレクションです。NLWebはMCPに対応しているため、人間とエージェントの両方から同じ自然言語APIを利用できます。

Schema.orgやRSSなどの半構造化フォーマットは1億以上のウェブサイトで利用され、実質的なシンジケーションの手段であり、ウェブのセマンティックレイヤーとなっています。NLWebはこれらを活用し、自然言語インターフェースの実装を容易にします。

NLWebは、AI Webの基盤を築くことを目的としたオープンプロトコルと関連するオープンソースツール群です。実装コードはあくまで一例であり、より優れた実装がコミュニティから生まれることを期待しています。初期のウェブが共通プロトコルにより発展したように、NLWebも共有プロトコルによる連携を目指します。

AIはウェブ体験を大きく向上させる可能性を持ちますが、その実現にはコミュニティによる共同作業が不可欠です。NLWebはプロトコル、Schema.org形式、サンプルコードを組み合わせ、サイトが迅速にエンドポイントを構築できるよう支援します。これにより人間向けの会話型インターフェースだけでなく、エージェント同士の自然な対話も実現できます。

> ぜひ、エージェントがつながるウェブの構築に参加してください。

## 仕組み

NLWebには2つの要素があります。

1. サイトと自然言語でやり取りするためのシンプルなプロトコルと、jsonとschema.orgを利用した回答フォーマット。
   詳細は[REST API](/docs/nlweb-rest-api.md)を参照してください。
2. 既存のマークアップを活用する実装例。製品、レシピ、観光名所、レビューなど、項目の一覧として抽象化できるサイト向けです。ユーザーインターフェースのウィジェットと組み合わせることで、サイトは簡単に会話型インターフェースを提供できます。仕組みの詳細は[Life of a chat query](docs/life-of-a-chat-query.md)を参照してください。

## NLWebとMCP

MCP(Model Context Protocol)は、チャットボットやAIアシスタントがツールと連携するための新しいプロトコルです。NLWebはMCPサーバーとして動作し、自然言語でサイトに質問する<code>ask</code>メソッドを提供します。レスポンスはschema.orgを利用して記述されます。つまり、MCPとNLWebの関係は、HTTPとHTMLの関係に相当します。

## NLWebとプラットフォーム

NLWebは以下の点で強くアグノスティックです。

- プラットフォーム: Windows、macOS、Linuxなどで動作確認済み
- ベクトルストア: Qdrant、Snowflake、Milvus、Azure AI Searchなど
- LLM: OAI、Deepseek、Gemini、Anthropic、Inceptionなど
- 軽量かつスケーラブルで、クラウドのクラスターからラップトップ、将来的にはスマートフォンまで対応予定

## リポジトリ内容

このリポジトリには以下が含まれます。

- コアサービスのコード — 自然言語クエリを処理し、拡張やカスタマイズが可能
- 主要なLLMやベクトルデータベースへのコネクター
- schema.org jsonlやRSSなどのデータを任意のベクトルデータベースへ追加するためのツール
- このサービス用のウェブサーバー。サービス自体は十分小さいため、ウェブサーバー内で動作します
- ユーザーがウェブサーバー経由でクエリを発行できる簡単なUI

多くの本番環境では独自のUIが使われると想定されます。また、スタンドアロンのNLWebサーバーではなく、アプリケーション環境に統合することが推奨されます。さらに、コンテンツのコピーではなくライブデータベースに接続することで、鮮度の問題を回避できます。

## ドキュメント

### はじめに

- [Hello world on your laptop](docs/nlweb-hello-world.md)
- [Running it on Azure](docs/setup-azure.md)
- GCPでの実行... 近日公開
- AWSでの実行... 近日公開

### NLWeb

- [Life of a Chat Query](docs/life-of-a-chat-query.md)
- [Modifying behaviour by changing prompts](docs/nlweb-prompts.md)
- [Modifying control flow](docs/nlweb-control-flow.md)
- [Modifying the user interface](/docs/user-interface.md)
- [REST interface](docs/nlweb-rest-api.md)
- [Adding memory to your NLWeb interface](/docs/nlweb-memory.md)

---

### License

NLWebは[MIT License](LICENSE)の下で提供されています。

### Deployment (CI/CD)

現時点では、このリポジトリは継続的インテグレーションを使用しておらず、ウェブサイトや成果物のデプロイも行っていません。

### Access

このGitHubプロジェクトに関する質問は[NLWeb Support](mailto:NLWebSup@microsoft.com)までご連絡ください。

### Contributing

詳細は[Contribution Guidance](CONTRIBUTING.md)を参照してください。

### Trademarks

このプロジェクトには、製品やサービスの商標またはロゴが含まれている場合があります。Microsoftの商標またはロゴを使用する場合は、[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)に従う必要があります。サードパーティの商標やロゴの使用は、それぞれのポリシーに従ってください。
