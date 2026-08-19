# 现代-RB：检测、分析与纯化的低技术化（调研笔记）

> 目的：为《临高启明》架空世界推演筛选"设备门槛低、但历史上应用晚"的检测/分析/纯化技术，论证"检测先行"（先有测量手段才有工业）在半导体材料链上的提前落地路径。
> 确定度标签：【一手文献】= 原始论文/专利/标准原文或当事人回忆；【教科书/综述】= 教科书、手册、行业综述；【存疑未证】。找不到的明确写"未找到"，不编造数值。
> 调研方法：WebSearch + FetchURL，中英文检索。调研日期：2026-08-19。
> 按任务书 10 问组织（问 10 拆为火焰光度/AAS 两小节附于第 10 节）。

---

## 核心结论速览（"纯度闭环"提前落地的关键抓手）

1. **电学检测是最便宜的纯度闭环**：四探针电阻率（Valdes 1954 方法、纯 19 世纪物理）+ 霍尔测量（1879）+ 冷热探针判型，即可对施主/受主净浓度做到 10¹³ cm⁻³（约 0.2 ppba）量级——比任何化学分析都灵敏两三个数量级，且只需电流表、检流计、磁铁。架空世界可提前 100 年。
2. **姜黄素比色法测硼**（1950s 半导体工业实测用，Luke 1955）只需分光光度计甚至目视比色，可达 ppb 级——硼是区熔硅最难除的杂质，此法是"硼闭环"的钥匙。
3. **发射光谱仪（电弧/火花 + 石英棱镜 + 照相干板）**全套是 1920s 工业成熟技术，冶金痕量分析 ppm 级、化学富集后可及 ppb；与照相干板工业天然协同。
4. **氦质谱检漏仪** = Nier 1940 小型磁偏转质谱计的工业衍生品；核心部件（扩散泵、永磁体、热阴极离子源、静电计）全部是 1930s 前技术。真空与封装气密性的定量检测可提前。
5. **RCA 清洗（SC-1/SC-2）与 SPM** 全部只用 19 世纪试剂（氨水、盐酸、硫酸、双氧水），其"配方知识"才是稀缺物——架空世界可零设备门槛直接移植。
6. **锁相放大器（Dicke 1946）+ 范德堡法（1958）**把弱信号电学测量的门槛降到变压器/机械斩波水平，霍尔和电阻率测量精度大幅提升。
7. **微孔滤膜（1918 Zsigmondy）+ 离子交换树脂（1935 Adams & Holmes）+ 混床（1949）**是超纯水/试剂链的全部核心，全部是有机合成化学门槛而非仪器门槛。
8. **吸杂（磷吸杂 1960、本征吸杂 1977）**是"低质量晶圆补救"工艺，本身只需扩散炉——知识密度高、设备密度低，是低技术场景的最佳补偿手段。
9. 液氢（Dewar 1898）/液氦（Onnes 1908）是 19 世纪末机械工业（多级高压压缩机 + 逆流换热器 + 节流阀）的产物；架空世界做到液氢级低温在工程上成立，液氦需要氦源（含氦天然气或独居石）——RRR 法可作为金属（铜、焊料）纯度的独立判据。
10. **AAS（1955）对钠沾污的监控**是 MOS 工艺的死穴解药；最低配置（空心阴极灯 + 火焰 + 单色器）全系 1910s–30s 技术。但注意：其原理依赖"锐线光源 + 调制"的组合思想，这才是 1955 年才有的东西——典型的"思想稀缺、设备不稀缺"案例。

---

# 01 氦质谱检漏仪

## 原理与年代

- 质谱计本身：J.J. Thomson 1910 年首台质谱仪（测氖同位素）；其后数十年均为"占满一间房"的专用设备。【教科书/综述】[DESY/CERN 真空讲稿, K. Zapfe, 2006/2007](https://www-eng.lbl.gov/~shuman/XENON/REFERENCES&OTHER_MISC/leak_testing_desy.pdf)
- 用质谱计检漏的思想起源于**曼哈顿计划 1942/43 年**：铀同位素气体扩散工厂对密封性要求空前，各种检漏法（皂泡、卤素、压升法）灵敏度都不够，最终选定 Nier 设计的、调谐到氦质量数（m/e=4）的简化小质谱计 + 氦示踪。早期仪器即可检出 10⁻⁶ std·cm³/s 量级的氦流。【教科书/综述】[同上 DESY 讲稿；heliumleak.com 行业史](https://www.heliumleak.com/about/blogs/history-of-helium-leak-detection)；【二手综述】[Nerken 1991 回顾（CS Analytical 转述）](https://csanalytical.com/ccit/helium-leak-detection/)
- Nier 的美国专利 **US 2,486,199**（1949-10-25 授权，检漏质谱计）被后世文献明确指认为氦检漏仪的源头。【一手文献（专利被引述）】[NASA STAR 1971 专利公告](https://ntrs.nasa.gov/api/citations/19710019516/downloads/19710019516.pdf)

## 最低设备配置（判定：全系 1930 年代前技术）

以 DESY 讲稿描述的检漏单元为基准：
- **180° 磁偏转分析室**：永磁体（约 1.5 kG 磁场，现代商品机即永磁体；1944 年 Taylor 的 Nier 型改机已用永磁体 + 干电池加速电源）。【一手文献（引述）】[Lehigh 大学学位论文，Taylor 1944 改机描述](https://preserve.lehigh.edu/system/files/derivatives/coverpage/439339.pdf)
- **电子轰击离子源**：热阴极 + 加速极，即三极电子管级别的真空技术。
- **离子收集极 + 静电计**：最高灵敏度档需测 10⁻¹⁵ A 级电流（现代用电子倍增器）；早期用振簧静电计/DC 放大器，灵敏度相应低（10⁻⁶ 量级起步）。19 世纪的象限静电计/镜式检流计即可测 10⁻¹³–10⁻¹⁵ A，是底线方案。
- **真空机组**：油扩散泵 + 旋片机械泵 + 液氮冷阱（选择性抽水、降氦抽速以提高灵敏度）。【教科书/综述】[DESY 讲稿 §5–7]
- 工作真空 ≤10⁻⁴ mbar（离子飞行程 ~15 cm 要求分子平均自由程 ≥60 cm）。【教科书/综述】同上
- 灵敏度历史轨迹：1945 年 10⁻⁶ mbar·l/s → 1970 年 10⁻⁹ → 现代 10⁻¹² mbar·l/s。【教科书/综述】[DESY 讲稿 §6]

## 半导体封装检漏何时引入

- 最早的半导体器件（1950 年代初晶体管）即为气密封装。【二手综述】[DfR Solutions, "Keep it tight: understanding hermeticity", 2012](https://cdn2.hubspot.net/hubfs/1871852/DfR_Solutions_Website/Resources-Archived/Publications/2011-2013/Keeping-it-Tight-Understanding-Hermiticity-Global-SMT-12.12.pdf?t=1489786101638)
- 军标体系：MIL-STD-750（分立器件，Method 1071 Seal）、MIL-STD-883（微电路，Method 1014 Seal）、MIL-STD-202 均含氦细检漏（10⁻⁴~10⁻¹⁰ atm·cc/s）与粗检漏（氟碳化合物浸渍/气泡法）；MIL-STD-883 系由 MIL-S-19500、MIL-STD-750、MIL-STD-202C 在 1960 年代中后期整合而来。【一手文献（标准被引述）】[FDA 检验指南](https://www.fda.gov/inspections-compliance-enforcement-and-criminal-investigations/inspection-guides/hermetically-sealed-electronic-component-leak-detection)；[National Semiconductor 军品质保手册（OCR）](https://e2e.ti.com/cfs-file/__key/communityserverdiscussions-components-files/73/Legacy_5F00_National_5F00_Quality_5F00_Pgms_2D00_OCR.pdf)；[Oneida Research 综述](https://orslabs.com/wp-content/uploads/2025/08/Ultra_High_Advanced_Leak_Detection_with_the_HSHLD_model_310.pdf)
- 氦检漏作为封装细检漏主流手段的固化时间约在 1960 年代（Kr-85 放射性同位素法同期并存）。【教科书/综述】[Palomar/SST 对 TM1014 的解读](https://www.palomartechnologies.com/blog/methods-of-testing-device-hermeticity-according-to-mil-std-883j-and-beyond-part-2)
- MIL-STD-883 首版确切年份：未找到一手标准原件，行业普遍表述为 1968 年首发——【存疑未证（首版年份）】。

## 对低技术场景的价值

- 真空设备（区熔炉、扩散炉、蒸发台、质谱计本身）与器件封装的**定量**气密检测；皂泡法只有 10⁻⁴ mbar·l/s 量级，氦质谱起步 10⁻⁶ 且可定位漏点。
- 低技术替代链：氦贵可用**氩示踪**（空气中本底 0.93% 导致灵敏度差，但检大漏够用）；更低端用**皮拉尼规 + 丙酮/CO₂ 示踪**（热导变化法）或电离规示差法——全是 1920s 真空技术。【教科书/综述】[DESY 讲稿 §4.3]
- 氦源问题：氦从含氦天然气或加热独居石获得，属 1900s–1910s 技术（见第 04 节）。

---

# 02 小型磁偏转质谱计作气体纯度分析仪

## 原理年代与自造可行性

- Nier 1940 年设计 **60° 扇形磁偏转质谱计**，目的正是"常规同位素与气体分析"：取代此前 2 吨磁铁 + 5 kW 稳流电源的巨型仪器。史密森尼学会藏品说明明确记载此设计动机。【一手文献（博物馆藏品说明）】[Smithsonian, Nier Mass Spectrograph](https://www.si.edu/object/nier-mass-spectrograph%3Anmah_334890)
- 二战期间 Nier 团队按此设计建造 12 台质谱计用于重水氘浓度监测（水样电解-平衡法配套）。【一手文献（传记综述）】[Díaz-Galiano 2024, "Alfred Otto Carl Nier", PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC11311244/)
- 战后 Nier 型质谱计随曼哈顿计划解密扩散，催生 1940s 末–1960s 的分析质谱工业（CEC 21-103 等商品机）。同上 PMC 综述。
- **能否用 1930 年代技术自造：可以，且有人做过。** Taylor 1944 年改机用永磁体 + 干电池（B battery）作离子加速电源，电子轰击离子源——连电磁铁稳流电源都不需要。【一手文献（引述）】[Lehigh 学位论文](https://preserve.lehigh.edu/system/files/derivatives/coverpage/439339.pdf) 电子倍增管（1930s 末已有）可用可不用：不用时靠振簧静电计/检流计，灵敏度降至分压 10⁻⁶–10⁻⁷ 量级仍够工业气体分析。
- 最低配置清单：热阴极离子源、永磁扇形磁铁、单缝收集系统、静电计/电子管 DC 放大器、汞或油扩散泵机组、进样微漏阀。全部是真空电子管工业同期水平。

## 对超纯气体的杂质分析价值

- 用途：H₂ 中 O₂/N₂/H₂O、Ar 中 N₂/O₂、SiH₄/氯硅烷气氛中碳氢化合物与空气漏入的在线监测；真空系统残气分析（检漏之外的第二功能）。
- 检测极限量级：无倍增器的小磁偏转计对轻杂质典型分压检测限约 10⁻⁷–10⁻⁸ mbar 分压；折算到 1 atm 工艺气体约为 **0.1–1 ppmv 级**。用倍增器可到 ppbv。【教科书/综述——按仪器原理推算，未找到 1950s 商品机对高纯氢检测限的原始数据，标【存疑未证】具体数值】
- 半导体史上质谱用于气体纯度监控的明确年代锚点：未找到 1950s 硅厂用质谱在线分析超纯氢的一手记录。氦检漏（1945+）与残气分析（1950s 真空工业）是确证的近邻应用。【未找到——直接一手】

---

# 03 发射光谱分析与 ppb 级"纯度闭环"

## 原理年代与设备

- 原子发射光谱定性：Bunsen & Kirchhoff 1859–60；定量化的关键方法（内标法、匀称线对）由 Gerlach 等在 1920s 建立。电弧/火花源 + 摄谱仪在 1920s–30s 已是冶金工业常规装备。【教科书/综述】[安特卫普大学原子光谱讲义](https://medialibrary.uantwerpen.be/oldcontent/container2642/files/ac04atomic.pdf)；[Spectroscopy Online 原子光谱年表](https://www.spectroscopyonline.com/view/timeline-atomic-spectroscopy)
- **光栅 vs 棱镜**：分析用摄谱仪在 1950s 前主流是石英棱镜（Hilger 等商品机），因为紫外区玻璃/空气吸收，必须用石英；光栅（Rowland 1882 发明、Wood 1910s 闪耀光栅）需要刻线机，属国家级精密机械能力。**低技术场景选石英棱镜**——石英熔炼与光学冷加工是 19 世纪技术。【教科书/综述】[史密森尼 Littrow 摄谱仪藏品（1930s 用 Wood 闪耀光栅属前沿）](https://airandspace.si.edu/collection-objects/spectrograph-littrow/nasm_A19840176000)
- **感光板检测**： gelatin 溴化银干板（Maddox 1871 发明、1878 起商品化）+ 测微光度计（microphotometer）读黑度。与照相干板工业完全协同——这是"检测先行"里供应链最顺的一条。【教科书/综述】
- 激发源：直流电弧（石墨电极，样品装电极孔中）对非金属/粉末样品最通用；火花对导电金属样。电极用光谱纯石墨——本身是碳弧灯工业的副产品，19 世纪末有。【教科书/综述】[Clarkson 实验室分析手册](https://www.clarksonlab.com/CAPS.pdf)

## 1950s 半导体材料痕量分析的实际做法

- **光谱纯锗/硅的金属杂质**：直流电弧摄谱 + 化学富集（基体挥发分离：GeCl₄/SiCl₄ 蒸馏除基体后残渣摄谱）。多晶硅商品规格表（流传的手册数据）即标注金属杂质"低于紫外光谱检测限"，如 Fe<5 ppba、Ca<1 ppba——说明配富集手段的发射光谱可到 ppba 级。【教科书/手册】[UiO FYS4310 讲义（引半导体级三氯氢硅规格表）](http://tid.uio.no/kurs/fys4310/Handout_Purification_Si.pdf)
- **硼的化学法**：硼光谱灵敏度差、又是区熔最难除的杂质，1950s 实测主力是**姜黄素比色法**（curcumin）：C.L. Luke, "Determination of traces of boron in silicon, germanium, and germanium dioxide", *Anal. Chem.* 27, 1150 (1955)——直接针对半导体材料的 ppb 级硼。姜黄素-硼显色反应本身已被知道"超过一个世纪"（19 世纪）。【一手文献（题录被引）】[Standard Methods 2023 引文表](https://www.abpsoil.com/images/Standardmethod2023.pdf)；[Orient. J. Chem. 综述（"known for more than a century"）](https://www.orientjchem.org/pdf/vol37no3/OJC_Vol37_No3_p_695-699.pdf)
  - 姜黄素定量比色法本身：Silverman & Trego, *Anal. Chem.* 25, 1264 (1953)。【一手文献（题录被引）】同上
  - **次甲基蓝（亚甲基蓝）氟硼酸萃取比色法测硼**：检索到 Stanton & McDonald 1966 的引证；更早的 Ducret 1957（*Anal. Chim. Acta*）为该方法常见原始文献——【存疑未证（Ducret 卷期未直接核实）】。[HAL 学位论文方法综述](https://theses.hal.science/tel-04228531v1/file/HIEN-NGUYEN_Thi-Thu.pdf)
- **活化分析**：Hevesy & Levi 1936 年首创中子活化分析；**1955 年即被用于硅中痕量杂质**：*Anal. Chem.* 1955 年 5 月号（v27 no5）载文明确写道"因半导体电学性质受极微量杂质影响，本法被用于分析硅中痕量杂质……锗中 10⁹ 分之一的杂质原子即影响晶体管行为"（该期所载即 Morrison & Cosgrove 用闪烁谱仪做硅活化分析的经典工作）。【一手文献（原文扫描）】[Anal. Chem. 1955, 27(5) 扫描 PDF](http://lib3.dss.go.th/fulltext/scan_ebook/ana_1955_v27_no5.pdf)；[NIST 活化分析文献目录](https://nvlpubs.nist.gov/nistpubs/Legacy/TN/nbstechnicalnote467.pdf)；[IntechOpen NAA 综述（Hevesy & Levi 1936）](https://cdn.intechopen.com/pdfs/43467/InTech-Concepts_instrumentation_and_techniques_of_neutron_activation_analysis.pdf)
  - 局限：需要核反应堆/强中子源 + NaI 闪烁谱仪（1948+）——架空世界短期不可复制，列为"远期"。

## 历史上 9N 硅靠什么仪器闭环（直接回答）

证据指向一个**多层闭环**而非单一仪器：

1. **电学法为主闭环**：电阻率（四探针，Valdes 1954 / Smits 1958 BSTJ 37:711）+ 霍尔 + 冷热探针判导电型号，折算净施主/受主浓度到 10¹²–10¹³ cm⁻³（≈0.02–0.2 ppba）。贝尔实验室口述史明确承认电阻率会被"补偿"欺骗（等浓度施主+受主显得高阻），所以还要靠**能否拉成单晶**作经验判据——"我们从来没有用 ppm 来测量过它"（Tanenbaum 原话）。【一手文献（口述史）】[CHM 贝尔实验室硅研发口述史](https://archive.computerhistory.org/resources/access/text/2015/06/102702097-05-01-acc.pdf)；【一手文献（题录被引）】Smits 1958, [引自 Univaq 学位论文参考文献](https://ricerca.univaq.it/retrieve/6594fe1c-426c-4d22-85da-7d474bd6839c/PhD%20thesis%20Palleschi.pdf)
2. **比色法补硼**（Luke 1955，见上）。
3. **发射光谱 + 富集**测金属（ppba 级，见上 UiO 表）。
4. **活化分析**（1955+）作仲裁与多元素扫描；1960s TI 等将 NAA 作为硅器件工艺监控手段。【一手文献（NIST SP-337 收录 Larrabee & Carlson, TI）】[NIST SP-337, "Silicon Device Processing"](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nbsspecialpublication337.pdf)
5. **少子寿命**（光电导衰退法）监控复合中心（Cu、Fe、Au 等深能级），1950s 中期成为锗硅常规质量指标。【教科书/综述】
6. RRR 对硅不适用（半导体不服从 Matthiessen 定则的简单形式），RRR 是金属纯度判据（见第 04 节）。

结论：**"9N"这个概念在 1950s 主要靠电学测量反推 + 化学法点验关键杂质（B、P、金属）来闭环**，而非任何单一 ppb 级仪器。这对架空世界是好消息：电学闭环的设备门槛是 19 世纪的。

---

# 04 RRR 与低温电学测量

## 原理年代

- Matthiessen 定则（杂质散射与声子散射电阻率可加性）：1860s（Matthiessen & Vogt）。【教科书/综述】
- RRR（ρ(300K)/ρ(4.2K) 或 R(273K)/R(4.2K)）作为金属纯度与完整性判据：随液氦普及（1920s–30s 欧美实验室、1934 Kapitza 液化器）成为常规；现代定义（Nb、Cu 的 RRR 分级）见超导腔与高纯金属文献。【教科书/综述】[McGill 学位论文 §2.4（电阻率测纯度综述）](https://escholarship.mcgill.ca/downloads/v405s997r.pdf)；[DESY 高纯铌 RRR 报告](https://bib-pubdb1.desy.de/record/91801/files/TTC-Report%202010-02.pdf?version=2)
- 只测单点低温电阻也行：Ekin《Experimental Techniques for Low-Temperature Measurements》明确说"知道某材料剩余电阻率的最简单办法就是把线状样品浸在液氦里测一次"——【教科书】[Ekin 教材（UW 镜像）](https://wiki.physics.wisc.edu/ObsCos/images/e/ea/Ekin_ExperimentalTechniquesForLowTemperatureMeasurements.pdf)

## 液化气体的低技术史（年代锚点）

- 1877 Cailletet/Pictet 液化氧；1884 Wroblewski 氢雾；1892 Dewar 真空绝热杜瓦瓶；1895 Linde 空气液化专利（焦耳-汤姆逊节流 + 逆流换热）；1898 Dewar 液化氢（20 K，液空减压预冷 + J-T，~0.25 L/h）；1908 Kamerlingh Onnes 液化氦（4.2 K，液氢减压预冷）；1934 Kapitza 膨胀机氦液化器。【教科书/综述】[Cryogenics Society 低温史年表](https://cryogenicsociety-archive.org/2008/04/18/history_of_cryogenics/)；[《Cryogenic Engineering: Fifty Years of Progress》](https://content.e-bookshelf.de/media/reading/L-1544-b1ce2f2e0b.pdf)；[APS "This Month in Physics History"](https://www.aps.org/publications/apsnews/201201/physicshistory.cfm)
- 工程要素全部是 19 世纪机械技术：多级高压活塞压缩机（~200 atm）、逆流换热器、节流阀、真空夹层镀银玻璃杜瓦。氢液化需要先把氢预冷到其转化温度（~200 K）以下——用减压液空/液氮即可；氦液化需再用减压液氢预冷到 ~15 K。
- 氦源：加热独居石（monazite）释氦（1895 Ramsay 发现氦即由此）、或含氦天然气（1903 美国）。均属 19 世纪化学门槛。【教科书/综述】

## 架空世界可行性判断（推演，非史实）

- 液空/液氧：1750s 工业水平（高压压缩机 + 换热）**可成立**——Linde 装置本质是蒸汽机时代机械。
- 液氢：成立，但需耐低温材料（铜、黄铜）与氢安全规程；Dewar 首台即 0.25 L/h 实验室级。
- 液氦：**设备同样成立，瓶颈在氦气源**——若架空世界无含氦天然气田认知，则走独居石提氦路线（克级到升级产量，够实验用）。
- 半导体价值：金属互连/焊料/蒸发料的纯度独立判据（RRR 对杂质种类不敏感，是"总量"指标，恰与发射光谱的"分元素"互补）；低温霍尔/电阻率测量可分离杂质散射与缺陷散射。对硅锗本体则用低温霍尔测载流子冻析（freeze-out）曲线反推杂质能级与补偿度——1950s 常规手段。

---

# 05 色谱与离子交换纯化

## 气相色谱

- 1950-10-20 Martin & James 在生化学会第 290 次会议首次报告气-液分配色谱；1952 年 *Biochem. J.* 正式论文（James & Martin, 1952, 50/52 卷；分离脂肪酸/胺类）。1952-09 牛津第一届国际分析化学大会后迅速被工业界接受。【一手文献（题录/当事人口述）】[AOCS: Martin 自述](https://www.aocs.org/resource/development-of-gas-liquid-chromatography/)；[Chromatography Online 60 周年回顾](https://www.chromatographyonline.com/view/beginnings-gas-adsorption-chromatography-60-years-ago)
- 设备门槛：玻璃柱 + 固定液涂渍硅藻土担体 + 载气 + 检测器。Martin & James 原始检测器是**自动滴定装置**（对脂肪酸）；1954 后热导池（katharometer，19 世纪热丝原理）与 1958 火焰离子化检测器（FID）成为主流。热导池完全 19 世纪物理（惠斯通电桥 + 铂丝）。【教科书/综述】
- **对氯硅烷纯度分析的应用史：未找到确切首用年代的一手文献。** 已知：硅烷/氯硅烷体系腐蚀性要求特殊柱材料与进样系统；1960s 起 GC 成为氯硅烷工厂常规分析（SiHCl₃ 中 SiCl₄、SiH₂Cl₂、BCl₃、PCl₃ 等）。1950s 末商品化气相色谱仪普及后应用于挥发性氯化物是合理推断，但具体首篇文献未检索到——【存疑未证/未找到】。
- 低技术价值：氯硅烷分馏纯度的**过程分析**闭环（沸点相近的 SiHCl₃/BCl₃ 用蒸馏终点难以判断，GC 可在线分辨），配合热导池即 19 世纪检测物理 + 20 世纪初化学（硅藻土、固定液）。

## 离子交换树脂

- 1850 Thompson/Way 土壤离子交换现象；1905 Gans 沸石软化水；1935 Adams & Holmes 酚醛缩聚合成首批有机离子交换树脂（解决无机沸石怕酸问题）；1949 混床除盐首次商用。【教科书/综述】[François de Dardel, "History of ion exchange"](http://dardel.info/IX/other_info/history.html)；[WCP Online 离子交换水处理简史](https://wcponline.com/2014/02/21/a-brief-history-of-ion-exchange-water-treatment/)
- 半导体意义：超纯水（18 MΩ·cm）= 混床离子交换 + 终端膜过滤；试剂纯化（去金属离子）亦可用螯合树脂。门槛是有机合成（苯乙烯-二乙烯苯磺化，1944 后）或酚醛（1935 水平），非仪器门槛。
- 萃取色谱（extraction chromatography，TBP 等萃取剂固载于担体上做反相分配）：1950s 末–60s 在放射化学/稀土分离中发展。对架空世界的价值：超纯试剂中特定金属的选择性富集分离，设备即玻璃柱。一手年代锚点未细查——【教科书/综述，具体首创年代存疑未证】。

---

# 06 微孔滤膜

- 1918 Zsigmondy & Bachmann 发表硝酸纤维素（collodion）微孔膜小量制备法；孔径由聚合物浓度调控的思想可溯至 Bechhold 1906；1926 年 Membranfilter GmbH 成立，商品化火棉胶微滤膜（Sartorius 等按 Zsigmondy 专利生产）。【一手文献（题录被引）/教科书】[accedaCRIS 膜史综述](https://accedacris.ulpgc.es/bitstream/10553/7740/4/0666268_00000_0000.pdf)；[R.W. Baker《Membrane Technology and Applications》](https://dadiirawan.wordpress.com/wp-content/uploads/2014/06/membrane_technology_and_applications1-_2nd_edition__2004__-_r-w-baker.pdf)
- 1954 Jack Bush 创立 Millipore Filter Corporation，将相转化法制膜工业化，随后成为超纯水/无菌过滤事实标准。【二手综述（公司史）】[Company-Histories: Millipore](https://www.company-histories.com/Millipore-Corporation-Company-History.html)
- 半导体意义：超纯水与工艺化学品的**终端（point-of-use）颗粒过滤**（0.05–0.45 µm），是洁净室水系统最后一道关；MF 膜可除 0.1–10 µm 颗粒。【教科书】[ThaiJO MF 综述](https://li01.tci-thaijo.org/index.php/cast/article/download/256991/177159)
- **自制难度评估（推演）**：硝酸纤维素（硝化棉，1846 年即有）溶于醚-醇浇铸、控制湿度/蒸发速率成膜——纯 19 世纪化学 + 环境控制；孔径均一性与无缺陷大面积成膜是工艺难点（Zsigmondy 本人即因均一性问题走向商品化合作）。判定：**实验室级自制可行，工业级均一膜需工艺攻关**，但无任何"超前设备"。

---

# 07 清洗化学的现代配方（全系 19 世纪试剂确认）

## RCA 清洗

- Werner Kern 于 1965 年在 RCA 开发（合作者 D. Puotinen），1970 年正式发表：W. Kern & D. Puotinen, "Cleaning solutions based on hydrogen peroxide for use in silicon semiconductor technology", *RCA Review* 31, 187–206 (1970)。该文后被 *Current Contents* 列为 Citation Classic（1983 年重印附 Kern 回顾）。【一手文献】[日本半导体历史馆展品说明](https://www.shmj.or.jp/english/pdf/em/exhibi2432E.pdf)；[1983 年 RCA 重印本（UIUC 镜像）](https://fabweb.ece.illinois.edu/lab/manual/op_proc_sp2013.pdf)
- 配方（教科书通行版）：
  - **SC-1**（标准 1 号洗液）：NH₄OH : H₂O₂ : H₂O = 1:1:5（体积比），75–80 °C，10–15 min。去颗粒与有机物：碱性双氧水氧化有机膜并使其溶于水；对 Si 表面轻微腐蚀-再氧化产生 zeta 电位排斥颗粒。
  - **SC-2**：HCl : H₂O₂ : H₂O = 1:1:6，75–80 °C。去金属离子（碱金属、Al³⁺、Fe³⁺、Mg²⁺ 等，形成可溶性氯化物配合物）；对 Au、Cu 等不完全有效（靠前道 SPM/王水类处理）。
  - 原理要点：两步均生长薄水合氧化层（~1 nm 化学氧化硅）钝化表面；zeta 电位防颗粒再沉积。【教科书】[Plummer《VLSI 工艺》第 4 章（IITB 镜像）](https://www.ee.iitb.ac.in/student/~manikandan/share/J%20Plummer%20VLSI/CH4.pdf)
- **试剂年代确认**：氨水（古代即得）、盐酸（中世纪/17 世纪工业）、双氧水（Thenard 1818）、硫酸（铅室法 1746）——**全部 19 世纪前工业试剂，确认**。稀缺的只是"配方与机理知识"本身。这正是"现代思想低技术化"的最纯粹案例。

## SPM / Piranha

- H₂SO₄ : H₂O₂ 典型 3:1，混合即生成过一硫酸（Caro's acid，H₂SO₅——Baeyer/Villiger 时代已知，Caro 1898），强放热、氧化一切有机残渣并氧化多数金属。半导体去胶/重垢清洗主力。【教科书】[Modutek 工艺说明](https://www.modutek.com/how-piranha-etch-is-used-in-silicon-wafer-cleaning/)；Caro 酸年代标【教科书】
- 半导体行业引入 SPM 的准确年代：未找到一手；1970s 随 RCA 清洗体系普及属合理推断——【存疑未证】。

## TMAH 显影液

- 四甲基氢氧化铵 N(CH₃)₄OH，2.38%（25 °C 下 0.26 N）水溶液为正性光刻胶标准显影液；取代早期 KOH/NaOH 显影液的根本原因是**无金属离子**（Na⁺ 是 MOS 死敌）。【教科书】
- 制备路线与难度：
  1. 三甲胺 + 氯甲烷 → 四甲基氯化铵（Menschutkin 反应，19 世纪有机化学；三甲胺可由甜菜碱/甲醛铵盐路线获得，Hofmann 1851 年已系统研究胺的甲基化）；
  2. Me₄NCl + Ag₂O（湿氧化银）搅拌 → TMAH + AgCl↓（经典实验室法，19 世纪即有）；
  3. 现代工业：电解/电渗析法（离子膜电解槽，20 世纪技术）。
  - 判定：路线 1+2 全系 19 世纪化学，**自制可行**；代价是银盐消耗（可回收）与痕量 Ag/Cl 控制。【教科书——各步反应年代为常识性化学史，未逐一核一手文献】

---

# 08 吸杂（gettering）

- **磷扩散吸杂**的概念源头：Goetzberger & Shockley, *J. Appl. Phys.* 31, 1821 (1960)——发现重磷（或硼）预淀积区可吸收金属杂质，防止其在 p-n 结处沉淀造成软击穿特性。这被广泛引为吸杂技术的经典起点。【一手文献（题录被引）】[JAP 1984 吸杂比较综述引文](https://pubs.aip.org/aip/jap/article/55/2/579/503004/)；[Lehigh 学位论文引文](https://preserve.lehigh.edu/system/files/derivatives/coverpage/425484.pdf)
- 机理：重掺层提高金属固溶度 + 失配位错/磷空位对提供沉淀点；降温时金属向高固溶度区分凝。太阳能级多晶硅至今靠磷吸杂提寿命。【教科书/综述】[pv-manufacturing.org](https://pv-manufacturing.org/solar-cell-manufacturing/gettering/)
- **背面损伤吸杂（extrinsic/backside damage）**：背面喷砂/划伤/多晶硅沉积产生位错网作为金属沉淀汇，1970s 成为 MOS 产线常规。具体首篇文献未核——【教科书，年代存疑未证】。
- **本征吸杂（intrinsic gettering）**：利用 CZ 硅中间隙氧经高温-低温-高温三步热处理在体内析出 SiO₂ 沉淀 + 层错（BMD），同时近表面形成洁净区（denuded zone）；概念由 Tan 等 1977 年系统提出（T.Y. Tan et al., *Appl. Phys. Lett.* 30, 175, 1977——卷期为常识引用，未直接核原文，标【教科书/综述】）。[NIH 磷吸杂论文引言提及本征吸杂概念归属](https://pmc.ncbi.nlm.nih.gov/articles/PMC3499143/)
- **氯/HCl 气氛氧化吸杂**：氧化气氛中加 HCl（或 TCE/TCA），Cl 与金属形成挥发性氯化物随气流带走，并钝化氧化层中 Na⁺；Nakamura 等 1968（JJAP 7:512）报道金属杂质吸杂效应研究；氯作用机理综述见 Baginski & Monkowski, *JES* 132, 2031 (1985)。【一手文献（题录被引）】[《Crystal Growth and Evaluation of Silicon for VLSI/ULSI》引文表](https://cetiquimica2.files.wordpress.com/2014/08/kry5t4l_6r0wth_51l1k0n.pdf)
- **低技术价值**：这是"补救低质量晶圆"的核心工艺包——设备即普通扩散炉 + POCl₃ 源（19 世纪化学品）/ HCl 气。对架空世界的意义：**材料纯度闭环未完全建立时，吸杂能把器件级硅的有效寿命提高一个量级**，相当于用工艺知识替代材料纯度。

---

# 09 霍尔/电学测试的现代化

## 锁相放大器

- 相敏检波/锁相放大的发明一般归于 **Robert Dicke，1946 年**（普林斯顿）；1961 年 Princeton Applied Research 成立，1962 年首台商品机 HR-8（电子管/晶体管模拟机）。【教科书/综述】[Princeton 信号恢复讲义](https://www.princeton.edu/~romalis/PHYS210/SignalRecovery.pdf)；[UIUC 讲义（PAR 公司史）](https://courses.physics.illinois.edu/phys403/fa2017/lectures/lock-in_2.pdf)
- 原理：信号被已知频率调制（机械斩波器/交流励磁），与参考信号相乘后低通滤波，等效噪声带宽压到 ~1/(4τ)，可把埋在噪声下 60 dB 的信号取出。
- 低技术实现：机械斩波器本身就是开关解调器（换向式斩波放大器，1940s 仪器工业已有）；变压器耦合 + 同步检波全电子管可实现。**无任何元件超出 1930s**。
- 价值：霍尔电压（µV 级）、热电势、低温电阻率等弱信号测量的精度跃升；配合交流法消除热电势漂移误差。

## 范德堡法

- L.J. van der Pauw, "A method of measuring specific resistivity and Hall effect of discs of arbitrary shape", *Philips Res. Repts* 13, 1–9 (1958)；姊妹篇 *Philips Tech. Rev.* 20, 220–224 (1958)。【一手文献】[原文 PDF（中科院半导体所镜像）](http://bdt.semi.ac.cn/library/upload/files/2021/7/131545415.pdf)
- 内容：任意形状薄片 + 边缘四个点接触，两次电阻测量解出电阻率（含修正因子），叠加磁场测霍尔系数；免除了规则切割样品的麻烦。
- 低技术价值：直接对手头不规则晶片/单晶碎料做电阻率与载流子浓度、迁移率测量——**把"制样门槛"从精密切片降到点四个铟点/压四根探针**。配套只需恒流源、电位差计/检流计、永磁铁。
- 前史：直线四探针 Valdes 1954（Proc. IRE）；四探针层电阻修正 Smits 1958。【一手文献（题录被引）】[Univaq 论文引文](https://ricerca.univaq.it/retrieve/6594fe1c-426c-4d22-85da-7d474bd6839c/PhD%20thesis%20Palleschi.pdf)

---

# 10 火焰光度 / 原子吸收（钠沾污监控）

## 为什么钠是 MOS 死敌（背景锚点）

- SiO₂ 中 Na⁺ 在栅偏压-温度应力下迁移，造成阈值电压漂移；1960s 中期（Fairchild/Bell，Snow 等 1965 年前后）确认为 MOS 不稳定性的首要原因。偏压-温度应力（BTS）试验 + C-V 测量是监控手段本身。此处具体首篇文献未逐一核——【教科书/综述，一手未核】。

## 火焰光度计

- 1929 Lundegårdh 将空气-乙炔火焰 + 气动雾化器组合用于火焰发射光谱，火焰光度法成熟；对 Na、K 的灵敏度达 ppm–ppb 级（Na 589 nm 双线极易激发）。【教科书/综述】[Spectroscopy Online 原子光谱年表](https://www.spectroscopyonline.com/view/timeline-atomic-spectroscopy)
- 最低配置：雾化器 + 本生/空气-乙炔焰 + 滤光片或小单色器 + 硒光电池/光电管。全系 1930s 前技术。对石英器皿、HF、双氧水、水中的 Na 监控直接可用。

## 原子吸收光谱（AAS）

- Alan Walsh（CSIRO）1955 年发表经典论文（*Spectrochim. Acta* 7, 108），提出用原子吸收做定量分析；1956 年 Shelton & Walsh 在里斯本 IUPAC 大会首次展示仪器；专利 1953 年底提交，1954 年 3 月墨尔本公开演示。【一手文献（题录/当事方回顾）】[Analyst 1979 回顾（扫描）](http://lib3.dss.go.th/fulltext/scan_ebook/anal_1979_v106_no2.pdf)；[e-PGPathshala 讲义](https://epgp.inflibnet.ac.in/epgpdata/uploads/epgp_content/S000944AC/P001632/M028138/ET/1520579859Q1M1.pdf)
- 关键思想（1955 年才有的"稀缺物"）：**用被测元素自身的锐线光源（空心阴极灯）+ 光源调制**，绕开对高分辨单色器的需求，并把火焰连续发射噪声排除在测量带宽外。【教科书/综述】同上
- 最低配置：
  - **空心阴极灯**：Paschen 1916 年即描述；钠灯用玻璃吹制 + 钠阴极 + 氖/氩充填，真空工业常规。【教科书/综述】[Lajunen《Spectrochemical Analysis》历史表（PDFCoffee 镜像）](https://pdfcoffee.com/spectrochemical-analysis-by-atomic-absorption-and-emission-lajunen-2nd-edition-2004-4-pdf-free.html)
  - 火焰原子化器：空气-乙炔（1929 年组合，见上）；
  - 单色器：小棱镜/光栅单色器（只需分开 589 nm 与邻近线，分辨率要求极低）；
  - 检测：光电管 + 选频放大（即锁相思想，斩波调制光源即可）。
  - 判定：**全部部件为 1910s–30s 技术**，AAS 是"思想 1955、设备 1930"的典型案例，架空世界可整体提前。
- 对 Na 的检测限：火焰 AAS 测 Na 常规 0.01–0.1 ppm 级（火焰光度法对 Na 更灵敏，可至 ppb）；对 MOS 工艺监控（BOE 缓冲液、石英、清洗剂中的 Na）够用。【教科书——具体检测限数值按手册常识，未逐一核一手】

---

# 附：本调研"未找到/存疑"清单

1. MIL-STD-883 首版确切年份（行业通说 1968，未核标准原件）。【存疑未证】
2. 1950s 硅厂用质谱计在线分析超纯氢/氩的一手记录（仅有氦检漏与残气分析的近邻证据）。【未找到】
3. 小磁偏转质谱计对 1 atm 高纯气体的杂质检测限原始数据（0.1–1 ppmv 为原理推算值）。【存疑未证】
4. 气相色谱用于氯硅烷/硅烷纯度分析的首篇文献与年代（1960s 常规化为推断）。【未找到】
5. 萃取色谱（TBP 固载）首创年代一手文献。【存疑未证】
6. SPM（Piranha）引入半导体清洗的准确年代与首篇文献（1970s 为推断）。【存疑未证】
7. 背面损伤吸杂的首篇文献与引入产线年代（1970s 为通说）。【存疑未证】
8. Tan et al. 1977 本征吸杂原文卷期（Appl. Phys. Lett. 30, 175 为常识引用，未直接核）。【存疑未证】
9. MOS 钠不稳定性首篇确认文献（Snow et al. 1965 为通说，未核原文）。【存疑未证】
10. Ducret 1957 次甲基蓝测硼原文卷期（Stanton & McDonald 1966 有引证）。【存疑未证】
11. 氦细检漏进入晶体管军标（MIL-STD-750 Method 1071 前身）的准确年份（1960s 为推断）。【存疑未证】
