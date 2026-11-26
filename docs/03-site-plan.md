# 二軸サイト設計・既存ノウハウの再利用

## 1. 基本方針

| | 日本軸（JA） | 海外軸（EN） |
|---|---|---|
| 読者 | 日本在住のP1/P2 | 米英を中心とした O1/O2 |
| 言語 | 日本語 | 英語 |
| 配信先 | `/`（日本語トップ） | `/en/`（英語トップ） |
| 主案件 | Q1（A8.net）＋ Q2（海外の一部） | Q3（海外ASP） |
| 収益の性格 | 早い・小さめ・円 | 遅い・大きめ・USD |

- **日本軸を先に構築し、海外軸はその構成を翻訳して立ち上げる**（記事を零から考えない）。
- 差別化は両軸共通で **公式情報＋確認日＋出典を明示する「検証型」比較**。体験の捏造なし。
- 前プロジェクトの教訓：**季節案件は避け、通年テーマに絞る**。AIツール比較は通年型。

## 2. サイト構造

```
ai-tool-guide/
├── index.html              日本語トップ（JA）
├── articles/*.html         日本語記事
├── en/
│   ├── index.html          英語トップ（EN）
│   └── articles/*.html     英語記事
├── about.html              運営方針／開示（JA）
├── en/about.html           Disclosure / Privacy（EN）
├── assets/                 各ツールの画像（軸共通、個別に差分）
├── sitemap.xml             JA用
├── en/sitemap.xml          EN用
├── robots.txt
└── .github/workflows/deploy.yml
```

- GSC／GA4 は **言語別にプロパティを分けるか、1プロパティ＋`/en/` フィルタ**で管理する（最初は分ける方が分かりやすい）。
- Bing Webmaster Tools も JA／EN それぞれにサイト登録が必要（メタタグ確認→sitemap→URL送信）。

## 3. 記事構成

### 日本軸：最初の10本

| # | タイトル案 | ペルソナ | 主案件 |
|---|---|---|---|
| 1 | AIツールの選び方｜用途別・無料枠から始める失敗しない比較 | P1/P2 | MiriCanvas／ConoHa |
| 2 | MiriCanvasの使い方と無料・有料の違い｜Canva・Gammaと比較 | P2 | MiriCanvas |
| 3 | AIプレゼン資料作成ツール比較2026｜MiriCanvas vs Gamma vs ChatGPT | P2 | MiriCanvas／Gamma |
| 4 | DMM生成AI CAMPの料金と内容｜無料セミナーから入会まで | P1/P2 | DMM CAMP |
| 5 | ConoHa AI Canvasの料金・使い方｜画像生成をブラウザで試す | P1/P2 | ConoHa |
| 6 | AIライティング比較｜Value AI Writer vs Writesonic | P1 | Value AI Writer／Writesonic |
| 7 | 生成AIの無料利用と有料利用の線引き｜いつ課金すべきか | P2 | 複数 |
| 8 | AI画像生成の商用利用で確認すべきこと | P1/P2 | ConoHa／OpenArt |
| 9 | 文字起こし・議事録AIの選び方 | P4/P3 | Descript／Granola |
| 10 | AI音声生成比較｜ElevenLabs vs Murf | P4 | ElevenLabs／Murf |

### 海外軸：日本軸10本の後に開始する最初の8本

| # | タイトル案（英） | ペルソナ | 主案件 |
|---|---|---|---|
| 1 | Best AI Tools by Use Case (2026): Free Tiers and What You Actually Pay | O1/O2 | 複数 |
| 2 | ElevenLabs vs Murf: Voice Quality, Pricing, and Commercial Rights | O1 | ElevenLabs／Murf |
| 3 | Best AI Presentation Tools: Gamma vs MiriCanvas vs PowerPoint | O1/O2 | Gamma |
| 4 | Semrush Review 2026: Who It's Worth For (and Who Should Skip) | O2 | Semrush |
| 5 | Surfer vs Frase: Which SEO Writer Actually Pays for Itself? | O2 | Surfer／Frase |
| 6 | GetResponse vs HubSpot for Small Businesses: Real Cost Comparison | O2 | GetResponse／HubSpot |
| 7 | n8n vs Zapier: When the 30% Recurring Program Makes Sense | O3 | n8n |
| 8 | AI Voice/Video Tools With Recurring Commissions (Verified 2026) | O1 | 複数 |

※ 各記事に **確認日・出典URL・disclosure** を入れる。

## 4. `A8-afiliate/` から再利用できるノウハウ

| 資産 | 再利用方法 |
|---|---|
| SEO実装（canonical／OGP／JSON-LD／sitemap／robots） | 両軸にテンプレート化。Lighthouse 1.00 チェックも流用 |
| GSC／GA4／Bing 設定手順 | JA／EN それぞれに適用（Bingはメタタグ→sitemap→URL送信） |
| A8 提携申請ログ | 日付・ASP・案件・状態・成果条件確認日を記録（Q1/Q3 両方で使う） |
| 効果測定ログ | imp／click／CV／amount に加え EPC・確定率・為替レートも記録 |
| note／はてな／X 転載フロー | JA軸はそのまま／EN軸は X と English note 相当を検討 |
| 画像ルール | ツールごとに個別サムネ。公式画像は著作物として明記 |
| 自動化 | A8日次レポートと同じ cron で、JA用・EN用の日次チェックを作成 |
| 人間認証の扱い | CAPTCHA／SMS／long-press はユーザーに handoff。AIでは解かない |

## 5. KPI（二軸・最初の90日）

| 期間 | 日本軸 | 海外軸 |
|---|---|---|
| 30日 | 記事8-10本／GSC・Bing登録／5案件申請／初CV | 英語トップ＋記事2本／program 3件申請 |
| 60日 | インデックス8本／初確定報酬／自然流入確認 | 英語記事5本／初 CV（承認待ち含む） |
| 90日 | 月1万円の確定報酬 | 初確定報酬（USD→円）／継続program 1件稼働 |

※ 海外軸は成果確定に半年近くかかる場合があるため、90日時点では「CV確定」より「program 承認数」を指標にする。

## 6. リスクと遵守事項

- **報酬条件の変動**：特にライティング系。掲載前に毎回公式確認。
- **国別制限**：CapCut のような geo-gated program は Q5 に該当するため絶対に紹介しない。
- **ステルスマーケ／FTC**：JAは冒頭にアフィリエイト開示、ENは FTC disclosure を明記。
- **AI生成コンテンツ**：料金・条件・出典は人が公式確認。体験談の捏造禁止。
- **無料体験**：自動更新・解約方法を必ず併記。
- **海外受取**：W-8BEN／円換算／確定申告／手数料を記録。未提出だと30%源泉徴収。
- **禁止行為**：自己クリック・テスト注文（A8）、クーポンサイト、branded keyword 入札。
- **副業規定**：勤務先ルールを確認してから開始。

## 7. 次のアクション（ユーザー確認が必要）

1. プロジェクト名／公開URL（`/en/` サブディレクトリ方式でよいか）
2. A8提携を新サイトで行うか、既存siteで行うか
3. 海外軸の開始タイミング（日本軸10本後でよいか、並行か）
4. 日本語記事1・2の構成確定
