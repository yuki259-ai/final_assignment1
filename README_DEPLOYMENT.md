# 社内情報特化型生成AI検索アプリ - デプロイガイド

## 概要
このアプリケーションは、社内文書を検索・問い合わせできるStreamlitアプリケーションです。

## デプロイ方法

### 1. Streamlit Cloudでのデプロイ（推奨）

#### 事前準備
1. GitHubアカウントを作成・ログイン
2. OpenAI API Keyを取得
3. このリポジトリをGitHubにプッシュ

#### デプロイ手順
1. [Streamlit Cloud](https://share.streamlit.io/)にアクセス
2. "New app"をクリック
3. 以下の設定を行う：
   - **Repository**: あなたのGitHubリポジトリURL
   - **Branch**: main
   - **Main file path**: `venv/main.py`
   - **App URL**: 任意のURL（例：`your-app-name`）

4. "Advanced settings"をクリックして以下を設定：
   - **Python version**: 3.11
   - **Secrets**: 以下の内容を追加
     ```
     OPENAI_API_KEY = "your_actual_openai_api_key"
     ```

5. "Deploy!"をクリック

### 2. ローカル環境での実行

#### 必要な環境
- Python 3.11以上
- OpenAI API Key

#### セットアップ手順
1. 仮想環境を作成・アクティベート
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```

2. 依存関係をインストール
   ```bash
   pip install -r requirements.txt
   ```

3. 環境変数を設定
   - `.env`ファイルを作成し、以下を記述：
     ```
     OPENAI_API_KEY=your_openai_api_key_here
     ```

4. アプリケーションを起動
   ```bash
   streamlit run main.py
   ```

## 環境変数

| 変数名 | 説明 | 必須 |
|--------|------|------|
| `OPENAI_API_KEY` | OpenAI API Key | はい |

## トラブルシューティング

### よくある問題
1. **OpenAI API Keyエラー**
   - API Keyが正しく設定されているか確認
   - API Keyに十分なクレジットがあるか確認

2. **依存関係エラー**
   - `pip install -r requirements.txt`を再実行
   - Python 3.11以上を使用しているか確認

3. **ファイル読み込みエラー**
   - `data/`フォルダが存在するか確認
   - ファイルのパーミッションを確認

## サポート
問題が発生した場合は、ログファイル（`logs/application.log`）を確認してください。
