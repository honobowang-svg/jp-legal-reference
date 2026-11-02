# 日本法律参考アシスタント — Knowledge Base

Free, public **Japan** legal **reference** knowledge base for a single Grok Bot with internal triage.

**法律相談・法律意見ではありません。弁護士ではありません。** 法令・金額・手続は改正されます。必ず e-Gov 法令検索・裁判所・省庁の公式情報で確認し、必要に応じて**弁護士**または**法テラス**に相談してください。

## What this is

- **日本国の全国法**を中心に、必要に応じて**都道府県条例・裁判所の土地管轄**に言及します。
- **11 branches**、各5ファイル: `system_prompt.md`, `knowledge_base.md`, `calculators.md`, `deadlines.md`, `templates.md`。
- 回答言語の既定は**日本語**。ユーザーが中国語または英語で書いた場合はそれに合わせて回答可（法令の公式名称は日本語で維持）。

## Branches

| Dir | Topic |
|-----|--------|
| `family/` | 離婚・親権・養育費（2026年共同親権改革を含む） |
| `inheritance/` | 相続・遺言・遺留分 |
| `contracts/` | 民法・債権（契約） |
| `torts/` | 不法行為・交通事故（民事） |
| `property/` | 不動産・借地借家・敷金 |
| `employment/` | 労働基準法・労働契約法・解雇・残業代・最低賃金（都道府県別） |
| `criminal/` | 刑事の**権利・手続のみ**（刑期予測・捜査回避は禁止） |
| `business/` | 会社法・商標・著作権 |
| `admin/` | 行政不服審査・入管/在留資格（**参考のみ**） |
| `consumer/` | 消費者契約法・特定商取引法・クーリングオフ |
| `procedure/` | 少額訴訟（60万円）・支払督促・調停・法テラス |

## How to use (Bot assembly)

1. ルートの `bot_master_prompt.md` を Bot Instructions に貼る／添付する。
2. 各ブランチの5ファイルをナレッジとして添付する。
3. `test_cases.md` と `eval_report.md` は QA 用。通常の回答ナレッジには付けない。

## Verification rule

条文の引用は公式ソースのみ（[e-Gov 法令検索](https://laws.e-gov.go.jp/)、[裁判所](https://www.courts.go.jp/)、[厚生労働省](https://www.mhlw.go.jp/)、[消費者庁](https://www.caa.go.jp/)、[法務省](https://www.moj.go.jp/)）。**法令名＋条号＋施行／改正日**を明示。未確認は **`【要確認】`**。法令・数字・判例の捏造は禁止。

## Disclaimer (every answer)

本プロジェクトは**参考情報のみ**を提供します。**法律意見ではなく**、アシスタントは**弁護士ではなく**、利用者は**弁護士または法テラス**に相談してください。

## License / cost

Free public reference materials. No affiliation with any commercial marketplace or private company brand is implied.
