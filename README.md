# XMouse 官网（xmouse.top）

XMouse macOS 应用的官方介绍站，托管在 GitHub Pages 上。

## 文件说明

| 文件 | 作用 |
|------|------|
| `index.html` | 首页（介绍、功能、定价、下载） |
| `privacy.html` | 隐私政策展示页（运行时加载 PRIVACY_POLICY.md 渲染） |
| `terms.html` | 用户协议展示页（运行时加载 TERMS_OF_SERVICE.md 渲染） |
| `PRIVACY_POLICY.md` | 隐私政策源文件（**只改这一份，HTML 自动生效**） |
| `TERMS_OF_SERVICE.md` | 用户协议源文件 |
| `CNAME` | GitHub Pages 自定义域名配置（绑 xmouse.top） |

## 部署到 GitHub Pages 步骤

1. 在 GitHub 创建新仓库 `xmouse-web`（建议 public，因为 GitHub Pages 免费版需要 public）
2. `git init && git add . && git commit -m "init"`
3. `git remote add origin https://github.com/Croky-zhao/xmouse-web.git`
4. `git push -u origin main`
5. 在 GitHub 仓库页 → Settings → Pages：
   - Source: `Deploy from a branch`
   - Branch: `main` + `/ (root)`
   - 保存
6. 等几分钟，访问 `https://croky-zhao.github.io/xmouse-web/` 看效果
7. 配置自定义域名（xmouse.top）：
   - 在域名服务商（购买 xmouse.top 的地方）添加 DNS 记录：
     - 类型: CNAME
     - 主机记录: `@` 或 `www`
     - 记录值: `croky-zhao.github.io`
   - 等 DNS 生效（5-30 分钟）
   - 回 GitHub Pages 设置页验证 xmouse.top → 启用 HTTPS

## 更新内容

- 改首页文案/样式：编辑 `index.html`，commit + push
- 改隐私政策：编辑 `PRIVACY_POLICY.md`，commit + push（HTML 自动重新渲染）
- 改用户协议：编辑 `TERMS_OF_SERVICE.md`，同上

## 待办

- [ ] 替换首页 Hero 区的截图占位为真实 App 截图
- [ ] 替换下载按钮的 `href="#"` 为真实 .dmg 下载链接（App 打包后）
- [ ] 同步 PRIVACY_POLICY.md 和 TERMS_OF_SERVICE.md 与 XMouse-backend/docs/legal/ 保持一致

## 协议同步

`PRIVACY_POLICY.md` 和 `TERMS_OF_SERVICE.md` 的"源头真理"在 `XMouse-backend/docs/legal/`。
本仓库的版本是为了 GitHub Pages 部署。两边修改时记得同步。

未来可优化方案：用 GitHub Actions 自动从 XMouse-backend 拉取文档。
