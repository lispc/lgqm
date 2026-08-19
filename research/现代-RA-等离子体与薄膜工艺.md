# 现代-RA：等离子体工艺与薄膜工艺的低技术化调研笔记

> 调研日期：2026-08-19。方法：WebSearch + FetchURL（英/中文网页；部分关键综述 PDF 直接引用）。
> 方向 A 任务书：**"现代半导体工艺思想的低技术化"——等离子体工艺与薄膜工艺**。核心假设：RF 电源（电子管振荡器）与真空系统（旋片泵 + 油扩散泵）在架空世界"电子管时代"（1640s）即已具备，一切以"RF + 真空 + 气体"为设备需求的工艺原则上都可提前落地。
> 确定度标签体例（与锗-R1 一致）：【一手文献】= 原始论文/专利/当事人回忆；【教科书/综述】= 教科书、综述论文、行业史；【存疑未证】。找不到的明确写"未找到"，未编造参数。
> 本文按任务书 7 个问题组织。

## 核心结论速览

- **PECVD、等离子去胶、等离子刻蚀、直流二极溅射：设备需求全部是"RF/DC 电源 + 中真空 + 气体"，电子管时代即可完整复刻。** 历史上它们拖到 1960–70 年代才用，瓶颈不在设备，在"没人想到/没人需要"。
- **磁控溅射的"磁"只需永磁体或电磁铁**——平面磁控 1974 年 Chapin 专利的结构被 Vossen 称为"令人尴尬地显而易见的方案，竟被拖延了 30 多年"；永磁体材料（铝镍钴 1931、铁氧体 1952）晚出，但靶面磁场只需 ~10² G 量级，钴钢磁体乃至电磁铁都够。
- **硅烷可以走 Stock 1916 路线（Mg₂Si + 酸/铵盐）**——全玻璃真空系统 + 低温分馏，17 世纪化学 + 电子管时代真空技术完全可做；但产率低（粗硅烷混合物，SiH₄ 只占一部分），且 SiH₄ 自燃，安全规程是第一优先级。
- **锗的干法刻蚀化学比硅更友好**：F、Cl、Br 等离子体刻锗都比刻硅快，GeCl₄（沸点 83 °C）、GeF₄ 均挥发；氯系气体（Cl₂，氯碱工业即可产）可用，绕开氟化工的高门槛。
- **真空测量整条链（皮拉尼 1906 → B-A 电离规 1950 → 电容薄膜规 1961）全部是电子管时代技术**；QCM 膜厚监控（Sauerbrey 1959）只需石英片 + 振荡电路 + 频率计，低技术可造。
- **PIII（等离子体浸没注入）设备上确实比束线注入机简单一个量级**（无磁分析器、无扫描，只要高压脉冲 + 等离子体），但无质量分选、剂量监控难，对掺杂应用的"友好度"存疑。

---

# 问题 1：PECVD（等离子体增强化学气相沉积）

## 1.1 原理提出与首次实用化年代

- 辉光放电化学（glow discharge chemistry）用于沉积的开创性工作在英国 Standard Telecommunication Laboratories（STL，Harlow）完成。R.C.G. Swann 发现 RF 放电促进硅化合物沉积到石英器皿壁上；1964 年提交了法国、英国、美国专利申请；公开论文为 **Sterling & Swann, "Chemical vapour deposition promoted by r.f. discharge", Solid-State Electronics, 8 (1965) 653–654**。来源：[Encyclopedia MDPI "Plasma-Enhanced Chemical Vapor Deposition"](https://encyclopedia.pub/entry/35260)【教科书/综述】；当事人回忆 [R.C.G. Swann, "The Birth of Glow Discharge Chemistry"（STL 前员工回忆网站）](https://stlqcc.org.uk/the-birth-of-glow-discharge-chemistry/)【一手文献（回忆）】。
- 教科书口径："Plasma CVD was first developed in the 1960s for semiconductor applications, notably for the deposition of silicon nitride." 来源：[Big Chemical Encyclopedia, "The CVD of Silicon Nitride"](https://chempedia.info/info/the_cvd_of_silicon_nitride/)【教科书/综述】。
- 1965 年 Sterling & Swann 同时报道了 RF 辉光放电中用硅烷沉积非晶硅（glassy/amorphous Si），1968 年 Vepřek & Mareček 用氢等离子体做出微晶硅。来源：[ScienceDirect "Diborane – an overview"（引 Sterling & Swann 1965、Vepřek & Mareček 1968）](https://www.sciencedirect.com/topics/earth-and-planetary-sciences/diborane)【教科书/综述】。
- 早期 PECVD 氮化硅膜报道：R.J. Joyce, H.F. Sterling, J.H. Alexander, "Silicon Oxide and Nitride Films..."（1967 前后，STL 同组）。来源：[Southampton 大学 Sparrow 博士论文参考文献列表](https://eprints.soton.ac.uk/42428/1/Sparrow_2005_thesis_3539.pdf)【教科书/综述】。
- **结论：原理 1964–65 年才公开，但纯系"没人想到"——辉光放电本身是 19 世纪物理，RF 振荡器和真空系统 1930 年代即成熟。**

## 1.2 最低 RF 频率 / 功率 / 真空度

任务书要求的"最低配置"定量数据，本轮检索未找到一手文献的逐项下限（Sterling 1965 原文未获取全文）；以下为教科书典型值【教科书/综述】：

- 频率：工业标准为 **13.56 MHz**（ISM 频段，避免干扰通信）；早期实验与部分设备用数百 kHz–数 MHz 乃至射频电源任意频率均可起辉，**原理上对频率无苛刻要求**（容性耦合平行板）。低气压下直流辉光放电亦可维持等离子体（溅射就是直流）。
- 功率：实验室平行板 PECVD 典型数十–数百 W（功率密度 ~0.05–0.5 W/cm² 量级）。
- 真空度：典型 **0.05–5 Torr**（约 5–500 Pa）——旋片泵单级即可达，扩散泵都用不上。
- 温度：PECVD SiO₂ **200–400 °C**、Si₃N₄ 典型 **250–350 °C**。来源：[MKS Handbook（tugraz 镜像）SiO₂ 工艺对比表："PECVD 200-400 °C"](http://lampz.tugraz.at/~hadley/semi/books/MKSHandBook.pdf)【教科书/综述】；[ScienceDirect "Plasma Enhanced CVD – an overview"："PECVD process at 350°C, the deposition of silicon nitride films will not destroy the IC chips"](https://www.sciencedirect.com/topics/chemical-engineering/plasma-enhanced-chemical-vapor-deposition)【教科书/综述】。
- 对照：热氧 900–1000 °C、LPCVD TEOS 650–750 °C（[TU Wien Heitzinger 学位论文，TEOS 热解 650–750 °C](https://repositum.tuwien.ac.at/bitstream/20.500.12708/20409/1/)【教科书/综述】）——**PECVD 是唯一全程低于锗热预算（<600 °C）的介质沉积路线**，这正是本方向对架空锗工艺的最大价值。

## 1.3 前驱体与最低制备路线

| 膜 | 前驱体配方 | 历史/来源 |
|---|---|---|
| SiO₂ | SiH₄ + O₂（或 SiH₄ + N₂O）；或 TEOS + O₂ | SiH₄+O₂ 的 APCVD 1960s 即用，450 °C 以下（Al-Si 合金化温度限制驱动）；[iczhiku 镜像教科书段落："The early deposition process used was a horizontal conduction heated APCVD system from silane and oxygen… SiH₄+O₂→SiO₂+2H₂"](https://picture.iczhiku.com/resource/eetop/SYkGDlqTyqqUsXcb.pdf)【教科书/综述】；SiH₄+2N₂O→SiO₂+2N₂+2H₂O 见 [US20100104852A1 专利 ¶98](https://patentimages.storage.googleapis.com/15/02/7a/acccf6eff3c93d/US20100104852A1.pdf)【一手文献（专利）】 |
| Si₃N₄ | SiH₄ + NH₃（或 N₂） | Sterling/Swann STL 1960s；【教科书/综述】 |
| TEOS | Si(OC₂H₅)₄，SiCl₄ + 乙醇酯化即可制（19 世纪有机硅化学） | TEOS-PECVD/LPCVD 1970s 起用于 SiO₂；【教科书/综述】 |

气体侧的低技术评估【教科书/综述】：
- **NH₃**：哈伯法或实验室铵盐 + 碱，无门槛。
- **N₂O**：加热硝酸铵（Priestley 1772 即知），无门槛；注意与 SiH₄ 同管混流是爆炸源（见 §1.5 大阪大学事故）。
- **O₂**：空分或电解，无门槛。
- **TEOS**：SiCl₄ + C₂H₅OH，经典酯化，无门槛；TEOS 常温液态、不自燃，**安全上远优于硅烷**，是低技术场景的首选氧化硅前驱体。

## 1.4 硅烷的最低技术制备路线（Stock 法）

- **发现史**：1857 年 Wöhler & Buff 用酸处理金属硅化物时首次观察到硅烷类气体；**1916 年 Alfred Stock 用硅化镁 Mg₂Si + 盐酸系统制得并分离出 SiH₄、Si₂H₆、Si₃H₈ 等硅氢化物**。来源：[evitachem 产品页"Historical Context"（1857 Wöhler & Buff；Stock 1916 Mg₂Si+HCl）](https://www.evitachem.com/product/evt-1207881)【教科书/综述】；Stock 本人著作 *Hydrides of Boron and Silicon*（Cornell Baker 讲座，1933）见 [Canterbury 大学图书馆条目](https://libcat.canterbury.ac.nz/Record/289357)【一手文献】。
- **工艺细节（教科书口径）**："A silane mixture (crude silane) is formed on hydrolysis of Mg₂Si with 20% phosphoric acid at 50–60 °C. As early as 1916, the analogous reaction with hydrochloric acid had been carried out [by Stock]." 来源：[asau.ru《Chemistry of the Non-Metals》PDF](https://www.asau.ru/files/pdf/2389744.pdf)【教科书/综述】。
- **变体（至今中国厂商在用）**：Mg₂Si 粉 + NH₄Cl 在液氨环境中反应（"硅化镁法"）；Mg₂Si 由硅粉与镁粉在氢气中约 **500 °C** 反应制得。来源：[huazhong-gas "How are silanes manufactured?"](https://www.huazhong-gas.com/how-are-silanes-manufactured/)【教科书/综述（厂商科普）】；[iotasilane "Silane production process comparison"](https://www.iotasilane.com/news1-4.html)【教科书/综述（厂商科普）】。
- **纯化**：Stock 的全部工作在**全玻璃真空系统**（汞扩散泵、玻璃旋塞、McLeod 规）上完成，靠**低温分凝/低温分馏**分离混合硅烷（SiH₄ 沸点 −112 °C，Si₂H₆ −14.5 °C，沸点差大，好分）。这是"17 世纪玻璃工 + 电子管时代真空 + 干冰/液空冷阱"即可复制的路线。【教科书/综述】
- **产率**：Stock 法的缺点即产率低——Mg₂Si 水解把硅分散成 SiH₄/Si₂H₆/Si₃H₈/聚合物硅氧烷混合物，SiH₄ 只是其中一部分。**具体百分数本轮未找到可靠原文数字（各种二手说法 20–40% 不等），标注：未找到，【存疑未证】**。低技术场景应对：高级硅烷（Si₂H₆+）热解回 SiH₄ 或直接用混合硅烷做 PECVD（膜含氢本来就有）。
- **结论：Stock 法整条链（制 Mg₂Si → 酸解 → 全玻璃真空低温分馏）无任何超出"电子管时代"的环节，是架空世界硅烷的正当来源。**

## 1.5 SiH₄ 安全性（自燃）与历史事故教训

- 硅烷为**高压自燃气体（pyrophoric）**，自 1960 年代中期 IC 工业起广泛使用；"泄漏后并不总是立即点燃，原因至今不完全清楚"——延迟点火反而是爆炸（蒸气云）而非单纯火灾的诱因。来源：[ACS CHAS, Eugene Ngai, "Silane safety"（Denver 2011 报告 PDF）](https://www.acs.org/content/dam/BEA/membership/divisions/subportals/chas/CHAS_Denver11.pdf)【教科书/综述（安全专家报告）】。
- **大阪大学硅烷爆炸事故（1991）**：N₂O 经老化 O 形圈的止回阀**逆流进入硅烷管路**，SiH₄/N₂O 混合气在管内爆炸。来源：[shipiai.org 失败知识数据库案例 CA1000614](https://www.shippai.org/fkd/en/cfen/CA1000614.html)【一手文献（事故调查）】。
- 行业调查：1994 年 AT&T 贝尔实验室与 SEMATECH 对硅烷使用行业做过事故普查；光伏/非晶硅氮化硅产线事故记录多为泄漏起火，两人受伤、$686K 损失量级（1988–1998 段）。来源：[TAMU Sposato 论文（silane jet mixing）](https://oaktrust.library.tamu.edu/bitstream/handle/1969.1/193835/Sposato.pdf?sequence=1)【教科书/综述】；[Columbia CLCA "Silane safety in amorphous silicon and silicon nitride operations"](http://www.clca.columbia.edu/papers/3DV.3.52_Silane_Dresden_06.pdf)【教科书/综述】。2025 年 Bosch 德国工厂硅烷泄漏致死 2 人，见 [semiconductorinsight 报道](https://semiconductorinsight.com/blog/silane-gas-leak-at-bosch-site-in-germany-claims-two-lives-sparks-safety-concerns/)【教科书/综述（新闻）】。
- **低技术场景教训（写入设定的硬规则）**：① 硅烷与氧化剂（O₂/N₂O）**分管路、双阀 + 中间抽空的隔离段**，止回阀不可作为唯一隔离手段；② 稀释使用（历史上 2% SiH₄/H₂ 或 /N₂ 钢瓶即为安全妥协）；③ 小钢瓶、室外/通风橱、尾气燃烧或水洗；④ 替代品优先：TEOS（不自燃）做 SiO₂，非必要不囤纯硅烷。

---

# 问题 2：等离子刻蚀 / 反应离子刻蚀（RIE）

## 2.1 等离子去胶（O₂ plasma ashing）首用年代与设备

- **1968 年 Stephen Irving（Signetics）首次演示氧等离子体去除光刻胶；1971 年公开数据**；同期 1971 年 Irving 还公开了 CF₄ 等离子体刻蚀硅的实验数据。来源：[JJAP 综述 "Developments of Plasma Etching Technology for Fabricating Semiconductor Devices"（47, 1435）："The capabilities of plasma processes were first demonstrated by the oxygen plasma ashing of a polymer-based photoresist film by Irving in 1968… In 1971, he disclosed experimental data pertaining to the plasma etching of silicon using CF4 plasma."](https://iopscience.iop.org/article/10.1143/JJAP.47.1435/pdf)【教科书/综述】；[Donnelly & Kornblit, "Plasma etching: Yesterday, today, and tomorrow", JVA 31, 050825 (2013)](https://pubs.aip.org/avs/jva/article/31/5/050825/244912/Plasma-etching-Yesterday-today-and-tomorrow)【教科书/综述】。
- 设备即**圆筒式（barrel）反应器**：石英/玻璃圆筒，筒外绕 RF 线圈或电极，O₂ 0.1–1 Torr，几十到几百瓦——**一台中功率电子管振荡器 + 旋片泵就是全部**。去胶是历史上第一个被工业采纳的等离子体工艺，正因为它对设备最宽容（不要求各向异性、不要求均匀性极致）。
- 商业史佐证：Ted Gallagher 1966 年在 Tracer Labs/LFE 推广等离子设备，1972 年创立 Tegal——第一批产品就是等离子去胶机。来源：[SEMI Oral History: Ted Gallagher](https://www.semi.org/en/Oral-History-Interview-Ted-Gallagher)【一手文献（口述史）】。

## 2.2 CF₄ / CF₄+O₂ 刻蚀 Si 与 SiO₂ 的年代

- Irving 1971 年 CF₄ 刻 Si 数据（见上）；**Heinecke 1975–76**（Standard Telecommunication Laboratories）确立 CF₄ 辉光放电刻硅及其化合物的工艺。ECS 综述引其 1976 年原文：**"...silicon and its compounds can be etched in a CF4 glow discharge through the formation of volatile compounds. Such a process, if applied to semiconductor processing, promises a number of advantages over liquid etching methods."** 来源：[ECS Interface, "Plasma Processing for Silicon-Based Integrated Circuits"（1999）](https://www.electrochem.org/dl/interface/sum/sum99/IF6-99-Pages34-40.pdf)【教科书/综述】。
- CF₄+O₂ 提高 F 原子浓度、加速刻硅；CF₄+H₂ 选择性刻 SiO₂ 快于 Si——均为 1970 年代确立【教科书/综述】。
- 1970 年代初 O₂ 去胶与各向同性等离子刻蚀已用于 16K DRAM 制造（JJAP 综述，同上）【教科书/综述】。

## 2.3 刻蚀锗的气体化学

- **锗在氟、氯、溴基低压等离子体中都比硅刻得更快**："germanium is more rapidly etched than silicon in conventional fluorine-, chlorine-, and bromine-based low-pressure plasmas"——Oehrlein et al., J. Electrochem. Soc. 138, 1443 (1991)。来源：[Mendeley 条目（Selective dry etching of germanium…）](https://www.mendeley.com/catalogue/3ba53784-b344-319d-9e48-211853841c61/)【教科书/综述（文献条目）】；[JICS 综述 "Selective and Anisotropic Dry Etching of Ge over Si"](https://jics.org.br/ojs/index.php/JICS/article/view/380/223)【教科书/综述】。
- 实例：ICP Ar/CCl₂F₂/Cl₂ 刻 Ge（[Kim et al. 2010, Springer](https://link.springer.com/article/10.3365/eml.2010.03.035)【一手文献】）；磁控增强 SF₆ 刻 Ge（McLane et al.，同上 JICS 综述引用）。
- **低技术场景的关键判断**：氟系气体（CF₄、SF₆、CCl₂F₂）都需要元素氟电解工业（Moissan 1886 之后），在架空世界属于"有门槛但可达"；**氯系（Cl₂、HCl、BCl₃ 中前两者）是氯碱工业/盐酸的直接产物，门槛最低**。锗的氯化物 GeCl₄ 沸点仅 83 °C（1886 年 Winkler 发现锗时即知），挥发性极佳 → **Cl₂ 基等离子刻锗是低技术场景的首选化学**；Si 路线则 Cl₂ 刻蚀速率/选择性不如氟系，需要权衡。【教科书/综述】

## 2.4 圆筒式（barrel）与平行板（RIE）反应器差异与最低配置

- 结构对比见 [DCU 学位论文 Fig 1.03（barrel / plasma mode / RIE 三种反应器示意）](https://doras.dcu.ie/19597/1/Liang_TAN_20130925144906.pdf)【教科书/综述】：
  - **Barrel（圆筒式）**：晶片置于接地圆筒内（常加铝蚀刻屏蔽隧罩），等离子体环绕，离子方向性弱 → **各向同性**，侧蚀明显，但容量大、结构极简；最低配置 = 玻璃筒 + RF 线圈 + 旋片泵 + O₂/CF₄ 气源。
  - **平行板 RIE（reactive ion etching）**：晶片直接放在**接 RF 的小电极**上，大电极（腔壁）接地，面积不对称产生自偏压（负直流偏压数十–数百 V），离子垂直轰击 → **各向异性**。最低配置 = 平行板电极 + 13.56 MHz（或更低频）RF 电源 + 匹配网络 + 0.01–0.5 Torr 真空。
- RIE 一词的工业推广在 1970 年代中后（Reinberg 径向流反应器等），配合 64K DRAM 代际成为主流【教科书/综述】。

## 2.5 湿法 vs 干法侧蚀对比

本轮未检索到给出统一定量侧蚀数据的一手文献【存疑未证】；教科书共识【教科书/综述】：

- **湿法各向同性刻蚀**：侧向钻蚀（undercut）≈ 刻蚀深度（1:1），线宽损失 ≈ 2×膜厚，1–2 µm 以下线条不可控；优点是无设备、选择比高。
- **Barrel 等离子刻蚀**：同样各向同性，但钻蚀可用工艺窗口压缩；**RIE**：近垂直侧壁（各向异性比 >5:1 量级），是 1970 年代末 <2 µm 图形转移的必要条件。
- 对架空锗分立管/小规模集成（特征尺寸 ≥10 µm 量级）的裁决：**湿法完全够用，干法是锦上添花**——去胶（ashing）反而是干法里最先值得落地的，因为湿法去胶（热浓硫酸/发烟硝酸）对锗表面和金属化有附带损伤且废酸处理麻烦。

---

# 问题 3：溅射镀膜（sputtering）

## 3.1 Grove 1852 原始记载

- **W. R. Grove, "On the electro-chemical polarity of gases", Philosophical Transactions of the Royal Society of London, 142, 87–101 (1852)**——在气体放电管中观察到阴极金属被"溅射"沉积到玻璃壁上，为溅射现象的首次记载。来源（含原始文献 DOI 10.1098/rstl.1852.… 的引用）：[Greene, "Review Article: Tracing the recorded history of thin-film sputter deposition: From the 1800s to 2017", J. Vac. Sci. Technol. A 35, 05C204 (2017)](https://pubs.aip.org/avs/jva/article/35/5/05C204/244891/Review-Article-Tracing-the-recorded-history-of)【一手文献（原始论文）+ 教科书/综述（Greene 史论）】。
- 后续早期应用：Edison 1904 年前后"Process of duplicating phonograms"专利即用溅射镀金属母模；20 世纪初溅射用于制镜。来源：[MDPI Materials 2(3)1341 参考文献（Edison US 专利）](https://www.mdpi.com/1996-1944/2/3/1341)【一手文献（专利条目）】；Greene 2017 史论【教科书/综述】。
- **要点：溅射是比真空蒸发更早被发现的镀膜现象（1852 vs 1857 前后蒸发观察），设备就是一根气体放电管。**

## 3.2 直流二极溅射的设备门槛

- 典型配置【教科书/综述】：Ar 气 **10–100 mTorr**、靶（阴极）加 **−1 至 −5 kV DC**、电流密度 mA/cm² 量级，基片放阳极侧。全部需求 = 高压直流电源（电子管整流即可）+ 中真空（旋片泵即够，扩散泵更好）+ 氩气（空分副产，19 世纪末可得）。
- 溅射绝缘体需 RF（13.56 MHz 直接馈靶）——RF 溅射 1960 年代成熟，但物理上同样是"电子管振荡器 + 匹配网络"【教科书/综述】。

## 3.3 磁控溅射：只需要一块磁体

- 原理谱系：**Penning 1936** 年磁约束放电（磁控规/溅射离子泵同源）；苏联 **Kesaev & Pashkova** 在汞弧灯研究中用电磁铁把等离子体稳定在汞池表面，发表过圆形和方形等离子体区的照片（Vossen 引为平面磁控最早描述之一）。来源：[Vossen & Kern《Thin Film Processes》章节 PDF（"embarrassingly obvious solution… eluded discovery and implementation for more than 30 years"）](https://sites.ifi.unicamp.br/fi204/files/2025/05/Vossen-chs-I-1-to-II-5.pdf)【教科书/综述】。
- 实用化时间线：**Clarke 专利申请 1968 年 11 月；Mullaly 解密报告 1969 年 11 月；Corbani 专利 1973 年 7 月；Chapin 平面磁控专利申请 1974 年 1 月 31 日（US 4,166,018，授权 1979-08-28）**。来源：[SVC《Foundations of Vacuum Coating Technology: the Stories Behind the Facts》](https://www.svc.org/clientuploads/directory/resource_library/03_011.pdf)【一手文献（专利时间线）】；[Stanford Advanced Materials 综述（Chapin 1974 US 4,166,018）](https://www.sputtertargets.net/sputtering-demystified-the-atomic-level-process-that-enables-modern-electronics/)【教科书/综述】；[Von Ardenne 公司史](https://vonardenne.com/news/magnetron-sputtering-how-it-began-and-how-von-ardenne-became-a-technology-pioneer/)【教科书/综述】。
- **磁体从哪来（关键问答）**：
  - 铝镍钴（AlNiCo）：**1931–32 年三岛德七（Mishima）MK 钢**，此前为碳钢/钨钢/钴钢磁体（1917 本多光太郎 KS 钢）。来源：[MPCO "Permanent Magnets in a Changing World Market"](https://mpcomagnetics.com/blog/permanent-magnets-in-a-changing-world-market/)【教科书/综述】；[Ferrocell 磁学年表 PDF](https://www.ferrocell.us/references/Magnetism in Ancient Societies to the Present Circa 1400 BCE to 2020 CE 9 37 pp.pdf)【教科书/综述】。
  - 钡铁氧体永磁：**1952 年 Philips 商品化**（MPCO，同上）【教科书/综述】。
  - 平面磁控靶面磁场需求约 **100–500 G 量级**（约束二次电子即可）——**钴钢/铝镍钴完全够，甚至电磁铁（Kesaev 当年就是电磁铁）也够**。架空世界裁决：磁场不是瓶颈，瓶颈只是"没人想到把磁体放在靶后面"。【教科书/综述】

## 3.4 溅射 vs 蒸发优劣（对电阻膜/介质膜的适用性）

教科书共识【教科书/综述】（Vossen & Kern《Thin Film Processes》；Greene 2017）：

| 维度 | 溅射 | 热蒸发 |
|---|---|---|
| 台阶覆盖 | 较好（原子到达角分布宽 + 气体散射 + 入射能量 eV 级 → 表面迁移） | 差（视线沉积、垂直入射为主，~0.1 eV） |
| 合金成分 | **基本保持靶成分**（不同元素溅射产额差异在瞬态后自补偿），NiCr、WTi 等合金膜首选 | 分馏严重（蒸气压差异），合金膜成分漂移 |
| 高熔点材料 | 容易（W、Ta、Mo 直接溅射） | 阻蒸困难，需电子束 |
| 膜纯度 | 受工作气体（Ar）夹杂影响（~% 级） | 高真空中纯度高 |
| 速率 | 二极溅射慢（~10–100 nm/min），磁控后 ×10 | 快 |
| 附着力 | 好（入射能量高） | 一般 |

- **镍铬电阻膜**：薄膜电阻工业标准做法即溅射 NiCr（成分保持 + 附着力好），蒸发 NiCr 因分馏需补偿【教科书/综述】。对架空世界"精密薄膜电阻/混合集成电路"路线，溅射是正当工艺。
- **介质膜**：RF 溅射 SiO₂ 可行但慢；介质钝化仍以 PECVD 为先，溅射介质作为补充。

---

# 问题 4：真空测量与控制的低技术史

## 4.1 各规原理、年代与制造难度

| 规 | 年代 | 原理 | 量程 | 低技术制造难度 |
|---|---|---|---|---|
| McLeod 压缩规 | 1874 | 压缩已知体积气体按玻意耳定律读压 | 10⁻⁵–10 Torr（不连续、含汞） | **纯玻璃工 + 汞**，Stock 时代标配 |
| 皮拉尼规（Pirani） | **1906**（Marcello Pirani） | 热丝电阻随气体热导变化；惠斯通电桥读数 | 10⁻³–10² Torr | **极低**：钨丝 + 电桥 + 表头，全部 19 世纪技术。来源：[Sens4 "History of the Pirani vacuum gauge"](https://www.sens4.com/blog/vacuum-technology-2/history-of-the-pirani-vacuum-gauge-2)【教科书/综述】 |
| 热电偶规 | **1906**（Voege 首次使用） | 热丝温度用热电偶直读 | 10⁻³–1 Torr | 极低：热电偶 + 毫伏表。来源：[Electronic Engineering 1951-01（WorldRadioHistory 扫描）："Voge first used a gauge of this type in 1906"](https://www.worldradiohistory.com/UK/Television-UK/50s/Electronic-Engineering-1951-01-S-OCR.pdf)【一手文献（1951 期刊原文）】 |
| 三极电离规 | 1920s 起 | 电子碰撞电离，离子流∝压强 | 10⁻⁶–10⁻² Torr | 相当于自制一只三极管，电子管时代熟练工种 |
| Bayard-Alpert 规 | **1950** | 细丝收集极置于栅内中心，降低 X 射线本底 → 下限 ~10⁻¹⁰ Torr | 10⁻¹⁰–10⁻³ Torr | 同样是一只"结构特殊的三极管"，玻璃吹制 + 钨丝；**电子管时代完全可以造**。来源：[IMEKO TC16 真空计量史 PDF](https://www.imeko.org/publications/tc16-2007/IMEKO-TC16-2007-KL-034u.pdf)【教科书/综述】；[Redhead, "The measurement of vacuum pressures", JVA 2(2)132 (1984)："The elegant simplicity of the Bayard-Alpert design in 1950 led to its immediate acceptance…"](https://pubs.aip.org/avs/jva/article-pdf/2/2/132/11506842/132_1_online.pdf)【一手文献（综述）】 |
| 电容薄膜规（CDG） | **1951 Alpert/Matland/McCoubrey 提出；1961 MKS Baratron 商品化** | 金属薄膜受压挠曲 → 与固定电极间电容变化；**与气体种类无关**，绝对读数 | 10⁻⁴–10³ Torr（多档） | 中等：精密膜片（因科镍）+ 电容电桥；电子技术无门槛，难点在膜片焊接与温度补偿。来源：[An-Najah 大学真空技术讲义："A capacitance manometer was originally suggested in 1951 by Alpert, Matland, and McCourby"](https://staff-old.najah.edu/sites/default/files/vacuum%20technology-c2_0.pdf)【教科书/综述】；[belljar.net《The Bell Jar》："The first capacitance manometers were developed in the late 1920s… made commercially viable in 1961 when MKS Instruments introduced their Baratron"](https://www.belljar.net/tBJ_First_Five_Years.pdf)【教科书/综述】；[MKS 公司史（1961 创立、Baratron 首个产品）](https://businessmodelcanvastemplate.com/blogs/brief-history/mks-instruments-brief-history)【教科书/综述】 |

- **对工艺控制的价值排序**：皮拉尼（泵/前级监控）→ CDG（PECVD/刻蚀的过程压力闭环，与气体无关这一性质对混气工艺是刚需）→ B-A（镀膜高真空监控）。三者全在"电子管时代"能力圈内，是低技术化收益最大的一组仪器。

## 4.2 真空阀门的低技术做法【教科书/综述】

- 全玻璃系统：**磨口玻璃旋塞 + 真空脂、汞隔断（mercury cutoff）**——Stock 1916 年全套如此，零门槛，但含汞且不耐大气差压侧操作。
- 金属系统：波纹管密封阀（bellows-sealed）需要焊接波纹管（有门槛）；**O 形圈密封的角阀/闸板阀**——需要合成橡胶（丁腈/氟橡胶为 1930–50 年代产品；架空世界若只有天然橡胶，真空脂封填料函 + 短行程阀杆是替代方案，漏气率差但可用）。
- 粗阀替代：液封 + 旋塞组合、快接法兰 + 甘油密封——17 世纪化学实验传统的直接延伸。
- **裁决**：阀门不是瓶颈；真瓶颈是批量一致性（每只阀的漏气率），这对架空世界的精密机械是合理考验。

---

# 问题 5：热蒸发镀膜的进阶

## 5.1 阻蒸钨舟/钼舟

- 电阻加热蒸发是真空镀膜最古老的工业路线（1930 年代灯具/镜面镀铝产业化）；钨/钼/钽丝篮与舟皿即可蒸发 Al、Au、Cu、Ge 等，电源只是大电流变压器——**零门槛**，为架空世界既定技术，无需展开。【教科书/综述】

## 5.2 电子束蒸发：难度评估

- 原理与参数：热灯丝发射电子，经 **5–10 kV** 加速、聚焦轰击坩埚内材料局部熔化蒸发；功率密度可达 **10⁴–10⁹ W/cm²**，高熔点金属（W、Mo、Ta、Pt）与介质（SiO₂）均可蒸发。来源：[Scholars Research Library PVD 综述："An electron beam is accelerated through potential of 5 to 10 kV and focused on the material"](https://www.scholarsresearchlibrary.com/articles/physical-vapor-deposition-pvd-methods-for-synthesis-of-thin-films.pdf)【教科书/综述】；[Wiley 手册章节 PDF（功率密度 10⁴–10⁹ W/cm²）](https://2024.sci-hub.ru/5927/729420fbb8f771f5a80ae498744511e7/10.1002@9783527696406.ch2.pdf)【教科书/综述】。
- 设备构成 = 电子枪（热阴极 + 聚焦极，与电子管/示波管枪同源）+ 5–10 kV 高压电源 + 磁偏转（270° 弯束使灯丝避开蒸气）+ 水冷铜坩埚 + 高真空（<10⁻⁵ Torr，扩散泵）。
- **难度评估**：所有部件都是电子管时代的熟练工种（X 射线管 1913 年 Coolidge 即含全部要素：热阴极、高压、水冷靶）。真正的工程细节在**高压绝缘、枪室污染、磁偏转设计**三点。裁决：**可行但非首选**——架空世界的 W/Mo/Ta 用磁控溅射更稳；电子束留给 SiO₂ 蒸发和高纯度 Au/Pt。【教科书/综述】

## 5.3 膜厚监控：QCM 低技术可造性

- 原理谱系：石英压电效应 **Curie 兄弟 1880** 发现；石英谐振器 1920 年代（Cady）用于稳频——电子管时代的标准技术；**Sauerbrey 1959** 年证明"刚性附着薄膜的质量增加与谐振频率下降成线性"（Δf = −Cf·Δm），QCM 随即成为真空镀膜标准膜厚监控。来源：[Nanoscience Instruments QCM 技术页](https://www.nanoscience.com/techniques/quartz-crystal-microbalance/)【教科书/综述】；[Frontiers 综述："In 1959 G. Sauerbrey discovered that thin solid coatings rigidly attached to quartz-crystal surface decrease its resonant frequency proportionally to the deposited mass"](https://www.frontiersin.org/journals/10.3389/fmolb.2022.935376/full)【教科书/综述】；[SRS 应用笔记（Sauerbrey 方程原文照录）](https://www.thinksrs.com/downloads/pdfs/applicationnotes/Hi_temp-microbalances.pdf)【教科书/综述】。
- **低技术可造性裁决：完全可造。** AT 切石英片（压电水晶开采 + 定向切割，1920 年代工艺）+ 电子管振荡电路 + 频率计（电子管计数器/外差法）。这是"知道原理就只差工程"的典型——Sauerbrey 的贡献纯粹是把两件事（石英钟 + 真空镀膜）连起来。

---

# 问题 6：电镀 / 化学镀的补充角色

## 6.1 化学镀镍（1946 Brenner）

- 谱系：**Wurtz 1844** 年首次观察到次磷酸盐还原镍的化学镀现象（"chemical accident"）；Roux 1911 报道但只会得到粉状沉淀；**1946 年 Abner Brenner & Grace Riddell（美国国家标准局 NBS）**在研究枪管内膛镀镍-钨合金时偶然发现可控的**自催化**化学镀镍工艺（次磷酸钠还原，得 Ni-P 合金）。来源：[Encyclopedia MDPI "Electroless Nickel Plating"（1844 Wurtz / 1911 Roux / 1946 Brenner & Riddell）](https://encyclopedia.pub/entry/36104)【教科书/综述】；当事人回忆 [Brenner, "Reminiscences of Early Electroless Plating", Products Finishing](https://www.pfonline.com/articles/reminiscences-of-early-electroless-plating)【一手文献（回忆）】。
- 设备门槛：**一只恒温水浴 + 玻璃/搪瓷槽**（85–95 °C），无电源、无真空。材料：镍盐 + 次磷酸钠（NaH₂PO₂，次磷酸 19 世纪已知）。【教科书/综述】
- 应用：化学镀 Ni-P 做阻挡层/可焊层/硬面层；化学镀金（浸金）做键合焊盘。

## 6.2 电镀金/铜在键合与互连中的应用史

- 电镀本身是 1839–40 年代的工业（镀银、镀镍），电镀金 19 世纪即用于饰品与触点——**电子管时代之前的成熟技术**。
- 半导体语境：1960 年代起电镀 Au 用于梁式引线（beam lead）与键合凸点；本项目已证实苏联 **Р12-2 用电镀 PbInSb 做锗晶体管发射极**（见 notes/01 与 锗-R1）——电镀直接进入器件核心的先例成立。【一手文献（项目内既有调研）】
- **对低技术场景的价值**：电镀/化学镀是"零真空设备"的金属化路线，与溅射互补——溅射打底（黏附/阻挡/种子层，几十–几百 nm）+ 电镀增厚（µm 级互连、凸点、功率器件厚金属）。这条"薄种子 + 厚电镀"组合正是现代封装的标准做法，架空世界可直接采用，跳过很多历史弯路。【教科书/综述】

---

# 问题 7：离子注入 vs 等离子体浸没注入（PIII）

## 7.1 束线注入机的门槛（对照基线）

- 经典束线注入机 = 离子源 + **磁质量分析器**（90° 分析磁铁）+ 加速管（10–200 keV）+ 扫描系统 + 末端站；1970 年代商品化后成为硅掺杂主流。**质量分析器要求精密磁铁 + 高稳定电源 + 高真空传输**，整机是"加速器级"设备——对架空世界属可望而重的工程。【教科书/综述】

## 7.2 PIII 的历史与设备

- 理论先声：1960 年代末 Widner 等人计算负脉冲偏压平板附近的离子声波波前/鞘层演化——15 年后被 Conrad 认出即 PIII 理论基础；1980 年代初 Adler 等（Mission Research）做短脉冲真空弧金属离子注入。**1987 年 Conrad 等提出 Plasma Source Ion Implantation（PSII）；1988 年 Tendys 等独立发表**；后统称 PIII。来源：[Anders, "From Plasma Immersion Ion Implantation to Deposition: A Historical Perspective…", eScholarship（Widner → Adler → Conrad 谱系）](https://escholarship.org/content/qt9hm8h1zj/qt9hm8h1zj.pdf)【一手文献（综述，当事领域权威）】；[CityU《Surface engineering of light alloys》章节："PIII was first introduced back in the mid-1980s by Conrad et al. (1987) and Tendys et al. (1988). Initially called plasma source ion implantation (PSII)…"](https://www.cityu.edu.hk/phy/appkchu/Publications/2010/10.17.pdf)【教科书/综述】。
- 设备构成：真空室 + 等离子体源（RF/直流辉光皆可）+ **高压脉冲电源（10–100 kV，µs 级脉冲，kHz 重复率）**。**没有磁分析器、没有加速管、没有扫描**——工件浸在等离子体里整体加负脉冲，全表面同时注入。
- 历史佐证"高压脉冲+等离子体"可低技术实现：文献中有用**电子管硬管脉冲调制器（hard tube pulser）**做 PIII 电源的工作（Rossi, Ueda & Barroso 2001 等）。来源：[OSTI 综述参考文献 [64][65][66]（high voltage hard tube pulser 等）](https://www.osti.gov/servlets/purl/877327)【教科书/综述】。电子管做高压脉冲开关正是雷达时代的看家本领。

## 7.3 对低技术场景的友好度评估

**设备上确实友好一个量级**，但有三条硬伤，裁决为"**有价值但不替代束线，且掺杂用途存疑**"：

1. **无质量分选**：等离子体里所有离子种类一起注入（载气离子、污染离子同入）。掺杂气体如 PH₃/B₂H₆/AsH₃ 本身是乙醚级毒性与制备门槛并存的氢化物气体——而这恰是 Stock 法能覆盖的（硼氢化物正是 Stock 的本行，B₂H₆ 1912 年起即由 Stock 系统制备）【教科书/综述】。
2. **剂量监控难**：无法拉第杯意义上的束流定义，剂量靠脉冲数×鞘层模型估算，历史上 PIII 主要成功在**冶金表面改性**（氮注入提高耐磨——气体单一、剂量不敏感），半导体掺杂要求 % 级剂量精度，这是 PIII 的弱项。
3. **能量分布宽**：脉冲上升沿与鞘层扩展导致注入能量非单值 → 结深控制粗。
- **对锗路线的具体价值**：锗注入后退火温度低（~300–500 °C，在锗热预算内），且锗路线本就缺高温扩散手段之外的掺杂选项；PIII 可作为"**实验性掺杂手段**"写入设定，但更稳的路径仍是：扩散（锗的开管锌扩散已由 Р12-5 证实）+ 合金/电镀结（Р12-2 证实）。【教科书/综述 + 项目内既有调研】

---

# 汇总裁决表：电子管时代（RF+真空+气体）可提前落地的工艺

| 工艺 | 历史首用 | 设备门槛 | 气体/材料门槛 | 电子管时代可落地？ | 备注 |
|---|---|---|---|---|---|
| O₂ 等离子去胶 | 1968（Irving） | 玻璃筒+RF+旋片泵 | O₂ | **是，零障碍** | 最该先落地 |
| Barrel 等离子刻蚀 Si/SiO₂/Ge | 1971–76 | 同上 + CF₄/Cl₂ | CF₄ 需氟化工；**Cl₂ 无门槛且刻 Ge 更快** | **是**（氯系路线） | 各向同性 |
| 平行板 RIE | 1970s 中 | + 匹配网络、自偏压 | 同上 | **是** | 需要匹配网络调试功夫 |
| PECVD SiO₂/Si₃N₄ | 1964–65（STL） | 平行板 + RF + 加热台（200–350 °C） | SiH₄（Stock 法可制，自燃危险品）/ **TEOS（液态安全）** + NH₃/N₂O | **是** | 对锗热预算（<600 °C）是刚需性补充 |
| 直流二极溅射 | 1852 发现 / 20 世纪初应用 | 几 kV DC + 中真空 + Ar | Ar（空分） | **是，甚至是 19 世纪技术** | 金属膜、NiCr 电阻膜 |
| 磁控溅射 | 1968–74 专利 | 二极溅射 + **一块磁体** | 同 | **是**（钴钢磁体或电磁铁） | "被拖延 30 年的显而易见方案" |
| RF 溅射介质 | 1960s | + 绝缘靶 RF 馈电 | Ar | **是** | 慢，作补充 |
| 皮拉尼/热电偶规 | 1906 | 热丝 + 电桥 | — | **是（本来就该有）** | |
| B-A 电离规 | 1950 | 特殊三极管 | — | **是**（电子管厂副产品级） | |
| 电容薄膜规 | 1951 提出 / 1961 商品 | 膜片 + 电容电桥 | — | **是**（机械加工稍难） | 混气工艺刚需 |
| QCM 膜厚监控 | 1959（Sauerbrey） | 石英片 + 振荡器 + 频率计 | 压电水晶 | **是** | "知道原理即可" |
| 电子束蒸发 | 1950s–60s | 5–10 kV 电子枪 + 磁偏转 + 高真空 | — | 可行但非首选 | 优先用磁控溅射替代 |
| 化学镀镍 | 1946（Brenner & Riddell） | 恒温水浴 | 次磷酸盐 | **是，零真空** | |
| 电镀 Au/Cu/PbInSb | 19 世纪起 | 直流电源 | 常规镀液 | **是**（Р12-2 已证） | 薄溅射种子 + 厚电镀 |
| PIII | 1987（Conrad） | 等离子体 + 10–100 kV 脉冲 | 掺杂氢化物气体（Stock 体系可制） | **设备可行，掺杂精度存疑** | 冶金改性可靠；半导体掺杂谨慎 |

## 未查到 / 存疑清单

1. **Stock 法硅烷的定量产率**（SiH₄ 占粗硅烷混合物的百分比、每吨 Mg₂Si 的硅烷产量）：各二手来源说法不一（20–40%），未找到 Stock 原著数字 → 需查 *Hydrides of Boron and Silicon*（1933, Cornell 讲座）原文。
2. **Sterling & Swann 1965 原文的 PECVD 最低 RF 频率/功率/气压**：未获取 Solid-State Electronics 8, 653 全文；现有"13.56 MHz / 数十–数百 W / 0.05–5 Torr"为教科书典型值而非历史首用值。
3. **湿法 vs 干法侧蚀的统一定量对比数据**：教科书共识（湿法 undercut≈1:1 深度）未落实到单一可引文献的具体数字表。
4. **工业等离子氮化（Berghaus 1930s）**作为"战前即有工业等离子体设备"的佐证：本轮未检索核实，仅凭记忆提及，【存疑未证】，建议补查。
5. **氯系刻蚀锗在 barrel/RIE（非 ICP）低压设备上的具体速率数据**：现有 Ge 刻蚀文献多为 ICP（高密度源），低功率平行板下的 Ge/Cl₂ 速率未找到。
6. **PIII 用于锗掺杂的任何实验先例**：未找到（PIII 半导体掺杂文献集中于 Si 的浅结与 SIMOX 相关），写入设定时应标注为"无历史先例的推演"。
