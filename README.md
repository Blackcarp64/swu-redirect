# 西南大学官网跳转

静态页面打开后立即跳转到 https://www.swu.edu.cn/。JavaScript 使用 `location.replace`，避免返回按钮再次进入跳转页；禁用 JavaScript 时使用 HTML 自动跳转，并提供手动链接。

## 托管

GitHub 仓库： https://github.com/Blackcarp64/swu-redirect

GitHub Pages 从 `main` 分支根目录发布。修改 `index.html` 并推送到 `main` 后自动部署，无需安装依赖。

## 域名

域名：西南奶龙大学.cn

GitHub Custom domain 和根目录 `CNAME` 使用编码：`xn--6kr28k0gz4e0t2h9y1a.cn`。

在腾讯云 DNSPod 选择该域名，添加以下记录，线路选择默认，TTL 使用默认值：

| 主机记录 | 记录类型 | 记录值 |
| --- | --- | --- |
| @ | A | 185.199.108.153 |
| @ | A | 185.199.109.153 |
| www | CNAME | blackcarp64.github.io |

DNSPod 免费套餐对同一主机名、同一线路的负载均衡记录上限为两条，因此 `@` 使用以上两条 GitHub Pages A 记录；`www` 属于另一个主机名，不占用 `@` 的配额。套餐约束来源： https://docs.dnspod.cn/dns/load-balancing-service/

如果 `@` 或 `www` 已有冲突的 A、AAAA、CNAME 或 URL 转发记录，先移除冲突项，保留其他用途的记录。

解析生效后，在仓库 Settings → Pages 等待证书签发并开启 Enforce HTTPS。浏览器访问域名后，最终地址栏显示学校官网地址。

DNS 配置权威来源： https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
