# 非欧盟国家/地区数字产品护照（DPP）进展调研报告

> 完成日期：2026-09-07
> 报告版本：v1.0
> 研究范围：美国、韩国、日本、新加坡、澳大利亚、英国、加拿大、印度及国际组织
> 时间聚焦：2025-2026年最新进展
> 服务目标：为DPP-CQ标准的"全球标准"定位提供支撑材料

---

## 执行摘要

全球数字产品护照（DPP）正从"欧盟独推"进入"全球共振"的新阶段。截至2026年9月，欧盟仍是唯一拥有全面、有法律约束力的DPP框架的司法管辖区（ESPR + 电池法规 + 建筑产品法规），但非欧盟国家/地区正以不同路径加速布局：

- **日本**以出口合规为直接驱动力，通过METI主导的Ouranos生态系统和ABtC平台，在汽车/电池领域走在非欧盟经济体前列
- **美国**无联邦DPP强制要求，但通过FSMA 204、DSCSA、Cyber Trust Mark等行业法规形成"DPP-adjacent"碎片化格局
- **韩国**以出口欧盟合规为核心驱动力，三大电池企业积极备战，政府层面战略尚在制定中
- **新加坡**依托贸易数字化和Smart Nation基础，成为DPP创业企业（如Orobo）的区域枢纽
- **澳大利亚**以农业追溯为突破口，AATP基于UNTP架构构建去中心化的农业DPP体系
- **英国**脱欧后处于立法过渡期，《产品监管和计量法2025》为数字标签和可能的DPP制度提供了法律框架
- **国际层面**，ISO/IEC JTC 5（2026年4月成立）、UNEP DPIS、UNECE UNTP三大并行框架正在推动全球互操作性

对于**DPP-CQ标准**而言，全球DPP格局呈现"法规欧盟领先、技术标准多极并行、互操作性是核心痛点"的特征，DPP-CQ有机会在亚洲标准对接、多标识符语法兼容、供应链实际落地三个方向构建差异化价值。

---

## 一、美国（United States）

### 1.1 政策法规

**总体定位：DPP-adjacent（DPP邻近型），无联邦层面DPP强制立法**

美国目前没有联邦层面的数字产品护照统一法规，被业界普遍视为"DPP-adjacent"司法管辖区——即不通过可持续立法实施产品护照，而是通过食品安全、海关合规、强制劳动执法等领域的法规构建了许多相同的技术基础 [(Tilkal)](https://www.tilkal.com/post/digital-product-passports-beyond-europe-how-global-markets-are-converging-toward-product-data-requi)。

**主要政策进展：**

| 政策/法规 | 主管机构 | 状态 | 最新进展 |
|-----------|---------|------|---------|
| FSMA Section 204 食品追溯规则 | FDA | 延期实施 | 合规日期从2026年1月20日延期30个月至2028年7月20日 [(FDA Federal Register)](https://public-inspection.federalregister.gov/2025-14967.pdf) |
| DSCSA 药品供应链安全法案 | FDA | 分阶段生效 | 制造商/批发商/大中型药房已分别于2025年5/8/11月生效，小药房豁免至2026年11月 [(Intuition Labs)](https://intuitionlabs.ai/articles/dscsa-vs-eu-fmd-serialization-traceability) |
| Cyber Trust Mark 物联网安全标签 | FCC | 重启推进 | 2026年4月任命ioXt Alliance为新首席管理员；联邦采购渠道2027年1月强制 [(Keystone Compliance)](https://keystonecompliance.com/fcc-cybersecurity-testing/) |
| IRA 低碳建筑材料标签（第60116条） | EPA | 资金撤销 | 1亿美元拨款于2025年7月被国会撤销 [(IRA Tracker)](https://iratracker.org/programs/ira-section-60116-low-embodied-carbon-labelling-for-federal-project-construction-materials/) |
| UFLPA 维吾尔强迫劳动预防法 | CBP | 实施中 | 通过供应链透明度和原产地核查推进产品数据化 |

**推进状态：讨论中/行业分散推进**（无统一DPP立法规划）

### 1.2 技术标准

- **标识体系**：GS1 GTIN/SSCC 为行业事实标准，GS1 Sunrise 2027 2D条码过渡在美加速推进
- **数据载体**：QR码为主，支持GS1 Digital Link URI解析
- **联邦参与**：ANSI组建美国技术咨询组（US TAG）参与ISO/IEC JTC 5工作 [(ANSI)](https://www.ansi.org/standards-news/all-news/3-5-26-new-joint-technical-committee-on-digital-product-passport-standards)
- **NIST角色**：Cyber Trust Mark基于NISTIR 8425指南；NIST也在供应链可视性和SBOM方面有相关研究

### 1.3 行业实践

- **食品行业**：Walmart等大型零售商的供应商追溯要求（ASN with KDE数据、SSCC-18托盘标签、GS1-128箱标签）已于2025年8月1日生效，早于联邦法定日期推动行业准备 [(inecta)](https://www.inecta.com/blog/fsma-204-compliance-guide)
- **医药行业**：DSCSA序列化已基本落地，EPCIS数据交换成为行业标准
- **物联网**：Cyber Trust Mark通过QR码链接到产品网络安全信息注册表，形成了"DPP-like"的消费者产品信息访问模式
- **建筑材料**：GSA的IRA低隐含碳（LEC）材料采购要求仍在执行，推动EPD（环境产品声明）发展

### 1.4 与DPP-CQ的关联

- **互补机会**：美国碎片化的行业追溯体系（食品/药品/物联网各有体系）缺乏统一DPP框架，DPP-CQ可作为跨行业产品数字身份的对接方案
- **标准对接**：美国通过ANSI深度参与ISO/IEC JTC 5，DPP-CQ若能与JTC 5标准进程对齐，将更易获得美国业界认可
- **市场切入点**：美国出口企业（尤其是对欧出口）事实上在按欧盟ESPR标准建设DPP能力，DPP-CQ可服务于"一次建设、多市场合规"需求

---

## 二、日本（Japan）

### 2.1 政策法规

**总体定位：合规驱动型，以出口欧盟合规为直接目标，国家层面有系统布局**

日本的DPP推进以**出口欧盟合规**为直接驱动力，但国家层面有系统的战略布局，核心依托METI（经济产业省）推动的**Ouranos生态系统**。

**主要政策进展：**

| 政策/举措 | 主管机构 | 状态 | 最新进展 |
|----------|---------|------|---------|
| Ouranos生态系统 | METI + IPA | 实施中 | 覆盖汽车、电池、建筑等领域，分布式数据架构，企业数据自主管理 [(中国信通院)](https://www.docin.com/touch_new/preview_new.do?id=4864512176) |
| 电池与电力产业战略 | METI | 修订发布 | 2026年6月2日修订，目标2030年国内150GWh产能，全固态电池2030年商业化 [(OpenPR)](https://www.openpr.com/news/4615992/battery-passport-market-to-reach-us-2-244-2-million-by-2035-as) |
| GX（绿色转型）法 | METI | 实施中 | 计划2025年前建立日本数字信息平台 [(Circular Economy Tokyo)](https://circulareconomy.tokyo/en/column/2780) |
| ABtC 公益数字平台认定 | METI | 已认定 | ABtC于2024年9月获得日本首个"公益数字平台运营商"认定 [(METI)](https://www.meti.go.jp/policy/mono_info_service/digital_architecture/ouranos/ouranos_trust/250131/siryo3.pdf) |

**推进状态：试点中→验证阶段**（汽车/电池领域进入连接认证阶段）

### 2.2 技术标准

- **国家级平台**：Ouranos生态系统 + ABtC数据共享平台，遵循IPA指南
- **标识体系**：支持GS1体系，同时兼容IEC 61406标识链接
- **国际互操作**：NEDO资助与欧洲Catena-X的互操作性测试，DENSO已成为全球首个同时连接Catena-X和Ouranos的企业应用 [(DENSO)](https://www.denso.com/global/en/news/newsroom/2026/20260305-g01/)
- **NEDO资助**：Ouranos项目期FY2025-2027，FY2026预算用于海外平台互操作、信任功能和电池碳足迹数据交换系统建设
- **ABtC V3.2.0**：追溯服务持续升级，支持CFP数据的持续管理和透明追踪

### 2.3 行业实践

- **汽车/电池**：ABtC连接认证体系逐步完善，DENSO、电通综研等企业获得认证；丰田、本田等车企通过Ouranos生态建设电池生命周期追踪能力
- **碳足迹**：DENSO的CFP计算应用获ABtC认证，电池护照服务计划2026年夏季发布，未来扩展至全品类DPP
- **循环经济试点**：丸红与荷兰Circularise合作在日本推进DPP，已开展PET瓶回收材料流追踪试点（J-CEP倡议下）
- **互操作验证**：NEDO支持的日本-韩国（Glassdome）互操作性演练正在进行

### 2.4 与DPP-CQ的关联

- **技术对标**：Ouranos生态系统的分布式数据架构、企业数据自主管理理念与DPP-CQ有契合点，可开展技术对标
- **中日互操作**：中日均为制造业和出口大国，DPP-CQ可探索与Ouranos/ABtC的互操作性对接，服务中日贸易供应链
- **亚洲标准**：日本在汽车/电池领域的DPP实践走在亚洲前列，DPP-CQ可借鉴其行业落地路径
- **标准协同**：日本和中国均参与ISO/IEC JTC 5，可在国际标准制定中协调亚洲立场

---

## 三、韩国（South Korea）

### 3.1 政策法规

**总体定位：出口合规驱动型，无独立DPP立法，政府战略制定中**

韩国目前没有独立的DPP立法，企业主要为出口欧盟的ESPR合规做准备。KATS（韩国技术标准院）正在跟踪ESPR进展并推动韩国产品标准与欧盟要求对齐 [(ESPR Registry)](https://esprregistry.com/south-korea-espr/)。

**主要政策进展：**

| 政策/举措 | 主管机构 | 状态 | 最新进展 |
|----------|---------|------|---------|
| K-Battery战略 | MOTIE | 实施中 | 电池产业全面发展战略，碳足迹/DPP是重要支撑 |
| 国家数字孪生战略 | MSIT | 规划中 | 计划提出DPP应对战略，2025年上半年计划发布 [(KIAT)](https://www.kiat.or.kr/commonfile/fileidDownLoad.do?file_id=3C287E8557664BC4AC2F46DD44A670A1) |
| KC认证 | KATS | 已实施 | 韩国强制安全认证，但KC标志不能满足ESPR合规要求 [(ESPR Registry)](https://esprregistry.com/south-korea-espr/) |
| KITIM ESPR/DPP咨询 | KITIM | 服务中 | 韩国产业技术评价院提供ESPR/DPP合规咨询服务 |

**推进状态：规划中/企业先行**（政府层面战略尚在制定，企业被动合规）

### 3.2 技术标准

- **标识体系**：以KC认证体系为基础，向ESPR/GS1标准对齐
- **技术服务商**：Glassdome（韩国）是代表性的碳足迹/DPP解决方案提供商，基于ISO 14067标准提供PCF计算和电池护照服务 [(Glassdome)](https://glassdome.com/ko/eu-battery-regulation-timeline-and-system-boundary-requirements/)
- **互操作**：NEDO支持下的日韩（Glassdome-ABtC）互操作性演练正在进行 [(OpenPR)](https://www.openpr.com/news/4615992/battery-passport-market-to-reach-us-2-244-2-million-by-2035-as)
- **供应链数据**：制造前环节排放占64%（LG新能源数据），上游供应链数据采集是主要挑战

### 3.3 行业实践

- **三大电池企业备战**：
  - 三星SDI：与Glassdome合作搭建ISO 14067碳核算体系 [(Digital Today)](https://www.digitaltoday.co.kr/cn/view/82899/eu-digital-battery-passport-mandate-next-year-worries-for-small-suppliers-in-south-korea)
  - LG新能源：公开电池护照系统试点方案，计划开发自有管理系统
  - SK On：依托供应链数据建设DPP能力
- **乐天铝业/Choil铝业**：引入Glassdome数字碳护照平台，覆盖Scope 3供应链排放
- **汽车行业**：现代汽车集团开发电池护照以满足欧盟合规要求
- **中小企业挑战**：中小配套企业数据能力不足，碳足迹数据采集是主要瓶颈

### 3.4 与DPP-CQ的关联

- **供应链协同**：中韩电池供应链深度交织，DPP-CQ可提供中韩供应链数据交换的互操作方案
- **标准对接**：韩国企业在ESPR合规方面已有实践积累，DPP-CQ若能兼容ESPR数据模型，将降低韩国企业对接成本
- **市场机会**：韩国DPP以出口合规为主要驱动，DPP-CQ可定位为"东亚DPP合规基础设施"，服务中韩制造业出口

---

## 四、新加坡（Singapore）

### 4.1 政策法规

**总体定位：贸易数字化驱动型，国家战略提供基础，企业为主力军**

新加坡没有专门的DPP法规，但其**贸易数字化战略**和**新加坡绿色计划2030**为DPP发展提供了坚实的政策基础和数字基础设施。

**主要政策进展：**

| 政策/举措 | 主管机构 | 状态 | 最新进展 |
|----------|---------|------|---------|
| 贸易和供应链数字化战略 | MDDI / IMDA | 实施中 | TradeNet系统持续优化，TradeTrust数字贸易标准与多国开展试点 [(MDDI)](https://www.mddi.gov.sg/newsroom/singapore-and-china-deepen-exchange-in-digital-economy-at-2nd-singapore-china-digital-policy-dialogue--dpd--in-chongqing--china/) |
| 新加坡绿色计划2030 | 政府 | 实施中 | 关注产品环保特性，建筑行业绿色标准推动产品环境信息披露 [(中国信通院)](https://www.docin.com/touch_new/preview_new.do?id=4870332423) |
| 塑料循环国家平台 | A*STAR + SMX | 试点中 | 2025年9月启动，2026Q1半工业整合，2027Q2全面商业展示 [(North Carolina Daily)](https://www.northcarolinadaily.com/news/278547581/singapore-a-star-and-smx-lead-drive-for-world-first-plastics-passport-program) |
| Smart Nation | 政府 | 实施中 | 国家数字基础设施为DPP提供技术底座 |

**推进状态：试点中/企业创新活跃**

### 4.2 技术标准

- **贸易数字化**：TradeTrust标准化数字贸易单证，与中国、沙特等多国开展试点
- **标识体系**：GS1 Singapore活跃，支持GS1 Digital Link和Sunrise 2027过渡
- **区块链技术**：IOTA分布式账本技术在新加坡有企业应用（Orobo）
- **分子标记技术**：A*STAR与SMX的塑料护照项目使用化学分子标记+区块链的创新方案
- **数据跨境**：新加坡的PETs（隐私增强技术）沙盒等创新监管环境有利于DPP数据交换

### 4.3 行业实践

- **Orobo DPP平台**：总部位于新加坡的可持续数据清算所，基于IOTA提供跨境DPP签发和验证的合规级基础设施，从EV电池开始，计划扩展到纺织品和建筑材料 [(IOTA Blog)](https://blog.iota.org/orobo-trusted-product-data/)
- **塑料护照计划**：A*STAR与SMX合作启动全球首个塑料护照，追踪5000+吨消费后塑料废物，支持新加坡零废Masterplan
- **食品追溯**：Cold Storage等零售企业开展食品区块链追溯试点
- **物流IoT**：YCH Group等物流企业推进供应链数字化

### 4.4 与DPP-CQ的关联

- **区域枢纽定位**：新加坡是东南亚数字经济和贸易枢纽，DPP-CQ可考虑与新加坡平台合作拓展东南亚市场
- **技术互补**：Orobo基于IOTA的DPP方案与DPP-CQ可探索技术互操作
- **中新合作**：中新数字政策对话机制（DPD）已建立，DPP可作为中新数字经济合作的新议题
- **贸易便利化**：TradeTrust经验可借鉴，DPP-CQ可融入贸易单证数字化体系

---

## 五、澳大利亚（Australia）

### 5.1 政策法规

**总体定位：农业追溯领先型，以国家农业追溯战略为核心**

澳大利亚在农产品追溯领域走在全球前列，其**国家农业追溯战略（2023-2033）** 投资超1亿澳元，是全球最系统的国家级追溯战略之一。

**主要政策进展：**

| 政策/举措 | 主管机构 | 状态 | 最新进展 |
|----------|---------|------|---------|
| 国家农业追溯战略（2023-2033） | 农业部 | 实施中 | 超1亿澳元投资，覆盖农业、渔业、林业 |
| AATP全国推广 | Standards Australia | 推广中 | 2026年7月追加53.4万澳元，由Standards Australia牵头全国推广 [(澳大利亚农业部)](https://minister.agriculture.gov.au/collins/media-releases/stronger-agricultural-traceability) |
| 国家治理小组 | NFF（全国农民联合会） | 筹建中 | 2026年7月拨款195万澳元建立新治理小组（接替AATGG） |
| NLIS 国家牲畜识别系统 | Meat & Livestock Australia | 已实施 | 成熟的牲畜电子标识系统，是AATP的身份锚点之一 |
| Buy Clean政策 | 州政府 | 州级推进 | 部分州（如西澳）推进建筑材料低碳采购 |

**推进状态：试点成功→全国推广**（农业领域）

### 5.2 技术标准

- **AATP架构**：去中心化的可验证链接数据架构，基于UNTP（联合国透明度协议）架构 [(AATP Specification)](https://aatp.foodagility.com/docs/specification/)
- **五类凭证**：产品护照（growers/processors签发）、追溯事件、合规凭证、身份锚点、聚合凭证
- **身份解析**：通过NLIS（牲畜）、PIC（养殖场）、ABN（企业号）、GTIN（商品编码）等身份解析器发现数据
- **标准治理**：每4周召开工作组会议，GitHub开源开发，公开透明
- **UNTP对齐**：AATP是UNTP在农业领域的国家实施范例

### 5.3 行业实践

- **农业追溯**：AgTrace Australia在多个农业行业成功试点AATP
- **牛肉供应链DPP**：Macka's牛肉供应链DPP试点使用GS1 2D码，覆盖7个国家（信息待进一步验证）
- **出口价值**：2025-26年农林渔业出口预计达约860亿澳元创纪录水平，追溯体系是市场准入的关键支撑 [(澳大利亚农业部)](https://minister.agriculture.gov.au/collins/media-releases/stronger-agricultural-traceability)
- **行业自主推进**：AATP作为公共物品，无许可限制，行业广泛参与

### 5.4 与DPP-CQ的关联

- **农业DPP标杆**：澳大利亚AATP是全球农业DPP最成熟的国家实践之一，DPP-CQ可借鉴其技术架构和治理模式
- **UNTP兼容**：AATP基于UNTP架构，DPP-CQ若兼容UNTP/VC标准，可与澳大利亚农业追溯体系直接互操作
- **贸易对接**：中澳农产品贸易量大，DPP-CQ可提供农产品追溯的双边对接通道
- **治理模式借鉴**：AATP的行业主导、公开治理模式可为DPP-CQ的标准治理提供参考

---

## 六、英国（United Kingdom）

### 6.1 政策法规

**总体定位：脱欧转型期，数字标签法律框架已建立，完整DPP尚不确定**

英国脱欧后，产品监管处于过渡期。《产品监管和计量法2025》（Product Regulation and Metrology Act 2025）为数字标签和可能的DPP制度提供了法律基础。

**主要政策进展：**

| 政策/举措 | 主管机构 | 状态 | 最新进展 |
|----------|---------|------|---------|
| 《产品监管和计量法2025》 | DESNZ | 已生效 | 2025年7月21日获御准，授权制定数字标签等二级立法 [(UK Legislation)](https://www.legislation.gov.uk/ukpga/2025/20/pdfs/ukpga_20250020_en.pdf?view=extent) |
| 数字标签咨询 | DESNZ | 咨询结束 | 2026年6月23日咨询关闭，政府回应预计2026年9月 [(Custom Labels)](https://www.customlabels.co.uk/asset-labels/uk-digital-labelling-law-2026-whats-changing-and-what-still-needs-a-physical-label) |
| DPP制度引入 | 政府 | 讨论中 | 是否引入完整DPP尚不确定；BRC等行业组织建议与ESPR对齐 |
| CE标记认可扩展 | 政府 | 咨询中 | 咨询是否延长CE标记认可机制以对接ESPR |

**推进状态：规划中/立法准备**（数字标签框架已就位，DPP待定）

### 6.2 技术标准

- **数字标签框架**：物理载体（序列号、批号）+ 数字信息（安全说明、警告、生产商联系方式），QR码/NFC为主要数据载体
- **与欧盟关系**：英国可能选择与ESPR对齐以确保贸易顺畅，北爱尔兰市场问题是重要考量因素
- **GS1体系**：GS1 UK活跃，支持Sunrise 2027过渡

### 6.3 行业实践

- **出口企业被动合规**：英国出口欧盟企业事实上在按ESPR要求建设DPP能力
- **零售行业**：英国零售协会（BRC）积极参与数字标签和DPP政策讨论，代表行业发声
- **时尚/纺织**：时尚行业被认为是英国DPP试点的优先领域之一

### 6.4 与DPP-CQ的关联

- **标准对接窗口期**：英国DPP制度尚未定型，DPP-CQ有机会参与英国标准制定进程
- **中英贸易**：中英贸易企业可通过DPP-CQ实现中英双向产品数据互通
- **欧洲市场桥梁**：英国作为英语国家和欧洲金融中心，可作为DPP-CQ进入欧洲市场的合作节点

---

## 七、加拿大（Canada）

### 7.1 政策法规

**总体定位：间接推动型，无独立DPP要求，相关政策分散**

加拿大目前没有独立的DPP强制要求，主要通过以下政策间接推动产品透明度：

- **《打击供应链强迫劳动和童工法》**：要求企业进行供应链尽职调查
- **Buy Clean政策**：公共采购中的低碳建筑材料要求（与美国Buy Clean趋势一致）
- **关键矿产战略**：关键矿产溯源需求增加

**推进状态：讨论中/行业分散推进**

### 7.2 行业实践

- 加拿大DPP服务商（如Peer Ledger）主要服务出口合规需求，覆盖CSRD、CS3D、CEPA、UFLPA等法规 [(Peer Ledger)](https://www.peerledger.com/digital-product-passport)
- 北美制造业供应链整合程度高，美国DPP-adjacent法规对加拿大企业有溢出效应

### 7.3 与DPP-CQ的关联

- 加拿大作为G7成员和贸易大国，DPP-CQ可将其纳入北美市场对接考虑
- 加拿大深度参与UNECE和ISO标准工作，可在国际标准层面协作

---

## 八、印度（India）

### 8.1 政策法规

**总体定位：机遇驱动型，纺织业出口受ESPR直接影响**

印度目前没有国家级DPP立法，但作为全球第六大纺织品出口国（占全球贸易4.1%），其纺织业受EU ESPR DPP影响巨大 [(EIJ News)](https://www.eij.news/post/scanning-the-future-how-europe-s-upcoming-digital-passport-rules-are-rewriting-indian-trade)。

**主要进展：**

| 领域 | 状态 | 说明 |
|------|------|------|
| 印欧自贸协定 | 已达成 | 2026年1月达成，覆盖全球GDP 25%，7年内逐步取消99.5%印度输欧商品关税 [(中国经济网)](http://m.ce.cn/bwzg/202602/t20260203_2746040.shtml) |
| 纺织业DPP准备 | 被动推进 | 供应链碎片化严重，追溯挑战大；出口企业开始准备ESPR合规 |
| 数字基础设施 | 发达 | UPI、Aadhaar、ONDC等国家数字基础设施发达 |
| 软件产业机遇 | 战略机会 | 政府将DPP视为软件产业的战略机遇 [INFO_GAP - 无官方来源确认] |

**推进状态：出口准备阶段**

### 8.2 与DPP-CQ的关联

- **南南合作**：中印均为发展中大国和制造业出口大国，DPP-CQ可探索与印度的DPP能力建设合作
- **供应链对接**：中印在纺织、制药、电子产品供应链上有交叉，DPP-CQ可服务供应链数据互通
- **数字基础设施借鉴**：印度的DPI（数字公共基础设施）模式值得DPP-CQ参考

---

## 九、国际组织与全球标准格局

### 9.1 ISO/IEC JTC 5 — 国际标准化主阵地

**成立时间**：2026年4月（德国DIN任秘书处）
**首次会议**：2026年9月7-9日，柏林
**成员规模**：31个参与国 + 17个观察国 [(ISO)](https://www.iso.org/cms/render/live/fr/sites/isoorg/contents/data/committee/11/76/11760382.html)
**职责范围**：
- DPP系统和生态系统的框架
- 跨行业、跨系统互操作性
- 供应链信息流使能
- **不制定**行业特定标准（由其他ISO/IEC技术委员会负责）

**首个项目**：ISO/AWI 25534-1《数字产品护照—第1部分：概述和基本原则》（2026年2月批准），涵盖：
- 通用DPP术语
- 基本原则
- DPP数据类别
- 治理与信任方法
- 与现有标准的关系

**对DPP-CQ的意义**：JTC 5是全球DPP标准的最高平台，DPP-CQ应密切跟踪并争取参与，确保中国标准在国际框架中有一席之地。

### 9.2 UNEP D4CE/DPIS — 全球发展中国家框架

**倡议发起**：UNEP + One Planet Network的D4CE（数字化促进循环经济）影响倡议
**全球蓝图发布**：2025年10月
**核心内容**：
- 7大类39子类数据（通用产品信息、合规与材料数据、环境与生命周期指标、社会责任指标、循环经济策略等）[(eproductpassport.eu)](https://eproductpassport.eu/from-european-to-global-interoperability-towards-a-unified-framework-for-digital-product-passports/)
- 技术架构（治理原则、互操作标准、访问级别、数据类别）
- 实施与能力建设（数字基础设施、中小企业支持、跨行业试点）

**试点项目**：
- 阿根廷纺织业（2025 Q3 - 2026 Q4）
- 印度电池业

**三阶段路线图**：
1. 2024年：数据评估 + 咨询（40+国家、200+组织）
2. 2025/2026年：试点测试 + 框架草案
3. 2026年及以后：发布推广，自愿采用

**对DPP-CQ的意义**：UNEP框架更具包容性，强调发展中国家能力建设，DPP-CQ可在此框架下贡献中国经验，提升发展中国家影响力。

### 9.3 UNECE UNTP — 联合国透明度协议

**定位**：基于W3C可验证凭证（VC）的全球可持续性数据互操作参考框架
**核心主张**：
- 联合国治理、非专有、开放免费
- 与各国体系互补而非竞争
- 统一标识符、凭证格式、追溯语义 [(UNECE UNTP FAQ)](https://untp.unece.org/docs/about/FAQ/)

**DPP规范**：
- ProductPassport类型凭证
- 支持model/batch/serialised item三级粒度
- 材料溯源、合规声明、尽职调查声明

**实施案例**：澳大利亚AATP是UNTP在农业领域的典型国家实施

**对DPP-CQ的意义**：UNTP基于VC的去中心化架构与DPP-CQ的技术方向高度契合，可作为DPP-CQ国际互操作的基准协议。

### 9.4 CEN-CENELEC EN 18xxx系列 — 欧盟横向标准

**发布时间**：2026年6月25日（6项已发布，2项安全标准投票中）
**标准清单**：
- EN 18216（框架）
- EN 18219（标识符和数据载体）——支持多种标识符语法：GS1 Digital Link、EN IEC 61406-2、ISO/IEC 18975、did:web等
- EN 18220（访问权）
- EN 18221（数据交换）
- EN 18222（生命周期可用性）
- EN 18223（系统互操作性）
- prEN 18239 / prEN 18246（安全标准，2026年7月16日投票截止）

**法律地位**：2026年7月15日，欧盟委员会实施决定(EU) 2026/1736发布6项协调标准的引用，符合这些标准的DPP系统被推定符合ESPR第10、11条要求

**对DPP-CQ的意义**：EN 18xxx系列是全球最成熟的DPP横向标准体系，DPP-CQ应将其作为基准参考，确保与欧盟体系的互操作性。

### 9.5 ITU-T L.1070/L.1071

ITU-T（国际电信联盟）已制定两项DPP相关标准：
- **L.1070**：DPP功能要求
- **L.1071**：DPP数据模型

**对DPP-CQ的意义**：ITU是联合国专门机构，标准具有官方国际地位，DPP-CQ可关注并参与相关工作。

---

## 十、综合对比表

| 国家/地区 | 政策状态 | 主管机构 | 核心驱动因素 | 重点行业 | 技术平台/标准 | 与ESPR关系 | 推进程度 |
|-----------|---------|---------|-------------|---------|--------------|-----------|---------|
| **美国** | 无联邦DPP强制，行业法规碎片化 | FDA / FCC / CBP / EPA | 食品安全、海关合规、网络安全 | 食品、医药、IoT | FSMA 204 / DSCSA / Cyber Trust Mark / GS1 | DPP-adjacent，无直接关联 | ★★★☆☆ 行业分散推进 |
| **日本** | 国家战略布局，生态系统建设中 | METI / IPA / NEDO | 出口欧盟合规 + 产业竞争力 | 汽车、电池、建筑 | Ouranos / ABtC / Catena-X互操作 | 主动对接，互操作验证 | ★★★★☆ 试点→验证阶段 |
| **韩国** | 无独立DPP立法，战略制定中 | MOTIE / KATS / MSIT | 出口欧盟合规 | 电池、汽车、电子 | Glassdome / 企业自有系统 | 被动应对，KATS跟踪对齐 | ★★★☆☆ 企业先行/规划中 |
| **新加坡** | 无专门DPP法规，贸易数字化提供基础 | MDDI / IMDA / A*STAR | 贸易数字化 + 绿色发展 | 塑料循环、电池、食品 | Orobo / IOTA / TradeTrust / GS1 | 企业层面对接，服务出口合规 | ★★★☆☆ 试点中/企业创新活跃 |
| **澳大利亚** | 国家农业追溯战略实施中 | 农业部 / Standards Australia | 农产品出口市场准入 | 农业、畜牧业 | AATP（基于UNTP） / NLIS | 间接关联，农业追溯可扩展至DPP | ★★★★☆ 农业领域试点成功→全国推广 |
| **英国** | 数字标签法律框架就位，DPP待定 | DESNZ | 脱欧后监管自主 + 对欧贸易 | 待定（可能时尚/纺织优先） | Product Regulation and Metrology Act 2025 | 可能对齐，北爱问题是考量 | ★★☆☆☆ 立法准备/讨论中 |
| **加拿大** | 无独立DPP要求 | 政府各部门 | 出口合规 + 关键矿产 | 矿产、建筑 | Peer Ledger等企业方案 | 间接关联，出口企业被动合规 | ★★☆☆☆ 讨论中 |
| **印度** | 无DPP立法，出口被动准备 | 各行业部门 | 对欧纺织出口 + 数字产业机遇 | 纺织、制药、电子 | TraceX等初创企业方案 | 被动应对，纺织业承压 | ★★☆☆☆ 出口准备阶段 |

> 推进程度说明：★★★★★ = 已强制实施；★★★★☆ = 试点验证/部分实施；★★★☆☆ = 试点/规划中；★★☆☆☆ = 讨论/准备阶段；★☆☆☆☆ = 初步探索

---

## 十一、技术标准对比与互操作性分析

### 11.1 标识符语法格局

| 标准 | 主导机构 | 状态 | 支持方 |
|------|---------|------|--------|
| GS1 Digital Link (ISO/IEC 18975) | GS1 | 事实标准，Sunrise 2027过渡 | 全球零售业、供应链 |
| IEC 61406-2 | IEC | 已发布 | 工业制造、IoT |
| W3C did:web | W3C | VC 2.0配套 | 去中心化身份生态 |
| EN 18219:2026 | CEN/CENELEC | 已发布，具推定合规效力 | 欧盟ESPR |

**关键发现**：EN 18219允许多种标识符语法共存，这意味着DPP-CQ无需绑定单一标识符标准，而应支持多语法解析器模式，与国际主流标准兼容。

### 11.2 数据载体格局

- **QR码**：主流数据载体，消费者可用智能手机直接扫描，Sunrise 2027推动POS端兼容
- **GS1 DataMatrix**：医疗保健等行业常用
- **NFC/RFID**：辅助方式，适用于高价值产品或特定场景
- **结论**：QR码 + GS1 Digital Link URI是当前DPP物理-数字链接的最具普适性方案

### 11.3 信任机制格局

| 机制 | 标准基础 | 应用场景 | 成熟度 |
|------|---------|---------|--------|
| W3C VC 2.0 | W3C Recommendation 2025-05 | UNTP、AATP、澳大利亚农业追溯 | ★★★★☆ |
| 数字签名/API | 各平台自定义 | Catena-X、Ouranos、集中式平台 | ★★★★☆ |
| 区块链/IOTA | 各链协议 | Orobo、Circularise、Peer Ledger | ★★★☆☆ |

### 11.4 互操作性挑战

全球DPP互操作性面临的核心挑战：
1. **标识符不统一**：多种标识符语法并存，需要解析器层
2. **数据模型差异**：欧盟ESPR、UNEP DPIS、UNTP各有数据分类方式
3. **信任机制不同**：集中式vs去中心化、VC证书vs数字签名
4. **治理模式不同**：政府监管驱动vs行业联盟vs联合国框架

---

## 十二、对DPP-CQ标准的启示与建议

### 12.1 全球定位建议

**定位：亚洲DPP基础设施 + 全球互操作桥梁**

基于全球格局分析，DPP-CQ应定位为：
- **中国DPP的国家标准载体**：服务国内双循环和产业升级
- **亚洲DPP的对接枢纽**：连接日本Ouranos、韩国DPP生态、新加坡平台、澳大利亚AATP
- **全球DPP的互操作节点**：与欧盟EN 18xxx、ISO/IEC JTC 5、UNTP、UNEP DPIS四大框架对接

### 12.2 差异化优势方向

1. **供应链深度**：中国拥有全球最完整的制造业供应链，DPP-CQ可在供应链上游数据采集（如原材料、零部件）方面构建深度优势
2. **多标准兼容**：支持GS1 Digital Link、W3C VC、IEC 61406等多种国际标准，提供"一次接入、多标准输出"能力
3. **产业落地速度**：依托中国制造业规模和数字化转型速度，DPP-CQ可在实际落地场景数量上形成优势
4. **新兴市场合作**：与印度、东南亚、拉美等新兴市场的DPP能力建设合作，输出标准和技术

### 12.3 关键行动建议

| 优先级 | 行动 | 依据 |
|--------|------|------|
| 🔴 高 | 密切跟踪ISO/IEC JTC 5进展，争取深度参与 | JTC 5是全球DPP标准最高平台，首次会议2026年9月召开 |
| 🔴 高 | 确保与EN 18219标识符标准兼容 | EN 18219是欧盟ESPR推定合规标准，出口企业必备 |
| 🔴 高 | 建立与日本Ouranos/ABtC的技术对话机制 | 日本在汽车/电池DPP走在前列，中日供应链紧密 |
| 🟡 中 | 研究UNTP/VC架构的兼容性 | 澳大利亚AATP等多国实践基于UNTP，去中心化架构有长期优势 |
| 🟡 中 | 关注韩国DPP进展，探索中韩DPP互操作 | 中韩电池/电子供应链深度交织 |
| 🟡 中 | 参与UNEP DPIS框架，贡献中国经验 | 发展中国家平台，提升国际话语权 |
| 🟢 低 | 跟踪英国DPP立法进程 | 英国制度尚未定型，有窗口期 |
| 🟢 低 | 探索与新加坡Orobo等平台的合作 | 东南亚区域枢纽作用 |

---

## 附录：信息来源说明

本报告所有事实陈述均标注了信息来源URL，主要来源类型包括：
- 政府/官方机构：FDA、FCC、METI、澳大利亚农业部、UK Legislation、ISO、UNECE、W3C、UNEP
- 行业组织：ANSI、GS1、Standards Australia
- 企业官网：DENSO、Glassdome、Orobo
- 研究机构/咨询：KIAT、CRS、Tilkal
- 专业媒体：Digital Today、Circular Economy Tokyo

标注 [INFO_GAP] 的内容表示缺乏权威来源确认，仅作提示性陈述。

---

*报告完成日期：2026年9月7日*
*调研证据文件：`non_eu_dpp_evidence.md`*
