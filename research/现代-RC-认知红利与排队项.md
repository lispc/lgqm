# 现代-RC：认知红利（零设备现代思想）与排队项（条件成熟后启用）调研笔记

> 调研日期：2026-08-19。方法：WebSearch + 少量 FetchURL；未抓取付费墙文献，以公开摘要/教科书 PDF/综述为准。
> 确定度标签：**【一手文献】**＝原始论文/当事人报告/官方报告的明确出处；**【教科书/综述】**＝教科书、行业综述、权威机构回顾；**【存疑未证】**＝只找到弱来源或二手转述，数字/年代需复核。找不到的明确写"未找到"。
> 本文按任务书 5 个问题组织：Q1 SPC/DOE 与良率工程；Q2 设计侧认知红利；Q3 工艺仿真 TCAD；Q4 排队项逐项评估；Q5 反面清单（隐藏前置链）。

## 核心结论速览

- SPC（1924/1931）、DOE（1935/1951）、田口方法（1950s 日本成型）全部是**纸笔＋台式计算尺/手摇计算机级别**的方法论，对架空世界零门槛；半导体业历史上迟至 1970s 末–1980s 才系统采用，此前良率爬坡靠经验调试＋失效分析。【教科书/综述】
- 量化收益的最佳历史代理证据：1980 年 HP 对美日 16K DRAM 的对比测试——**美国最好厂商的失效率是日本最差厂商的 6 倍**（30 万颗样本）；摩托罗拉 6σ（1986 起）宣称 4 年节省 22 亿美元、缺陷以 ppm 计。【一手文献】（HP/OTA 报告原文）
- 良率模型：Poisson（1960 前后，小芯片）→ Murphy 1964（Proc. IEEE 52:1537，缺陷密度非均匀的首个复合 Poisson 模型）→ Seeds 1967 → Stapper 负二项模型（1973–76，簇生缺陷/大芯片最准）。全部是纸笔公式。【一手文献】
- DRAM 冗余行/列修复：概念 1978（Schuster）、64K DRAM 实现 1979（Cenker，熔丝）、激光修复 1981（JSSC）。冗余使存储器在同等缺陷密度下比逻辑多容纳约两个数量级的晶体管。【一手文献】
- Mead-Conway λ 设计规则（1980）是纯方法论革命：用无量纲 λ 解耦工艺与设计，此前的设计规则是各厂保密的绝对微米数。对架空世界可直接"第一天就用"，代价是版图密度偏保守——对 5–10 µm 早期节点无所谓。【教科书/综述】
- TCAD：SUPREM（斯坦福 1977 起，1D）、SEDAN（器件仿真）在 1970s 大型机（IBM/370 级，数百 KB 内存）上即可运行；"仿真压缩实验次数"的飞轮历史上 1980s 启动。【教科书/综述】
- 排队项落地条件：**MCZ 常规电磁铁即可**（0.1–0.4 T，超导非必需，功耗数十 kW 级）；电子束制版需要 HeNe 激光干涉仪工作台（排队项套排队项）；红宝石激光器是全场最低门槛（焰熔红宝石 1902 ＋ 照相氙灯）；HeNe 激光器卡在超纯气体充填与 ZnS/MgF₂ 介质膜工艺；全息术依赖激光，对掩模检测的价值【存疑未证】，干涉计量才是真红利。
- 反面清单：化学放大胶（ppb 级胺控制）、浸没光刻（mK 级水温＋气泡）、CMP（纳米磨料＋终点检测）等详见 Q5。

---

# Q1. SPC/DOE 在半导体良率中的应用史

## 1.1 方法论各自的年代与原始文本

| 方法 | 年代 | 原始文本/出处 | 确定度 |
|------|------|--------------|--------|
| SPC 控制图 | 1924（Shewhart 在贝尔实验室/西方电气提出控制图备忘录） | 1931 年专著 *Economic Control of Quality of Manufactured Product*（Van Nostrand） | 【教科书/综述】[1][2] |
| DOE | Fisher 在 Rothamsted 农业试验站发展（1920s） | *Statistical Methods for Research Workers*（1925）；*The Design of Experiments*（1935，Oliver & Boyd，爱丁堡） | 【一手文献】[3] |
| 部分因子设计 | 1946 | Plackett & Burman, "The design of optimum multifactorial experiments", *Biometrika* 33:305–325 | 【一手文献】[4] |
| 响应曲面法（RSM） | 1951 | Box & Wilson, "On the experimental attainment of optimum conditions", *JRSS-B* 13:1–45 | 【一手文献】[4][5] |
| 田口方法 | 1950s 末起源（田口玄一在日本电电公社 ECL），1970s 中在日本成型为"品质工学"；1980 年由田口本人访美引入美国，1980s 经 Ford/AT&T/Xerox 扩散 | Taguchi (1987) 等 | 【教科书/综述】[6][7][8] |

要点：Shewhart 的核心概念是"assignable-cause vs chance-cause"变差与控制图判别；Fisher 的核心是随机化、重复、区组；Box-Wilson 给出用序贯实验逼近工艺最优点的范式。这些全部只需要：测量数据记录、算术、方差分析表——**17 世纪数学基础上，培训过的归化民计算员用纸笔即可完成**（ANOVA 手算在 1930s 农业试验站就是常态）。

[1] https://www.euroqual.pub.ro/a-century-of-modern-quality/ （Shewhart 1924 控制图、1931 专著）
[2] https://pdfcoffee.com/the-certified-quality-engineer-handbook-fourth-edition-10-pdf-free.html （ASQ 手册年表：1931 Shewhart 专著；1932–33 英纺织业/德化工业开始用 DOE）
[3] https://repository.rothamsted.ac.uk/id/eprint/23493/1/Yates-1963-Ronald-aylmer-fisher--.pdf （Yates 1963 讣告：1935 年《实验设计》是该主题第一部专著）
[4] https://www.iapsam.org/PSAM16/papers/MA19-PSAM16.pdf （参考文献列出 Fisher 1935、Plackett-Burman 1946、Box-Wilson 1951 完整出处）
[5] https://gmpua.com/Process/EncyclopediaPT.pdf （制药技术百科：Box-Wilson 1951 响应曲面法原始出处）
[6] https://engineering.esteco.com/blog/quality-engineering-taguchi-framework/ （田口方法 1950s 末起源，1970s 中在日本成型）
[7] https://elearning.unite.it/pluginfile.php/221606/mod_resource/content/1/BookDOEwithR.pdf （田口 1980 年将其方法介绍到美国）
[8] https://link.springer.com/content/pdf/10.1007/978-1-4684-1472-1.pdf （*Quality Control, Robust Design, and the Taguchi Method*，含田口 1949–1964 著作系列）

## 1.2 半导体行业何时系统使用 SPC/DOE；之前靠什么

- **时间线判断：美国半导体业系统采用 SPC/DOE 在 1970s 末–1980s**，直接触发是日本 DRAM 的质量冲击。标志物：1980 年 HP 对比测试公开（见 1.5）；1980 年田口方法入美；摩托罗拉 1986 年发起 6σ；1987 年 SEMATECH 成立（其方法论核心即统计制程管制与缺陷学习）。【教科书/综述】[9][10]
- 支撑叙述：质量史学者 Michel Baudin 回忆，1981 年前后才出现以良率提升为目标的 MES（制造执行系统）尝试——即"数据驱动的良率管理"本身是 1980s 初的新鲜事物。【教科书/综述】[9]
- **之前靠什么**：经验调试（"art of process tuning"）＋ 失效分析（切片、染色、显微观察）＋ 老师傅直觉。良率学习曲线模型文献（Tirkel 2013 综述；Maly 讲义）把良率爬坡描述为"缺陷侦测→纠正措施→缺陷密度下降"的循环，早期这个循环没有统计工具，纯靠试片与失效分析排障。【教科书/综述】[10][11][12]
- 反面参照：日本厂商（NEC、东芝、日立等）自 1950s 起接受 Deming 流统计品质管理，1960s 起 QCC/全公司品管，到 1970s 末其 DRAM 失效率已显著低于美国同行——同样的 Mostek 设计、同样的设备代际，差距主要来自制造纪律与统计方法。【一手文献】[13][14]

[9] https://michelbaudin.com/2025/08/27/quality-and-me-part-i-semiconductors/ （1981 年 MES 与良率管理）
[10] https://cris.bgu.ac.il/en/publications/yield-learning-curve-models-in-semiconductor-manufacturing/ （良率学习曲线综述条目）
[11] http://users.ece.cmu.edu/~maly/maly/YieldLearning.pdf （CMU 讲义：良率学习=制造+失效分析的循环）
[12] https://madoc.bib.uni-mannheim.de/63413/1/Dissertation_Johannes_Finale_Druckversion.pdf （学习曲线文献史：Wright 1936 → Yelle 1979 → Tirkel 2013 半导体良率学习曲线综述）
[13] https://www.princeton.edu/~ota/disk3/1983/8314/831409.PDF （美国国会 OTA 1983 报告：1979 年底 HP 的美国供应商质量水平远逊日本厂商）
[14] https://www.princeton.edu/~ota/disk2/1990/9007/900711.PDF （OTA 1990：日本 16K DRAM 失效率远低于美国厂商——尽管几乎全部源自同一 Mostek 设计；美国厂商花了数年才追平）

## 1.3 良率模型史与适用场景

| 模型 | 年代/出处 | 公式（D=缺陷密度，A=芯片面积） | 适用场景 | 确定度 |
|------|-----------|------------------------------|----------|--------|
| Poisson | ~1960 起用（行业默认，无单一首创者） | Y = exp(−AD) | 缺陷均匀随机分布、小芯片；形式最简单 | 【教科书/综述】[15] |
| Murphy | 1964, *Proc. IEEE* 52(12):1537–1545, "Cost-size optima of monolithic integrated circuits" | 对缺陷密度的三角分布作复合（首个"复合 Poisson"），Y = [(1−e^(−AD))/AD]² | 考虑缺陷密度片内非均匀；中等芯片 | 【一手文献】[16][17] |
| Seeds | 1967, *IEEE Int. Conv. Rec.* part 6, pp.61–66, "Yield, economic, and logistic models for complex digital arrays" | D 取指数分布 → Y = 1/(1+AD)（Seeds 模型的常见形式） | 高缺陷密度情形比 Poisson 宽松 | 【一手文献】[17] |
| Okabe–Nagata–Shimada | 1972, *Electr. Eng. Jpn.* 92 | 新产线/经验式 | 日本产线实证 | 【一手文献】[17] |
| Stapper 负二项 | 1973–1976（IBM；Defect density distribution for LSI yield calculations, *IEEE Trans. ED*） | Y = (1 + AD/α)^(−α)，α 为簇生参数 | **缺陷簇生（clustering）＋大芯片**，最贴近量产实测；α→∞ 退化为 Poisson | 【一手文献】[17][18] |
| Bose-Einstein | 代工厂常用（等价于 Seeds 形式推广） | Y = 1/(1+AD) 族 | 大芯片代工惯例 | 【教科书/综述】[15] |

选择经验法则（代工厂实践）：小芯片用 Poisson（简单）；大芯片用 Murphy 三角分布或 Bose-Einstein；有簇生数据时用负二项拟合 α。【教科书/综述】[15]
综述入口：Cunningham 1990, "The use and evaluation of yield models in integrated circuit manufacturing", *IEEE Trans. Semiconductor Manufacturing* 3:60–71。【一手文献】[19]

[15] https://www.viksnewsletter.com/p/how-foundries-calculate-die-yield （代工厂良率模型选用实践）
[16] https://asmedigitalcollection.asme.org/electronicpackaging/article/117/2/159/404144/On-Murphy-s-Integrated-Circuit-Yield-Integral （Murphy 1964 原文信息）
[17] https://arxiv.org/pdf/physics/0303039 （统计良率建模综述，列 Murphy 1964 / Seeds 1967 / Okabe 1972 / Stapper 完整出处；明确 Murphy 引入复合 Poisson 以处理缺陷簇生）
[18] https://www.sciencedirect.com/science/article/pii/S0026271405001617 （负二项模型用于偏离均匀分布的缺陷）
[19] https://link.springer.com/article/10.1007/s00170-004-2382-2 （引 Cunningham 1990 完整出处）

## 1.4 缺陷密度管理：分类学、kill ratio、冗余设计

- **缺陷分类学**（教科书共识）：点缺陷（颗粒沾污造成短路/断路）、线缺陷（划伤）、针孔（氧化层 pinhole）、位错与层错（晶体缺陷）、图形缺陷（光刻桥连/缺口）、系统缺陷（掩模版缺陷在每片重复出现）。【教科书/综述】（通用教科书知识，未单列特定 URL；可参 [12] 与 [20]）
- **kill ratio（杀伤率）**：并非每个物理缺陷都杀死电路——只有落在"关键面积（critical area）"上的缺陷才造成失效。良率模型中的有效缺陷密度 = 物理缺陷密度 × kill ratio。关键面积分析是 Murphy/Stapper 传统的延伸。【教科书/综述】[20]
- **冗余设计（DRAM 修复）时间线**【一手文献】：
  - 1978：S. E. Schuster, "Multiple word/bit line redundancy for semiconductor memories", *IEEE JSSC* SC-13 —— 多字线/位线冗余概念。[21]
  - 1979：R. P. Cenker et al., "A fault-tolerant 64 K dynamic RAM", *IEEE Trans. ED* ED-26:853–860 —— 贝尔实验室 64K DRAM，多晶硅熔丝重连。[21]
  - 1980：Fitzgerald & Thoma, IBM *J. Res. Develop.* 24:291–298 —— RAM 熔丝冗余地址的电路实现。[21]
  - 1981：Smith/Mantz et al., "Laser Programmable Redundancy and Yield Improvement in a 64K DRAM", *JSSC* —— 激光熔断修复。[22]
  - 1985：J. R. Day, 冗余分配算法（fault-driven redundancy algorithm）。[21]
  - 概念起源口述史：Dennard（IBM）回忆其团队在 DRAM 研发中提出位线/字线冗余＋熔丝重连的动机——"这么多晶体管，一个缺陷就废片"。【一手文献】[23]
- 冗余的收益量级：带冗余的 DRAM 设计可以在良率开始崩塌之前比逻辑芯片（如 MPU）多容纳约**两个数量级**的晶体管（1995 年最大存储芯片 >10⁹ 晶体管 vs 最大 MPU <10⁷）。【教科书/综述】[24]
- 激光修复用 Nd:YAG（1.06 µm）是历史主流；红宝石 694 nm 对硅吸收强、易造成衬底损伤——架空世界若用红宝石激光做修复需验证参数窗口。【存疑未证】（YAG 主流为教科书共识；红宝石用于熔丝修复的具体文献未找到）

[20] https://www.kla.com/documents/01_ProcessWatchAutomotive_2018_01.pdf （KLA：良率曲线与缺陷密度管理）
[21] https://web.sfc.keio.ac.jp/~takefuji/publications/pdf/sparecell.pdf （冗余文献引用链：Schuster 1978 / Cenker 1979 / Fitzgerald 1980 / Day 1985）
[22] https://arxiv.org/html/2306.17061v4 （引 Mantz, "Laser Programmable Redundancy and Yield Improvement in a 64K DRAM", JSSC 1981）
[23] https://archive.computerhistory.org/resources/access/text/2012/05/102702124-05-01-acc.pdf （CHM 口述史：Dennard 谈位线/字线冗余与熔丝重连的由来）
[24] https://www.eecg.utoronto.ca/~stumm/Theses/Elliott-PhD98.pdf （冗余使 DRAM 比逻辑多容纳约两个数量级晶体管）

## 1.5 关键问题："第一天就用 SPC/DOE 建厂，能比历史快多少"

**找不到直接回答该反事实的量化文献**（没有哪家厂做过"有/无 SPC"的对照实验）。可用的历史代理证据（【一手文献】为主）：

1. **HP 1980 年 DRAM 对比测试**（Richard Anderson / HP 数据，经 OTA 报告固化）：测试 3 家美国＋3 家日本厂商的 16K DRAM（累计 30 万颗），结论是"**美国最好厂商的失效率是日本最差厂商的 6 倍**"。日本优势主要来自统计品质管理传统而非设备代差（双方设备同源、设计同源 Mostek）。→ 代理估计：制造方法论差异可在**同代设备上**造成 ≥6 倍的现场失效率差距。[25][26][13][14]
2. **摩托罗拉 6σ**：1986 年由 Bill Smith 发起、Mikel Harry 建实施体系；从 4σ 提升到 5.5σ，官方口径**4 年节省 22 亿美元**（15 年 160 亿美元），缺陷以 3.4 ppm 为目标。注意这是全公司口径，非纯半导体晶圆厂数据。【一手文献/公司口径】[27][28]
3. **良率学习曲线的形态**（教科书共识）：新产线良率爬坡呈三阶段——初期快速纠正致命缺陷、中期缺陷密度持续下降、后期平台期；量产 DRAM 代际间缺陷密度持续下降是行业常态。具体的"斜率量化值"（如每月缺陷密度下降 %）**未找到可靠公开数字**——各厂保密，公开文献只有模型没有全行业统计。【存疑未证】[11][12]
4. 日本 64K/128K/256K DRAM 连续三代在量产时点领先美国（1981/1983/…），与 SQC 体系的代差吻合。【教科书/综述】[29]

**推演判断**（本仓库自评，非文献结论）：SPC/DOE 的真正杠杆不在"良率天花板"而在"爬坡速度"——DOE 把工艺窗口寻优从单因子轮换（每次实验只动一个变量、数月摸索一个工序）变成因子设计（一次 8–16 片实验片确定 5–7 个因子的主效应与交互），实验效率提升一个数量级是文献常识级结论；叠加控制图把"异常批次"从月检提前到天检。对架空世界，合理的设定是：**良率爬坡时间压缩到历史的 1/3–1/2**，天花板不变（天花板由设备/材料物理决定）。【推演】

[25] https://fass.nus.edu.sg/gpn/wp-content/uploads/sites/31/2020/09/Shin-Jang-sup_GPN2015_001.pdf （引 1980 HP 评估："the parts that came from the very best American firm showed six times as many [failures as the worst Japanese]"）
[26] https://osuva.uwasa.fi/server/api/core/bitstreams/44b32313-1b6e-4a9c-a522-c94c0be5b913/content （Garvin 1998：HP 检验 30 万颗 RAM 芯片后管理层震动）
[27] https://vtechworks.lib.vt.edu/server/api/core/bitstreams/da5e90ed-d8da-4ac8-bce5-cb124b28fea9/content （摩托罗拉 4σ→5.5σ 节省 22 亿美元）
[28] https://lssa.eu/en/history-of-six-sigma/ （4 年 22 亿、15 年 160 亿美元；Bill Smith/Mikel Harry 1986）
[29] https://www.hpmemoryproject.org/timeline/art_fong/chuck_house_thoughts.htm （HP 内部回顾：日本 64K 1981、128K 1983 连续领先）

---

# Q2. 设计侧认知红利

## 2.1 λ 设计规则（Mead-Conway 1980）

- 原始文本：Carver Mead & Lynn Conway, *Introduction to VLSI Systems*, Addison-Wesley, 1980。核心：把所有版图几何规则（最小线宽、间距、包围、交叠）表达为单一无量纲单位 **λ** 的整数/半整数倍（λ ≈ 工艺半节距/最小特征尺寸）。【一手文献】（书目信息）[30][31]
- 此前的世界：设计规则是各厂保密的、以绝对微米书写的厚厚手册，设计师与工艺线深度绑定，设计公司（fabless）概念不存在，跨厂移植设计等于重画。【教科书/综述】[31][32]
- λ 规则的本质：**用无量纲单位把"工艺演进"与"设计资产"解耦**——工艺换代时只要重新定义 λ 的物理值，版图按比例缩放即可沿用；同时它把设计规则简化为可在课堂教授的有限条数，配合 MOSIS（1981 起，DARPA 资助的多项目晶圆服务）催生了 fabless/代工生态与 EDA 产业。【教科书/综述】[30][32][33]
- 代价（对架空世界重要）：λ 规则是"最大公约数"式的保守规则，牺牲版图密度（估计比厂内定制规则浪费 10–30% 面积——**此具体数字未找到文献，存疑**）；且 λ 规则适用于等比例缩放的数字 MOS，对双极/模拟/高压不适用。【存疑未证】（密度惩罚量级）
- **架空适用性判断【推演】**：零设备门槛。第一天就可建立 λ 规则体系；5–10 µm 节点密度惩罚无关紧要；且架空世界没有"跨厂移植"需求，λ 规则的最大历史价值（解耦代工与设计）打折扣——但"规则条数有限、可教学、可写成检查表"这一面仍然值钱，直接服务归化民设计员的批量培训。

[30] https://arxiv.org/html/2606.17899v1 （EDA 史综述：Mead-Conway 1980 是 VLSI 设计范式转折点）
[31] https://computerhistory.org/profile/lynn-conway/ （CHM Lynn Conway 档案）
[32] https://ai.eecs.umich.edu/people/conway/Impact/FundingaRevolution.html （NAP《Funding a Revolution》节选：Mead-Conway 方法论与 MOSIS 的影响）
[33] https://www.computerworld.com/article/1569500/unsung-innovators-lynn-conway-and-carver-mead.html （Mead-Conway 革命回顾）

## 2.2 标准单元库 / PDK / DRC / LVS

- 门阵列（gate array）：1970s 已有（预定扩散层＋定制金属层）；**标准单元法（standard cell）作为主流 ASIC 方法在 1980s 初成型**（LSI Logic 1980–81 等）；PDK（工艺设计套件）作为"厂方交付给设计方的标准化数据包"概念是 1990s 产物。【教科书/综述】[34]（具体年份颗粒度较粗，存疑部分已注明）
- DRC（设计规则检查）：把设计规则写成可执行的布尔几何运算，人工检查也可用"规则检查表＋坐标纸/红蓝图"完成——λ 规则使 DRC 条目有限且无量纲，**手算 DRC 在低集成度下可行**（数千晶体管版图、规则 ~20 条）。【推演】
- LVS（版图 vs 原理图一致性检查）：概念随版图 CAD 出现（1970s 末）；低集成度下可用"节点标注法"人工核对。【教科书/综述】（具体首创文献未找到——**DRC/LVS 的精确首创年份未找到可靠出处**）【存疑未证】
- 对架空世界：标准单元库思想（预设计、预表征、可复用的门/触发器单元＋时序/功耗表征卡片）是纯组织性红利，第一块门阵列之前就该建好。【推演】

[34] https://huluic.com/page/standard-cell-library （标准单元库概念概述）

## 2.3 冗余与容错设计：Hamming 码与 ECC 内存

- Hamming 码：R. W. Hamming, "Error Detecting and Error Correcting Codes", *Bell System Technical Journal* 29(2):147–160, **1950**。动机：继电器计算机读卡不可靠，周末算题被迫重算。【一手文献】[35][36]
- ECC 内存首次工程应用：**IBM Stretch（7030，1961）是 IBM 第一台使用 Hamming 码的计算机**（SECDED，单纠错双检错）。【教科书/综述】[37]
- 架空适用性：零门槛。存储器位宽 +log₂ 位即可 SECDED（64 位数据 +8 校验位）；对早期低良率存储器，ECC 同时是**可靠性手段和良率手段**（容忍单比特失效的芯片仍可出厂）。【推演】

[35] https://yiweimao.github.io/blog/hamming/ （Hamming 1950 BSTJ 完整出处）
[36] https://robotics.shanghaitech.edu.cn/courses/ca/20s/lectures/2020-CA-L28_Dependability.pdf （Hamming 码背景与出处）
[37] https://zzzchan.xyz/file/f89446c3655975af750b964c70bb8fbeb0567a970a62032f9f9139d00f0523c0.pdf （Hacker's Delight 2nd ed.：IBM Stretch 是 IBM 首台使用 Hamming 码的计算机）

## 2.4 可测试性设计（DFT）：扫描链 / LSSD

- 原始文本：E. B. Eichelberger & T. W. Williams, "A logic design structure for LSI testability", *Proc. 14th Design Automation Conference*, pp.462–468, **1977**（IBM LSSD，Level-Sensitive Scan Design）；Eichelberger 1973 年已因 LSSD 获 IBM 杰出贡献奖，说明技术开发在 1970s 初。【一手文献】[38][39]
- 综述入口：T. W. Williams & K. P. Parker, "Design for testability: a survey", *Proc. IEEE* 71(1):98–112, 1983。【一手文献】[40]
- 思想内核：把所有触发器在测试模式下串成移位寄存器（扫描链），使时序电路测试退化为组合电路测试——可控制性/可观测性问题的方法论解。【教科书/综述】[41]
- 架空适用性：零门槛（代价是 5–15% 面积开销与少量 I/O 引脚）；在早期良率低下、测试向量靠手算的世界里，扫描链把测试生成复杂度降一个数量级，值得第一代 MPU 级芯片就引入。【推演】

[38] https://dl.acm.org/doi/abs/10.5555/2821565 （VLSI Test Principles 参考文献：Eichelberger & Williams, DAC 1977, pp.462–468）
[39] http://bitsavers.informatik.uni-stuttgart.de/pdf/ibm/IBM_Journal_of_Research_and_Development/273/ibmrd2703H.pdf （Eichelberger 1973 年因 LSSD 获 IBM 杰出贡献奖）
[40] https://dl.acm.org/doi/abs/10.5555/2821565 （同上条目引 Williams & Parker 1983 Proc. IEEE 综述）
[41] https://ntrs.nasa.gov/api/citations/19890010087/downloads/19890010087.pdf （NASA 报告：结构化 DFT 分类，LSSD 居首）

---

# Q3. 工艺仿真（TCAD）：SUPREM 与 SEDAN

## 3.1 诞生年代与谱系

- 解析模型的史前：Deal-Grove 氧化模型（1965）、Fick 扩散解析解——手算/计算尺时代即可用，本身就是最早的"工艺仿真"。【教科书/综述】
- **SUPREM**（Stanford University Process Engineering Models）：斯坦福 Robert Dutton 组。**SUPREM I 1977 年（1D）**；SUPREM II 1978（Antoniadis, Hansen, Dutton，斯坦福电子实验室技术报告）；SUPREM III ~1980；SUPREM IV 2D（1980s 中）；商业化后裔 TSUPREM-4（TMA，后 Synopsys）。【教科书/综述】[42][43][44]
- **SEDAN**（SEmiconductor Device ANalysis）：斯坦福 1D 器件仿真器；SEDAN III 技术报告 Z. Yu & R. W. Dutton, 1985。更早的器件仿真：De Mari 1968（首个 1D 数值器件仿真）、Scharfetter-Gummel 1969（2D 大信号）。【教科书/综述】[45][46]
- 并行线：SPICE（Nagel, UC Berkeley, ERL-M520, 1975）——电路仿真，同样 1970s 大型机产物。【一手文献】[47]

[42] https://www.warse.org/IJETER/static/pdf/file/ijeter01642018.pdf （SUPREM 1977 年始于斯坦福，1D）
[43] https://era.ed.ac.uk/bitstream/handle/1842/12182/Duncan1994.pdf?sequence=1&isAllowed=y （引 Antoniadis, Hansen, Dutton, "SUPREM II – A Program for IC Process Modelling and Simulation", Stanford 技术报告）
[44] https://www.iue.tuwien.ac.at/phd/minixhofer/node22.html （TSUPREM-4 是斯坦福 SUPREM-4 的后裔）
[45] https://www2.eecs.berkeley.edu/Pubs/TechRpts/1993/ERL-93-51.pdf （引 Yu & Dutton, "SEDAN III – a general purpose one-dimensional semiconductor analysis program", Stanford ICL 技术报告, 1985-07）
[46] http://thesis.univ-biskra.dz/3894/1/KHADIR-Abdelkader-Thesis-final.pdf （仿真史：De Mari 首个 1D、Scharfetter 2D；SUPREM 与 SEDAN 是仿真开端）
[47] https://link.springer.com/chapter/10.1007/978-1-4615-3208-8_1 （引 Nagel, "SPICE 2", ERL-M520, UC Berkeley, 1975-05）

## 3.2 算力需求与"飞轮"启动时点

- SUPREM I/II 是 1D 程序（杂质再分布、氧化、注入的数值积分），FORTRAN 编写，跑在 1970s 大型机上；同期同类仿真程序的内存需求量级为**数百 KB**（旁证：1977 年 WSC 论文报告某大型仿真在 IBM 360/75–91 上核心需求 150 KB）。"1960s 大型机即可跑早期 SUPREM"——**方向正确但未找到 SUPREM 具体 CPU/内存数值的一手数据**。【存疑未证】（精确算力数字）[48]
- 定性判断【教科书/综述】：1D 工艺仿真的计算量（百级网格 × 数十时间步的抛物型 PDE）对 1960s 中后期的晶体管大型机（甚至架空世界第一代硅 MPU 级机器）是轻负载；真正的算力墙在 2D 器件仿真（PISCES 级，1980s 小型机/工作站）。
- **飞轮何时启动**：文献表述——仿真让设计者"无需多次流片分批实验即可廉价地优化器件与模型"【教科书/综述】[49]。斯坦福 SUPREM 项目 1977 启动，产业界 TCAD 组 1980s 中普及（Intel/TI/IBM 内部 TCAD 组），商业 TCAD（TMA SUPREM-IV/PISCES）1980s 后半，1990s 成为流片前标配。【教科书/综述】[50]
- 架空含义【推演】：飞轮可以在架空世界"第一台可用计算机＋第一条工艺线并存"的时刻就启动——比历史提前的原因是方法论（SUPREM 的模型方程：Fick 定律＋点缺陷动力学）本身可以**纸笔推导好等着算力**，且架空世界知道哪些模型值得编（历史花了 10 年试错）。

[48] https://informs-sim.org/wsc77papers/1977_0072.pdf （旁证：1977 年 FORTRAN IV 仿真程序在 IBM/360/75-91 上核心需求 150 KB）
[49] https://carleton.scholaris.ca/server/api/core/bitstreams/5b389014-dcbc-45e5-955d-791ce5a47f44/content （"cheaply optimize and model devices without needing to do split or multiple fabrication runs"；SUPREM 谱系）
[50] https://profiles.stanford.edu/jim-plummer （Plummer-Dutton 合作发展多代 SUPREM，成为全球标准工艺建模工具）

---

# Q4. 排队项评估（最早可能落地条件）

## 4.1 磁拉单晶（MCZ）

- 历史：Hoshi 等 1980 年前后首次报道横向磁场 CZ 硅生长（抑制熔体对流的概念更早用于 InSb）；1980 起发展出纵场（VMCZ）、横场（HMCZ）、Cusp 场三类。【教科书/综述】[51][52]
- **磁场强度**：横场 MCZ 典型 0.1–0.4 T（1000–4000 G）；NASA 1985 年研讨会记录轴向场 5500 G（0.55 T）实验。任务书给的 0.1–0.4 T 区间与文献一致。【教科书/综述】[52][53]
- **常规电磁铁即可，不必超导**：现代超导磁体相对电阻式铜线磁体的卖点是功耗约 1/10——这本身就说明电阻式方案在工程上可行（只是费电）；1980s 早期 MCZ 用的就是常规电磁铁。【教科书/综述】[54]（"1980s 早期用常规电磁铁"一句为常识级表述，未找到逐字一手出处，标【存疑未证】）
- 功耗量级：大型磁体铜线圈水冷方案数十至上百 kW 级（旁证：GSI 类似口径磁体单台 70 kW、水冷）。【教科书/综述】[55]
- 改善数据：氧含量可在 2–20 ppm 范围受控、径向均匀性改善（商业页面，弱来源）【存疑未证】[56]；Cusp 场实验显示**晶体氧含量约减半**、电阻率轴向均匀性改善【一手文献/会议论文】[54]；横场抑制垂直方向熔体流动、消除杂质条纹【教科书/综述】[52]。
- **最早落地条件【推演】**：直拉炉（已排队）＋ 大型稳定直流电源（数十 kW 级，纹波要求不高）＋ 水冷铜线圈电磁铁＋高斯计（霍尔片需半导体，可用磁强计/翻转线圈替代）。不需要超导、不需要低温。对架空世界：电力和电工水平到位即可，**估计与 4–6 英寸直拉扩产同期**。

[51] https://pdfcoffee.com/handbook-of-semiconductor-manufacturing-2nd-edition-pdf-free.html （《半导体制造技术手册》第 2 版：Hoshi et al. 首报横场 CZ；MCZ 用于低氧、低微缺陷、高阻硅）
[52] https://www.mdpi.com/2079-6412/13/9/1634 （MCZ 1980 起；VMCZ/HMCZ/Cusp 三类；Gauss 计定位零高斯面）
[53] https://ntrs.nasa.gov/api/citations/19860010252/downloads/19860010252.pdf?attachment=true （NASA 1985 研讨会：5500 G 轴向场实验记录）
[54] https://www.pvatepla-cgs.com/fileadmin/user_upload/CGS/Mediathek/pva-cgs-crystal-growing-systems-growth-high-quality-Si-ingots-CUSP-field.pdf （PVA：免液氦超导 Cusp 磁体功耗约为电阻式铜线磁体的 10%；Cusp 场使晶体氧含量约减半、硼轴向分布均匀化）
[55] https://indico.gsi.de/event/2200/attachments/6045/7421/CR_Paramaters_July_2012.pdf （旁证：同类铜线圈水冷磁体 3215 A、70 kW）
[56] https://www.powerwaywafer.com/magnetic-czochralski.html （商业页：MCZ 氧含量可控 2–20 ppm、杂质均匀——弱来源）

## 4.2 电子束曝光制版

- 技术谱系：TEM 1931（Knoll & Ruska）；SEM 概念 1935（Knoll）、STEM 1938（von Ardenne）、RCA 1942（Zworykin/Hillier/Snyder）、**首台商品 SEM：剑桥 Stereoscan 1965（Oatley 组）**；**首次电子束直写演示 1960（Möllenstedt & Speidel，~60 nm 线宽）**；EBL 1960s 作为电子显微学的衍生品出现；1970s 初贝尔实验室等建起第一批机器（EBES，用于掩模制作）。【教科书/综述】[57][58][59][60]
- 历史动因（为什么行业接受了这个慢技术）：光学图形发生器（PG）制一块复杂掩模超过 100 小时，达到实用极限；电子束写掩模/中间版（reticle）成为 1970s 末–80s 的标配。【一手文献/博物馆】[61]
- **直写速度量化**（教科书公式 T = D·A/I）：以 1 cm²、剂量 10⁻³ C/cm²、束流 10 nA（高斯束典型）计 → **10⁵ s ≈ 28 小时/cm²**。现代可变矩形束机器写一块先进门层掩模约 24 小时。→ 1970s 级机器写一块 10× 中间版（~1 cm² 有效图形区）：**数小时到一天量级**，只适合做掩模车间母版，不适合直接写晶圆。【教科书/综述】[62][63]
- 最小可行配置：热钨阴极（发夹式，10⁻⁴–10⁻⁵ Pa 真空）、磁透镜 2–3 级、静电/磁偏转线圈、法拉第杯束流计、**激光干涉仪精密工作台**（图形套刻精度的关键——依赖 HeNe 激光器，排队项套排队项）、图形数据计算机（纸带/磁带输入矢量数据）。【教科书/综述】（配置综合 [57][62]）
- **最早落地条件【推演】**：电子光学（真空＋高压＋磁透镜，1930s 技术）对架空世界可达；卡点排序：① HeNe 激光干涉仪（等 Q4.4）② 稳定高压电源与真空机组 ③ 图形数据处理。落地形态=掩模车间电子束图形发生器，替代光学 PG/精缩机，用于 stepper 中间版直写。

[57] https://eipbn.org/abstracts/2010/papers/1A1.pdf （EIPBN 回顾：Möllenstedt & Speidel 1960 首次电子束书写，60 nm 线宽）
[58] https://www-g.eng.cam.ac.uk/125/achievements/mcmullan/mcm.htm （剑桥：Knoll 1935 → Oatley 组 → Stereoscan 1965）
[59] https://poster.sciencemag.org/sem/ （Science：Knoll 1935 首次扫描成像）
[60] https://www.genisys-gmbh.com/files/daten/pdf/beameeting/BEAMeeting%20Munich%202025/EBL_at_age_65_a_retrospect.pdf （EBL 65 年回顾：1970s 初贝尔实验室等第一批机器、掩模制作）
[61] https://www.shmj.or.jp/english/pdf/em/exhibi2444E.pdf （日本半导体历史馆：光学 PG 制掩模超 100 小时达极限，EB 因高速图形生成成为掩模/中间版制作不可或缺）
[62] https://willson.cm.utexas.edu/Teaching/LithoClass2018/Files/2018-09-27_Adam Ramm_Electron Beam Lithography.pdf （UT Austin 讲义：T = D·A/I；1 cm²、10⁻³ C/cm²、10 nA 的算例）
[63] https://repositories.lib.utexas.edu/server/api/core/bitstreams/564b1c21-0457-4a99-b41a-e066e04fa600/content （现代门层掩模电子束写入约 24 小时/块）

## 4.3 红宝石激光器（Maiman 1960）

- 配置史实：Maiman 1960 年 5 月 16 日在 Hughes 实现首台激光器；增益介质为**合成红宝石棒（Al₂O₃ 掺 ~0.05 wt% Cr₂O₃）**——Verneuil 焰熔法 1902 年即成熟（钟表轴承工业量产）；泵浦源是**摄影用螺旋氙闪光灯**（GE FT-524 型一类，现成商品）；两端镀银膜（一端全反一端半透）。整个装置"低技术"到 Maiman 的总预算约 5 万美元（1960 年币值）。【一手文献/权威回顾】[64][65][66]
- **阈值泵浦能量量级**：红宝石是三能级系统，须把 >50% 的 Cr³⁺ 抽至上能级才能反转，阈值高。教科书参数：中压（~500 Torr）氙闪光灯泵浦、棒径 5–10 mm × 长 5–20 cm；典型小型红宝石激光器**闪光灯电输入阈值在 10²–10³ J/脉冲量级**（ Hughes 测距机级整机输出 50 mJ/脉冲；Q 开关后 MW 级峰值、10 ns 脉宽）。**未找到 Maiman 首台的精确阈值焦耳数一手值**——区间表述标【教科书/综述】，精确值【存疑未证】。[67][68][69]
- Q 开关低技术方案：旋转棱镜（Hughes 测距机用 30000 rpm 电机＋磁拾取触发）或可饱和染料盒——两者对架空世界均可达。【一手文献/修理档案】[70]
- 干涉仪以外的用途：
  - **激光修整电阻（laser trimming）**：1970s 已是混合电路工业标准工艺（薄/厚膜电阻切割调值，精度优于 1%、单点 <1 s；此前用喷砂修整）。【一手文献/期刊扫描】[71][72]
  - 打标/划片（硅片划片、蓝宝石划片）：教科书共识。【教科书/综述】
  - 激光退火：需要 Q 开关巨脉冲或扫描聚焦；用于注入退火是 1970s 末研究热点（红宝石/Nd:YAG）；对架空世界可行性【存疑未证】（能量密度窗口窄、均匀性差，历史上被卤素灯 RTA 取代）。
  - 脉冲全息（Q4.5）与精密干涉计量。
- **最早落地条件【推演】**：焰熔红宝石（已有宝石/轴承工业即具备）＋氙闪光灯（弧光灯/摄影闪光技术）＋镀银/介质膜＋触发脉冲变压器。**全场排队项中门槛最低**，可在电子管时代就实现。

[64] https://opticaorgdev.blob.core.windows.net/$web/optica/media/osa.history/century_of_optics/1960-1974/1960-1974.pdf （Optica 官方世纪光学史：Maiman 计算显示最亮弧灯也只能勉强 CW → 选脉冲；三能级问题）
[65] https://link.springer.com/article/10.1007/s11245-026-10395-5 （Maiman 首台的器件选型：闪光灯是当时摄影用氙灯、红宝石棒来自 Hughes 库存）
[66] https://shop.adhmt.com/the-history-and-evolution-of-laser-welding-machines/ （Maiman 首台预算约 $50,000 的说法——行业博客弱来源，仅作背景）【存疑未证】
[67] https://physics.mff.cuni.cz/kchfo/ooe/lasery/p8.pdf （Svelto《Principles of Lasers》章节 PDF：~500 Torr 氙灯、棒 5–10 mm × 5–20 cm、脉冲运转）
[68] http://www.repairfaq.org/sam/laserpic/hbl1pics.htm （Hughes 测距机红宝石激光器参数：694.3 nm R1 线、最大输出 50 mJ）
[69] https://www.engineeringphysics.weebly.com/uploads/8/2/4/3/8243106/srit__unit_i_laser.pdf （教科书：红宝石激光 MW 级峰值、10 ns 脉宽）
[70] http://www.repairfaq.org/sam/laser/ssltech/rw-mopa-ver5.htm 及 https://www.repairfaq.org/sam/laserscl.new （Q 开关：旋转棱镜 30000 rpm＋SCR 脉冲成形网络；染料 Q 开关）
[71] http://www.bitsavers.org/magazines/EDN/EDN_V15_N19_19701001.pdf （EDN 1970：混合电路电阻修整手段综述——喷砂、激光等）
[72] https://totalelectricaltraining.co.uk/wp-content/uploads/2023/03/The-Electronics-Handbook-Second-Edition-Electrical-Engineering-Handbook-PDFDrive-.pdf （激光修整可优于 1%、<1 s/点、高度自动化）

## 4.4 HeNe 激光器（1960）制造门槛复核

- 史实：Javan、Bennett、Herriott，贝尔实验室，1960 年 12 月，首台连续波激光器，1.15 µm（红外）；632.8 nm 红线 1962（White & Rigden）。【一手文献/博物馆】[73][74]
- 结构细节【教科书/综述】[75][76][77]：
  - 熔融石英放电管，典型 ~80 cm 长 × 1.5 cm 径（早期）；现代小型管 10–50 cm。
  - 充填 He:Ne ≈ 10:1（分压 He ~1 mmHg、Ne ~0.1 mmHg）——**要求分压精确的超高纯气体充填与彻底烘烤除气**。
  - 布儒斯特窗（硼硅玻璃，θ = arctan n）输出线偏振。
  - 外腔镜：**蒸镀多层介质高反膜（ZnS/MgF₂ λ/4 膜堆，~20 层量级）**——需要真空镀膜＋膜厚监控（单波长透射极值监控即可，光电管+单色仪级别）。
  - 金属-玻璃封接保证长期真空密封；冷阴极（铝）直流放电激发（mA 级、~kV 级）。
- 门槛复核结论【推演】：所有子技术（玻璃吹制、真空机组、高纯气体提纯、真空蒸镀、膜厚光学监控、金属-玻璃封接）均为 1950s 以前成熟技术；真正的难点是**工艺纪律**（除气彻底性、氦气提纯除氖/氩、镜片平行度调整——需要另一台干涉仪或自准直仪做调整基准）。历史上 Javan 团队花约两年，主要耗在气体纯度与放电条件摸索——架空世界已知最佳配比与气压，可跳过。
- **最早落地条件【推演】**：真空工业（电子管产业共生）＋光学镀膜＋氦氖气源（空气分馏副产/天然气提氦）。优先级：它是激光干涉仪（光刻机对准、电子束工作台、长度计量）的光源，**应列为排队项第一梯队**。

[73] https://www.si.edu/object/nmah_1339868 （史密森尼馆藏：Javan/Bennett/Herriott 1960 年 12 月演示）
[74] https://www.photonics.com/Articles/Inventing-the-Worlds-First-Continuous-Wave-Laser/a65796 （1960-12 首台 CW 激光，1.15 µm）
[75] http://lib.ysu.am/disciplines_bk/3265771a9c8a7f1d6bdd38cfe47fddc8.pdf （Springer Handbook of Lasers and Optics：HeNe 结构图——玻璃管两端熔接金属端帽、端帽接腔镜、金属-玻璃封接保证真空）
[76] http://hs.griet.ac.in/pdf/studymaterials-gr20/Applied%20Physics%20Theory%202020-21.pdf （教科书：石英管 ~80 cm × 1.5 cm、He:Ne=10:1、He 1 mmHg / Ne 0.1 mmHg、布儒斯特窗 θ=arctan n）
[77] https://teachmint.storage.googleapis.com/public/132843310/StudyMaterial/efa6eeb8-74b4-49fc-a2e9-acfe1a63c33f.pdf （教科书：分压与布儒斯特窗细节）
  - 注：ZnS/MgF₂ 介质膜堆为 1960s HeNe 高反膜的标准材料组合（镀膜教科书共识），本次未检索到逐字来源 URL——【存疑未证】

## 4.5 全息术（Gabor 1948 / Leith 1962）

- 谱系：Gabor 1948 发明（同轴全息，汞灯光源，原为改善电镜分辨率，1971 年诺贝尔奖）；Leith & Upatnieks 1962 离轴全息＋激光光源后实用化。【教科书/综述】[78]
- 技术需求：相干光源（激光；Gabor 时代用滤波汞灯＋极小样品勉强可行）、**高分辨率感光版**（Agfa 8E75/Kodak 649F 级，~3000 lp/mm 卤化银细颗粒乳剂）、隔振台（曝光期间光程稳定 λ/10 级）。
- 对掩模检测/干涉计量的价值评估：
  - **全息掩模检测**：历史上被研究过（全息比对"标准掩模"与"待检掩模"的波前差），但**未成为产业主流**（主流是 die-to-die 光学比对与后来的 SEM 复检）。本次未找到可引用的一手工艺文献——全息用于掩模检测的产业案例【存疑未证】。[79]
  - **真正的低技术红利是经典干涉计量**（不需要全息术）：Twyman-Green/Fizeau 干涉仪检测光学镜头与平面度（掩模基板、晶圆平整度）、激光干涉位移计量——只需 HeNe ＋ 分光镜 ＋ 感光板/光电接收。全息术的增量价值主要是"波前存储比对"（可对复杂形面做无损比对）。【推演】
- **最早落地条件【推演】**：HeNe（Q4.4）＋细颗粒照相乳剂（照相工业可攻关，19 世纪乳剂技术基础上的颗粒细化）＋光学平台隔振（沙箱/气垫均可低技术实现）。优先级低于经典干涉仪。

[78] https://www.frontiersin.org/journals/neuroscience/articles/10.3389/fncom.2026.1833027/full （全息史：Gabor 1948 同轴、为改善电镜；Leith-Upatnieks 激光离轴）
[79] https://www.govinfo.gov/content/pkg/GOVPUB-C13-44ab1dd143ddf4eea9c39c3047dec972/pdf/GOVPUB-C13-44ab1dd143ddf4eea9c39c3047dec972.pdf （NIST 自动掩模检测综述：主流是视觉/尺寸缺陷检测——侧面印证全息非主流）

---

# Q5. 反面清单：看似 low-tech、实则有深前置链的现代技术

## 5.1 化学放大光刻胶（CAR，1982）

- 表面假象：光刻胶配方，化学工业产品，"调出来就能用"。
- 隐藏依赖链：
  1. **深紫外光源**：tBOC 类 CAR 为 248 nm（KrF 准分子激光）或汞灯深紫外设计——准分子激光本身需要闸流管高压快脉冲＋卤素气体处理链。
  2. **环境胺控制**：CAR 对空气中碱性污染物（胺类，来自建材、人员、工艺化学品）敏感，**ppb 量级**即造成 T-top/线宽漂移——需要整个洁净室的活性炭化学过滤新风系统（MacDonald et al., *Chem. Mater.* 5:348, 1993, "Airborne Contamination of a Chemically Amplified Resist"）。【一手文献】[80][81]
  3. **PEB（曝光后烘烤）温控 ±0.1 °C 级**（酸扩散长度对温度极敏感）。【教科书/综述】[82]
  4. 光酸发生剂（PAG）合成与金属离子纯化。
- 原始出处：Ito, Willson, Fréchet 1982（tBOC，VLSI Technology Symp.）；Ito & Willson 1983 *Polym. Eng. Sci.* 23:204。【一手文献】[83][84]

## 5.2 浸没式光刻

- 表面假象："镜头和晶圆之间加一层水，NA 立刻 ×1.44"。
- 隐藏依赖链：超纯水的 **dn/dT 温控**（mK 级温度均匀性，水温波动直接变成焦距漂移）；高速扫描工作台下维持**无气泡水膜**（纳米气泡缺陷）；防水表层（topcoat）与抗水浸胶配方；水的回收循环与颗粒控制；局部浸没头流场工程。【教科书/综述】[85][86][87]

## 5.3 CMP（化学机械抛光）

- 表面假象："晶圆抛光，磨料+转台，1961 年 Monsanto 就在做了"。
- 隐藏依赖链：**胶体二氧化硅磨料的粒径分布与金属纯度控制**（纳米级窄分布、离子交换法制备降 Fe/Ni/Cu）；抛光垫（发泡聚氨酯的孔结构一致性）；**终点检测**（电机电流/摩擦力/光学终点——否则碟形凹陷 dishing 失控）；后 CMP 清洗（磨料残留=致命颗粒）；晶圆级压力均匀性（气膜载头）。【教科书/综述】[88][89]
- 史实锚点：1961 Monsanto Bob Walsh 把光学玻璃抛光移植到裸硅片（胶体硅浆料）；1980s 末 IBM 把 CMP 引入 ILD 平坦化，成为多层金属互连的使能技术。【教科书/综述】[88]

## 5.4 离子注入机

- 表面假象："加速离子打进去，加速器是 1930s 物理"。
- 隐藏依赖链：**同位素级质量分析磁体**（把 N⁺/CO⁺ 与 P⁺ 分开，质量分辨 M/ΔM >100）；高真空束线（10⁻⁵ Pa 级，防电荷交换）；剂量法拉第杯计量与束流均匀性扫描；注入损伤退火配套（RTA 需要卤素灯阵列或石墨加热快速炉）；通道效应控制（晶向偏转 7° 之类的工艺知识）。【教科书/综述】（综合常识，未单列 URL）

## 5.5 EUV 光刻（极端反例，防穿越者心态）

- 表面假象："换一种更短波长的灯"。
- 隐藏依赖链：LPP 光源（CO₂ 激光打锡滴，每秒 5 万发、预脉冲整形）；**Mo/Si 40 对双层反射膜**（每层 ~3.4/4.1 nm、界面粗糙度 <0.1 nm）；全系统真空（EUV 被一切物质吸收）；无缺陷反射式掩模坯。每一项单独都是一个大产业。【教科书/综述】

## 5.6 步进光刻机镜头组

- 表面假象："照相放大镜头，光学工业老手艺"。
- 隐藏依赖链：g/i 线镜头需要熔石英＋特种玻璃的像差校正组合（十几片镜片、衍射极限、大视场）；193 nm 需要 **CaF₂ 晶体**（生长与加工链）；镜筒热稳定与像差在线检测；Zeiss 级装配计量（干涉仪群）。这就是 notes/07 选定 Offner 1:1 反射式路线的历史原因——环形视场反射系统镜片数少、材料门槛低。【教科书/综述】（与 notes/07 结论一致）

[80] https://imicromaterials.com/index.php/technical/duv-photoresist-processing （DUV 胶工艺：空气中胺类导致 CAR 污染问题）
[81] https://www.electrochem.org/dl/interface/spr/spr09/spr09_p37-43.pdf （Willson 荣誉文：列 MacDonald et al., "Airborne Contamination of a Chemically Amplified Resist", Chem. Mater. 5:348, 1993）
[82] https://clara.nz/docs/books/Semiconductor Manufacturing/Optical Lithography: Here is Why, 2nd edition - Burn J. Lin.pdf （Burn Lin 教科书：CAR 酸扩散、PEB 控制、淬灭剂）
[83] https://www.sciencehistory.org/stories/magazine/patterning-the-world-the-rise-of-chemically-amplified-photoresists/ （科学史研究所：Willson/Fréchet/Ito 1982 tBOC 专利）
[84] https://ptacts.uspto.gov/ptacts/public-informations/petitions/1553819/download-documents?artifactId=7vKR14DfRYPJEqIBKfMAwmb_sizD2-4Yvpzw75lKyTF_ddDIBKI0v2o （USPTO 文书：Ito & Willson 1983 Polym. Eng. Sci. 23:204；Ito/Willson/Frechet 1982 完整出处）
[85] https://archive.nptel.ac.in/content/storage2/courses/103105065/M11l14.pdf （NPTEL：浸没光刻工业化障碍——高速工作台＋无气泡液体维持）
[86] https://www.asml.com/company/stories/2023/how-immersion-lithography-saved-moores-law （ASML：气泡与浸没缺陷来源）
[87] https://www.rit.edu/~w-lithography/research/immersion/SPIE_5040_58_immersion.pdf （RIT/SPIE：水的 193 nm 吸收与 dn/dT 温度色散数据）
[88] https://jeez-semicon.com/blog/planarization-in-semiconductor-manufacturing-complete-guide/ （CMP 史：1961 Monsanto Walsh 胶体硅抛光裸片；1980s 末 IBM 引入 ILD）【行业博客，中等可信度】
[89] https://www.jos.ac.cn/en/article/doi/10.1088/1674-4926/25060003 （半导体学报综述：胶体硅磨料粒径/纯度控制史，离子交换法降金属杂质）

---

# 未查到清单（本轮调研留白）

1. SUPREM I/II 的具体 CPU 时间/内存占用一手数据（"1960s 大型机可跑"只有间接旁证）。
2. 行业良率学习曲线斜率的公开量化统计（各厂保密；只有模型文献无全行业数字）。
3. Maiman 首台红宝石激光器的精确阈值泵浦能量（焦耳数）；只有教科书级区间（10²–10³ J 电输入）。
4. HeNe 高反膜"ZnS/MgF₂ 膜堆"的逐字来源（教科书常识，未检索到可引用 URL）。
5. DRC/LVS 工具的精确首创年份与作者（Baker-Terman 1980 常见但未核实到一手出处）。
6. 全息术用于掩模缺陷检测的产业级一手文献（只确认其未成为主流）。
7. λ 规则相对厂内定制规则的版图密度惩罚的量化数据（10–30% 为经验说法，未找到文献）。
8. 红宝石激光替代 Nd:YAG 做 DRAM 熔丝修复的可行性文献（历史上主流是 YAG）。
9. 1980s 早期 MCZ "使用常规电磁铁"的逐字一手出处（由现代超导磁体宣传材料的对比反推）。
10. 摩托罗拉 6σ 收益中可归因于晶圆厂良率（而非全公司质量成本）的拆分数据。
