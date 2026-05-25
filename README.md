# parallel-calc — 並行2タスクの最小スケルトン

電卓関数とテストを**別セッション**で並行開発する最小例。

## セットアップ

```bash
cp -r ../parallel-calc my-parallel-calc
cd my-parallel-calc
uv init --name parallel-calc
uv add --dev pytest
```

## 並行起動

ターミナル1（サブA-1: 関数本体）:
```bash
# AIセッションを起動。PROMPTS.md のサブA-1 セクションを投入
```

ターミナル2（サブA-2: テスト）:
```bash
# AIセッションを起動。PROMPTS.md のサブA-2 セクションを投入
```

## 統合（ゲート3）

```bash
uv run pytest
```

両サブが揃ったら緑になることを確認。NG ならゲート判定に基づき差し戻し。

## ファイル

- [INTERFACE.md](./INTERFACE.md) — 契約書（変更厳禁）
- [PROMPTS.md](./PROMPTS.md) — 範囲縛りプロンプト雛形
- `src/calc.py` — サブA-1 の編集対象（最初は空）
- `tests/test_calc.py` — サブA-2 の編集対象（最初は空）
"# parallel-calc" 
