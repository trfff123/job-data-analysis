# 谭茹方 · 数据分析作品集网站 —— 部署说明

这个文件夹是**可直接上传的静态网站**，共 7 个页面 + 1 个 404 页。全部页面自包含（图片已内嵌、无外部 CSS/JS 依赖），上传后即可访问，不需要构建、不需要装任何东西。

---

## 一、文件清单

| 文件 | 内容 | 大小 |
|---|---|---|
| `index.html` | 首页，全部文档入口 | 13 KB |
| `report-graduate-employment.html` | **主项目报告**（6 章、8 图、12 表） | 1.07 MB |
| `visualization-design.html` | 可视化设计方案与业务结论 | 578 KB |
| `data-cleaning-eda.html` | 数据清洗与 EDA 分析报告 | 232 KB |
| `data-sources-audit.html` | 数据源核实清单 | 29 KB |
| `project-charter.html` | 项目立项方案 | 33 KB |
| `job-posting-analysis.html` | 延伸分析 · 招聘岗位视角 | 821 KB |
| `404.html` | 访问错误页，自动列出全部文档 | — |
| `.nojekyll` | GitHub Pages 用，阻止 Jekyll 处理（隐藏文件，别漏传） | 0 |

---

## 二、推荐部署方式

### 方式 A：GitHub Pages 个人站（推荐，链接最短）

链接会变成 `https://你的用户名.github.io`，简历上直接写这个，最干净。

**1. 在 GitHub 新建仓库**，仓库名必须**严格等于** `你的用户名.github.io`
> 例如用户名是 `tanrufang`，仓库名就得是 `tanrufang.github.io`。名字不对，站点不会在根域名生效。

**2. 上传文件**

网页操作最快：进入仓库 → **Add file → Upload files** → 把这个文件夹里的**所有文件**（含 `.nojekyll`）拖进去 → Commit。

> ⚠️ 拖拽上传时，Windows 资源管理器默认不显示 `.nojekyll` 这类隐藏文件。先开启「查看 → 显示 → 隐藏的项目」，否则会漏传。这个文件缺了通常也能跑，但某些情况下 `_` 开头的资源会被忽略。

命令行方式：

```bash
cd "D:/桌面/作品集网站_部署包"
git init -b main
git add -A
git commit -m "portfolio: 高校毕业生就业数据统计分析作品集"
git remote add origin https://github.com/你的用户名/你的用户名.github.io.git
git push -u origin main
```

**3. 开启 Pages**：仓库 → **Settings → Pages** → Source 选 `Deploy from a branch` → Branch 选 `main` / `/ (root)` → Save。

**4. 等 1–3 分钟**，访问 `https://你的用户名.github.io`。

---

### 方式 B：作为现有仓库的子页面

如果你想挂到已有的项目仓库下（链接形如 `https://用户名.github.io/graduate-employment-analysis/`）：

把本文件夹内容放到那个仓库的 `docs/` 目录，然后 Settings → Pages → Branch 选 `main`，目录选 `/docs`。

> 项目仓库根目录已有 `README.md`，不会和这里的 `index.html` 冲突——Pages 访问 `/docs/` 时优先用 `index.html`。

---

### 方式 C：不想碰 Git（最快，1 分钟）

**Netlify Drop**：打开 https://app.netlify.com/drop ，把整个文件夹拖进浏览器窗口，几秒后拿到一个 `https://xxx.netlify.app` 的链接。

**Vercel**：https://vercel.com/new ，选静态站点上传，流程类似。

两者都免费、自动 HTTPS、支持自定义域名。缺点是链接是随机子域名，不如 GitHub Pages 体面。

---

## 三、一个必须提醒的现实问题

**GitHub Pages 在国内访问不稳定**，部分网络环境会超时或加载极慢。

你的求职区域是川渝，HR 大概率在国内网络打开链接。一份打不开的作品集，等于没有。

**建议同时准备一个国内可访问的备份：**

| 方案 | 成本 | 说明 |
|---|---|---|
| **腾讯云 COS / 阿里云 OSS 静态托管** | 几元/月 | 最稳。上传文件、开启静态网站功能即可，可绑自定义域名 |
| **Vercel / Netlify** | 免费 | 国内访问比 GitHub Pages 好，但仍受线路影响 |
| **Gitee Pages** | 免费 | 需实名认证，且 Pages 服务时开时关，不太可靠 |

**最低成本的兜底**：把 `report-graduate-employment.html` 和 `index.html` 两个文件单独发给 HR，或者打成压缩包作为附件随简历发。这两个页面自包含，下载到本地双击就能看，不需要联网。

---

## 四、部署后自查清单

打开链接后逐项确认：

- [ ] 首页能正常显示，四张统计卡是 2×2（手机上）或 1×4（电脑上）
- [ ] 点「完整项目报告」，能进入报告页，**8 张图都能显示**
- [ ] 报告页右下角有「← 作品集首页」悬浮按钮，点击能回到首页
- [ ] 五个支撑文档逐个点开，都能正常打开
- [ ] 用手机打开一次，确认文字没有横向溢出
- [ ] 随便输一个不存在的地址（如 `/abc`），能看到 404 页而不是 GitHub 的默认错误

---

## 五、常见问题

**Q：图片全都不显示，只有空白框？**
这个包里所有图片都是 base64 内嵌的，理论上不会失图。如果出现，说明文件上传不完整或传输被截断，重新上传一次。

**Q：点进子页面回不去首页？**
已在每个子页面右下角加了悬浮按钮。如果没看到，说明浏览器缓存了旧版本，强制刷新（Ctrl+F5）。

**Q：链接变成 `%E6%AF%95%E4%B8%9A...` 这种乱码？**
不会了。原文件名是中文，GitHub Pages 会把中文 URL 编码成这种形式，难看且容易被复制错。这个包里的文件名已全部改成英文，链接干净。

**Q：改了内容怎么更新？**
修改工作区里的原始 HTML（`C:\Users\19582\WorkBuddy\2026-10-26-11-21-49\`），然后重新生成部署包、重新上传。

**Q：要不要买域名？**
求职阶段不必。`用户名.github.io` 已经够专业。如果以后要买，10 元/年的 `.top` 或几十元的 `.com` 都行，配 DNS 解析后 Pages 里填 Custom domain 即可，HTTPS 会自动开启。

---

## 六、别忘了改这两处

1. **首页的联系方式**：`index.html` 里目前只有学校和求职方向，**没有邮箱和手机**。HR 想联系你却没有入口，这是作品集最不该缺的东西。建议在页面顶部右侧或页脚加一行邮箱。

2. **报告里的作者信息**：`report-graduate-employment.html` 中「作者 / 专业 / 文档版本」一栏，确认无误后再发布。

---

*打包时间：2026-10-26　·　页面总数：8　·　总大小：约 2.8 MB*
