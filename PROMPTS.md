# 範囲縛りプロンプト雛形 — parallel-calc

> 各サブタスクのセッションへ最初に投入するプロンプト。
> プロンプトデザイナーが必要に応じて埋める。

---

## サブA-1: 関数本体

```
あなたが作るのは src/calc.py だけです。

共通仕様（INTERFACE.md より）:
def calc(a: float, op: str, b: float) -> float:
  - op は '+', '-', '*', '/' のいずれか
  - op がそれ以外なら ValueError
  - op == '/' かつ b == 0 なら ValueError("Division by zero")

受け入れ基準:
- [ ] 4演算が正しく計算できる
- [ ] 不正 op で ValueError
- [ ] 0除算で ValueError("Division by zero")
- [ ] 型ヒントあり

触ってはいけない:
- tests/ 以下のファイル
- INTERFACE.md
- pyproject.toml への新規依存追加（必要なら停止して確認）

完成したら src/calc.py の中身だけ提示してください。
```

---

## サブA-2: テスト

```
あなたが作るのは tests/test_calc.py だけです。

共通仕様（INTERFACE.md より）:
- src/calc.py に calc(a: float, op: str, b: float) -> float がある
- 不正 op / 0除算で ValueError

受け入れ基準:
- [ ] 正常系3ケース（足し算・引き算・掛け算）
- [ ] 異常系2ケース（不正op・0除算）
- [ ] pytest で全 pass

触ってはいけない:
- src/ 以下のファイル
- INTERFACE.md
- 仕様の変更（必要なら停止して確認）

import 例: from calc import calc

完成したら tests/test_calc.py の中身だけ提示してください。
```

---

## 差し戻しテンプレート

ゲート判定で NG の場合、以下を埋めて再委任。

```
ゲート[N]で問題があった。
問題: ___
共通仕様（再掲）: calc(a: float, op: str, b: float) -> float
このタスクの範囲だけで [ここをこう直す] してほしい。
他のタスクのファイル・INTERFACE.md は触らないこと。
```
