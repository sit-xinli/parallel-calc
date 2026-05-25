# 共通インターフェース — parallel-calc

> このファイルが**契約書**。全サブタスクはここに従う。変更時はアーキテクトが裁定。

---

## 関数シグネチャ

```python
# src/calc.py
def calc(a: float, op: str, b: float) -> float:
    """4演算と0除算チェック。

    Args:
        a, b: 数値
        op: '+', '-', '*', '/' のいずれか

    Returns:
        計算結果（float）

    Raises:
        ValueError: op が4演算以外、または b == 0 で op == '/'
    """
```

---

## ファイル配置

```
parallel-calc/
├── INTERFACE.md         # この契約書（変更厳禁・アーキテクトのみ）
├── pyproject.toml       # uv が管理
├── src/
│   └── calc.py          # サブA-1 が編集
└── tests/
    └── test_calc.py     # サブA-2 が編集
```

---

## サブタスク分解

| サブ | 編集対象 | 編集禁止 |
|------|---------|---------|
| A-1: 関数本体 | `src/calc.py` | `tests/`, `INTERFACE.md` |
| A-2: テスト | `tests/test_calc.py` | `src/`, `INTERFACE.md` |

---

## 受け入れ基準

### サブA-1
- [ ] `calc` が `+ - * /` を正しく計算
- [ ] `op` が4演算以外なら `ValueError`
- [ ] `op == '/'` かつ `b == 0` なら `ValueError`（メッセージ "Division by zero"）
- [ ] 型ヒントあり

### サブA-2
- [ ] 正常系3ケース（足し算・引き算・掛け算 or 割り算）
- [ ] 異常系2ケース（不正op・0除算）
- [ ] `uv run pytest` で全 pass

### 統合（ゲート3）
- [ ] サブA-1 + サブA-2 を同じディレクトリに置いて `uv run pytest` が緑
