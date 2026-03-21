# 网络犯罪分类数据集说明文档

## 📊 数据集概述

**文件名**: `network_crime_classified.csv`  
**数据来源**: 基于 `reports.csv` 原始数据，结合 `incidents.csv` 和 `classifications_MIT.csv` 进行增强  
**总记录数**: 6,786 条  
**创建日期**: 2026-03-21

## 🎯 分类体系

### 6 大网络犯罪类型

| 编号 | 分类名称 | 案例数 | 占比 |
|------|---------|--------|------|
| 1 | **欺诈与金融犯罪** | 1,905 | 28.1% |
| 2 | **隐私与身份侵犯** | 970 | 14.3% |
| 3 | **恶意内容传播** | 596 | 8.8% |
| 4 | **恶意软件与攻击** | 433 | 6.4% |
| 5 | **知识产权侵犯** | 147 | 2.2% |
| 6 | **社会工程与骚扰** | 2,735 | 40.3% |

## 🔬 四个核心研究参数

### 1. 犯罪手段 (crime_means)
描述犯罪分子使用的技术和方法，主要包括：
- **AI 生成内容**: 使用 AI 生成虚假内容
- **数据泄露**: 非法获取和泄露敏感数据
- **网络钓鱼**: 社会工程学攻击
- **恶意软件**: 病毒、勒索软件等
- **算法操纵**: 利用算法偏见进行操纵
- **虚假信息传播**: 传播虚假或误导性信息
- **身份盗用**: 冒充他人身份
- **未授权访问**: 黑客入侵
- **自动化攻击**: 使用自动化工具进行攻击
- **深度伪造**: Deepfake 技术滥用

### 2. 犯罪动机 (crime_motive)
描述犯罪背后的驱动力：
- **故意犯罪**: Intentional - 有预谋的犯罪
- **过失/意外**: Unintentional - 非故意的危害
- **经济利益**: 追求经济回报
- **个人报复**: 个人恩怨驱动
- **政治/意识形态**: 政治目的或意识形态驱动
- **研究/实验**: 实验性质的行为
- **其他**: 未明确或其他动机

### 3. 针对人群 (target_victims)
描述犯罪目标群体：
- **儿童/未成年人**: children, minor, student
- **女性**: women, female
- **少数族裔**: racial/ethnic minorities
- **老年人**: elderly, senior
- **消费者**: consumers, users
- **患者**: patients, medical
- **员工/工人**: employees, workers
- **学生**: students
- **普通公众**: general public
- **企业/组织**: companies, organizations
- **政府机构**: government agencies

### 4. 犯罪场景 (crime_context)
描述犯罪发生的环境和背景：
- **社交媒体**: Facebook, Twitter, YouTube, TikTok
- **电子商务**: Amazon, eBay, online shopping
- **金融服务**: banking, payment, cryptocurrency
- **医疗健康**: healthcare, hospital
- **教育**: school, university, learning
- **就业/招聘**: hiring, employment
- **政府服务**: government, public service
- **新闻媒体**: news, media
- **娱乐**: gaming, streaming
- **交通**: transportation, autonomous vehicles

## 📋 数据字段说明

### 核心字段（研究参数）
| 字段名 | 说明 | 示例值 |
|--------|------|--------|
| `category_id` | 网络犯罪分类 ID (1-6) | `1` |
| `category_name` | 网络犯罪分类名称 | `欺诈与金融犯罪` |
| `crime_means` | 犯罪手段 | `AI 生成内容; 自动化攻击` |
| `crime_motive` | 犯罪动机 | `故意犯罪` |
| `target_victims` | 针对人群 | `儿童/未成年人; 消费者` |
| `crime_context` | 犯罪场景 | `社交媒体 (en, 2015)` |

### 基础信息字段
| 字段名 | 说明 |
|--------|------|
| `report_id` | 原始 MongoDB 报告 ID |
| `report_number` | 报告编号 |
| `title` | 报告标题 |
| `description` | 报告描述摘要 |

### 来源信息字段
| 字段名 | 说明 |
|--------|------|
| `source_url` | 原始来源 URL |
| `date_published` | 发表日期 |
| `source_domain` | 来源网站域名 |
| `language` | 语言 |

### 关联字段
| 字段名 | 说明 |
|--------|------|
| `incident_id` | 关联的事故 ID |
| `mit_risk_domain` | MIT 风险主分类 |
| `mit_risk_subdomain` | MIT 风险子分类 |
| `mit_intent` | MIT 意图分类 |

## 🔗 数据关联关系

```
network_crime_classified.csv
    ↓ (通过 report_number)
reports.csv (原始报告数据)
    ↓ (通过 incident_id)
incidents.csv (事故数据)
    ↓ (通过 Incident ID)
classifications_MIT.csv (MIT 分类标注)
```

## 📊 各类别统计特征

### 1. 欺诈与金融犯罪 (1,905 例)
- **主要手段**: 自动化攻击 (290 例)、AI 生成内容 (210 例)、深度伪造 (133 例)
- **主要场景**: 新闻媒体 (236 例)、金融服务 (22 例)
- **典型案件**: 金融诈骗、投资欺诈、加密货币骗局

### 2. 隐私与身份侵犯 (970 例)
- **主要手段**: 自动化攻击 (216 例)、AI 生成内容 (101 例)、算法操纵 (34 例)
- **主要场景**: 社交媒体 (26 例)、电子商务 (15 例)
- **典型案件**: 数据泄露、身份盗用、隐私侵犯

### 3. 恶意内容传播 (596 例)
- **主要手段**: 虚假信息传播 (69 例)、自动化攻击 (56 例)
- **主要场景**: 新闻媒体 (82 例)、社交媒体 (19 例)
- **典型案件**: 假新闻、虚假信息、宣传操纵

### 4. 恶意软件与攻击 (433 例)
- **主要手段**: 自动化攻击 (86 例)、AI 生成内容 (18 例)
- **主要场景**: 新闻媒体 (58 例)
- **典型案件**: 网络攻击、恶意软件、系统入侵

### 5. 知识产权侵犯 (147 例)
- **主要手段**: 自动化攻击 (46 例)、AI 生成内容 (24 例)
- **典型案件**: 版权侵犯、商标假冒、专利侵权

### 6. 社会工程与骚扰 (2,735 例)
- **主要手段**: 自动化攻击 (540 例)、AI 生成内容 (176 例)、算法操纵 (97 例)
- **主要场景**: 新闻媒体 (195 例)、交通 (75 例)、社交媒体 (72 例)
- **典型案件**: 网络骚扰、社会工程攻击、算法歧视

## 💡 使用建议

### 研究方法
1. **定量分析**: 使用 `category_id` 进行分组统计
2. **关系分析**: 分析四个核心参数之间的关联关系
3. **趋势分析**: 使用 `date_published` 分析时间趋势
4. **场景分析**: 使用 `crime_context` 进行场景分类研究

### 数据筛选示例
```python
import csv

# 筛选欺诈与金融犯罪案例
with open('network_crime_classified.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    fraud_cases = [row for row in reader if row['category_id'] == '1']

# 筛选针对儿童的故意犯罪
with open('network_crime_classified.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    child_targeted = [
        row for row in reader 
        if '儿童/未成年人' in row['target_victims'] 
        and row['crime_motive'] == '故意犯罪'
    ]

# 分析社交媒体上的犯罪手段
with open('network_crime_classified.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    social_media_crimes = [
        row for row in reader 
        if '社交媒体' in row['crime_context']
    ]
```

## ⚠️ 注意事项

1. **数据质量**: 
   - 部分记录的 `target_victims` 为"未明确"，这是原始数据限制
   - `crime_motive` 大部分为"其他"，需要结合 `description` 进一步分析

2. **分类方法**:
   - 优先使用 MIT 分类映射
   - 其次使用关键词匹配
   - 默认归类为"社会工程与骚扰"

3. **多标签处理**:
   - `crime_means` 和 `target_victims` 可能包含多个值，用分号分隔
   - 分析时需要进行拆分处理

4. **语言限制**:
   - 大部分数据为英文 (`en`)
   - 犯罪场景中的年份信息来自 `date_published`

## 📁 相关文件

- `network_crime_classified.csv` - 主数据文件
- `create_cybercrime_dataset.py` - 数据生成脚本
- `show_stats.py` - 统计信息展示脚本
- `reports.csv` - 原始报告数据源
- `incidents.csv` - 事故数据
- `classifications_MIT.csv` - MIT 分类标注

## 📞 数据用途

本数据集专为网络犯罪研究设计，适用于：
- 犯罪手段与动机的关系分析
- 针对人群特征研究
- 犯罪场景模式识别
- AI 在网络犯罪中的角色分析
- 网络犯罪趋势预测
