# 部署指南

## 一键部署步骤

### 第一步：复制仓库

点击右上角 **Fork** 将此仓库复制到你的 GitHub 账号下

### 第二步：生成 GitHub Token

1. 进入 GitHub 设置 → Developer settings → Personal access tokens
2. 点击 **Generate new token (classic)**
3. 设置 Token 名称（如 `inspection-system`）
4. 勾选权限：
   - [x] `repo` (Full control of private repositories)
   - [x] `workflow` (Update GitHub Actions workflows)
5. 点击 Generate token
6. **立即复制保存 Token**（关闭页面后无法再次查看）

### 第三步：启用 GitHub Pages

1. 进入仓库 **Settings** → **Pages**
2. Source 选择：**Deploy from a branch**
3. Branch 选择：**main** / **(root)**
4. 点击 **Save**

### 第四步：等待部署

等待 1-2 分钟，GitHub Pages 会自动部署

访问：`https://[你的用户名].github.io/[仓库名]/`

---

## 使用流程

### 首次配置

1. 打开部署好的网页
2. 滚动到页面底部
3. 展开「GitHub 配置」面板
4. 填写：
   - **仓库 Owner**：你的 GitHub 用户名
   - **仓库名称**：你的仓库名（如 `inspection-github-storage`）
   - **GitHub Token**：第二步生成的 Token
5. 点击「保存配置」

### 填写表单

1. 选择巡检日期
2. 填写巡检地点和人员
3. 选择检查项目和结果
4. 描述问题和整改要求
5. 拍摄/上传现场照片
6. 点击「提交巡检记录」

### 查看数据

- 所有数据自动存入仓库的 `data/` 文件夹
- 照片自动存入 `images/` 文件夹
- GitHub Actions 会自动生成 Excel 台账

---

## 活码功能

在「活码生成」页面：
1. 选择表单类型
2. 填写活码名称
3. 一键下载二维码
4. 打印张贴即可

---

## 数据结构

```
仓库结构：
├── index.html          # 主页面
├── data/              # JSON 数据文件
│   └── INS-xxx.json
├── images/            # 上传的照片
│   └── INS-xxx_1.jpg
└── .github/
    └── workflows/
        └── generate-excel.yml  # 自动生成 Excel
```

---

## 国内访问

GitHub Pages 在国内访问可能较慢，可以使用以下镜像：

1. **jsDelivr CDN**（推荐）：
   ```
   https://cdn.jsdelivr.net/gh/[用户名]/[仓库名]/
   ```

2. **Gitee Pages**（需要同步）：
   - 创建同名 Gitee 仓库
   - 设置 Gitee Pages 服务

---

## 自定义表单

如需修改表单字段，编辑 `index.html` 中的表单部分：

```html
<div class="form-group">
    <label class="form-label">你的字段名<span class="required">*</span></label>
    <input type="text" id="yourField" class="form-input" placeholder="提示文字">
</div>
```

---

## 常见问题

**Q: Token 失效怎么办？**
A: 重新生成 Token 并更新本地配置

**Q: 照片上传失败？**
A: 检查 Token 是否有 repo 权限，或图片是否超过 5MB

**Q: Excel 台账没有自动生成？**
A: 检查 Actions 是否有执行错误，确保 data 文件夹有数据

---

## 技术支持

如有问题，请在 GitHub 仓库提交 Issue
