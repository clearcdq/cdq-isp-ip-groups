# ISP IP 地址分组 & 全球地址表 & 恶意情报库

> 适用于防火墙策略配置、路由器 ACL、上网行为管理、出口路由优化等场景。

## 📁 目录结构

```
cdq-isp-ip-groups/
├── IPGroup_国内ISP.conf          # 国内运营商 IP 段（联通/电信/移动等）
├── IPGroup_香港ISP.conf          # 香港地区 ISP IP 段
├── IPGroup_台湾ISP.conf          # 台湾地区 ISP IP 段
├── IPGroup_澳门ISP.conf          # 澳门地区 ISP IP 段
├── IPGroup_国外ISP1.conf ~ 国外ISP10.conf  # 国外 ISP IP 段（分 10 组）
├── 全球各国家地址表集/             # 全球 237 个国家/地区的 IP 地址段
│   ├── 中国.txt
│   ├── 美国.txt
│   ├── 日本.txt
│   ├── ...
│   └── IP表汇总.xlsx
├── 恶意域名ip/                    # 威胁情报 IP/域名黑名单
│   ├── IPGroup_恶意IP.conf
│   ├── URLGroup_恶意域名.txt
│   ├── IPGroup_威胁情报-BJ.conf
│   ├── URLGroup_威胁情报-BJ.txt
│   ├── IPGroup_黑客银狐.conf
│   └── URLGroup_黑客银狐.txt
```

## 📊 数据统计

| 分类 | 文件数 | 说明 |
|------|--------|------|
| ISP IP 分组 | 14 个 | 国内/港澳台/国外，按运营商/地区划分 |
| 全球国家地址表 | 237 个 | 覆盖全球主要国家和地区的 IP 段 |
| 恶意情报 | 6 个 | 恶意 IP、域名、威胁情报源 |

## 🔧 使用方式

### 1. 防火墙 / 路由器 ACL 配置

```bash
# 示例：华为/H3C 防火墙导入国内 IP 段
# 将 .conf 文件中的 IP 段配置为地址组
ip ip-group domestic-isp
 # 批量导入 IPGroup_国内ISP.conf 内容
```

### 2. 上网行为管理策略

```bash
# Panabit / 深信服等设备导入 ISP 分组
# 用于区分国内外流量、按运营商计费等
```

### 3. 威胁情报阻断

```bash
# 将恶意 IP/域名导入防火墙黑名单
# 实时阻断已知恶意地址
```

### 4. 脚本批量处理

```python
# 读取 IP 段文件
with open('IPGroup_国内ISP.conf', 'r') as f:
    ip_list = [line.strip() for line in f if line.strip()]
print(f"国内 ISP IP 段共 {len(ip_list)} 条")
```

## ⚠️ 注意事项

- IP 地址段基于公开 Whois 数据整理，**建议定期更新**
- 使用前请确认与目标设备的格式兼容性（CIDR / 起止地址）
- 恶意情报仅供参考，生产环境需结合多源验证
- `IP表汇总.xlsx` 包含汇总统计，可用 Excel/WPS 打开

## 📝 更新日志

- **2025-12-10** — 初始版本，ISP 分组 + 全球地址表 + 恶意情报

## 📄 License

MIT License - 自由使用，请保留出处说明。
