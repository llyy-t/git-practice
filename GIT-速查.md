# Git / GitHub 速查表

## 一、只做一次的配置

```bash
git config --global user.name "你的名字"
git config --global user.email "你的GitHub邮箱"
git config --global core.quotepath false   # 让中文文件名不乱码
```

看当前配置：`git config --list`

## 二、本地四区（核心心智模型）

```
工作区 --git add--> 暂存区 --git commit--> 本地仓库 --git push--> GitHub
```

反方向：`git pull` 把远程更新拉回工作区。

## 三、日常九成场景

| 目的 | 命令 |
|---|---|
| 看状态（最常敲，随便敲不坏事） | `git status` |
| 看改了哪几行 | `git diff` |
| 把改动放进暂存区 | `git add .` / `git add 文件名` |
| 存成一个版本 | `git commit -m "说明"` |
| 改已跟踪文件后，add+commit 一步到位 | `git commit -am "说明"` |
| 推到 GitHub | `git push` |
| 拉取别人的更新 | `git pull` |
| 看历史 | `git log --oneline --graph --all` |
| 撤销工作区里没提交的改动 | `git restore 文件名` |
| 把文件踢出暂存区（保留改动） | `git restore --staged 文件名` |
| 临时存一下还没改完的活 | `git stash` / `git stash pop` |

## 四、分支

```bash
git switch -c feature/xxx   # 新建并切过去
git switch main             # 切回主线
git branch                  # 看本地分支
git merge feature/xxx       # 把分支合进当前分支
git branch -d feature/xxx   # 删掉已合并的分支
```

> 切换分支 = 工作目录里的文件跟着换，所以同一个文件夹能“变身”成不同版本。

## 五、接上 GitHub

```bash
git remote add origin git@github.com:用户名/仓库名.git
git remote -v                       # 检查是否加对
git push -u origin main             # 第一次推（-u 记住上游，以后只敲 git push）
git clone git@github.com:用户名/仓库名.git   # 下载别人的项目
```

## 六、三条铁律

1. `.env`、密钥、token 绝不提交，先写进 `.gitignore`。
2. 视频、数据集、安装包不进仓库，放 Releases 或网盘。
3. `push` 被拒先 `git pull` 再推；`push -f` 会覆盖别人的提交，慎用。
