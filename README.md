# AIツール共通開発プラットフォーム

## 1. システム要件
* **ローカル完結 & ナレッジ保持:** 外部クラウドに依存せず、PCローカルのGPUとストレージで推論およびベクトルDBによるナレッジ蓄積を完結させる。
* **モデル非依存（疎結合アーキテクチャ）:** OpenAI互換APIを介してモデルにアクセスし、モデル変更やクラウド移行時にもコード修正を不要とする。
* **コンテナ化による再現性:** Docker / Docker Compose により、ベクトルDBやエージェント実行環境を一元管理し、環境差分を排除する。
* **自律的な品質監査 & 技術監視:** LangGraphを用いてコード監査エージェントと最新技術監視エージェントを構築し、自己改善パイプラインを形成する。

## 2. 技術スタック
* **開発言語:** Python
* **AIエージェントフレームワーク:** LangGraph（状態管理・フロー制御）
* **ローカルLLM推論基盤:** Ollama（OpenAI互換APIエンドポイント）
* **ナレッジ / ベクトルDB:** Chroma（Dockerコンテナ内でボリューム永続化）
* **コード監査:** Radon（複雑度計測）、Flake8（静的構文チェック）
* **インフラ / コンテナ:** Docker, Docker Compose（WSL環境）

## 3. 開発ツール
* **統合開発環境:** VS Code
* **AI開発エージェント:** Cline（VS Code拡張機能 / モデル・APIの柔軟な切り替えが可能）
* **バージョン管理:** Git / GitHub（WSL上のSSH接続）

## 4. ディレクトリ構成
/ai-agent-platform
 ├── README.md               # プロジェクト要件・設計書
 ├── .clinerules             # Cline向け開発規約・制約定義
 ├── docker-compose.yml      # Chroma等のローカル基盤サービス定義
 ├── docs/
 │    ├── architecture.md    # アーキテクチャ設計・APIエンドポイント定義
 │    ├── agents.md          # 監視役・監査役エージェントの定義
 │    └── knowledge/         # 蓄積するナレッジドキュメント
 ├── src/
 │    ├── agents/            # LangGraphワークフロー実装
 │    └── utils/             # LLM/Chroma接続ユーティリティ
 └── requirements.txt