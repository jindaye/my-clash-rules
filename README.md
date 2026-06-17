# My Clash Rules

自用 Clash 规则集，基于 [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) 整理。

## 分类

| 文件 | 用途 | 行为 |
|------|------|------|
| `rules/proxy.txt` | 被墙域名，走代理 | domain |
| `rules/direct.txt` | 国内域名，直连 | domain |
| `rules/private.txt` | 局域网 / 内网，直连 | domain + ipcidr |
| `rules/reject.txt` | 广告 / 追踪，拦截 | domain |

## 使用方式

在 Clash 配置中通过 Rule Provider 引用：

```yaml
rule-providers:
  my-proxy:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/你的用户名/my-clash-rules@main/rules/proxy.txt"
    path: ./ruleset/my-proxy.yaml
    interval: 86400
```

## 更新规则

1. 编辑对应的 `.txt` 文件，每行一个域名
2. `git commit && git push`
3. Clash 客户端会在 interval 后自动拉取（默认 24h）

## 上游

- [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules)
- [ACL4SSR](https://github.com/ACL4SSR/ACL4SSR)
