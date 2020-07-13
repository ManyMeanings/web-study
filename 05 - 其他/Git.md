### 全局配置用户信息

```bash
git config --global user.name "ManyMeanings"
git config --global user.email "manymeanings@outlook.com"
```

### 提交代码一般流程

```bash
git add .
git commit -m 'fix'
git pull origin master
git push origin master
```

### 分支的合并

#### 场景：基于 master 分支的代码，开发一个新特性

如果你直接在 master 分支上开发这个新特性，是不好的，万一你在开发`特性1`的时候，领导突然又要叫你去开发`特性2`，就不好处理了。难道开发的两个特性都提交到 master？一会儿提交`特性1`的 commit，一会儿提交`特性2`的 commit？这会导致 commit 记录很混乱。所以，一般的建议做法是：给每个特性都单独建一个的新的分支。

1. 基于 master 分支，创建一个新的分支，起名为`feature_item_recommend`。

```bash
git checkout -b feature_item_recommend

#上面这行命令相当于：
git branch feature_item_recommend
git checkout feature_item_recommend
```

2. 在新的分支`feature_item_recommend`上完成开发工作，并 commit, push。
3. 将分支`feature_item_recommend`上的开发进度合并到 master 分支。

```bash
git checkout master
git merge feature_item_recommend
```

4. 删除分支`feature_item_recommend`。

```bash
git branch -d feature_item_recommend
```

#### 合并分支时，如果存在分叉。

![](http://img.smyhvae.com/20180610_1650.png)

比如说上面这张图，最早的时候，master 分支是位于`C2`节点。我基于`C2`节点，new 出一个新的分支`iss53`，我在`iss53`上提交了好几个 commit。现在，我准备把`iss53`上的几个 commit 合并到 master 上，此时发现，master 分支已经前进到 C4 了。那该怎么合并呢？

```bash
git checkout master
git merge iss53
```

**解释**

由于当前 master 分支所指向的 commit（C4） 并非想要并入分支（iss53）的直接祖先，Git 不得不进行一些处理。就此例而言，Git 会用两个分支的末端（C4 和 C5）和它们的共同祖先（C2）进行一次简单的三方合并计算。

Git 没有简单地把分支指针右移，而是对三方合并的结果作一新的快照，并自动创建一个指向它的 commit（C6）（如下图所示）。我们把这个特殊的 commit 称作合并提交（mergecommit），因为它的祖先不止一个。

![](http://img.smyhvae.com/20180610_1710.png)

#### 解决合并时发生的冲突

![](http://img.smyhvae.com/20180610_1740.png)

如果 feature1 和 feature2 修改的是同一个文件中**代码的同一个位置**，那么，把 feature1 合并到 feature2 时，就会产生冲突。这个冲突需要人工解决。步骤如下：

1. 手动修改文件：手动修改冲突的文件，决定到底要用哪个分支的代码。
2. `git add .`
3. `git commit`
4. 继续把 feature1 分支合并到 master 分支，最后删除 feature1、feature2。

**注意**： Git 自动合并成功后，在提交代码之前，需要对代码进行测试。

### 将 Git 项目迁移到另一个仓库

我们假设旧仓库的项目名称叫`old-repository`，新仓库的项目名称叫`new-repository`。操作如下：

1. 创建旧仓库的裸克隆：

```bash
git clone --bare https://github.com/exampleuser/old-repository.git
```

执行上述命令后，会在本地生成一个名叫 `old-repository.git`的文件夹。

2. 迁移到新仓库：

```bash
cd old-repository.git

git push --mirror https://github.com/exampleuser/new-repository.git
```
