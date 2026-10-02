# git branch 有何用
`git branch` 可以把它想成 **「Git 裡面的分身／平行版本」**。

它的主要用途是：**讓你可以在不影響主要程式的情況下，另外做功能、修改或實驗。**

### 🌱 舉個你比較容易理解的例子

假設你現在的專案是：

```text
main
│
├── 登入功能
├── 首頁
└── 個人資料
```

現在你想新增「聊天室功能」。

你可以開一個新的 branch：

```bash
git branch chat
```

變成：

```text
main       ← 原本穩定的版本
  \
   chat    ← 你專門開發聊天室
```

接著切換到 `chat`：

```bash
git switch chat
```

你就在 `chat` 裡面寫聊天室。

即使你把聊天室寫壞了，**main 還是維持原本正常的狀態**。

---

### 常見指令

查看目前有哪些 branch：

```bash
git branch
```

例如：

```text
* main
  chat
  test
```

`*` 表示你目前正在 `main`。

---

建立新的 branch：

```bash
git branch chat
```

建立並直接切過去：

```bash
git switch -c chat
```

這個很常用。

---

切換 branch：

```bash
git switch chat
```

回到 main：

```bash
git switch main
```

---

### 🔥 最重要的是「合併」

假設你在 `chat` 完成聊天室：

```text
main
  \
   chat ← 聊天室完成
```

你可以切回 `main`：

```bash
git switch main
```

再把 `chat` 合併進來：

```bash
git merge chat
```

變成：

```text
main
│
├── 原本功能
├── 登入
├── 首頁
└── 聊天室 ← 從 chat 合併進來
```

---

### 你可以把它想成

如果你用 VS Code + OpenCode 做專案：

> **main = 老師目前看到的穩定版本**  
> **chat = 你正在開發的新功能**  
> **test = 你拿來亂改、測試的版本**

這樣就算你測試失敗，也不會直接把 `main` 搞壞。

所以 `git branch` **不是複製一整個資料夾**，而是 Git 用來管理「不同開發線」的工具。

如果你現在正在做老師的專案，通常最基本的流程可以記成：

```bash
git switch -c 新功能
# 開始修改程式
git add .
git commit -m "完成新功能"

git switch main
git merge 新功能
```

這就是 branch 最核心的用途。