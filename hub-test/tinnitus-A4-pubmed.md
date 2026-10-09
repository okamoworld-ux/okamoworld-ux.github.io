# 臨床班調査「耳鳴」— 手段 A4：PubMed 検索

- 実施日：2026-10-09（PubMed build 2026.10.09.00.26）
- 到達確認：`einfo.fcgi?db=pubmed` に 1 回 → HTTP 200（前回の 403 から解消）。そのまま本番を実施。
- やり方：CQ ごとに検索式 1 本で `esearch`（`sort=relevance`＝Best Match、`retmax`＝指定本数）→ 返った PMID を 1 回の `esummary` に渡し、題名・年・雑誌・DOI をそのまま写した（確かめ直しなし）。抄録・PDF・患者情報は取っていない。他の手段（Consensus 等）は使っていない。
- 本数：CQ5 は全体のヒットが 19 件しかなく、指定の 30 本に届かなかった（19 本すべてを採用）。

## CQ ごとの検索式／ヒット数／採った本数

耳鳴の部分 `T` ＝ `("Tinnitus"[Majr] OR tinnitus[ti])`（耳鳴を主題とする文献に絞る）

| CQ | 検索式 | ヒット数 | 採った本数（指定） |
|---|---|---|---|
| CQ1 慢性耳鳴の薬物療法のエビデンス（ガイドライン・薬ごとの SR） | `T AND ("Drug Therapy"[sh] OR pharmacotherap*[tiab] OR pharmacological[tiab] OR antidepressant*[tiab] OR anticonvulsant*[tiab] OR antiepileptic*[tiab] OR benzodiazepine*[tiab] OR betahistine[tiab] OR ginkgo[tiab] OR zinc[tiab] OR melatonin[tiab] OR lidocaine[tiab] OR steroid*[tiab] OR corticosteroid*[tiab] OR NMDA[tiab] OR guideline*[ti]) AND (guideline[pt] OR practice guideline[pt] OR systematic review[pt] OR meta-analysis[pt] OR "systematic review"[tiab] OR "meta-analysis"[tiab] OR guideline*[ti] OR Cochrane[tiab])` | 94 | 50（50） |
| CQ2 薬物療法の効果の時間経過（THI 等の推移・プラセボ反応） | `T AND ("Placebo Effect"[MeSH] OR "placebo response"[tiab] OR "placebo effect"[tiab] OR "time course"[tiab] OR trajector*[tiab] OR "natural history"[tiab] OR "natural course"[tiab] OR "Tinnitus Handicap Inventory"[tiab] OR THI[tiab]) AND ("Drug Therapy"[sh] OR placebo*[tiab] OR pharmacolog*[tiab] OR drug*[tiab])` | 215 | 30（30） |
| CQ3 加齢性難聴に伴う耳鳴への補聴器・人工内耳・サウンドジェネレータ（薬との比較・併用） | `T AND ("Presbycusis"[MeSH] OR presbycusis[tiab] OR "age-related hearing loss"[tiab] OR "hearing loss"[tiab]) AND ("Hearing Aids"[MeSH] OR "hearing aid*"[tiab] OR "Cochlear Implants"[MeSH] OR "cochlear implant*"[tiab] OR "sound generator*"[tiab] OR "sound therapy"[tiab])` | 355 | 30（30） |
| CQ4 新しい薬と神経調節（二刺激・rTMS・tDCS・VNS・Kv7） | `T AND (bimodal[tiab] OR Lenire[tiab] OR "Transcranial Magnetic Stimulation"[MeSH] OR "transcranial magnetic stimulation"[tiab] OR rTMS[tiab] OR "Transcranial Direct Current Stimulation"[MeSH] OR "transcranial direct current"[tiab] OR tDCS[tiab] OR "Vagus Nerve Stimulation"[MeSH] OR "vagus nerve stimulation"[tiab] OR VNS[tiab] OR Kv7[tiab] OR KCNQ[tiab] OR retigabine[tiab] OR "novel drug*"[tiab] OR "drug development"[tiab])` | 487 | 30（30） |
| CQ5 急性（3 か月未満）と慢性でエビデンスを分けているか・それぞれの薬物療法 | `T AND (acute[tiab] OR "recent onset"[tiab] OR "recent-onset"[tiab] OR "early stage"[tiab]) AND chronic*[tiab] AND (guideline[pt] OR practice guideline[pt] OR guideline*[tiab] OR systematic review[pt] OR meta-analysis[pt] OR "Drug Therapy"[sh] OR pharmacotherap*[tiab])` | 19 | 19（30） |

**検索式の手直しを 1 回した**：最初は `T` を `("Tinnitus"[MeSH] OR tinnitus[tiab])` として回した（ヒット数 CQ1 226・CQ2 260・CQ3 689・CQ4 606・CQ5 37）。しかし Best Match の上位に、耳鳴が症状の 1 つとして出てくるだけの文献（メニエール病・突発性難聴の GL・頭蓋内圧亢進症・Q 熱など）が多く混ざった。そこで耳鳴を主題とする文献だけに絞り直し、その結果を下に載せた。最初の結果は使っていない。

**種類の付け方**：esummary の `pubtype` に Guideline / Practice Guideline があれば GL、Systematic Review / Meta-Analysis があれば SR、Randomized Controlled Trial があれば RCT。`pubtype` で決まらないときは、題名に guideline / consensus statement があれば GL、systematic review / meta-analy があれば SR とした。どれにも当たらなければ「その他」。Cochrane レビューの多くは `pubtype` で SR になる。一方、題名に「guideline」とあるだけの論評・返信も GL になる（例：27654612/27654616）。種類は機械的に付けたもので、目安として見てほしい。

**気づいたこと（あとで PMID 集合を比べるときの参考）**
- CQ1：AAO-HNS 2014（25273878・25274374）、Cima 2019 欧州 GL（30847513）、独 S3 改訂（38830358）、US VA/DoD 2025（40111327）は上位 50 本に入った。日本聴覚医学会 2019 と NICE NG155 は入らなかった（NICE は PubMed に収載されていない見込み）。
- CQ3：Best Match の上位には耳鳴全般の総説が多く、補聴器・人工内耳に絞った研究は少なかった。この 1 本の式では、補聴器などの個別研究を取り込む力が弱い。
- CQ5：急性と慢性を分けて扱う文献は、PubMed の題名・抄録ではまれだった（19 件）。ドイツ語の文献が目立つ。

## CQ1　慢性耳鳴の薬物療法のエビデンス（ガイドライン・薬ごとの SR）

ヒット 94 件中、関連の高い順に 50 本（GL 15・SR 28・RCT 0・その他 7）

| # | PMID | DOI | 題名 | 年 | 雑誌 | 種類 |
|---|---|---|---|---|---|---|
| 1 | 39138756 | 10.1007/s10162-024-00960-3 | The Current State of Tinnitus Diagnosis and Treatment: a Multidisciplinary Expert Perspective. | 2024 | J Assoc Res Otolaryngol | その他 |
| 2 | 25273878 | 10.1177/0194599814545325 | Clinical practice guideline: tinnitus. | 2014 | Otolaryngol Head Neck Surg | GL |
| 3 | 30908589 | 10.1002/14651858.CD013093.pub2 | Betahistine for tinnitus. | 2018 | Cochrane Database Syst Rev | その他 |
| 4 | 25328113 | （記録になし） | Tinnitus. | 2014 | BMJ Clin Evid | SR |
| 5 | 36827524 | 10.1002/14651858.CD015171.pub2 | Systemic pharmacological interventions for Ménière's disease. | 2023 | Cochrane Database Syst Rev | SR |
| 6 | 22331367 | （記録になし） | Tinnitus. | 2012 | BMJ Clin Evid | SR |
| 7 | 21726476 | （記録になし） | Tinnitus. | 2009 | BMJ Clin Evid | SR |
| 8 | 21735419 | 10.1002/14651858.CD007960.pub2 | Anticonvulsants for tinnitus. | 2011 | Cochrane Database Syst Rev | SR |
| 9 | 19454115 | （記録になし） | Tinnitus. | 2007 | BMJ Clin Evid | SR |
| 10 | 40111327 | 10.1001/jamaoto.2025.0052 | Clinical Practice Guideline for Management of Tinnitus: Recommendations From the US VA/DOD Clinical Practice Guideline Work Group. | 2025 | JAMA Otolaryngol Head Neck Surg | GL |
| 11 | 25316368 | （記録になし） | [Tinnitus guidelines and treatment]. | 2014 | Ugeskr Laeger | GL |
| 12 | 30847513 | 10.1007/s00106-019-0633-7 | A multidisciplinary European guideline for tinnitus: diagnostics, assessment, and treatment. | 2019 | HNO | GL |
| 13 | 30339143 | 10.5867/medwave.2018.06.7294 | Ginkgo biloba for the treatment of tinnitus. | 2018 | Medwave | その他 |
| 14 | 27879981 | 10.1002/14651858.CD009832.pub2 | Zinc supplementation for tinnitus. | 2016 | Cochrane Database Syst Rev | SR |
| 15 | 23543524 | 10.1002/14651858.CD003852.pub3 | Ginkgo biloba for tinnitus. | 2013 | Cochrane Database Syst Rev | SR |
| 16 | 21177640 | 10.1177/0163278710390355 | Clinical guidelines and practice: a commentary on the complexity of tinnitus management. | 2011 | Eval Health Prof | GL |
| 17 | 33255533 | 10.3390/audiolres10020010 | Chronic Primary Tinnitus: A Management Dilemma. | 2020 | Audiol Res | その他 |
| 18 | 29192525 | 10.1080/14992027.2017.1405288 | Caring for musicians' ears: insights from audiologists and manufacturers reveal need for evidence-based guidelines. | 2018 | Int J Audiol | GL |
| 19 | 27654616 | 10.1001/jama.2016.11908 | Guidelines for Tinnitus-Reply. | 2016 | JAMA | GL |
| 20 | 27654612 | 10.1001/jama.2016.11905 | Guidelines for Tinnitus. | 2016 | JAMA | GL |
| 21 | 36383762 | 10.1002/14651858.CD013514.pub2 | Ginkgo biloba for tinnitus. | 2022 | Cochrane Database Syst Rev | SR |
| 22 | 36102987 | 10.1007/s00405-022-07645-8 | The effect of lidocaine iontophoresis for the treatment of tinnitus: a systematic review. | 2023 | Eur Arch Otorhinolaryngol | SR |
| 23 | 17054188 | 10.1002/14651858.CD003853.pub2 | Antidepressants for patients with tinnitus. | 2006 | Cochrane Database Syst Rev | SR |
| 24 | 22972065 | 10.1002/14651858.CD003853.pub3 | Antidepressants for patients with tinnitus. | 2012 | Cochrane Database Syst Rev | SR |
| 25 | 37599251 | 10.3760/cma.j.cn115330-20221023-00626 | [Comparison of guidelines on tinnitus]. | 2023 | Zhonghua Er Bi Yan Hou Tou Jing Wai Ke Za Zhi | GL |
| 26 | 39844318 | 10.1097/01.NPR.0000000000000274 | Tinnitus, the phantom sound: A review of history and guidelines for care. | 2025 | Nurse Pract | GL |
| 27 | 35239301 | 10.5935/0946-5448.20210030 | Ozonetherapy In The Treatment Of Nocturnal Tinnitus. | 2022 | Int Tinnitus J | SR |
| 28 | 32134348 | 10.1080/14992027.2020.1733677 | A process for prioritising systematic reviews in tinnitus. | 2020 | Int J Audiol | SR |
| 29 | 37176527 | 10.3390/jcm12093087 | Tinnitus Guidelines and Their Evidence Base. | 2023 | J Clin Med | GL |
| 30 | 25274374 | 10.1177/0194599814547475 | Clinical practice guideline: tinnitus executive summary. | 2014 | Otolaryngol Head Neck Surg | GL |
| 31 | 30522352 | 10.1080/14728214.2018.1555240 | An update: emerging drugs for tinnitus. | 2018 | Expert Opin Emerg Drugs | その他 |
| 32 | 26100030 | 10.1007/s00405-015-3689-3 | Intratympanic corticosteroids injections: a systematic review of literature. | 2016 | Eur Arch Otorhinolaryngol | SR |
| 33 | 25858126 | 10.1017/S0022215115000808 | The use of benzodiazepines for tinnitus: systematic review. | 2015 | J Laryngol Otol | SR |
| 34 | 15106224 | 10.1002/14651858.CD003852.pub2 | Ginkgo biloba for tinnitus. | 2004 | Cochrane Database Syst Rev | SR |
| 35 | 27995315 | 10.1007/s00405-016-4401-y | A multidisciplinary systematic review of the treatment for chronic idiopathic tinnitus. | 2017 | Eur Arch Otorhinolaryngol | SR |
| 36 | 28723605 | 10.5935/0946-5448.20170013 | Tinnitus Patients Suffering from Anxiety and Depression: A Review. | 2017 | Int Tinnitus J | SR |
| 37 | 21940981 | 10.1044/1059-0889(2011/10-0041) | Gabapentin for tinnitus: a systematic review. | 2011 | Am J Audiol | SR |
| 38 | 24049842 | （記録になし） | （記録になし） | 2013 | （記録になし） | その他 |
| 39 | 33931188 | 10.1016/bs.pbr.2021.01.022 | Evidence for biological markers of tinnitus: A systematic review. | 2021 | Prog Brain Res | SR |
| 40 | 38830358 | 10.1055/a-1994-5307 | [S3-Guideline Chronic Tinnitus - Update]. | 2024 | Laryngorhinootologie | GL |
| 41 | 35323825 | 10.5867/medwave.2022.02.8695 | Intratympanic gentamicin compared with placebo for Ménière's disease. | 2022 | Medwave | SR |
| 42 | 42810932 | 10.1016/j.otc.2026.08.005 | Audiologic Assessment of Tinnitus: Integrating Contemporary Clinical Practice and International Guideline Recommendations. | 2026 | Otolaryngol Clin North Am | GL |
| 43 | 34566871 | 10.3389/fneur.2021.726803 | Treatment of Tinnitus in Children-A Systematic Review. | 2021 | Front Neurol | SR |
| 44 | 21671234 | 10.1002/lary.21825 | Systematic review and meta-analyses of randomized controlled trials examining tinnitus management. | 2011 | Laryngoscope | SR |
| 45 | 22902416 | 10.1097/MOO.0b013e328357a6c8 | Endolymphatic hydrops perspectives 2012. | 2012 | Curr Opin Otolaryngol Head Neck Surg | その他 |
| 46 | 34611615 | 10.1016/j.eclinm.2021.101080 | Efficacy of pharmacologic treatment in tinnitus patients without specific or treatable origin: A network meta-analysis of randomised controlled trials. | 2021 | EClinicalMedicine | SR |
| 47 | 11678946 | 10.1046/j.1365-2273.2001.00490.x | Guidelines for the grading of tinnitus severity: the results of a working group commissioned by the British Association of Otolaryngologists, Head and Neck Surgeons, 1999. | 2001 | Clin Otolaryngol Allied Sci | GL |
| 48 | 21857784 | 10.2147/NDT.S22793 | Ginkgo biloba extract in the treatment of tinnitus: a systematic review. | 2011 | Neuropsychiatr Dis Treat | SR |
| 49 | 34293623 | 10.1016/j.amjoto.2021.103116 | The efficacy of acoustic therapy versus oral medication for chronic tinnitus: A meta-analysis. | 2021 | Am J Otolaryngol | SR |
| 50 | 34233329 | 10.1159/000515821 | Betahistine in Ménière's Disease or Syndrome: A Systematic Review. | 2022 | Audiol Neurootol | SR |

## CQ2　薬物療法の効果の時間経過（THI 等の推移・プラセボ反応）

ヒット 215 件中、関連の高い順に 30 本（GL 0・SR 8・RCT 8・その他 14）

| # | PMID | DOI | 題名 | 年 | 雑誌 | 種類 |
|---|---|---|---|---|---|---|
| 1 | 30908589 | 10.1002/14651858.CD013093.pub2 | Betahistine for tinnitus. | 2018 | Cochrane Database Syst Rev | その他 |
| 2 | 24622859 | 10.3766/jaaa.25.1.3 | Medical management of tinnitus: role of the physician. | 2014 | J Am Acad Audiol | その他 |
| 3 | 31795642 | 10.1121/1.5132551 | Blast-induced tinnitus: Animal models. | 2019 | J Acoust Soc Am | その他 |
| 4 | 21735419 | 10.1002/14651858.CD007960.pub2 | Anticonvulsants for tinnitus. | 2011 | Cochrane Database Syst Rev | SR |
| 5 | 34303210 | 10.1016/j.amjoto.2021.103151 | Efficacy of tinnitus retraining therapy in the treatment of tinnitus: A meta-analysis and systematic review. | 2021 | Am J Otolaryngol | SR |
| 6 | 15106224 | 10.1002/14651858.CD003852.pub2 | Ginkgo biloba for tinnitus. | 2004 | Cochrane Database Syst Rev | SR |
| 7 | 21975776 | 10.1002/14651858.CD007946.pub2 | Repetitive transcranial magnetic stimulation for tinnitus. | 2011 | Cochrane Database Syst Rev | SR |
| 8 | 21673362 | （記録になし） | Drug-mediated ototoxicity and tinnitus: alleviation with melatonin. | 2011 | J Physiol Pharmacol | その他 |
| 9 | 31926598 | 10.1016/j.amjoto.2020.102390 | The effect of fibromyalgia treatment on tinnitus. | 2020 | Am J Otolaryngol | その他 |
| 10 | 18522937 | 10.1093/bja/aen137 | I.V. ropivacaine compared with lidocaine for the treatment of tinnitus. | 2008 | Br J Anaesth | RCT |
| 11 | 19865063 | （記録になし） | The effects of alprazolam on tinnitus: a cross-over randomized clinical trial. | 2009 | Med Sci Monit | RCT |
| 12 | 38788246 | 10.1016/j.bjorl.2024.101438 | Non-invasive treatments improve patient outcomes in chronic tinnitus: a systematic review and network meta-analysis. | 2024 | Braz J Otorhinolaryngol | SR |
| 13 | 23543524 | 10.1002/14651858.CD003852.pub3 | Ginkgo biloba for tinnitus. | 2013 | Cochrane Database Syst Rev | SR |
| 14 | 28393057 | （記録になし） | Short-Term Effect of Gabapentin on Subjective Tinnitus in Acoustic Trauma Patients. | 2017 | Iran J Otorhinolaryngol | その他 |
| 15 | 17114152 | 10.1080/03655230600895465 | Effects of repetitive transcranial magnetic stimulation (rTMS) on chronic tinnitus. | 2006 | Acta Otolaryngol Suppl | その他 |
| 16 | 18359360 | 10.1016/j.otohns.2007.11.027 | Tinnitus treatment with memantine. | 2008 | Otolaryngol Head Neck Surg | RCT |
| 17 | 25066140 | 10.1016/j.amjoto.2014.06.009 | Intratympanic dexamethasone plus melatonin versus melatonin only in the treatment of unilateral acute idiopathic tinnitus. | 2014 | Am J Otolaryngol | RCT |
| 18 | 25080038 | 10.1097/MAO.0000000000000526 | Prognostic factors for the outcomes of intratympanic dexamethasone in the treatment of acute subjective tinnitus. | 2014 | Otol Neurotol | その他 |
| 19 | 32861124 | 10.1016/j.amjoto.2020.102680 | Proficiency of virtual follow-up amongst tinnitus patients who underwent intratympanic steroid therapy amidst COVID 19 pandemic. | 2020 | Am J Otolaryngol | その他 |
| 20 | 25413777 | （記録になし） | Medical and surgical treatments for tinnitus: the efficacy of combined treatment with sulodexide and melatonin. | 2015 | J Neurosurg Sci | その他 |
| 21 | 35741602 | 10.3390/brainsci12060719 | Broadband Amplification as Tinnitus Treatment. | 2022 | Brain Sci | その他 |
| 22 | 9504599 | 10.1097/00005537-199803000-00001 | Effect of melatonin on tinnitus. | 1998 | Laryngoscope | RCT |
| 23 | 34611615 | 10.1016/j.eclinm.2021.101080 | Efficacy of pharmacologic treatment in tinnitus patients without specific or treatable origin: A network meta-analysis of randomised controlled trials. | 2021 | EClinicalMedicine | SR |
| 24 | 18412944 | 10.1186/1471-244X-8-23 | Design of a placebo-controlled, randomized study of the efficacy of repetitive transcranial magnetic stimulation for the treatment of chronic tinnitus. | 2008 | BMC Psychiatry | RCT |
| 25 | 26547700 | 10.1016/j.bjorl.2015.04.016 | Antioxidant therapy in the elderly with tinnitus. | 2016 | Braz J Otorhinolaryngol | RCT |
| 26 | 24622863 | 10.3766/jaaa.25.1.7 | Experimental, controversial, and futuristic treatments for chronic tinnitus. | 2014 | J Am Acad Audiol | その他 |
| 27 | 8915419 | （記録になし） | A double-blind placebo-controlled trial of baclofen in the treatment of tinnitus. | 1996 | Am J Otol | RCT |
| 28 | 19543742 | 10.1007/s00405-009-1015-7 | Personal experience with tinnitus retraining therapy. | 2010 | Eur Arch Otorhinolaryngol | その他 |
| 29 | 31447630 | 10.3389/fnins.2019.00802 | Why Is There No Cure for Tinnitus? | 2019 | Front Neurosci | その他 |
| 30 | 36905913 | 10.1016/j.amjoto.2023.103821 | Efficacy and safety of acupuncture and moxibustion for primary tinnitus: A systematic review and meta-analysis. | 2023 | Am J Otolaryngol | SR |

## CQ3　加齢性難聴に伴う耳鳴への補聴器・人工内耳・サウンドジェネレータ（薬との比較・併用）

ヒット 355 件中、関連の高い順に 30 本（GL 1・SR 4・RCT 0・その他 25）

| # | PMID | DOI | 題名 | 年 | 雑誌 | 種類 |
|---|---|---|---|---|---|---|
| 1 | 34060792 | （記録になし） | Tinnitus: Diagnosis and Management. | 2021 | Am Fam Physician | その他 |
| 2 | 33480192 | 10.3988/jcn.2021.17.1.1 | Tinnitus Update. | 2021 | J Clin Neurol | その他 |
| 3 | 34391534 | 10.1016/j.mcna.2021.05.003 | Hearing Loss and Tinnitus. | 2021 | Med Clin North Am | その他 |
| 4 | 23827090 | 10.1016/S0140-6736(13)60142-7 | Tinnitus. | 2013 | Lancet | その他 |
| 5 | 39138756 | 10.1007/s10162-024-00960-3 | The Current State of Tinnitus Diagnosis and Treatment: a Multidisciplinary Expert Perspective. | 2024 | J Assoc Res Otolaryngol | その他 |
| 6 | 19454115 | （記録になし） | Tinnitus. | 2007 | BMJ Clin Evid | SR |
| 7 | 26204362 | 10.1097/MOO.0000000000000186 | Current opinion: the management of tinnitus. | 2015 | Curr Opin Otolaryngol Head Neck Surg | その他 |
| 8 | 30342610 | 10.1016/j.mcna.2018.06.014 | Tinnitus. | 2018 | Med Clin North Am | その他 |
| 9 | 845067 | （記録になし） | Attemps to relieve tinnitus. | 1977 | J Am Audiol Soc | その他 |
| 10 | 23406991 | 10.1136/dtb.2013.1.0162 | Tinnitus. | 2013 | Drug Ther Bull | その他 |
| 11 | 25273878 | 10.1177/0194599814545325 | Clinical practice guideline: tinnitus. | 2014 | Otolaryngol Head Neck Surg | GL |
| 12 | 38532055 | 10.1007/s10162-024-00939-0 | Tinnitus: Clinical Insights in Its Pathophysiology-A Perspective. | 2024 | J Assoc Res Otolaryngol | その他 |
| 13 | 30892661 | 10.25318/82-003-x201900300001-eng | Tinnitus in Canada. | 2019 | Health Rep | その他 |
| 14 | 25328113 | （記録になし） | Tinnitus. | 2014 | BMJ Clin Evid | SR |
| 15 | 29397946 | 10.1016/j.otc.2017.11.007 | The Audiology of Otosclerosis. | 2018 | Otolaryngol Clin North Am | その他 |
| 16 | 22331367 | （記録になし） | Tinnitus. | 2012 | BMJ Clin Evid | SR |
| 17 | 30694350 | 10.1007/s00106-019-0609-7 | [Tinnitus: psychosomatic aspects]. | 2019 | HNO | その他 |
| 18 | 21726476 | （記録になし） | Tinnitus. | 2009 | BMJ Clin Evid | SR |
| 19 | 39939091 | 10.1016/j.pop.2024.09.008 | Tinnitus. | 2025 | Prim Care | その他 |
| 20 | 10451267 | （記録になし） | Subjective idiopathic tinnitus. | 1998 | Clin Excell Nurse Pract | その他 |
| 21 | 11898561 | 10.1007/s11910-001-0112-9 | Tinnitus. | 2001 | Curr Neurol Neurosci Rep | その他 |
| 22 | 30002023 | （記録になし） | Approach to tinnitus management. | 2018 | Can Fam Physician | その他 |
| 23 | 18512635 | （記録になし） | Managing tinnitus. | 2008 | J Fam Health Care | その他 |
| 24 | 33165158 | 10.1097/MAO.0000000000002932 | What Makes Tinnitus Loud? | 2021 | Otol Neurotol | その他 |
| 25 | 26190041 | 10.1055/s-0035-1550039 | [Long-term Development of Acute Tinnitus]. | 2015 | Laryngorhinootologie | その他 |
| 26 | 29772954 | 10.1080/14670100.2018.1473940 | Electric-acoustic stimulation suppresses tinnitus in a subject with high-frequency single-sided deafness. | 2018 | Cochlear Implants Int | その他 |
| 27 | 29794417 | 10.1159/000485546 | Extended Applications for Cochlear Implantation. | 2018 | Adv Otorhinolaryngol | その他 |
| 28 | 19380508 | 10.1044/1059-0889(2009/08-0037) | Patient-centered tinnitus management tool: a clinical audit. | 2009 | Am J Audiol | その他 |
| 29 | 6523048 | 10.3109/01050398409042138 | Tinnitus--incidence and handicap. | 1984 | Scand Audiol | その他 |
| 30 | 36212710 | 10.1155/2022/9236822 | Comparison of Different Therapeutic Effects of T-MIST for Chronic Idiopathic Tinnitus. | 2022 | Biomed Res Int | その他 |

## CQ4　新しい薬と神経調節（二刺激・rTMS・tDCS・VNS・Kv7）

ヒット 487 件中、関連の高い順に 30 本（GL 1・SR 3・RCT 1・その他 25）

| # | PMID | DOI | 題名 | 年 | 雑誌 | 種類 |
|---|---|---|---|---|---|---|
| 1 | 29336129 | 10.5935/0946-5448.20170022 | Somatic Tinnitus. | 2017 | Int Tinnitus J | その他 |
| 2 | 39138756 | 10.1007/s10162-024-00960-3 | The Current State of Tinnitus Diagnosis and Treatment: a Multidisciplinary Expert Perspective. | 2024 | J Assoc Res Otolaryngol | その他 |
| 3 | 17956813 | 10.1016/S0079-6123(07)66047-6 | Residual inhibition. | 2007 | Prog Brain Res | その他 |
| 4 | 25273878 | 10.1177/0194599814545325 | Clinical practice guideline: tinnitus. | 2014 | Otolaryngol Head Neck Surg | GL |
| 5 | 32362562 | 10.1016/j.otc.2020.03.011 | Alternative Treatments of Tinnitus: Alternative Medicine. | 2020 | Otolaryngol Clin North Am | その他 |
| 6 | 42168216 | 10.1038/s41572-026-00702-0 | Tinnitus. | 2026 | Nat Rev Dis Primers | その他 |
| 7 | 38353342 | 10.1002/ohn.671 | Neuromodulation for Treatment of Tinnitus: A Systematic Review and Meta-Analysis. | 2024 | Otolaryngol Head Neck Surg | SR |
| 8 | 29283017 | 10.1177/1073858417733415 | Tinnitus: Prospects for Pharmacological Interventions With a Seesaw Model. | 2018 | Neuroscientist | その他 |
| 9 | 33543988 | 10.1177/0004867421993541 | The positioning of rTMS. | 2021 | Aust N Z J Psychiatry | その他 |
| 10 | 32575951 | 10.7874/jao.2020.00052 | Non-Invasive Neuromodulation for Tinnitus. | 2020 | J Audiol Otol | その他 |
| 11 | 22853891 | 10.1016/j.brs.2012.07.002 | Frontal cortex TMS for tinnitus. | 2013 | Brain Stimul | その他 |
| 12 | 33575914 | 10.1007/s10162-021-00786-3 | Transient Delivery of a KCNQ2/3-Specific Channel Activator 1 Week After Noise Trauma Mitigates Noise-Induced Tinnitus. | 2021 | J Assoc Res Otolaryngol | その他 |
| 13 | 32477049 | 10.3389/fnins.2020.00422 | Sex Differences in the Response to Different Tinnitus Treatment. | 2020 | Front Neurosci | その他 |
| 14 | 33826134 | 10.1007/7854_2021_219 | Tinnitus and Brain Stimulation. | 2021 | Curr Top Behav Neurosci | その他 |
| 15 | 21527325 | 10.1016/j.heares.2011.04.004 | Inhibitory neurotransmission in animal models of tinnitus: maladaptive plasticity. | 2011 | Hear Res | その他 |
| 16 | 36401858 | （記録になし） | [Transcranial electrical stimulation of audiology patients of different ages.]. | 2022 | Adv Gerontol | その他 |
| 17 | 35051404 | 10.1016/j.brainres.2022.147797 | The role of the medial geniculate body of the thalamus in the pathophysiology of tinnitus and implications for treatment. | 2022 | Brain Res | その他 |
| 18 | 23764817 | 10.1016/j.otc.2013.02.005 | Complementary and integrative treatments: tinnitus. | 2013 | Otolaryngol Clin North Am | その他 |
| 19 | 39160146 | 10.1038/s41467-024-50473-z | Combining sound with tongue stimulation for the treatment of tinnitus: a multi-site single-arm controlled pivotal trial. | 2024 | Nat Commun | その他 |
| 20 | 22217183 | 10.1186/1471-2202-13-3 | Altered networks in bothersome tinnitus: a functional connectivity study. | 2012 | BMC Neurosci | RCT |
| 21 | 17691335 | 10.1007/978-3-211-33081-4_52 | Auditory cortex stimulation for tinnitus. | 2007 | Acta Neurochir Suppl | その他 |
| 22 | 17956774 | 10.1016/S0079-6123(07)66008-7 | Functional imaging of chronic tinnitus: the use of positron emission tomography. | 2007 | Prog Brain Res | その他 |
| 23 | 24888372 | 10.1007/s13311-014-0283-0 | Use of cortical stimulation in neuropathic pain, tinnitus, depression, and movement disorders. | 2014 | Neurotherapeutics | その他 |
| 24 | 26204362 | 10.1097/MOO.0000000000000186 | Current opinion: the management of tinnitus. | 2015 | Curr Opin Otolaryngol Head Neck Surg | その他 |
| 25 | 19303613 | 10.1016/j.neuchi.2009.01.016 | [Tinnitus treatment: neurosurgical management]. | 2009 | Neurochirurgie | その他 |
| 26 | 31434985 | 10.1038/s41598-019-48750-9 | RTMS parameters in tinnitus trials: a systematic review. | 2019 | Sci Rep | SR |
| 27 | 39046497 | 10.1007/s00405-024-08858-9 | The efficacy of transcranial random noise stimulation in treating tinnitus: a systematic review. | 2024 | Eur Arch Otorhinolaryngol | SR |
| 28 | 17956776 | 10.1016/S0079-6123(07)66010-5 | Neural mechanisms underlying somatic tinnitus. | 2007 | Prog Brain Res | その他 |
| 29 | 26583514 | 10.1001/jamaoto.2015.2422 | Assessment of Blinding in a Tinnitus Treatment Trial-Reply. | 2015 | JAMA Otolaryngol Head Neck Surg | その他 |
| 30 | 26583513 | 10.1001/jamaoto.2015.2425 | Assessment of Blinding in a Tinnitus Treatment Trial. | 2015 | JAMA Otolaryngol Head Neck Surg | その他 |

## CQ5　急性（3 か月未満）と慢性でエビデンスを分けているか・それぞれの薬物療法

ヒット 19 件中、関連の高い順に 19 本（GL 1・SR 6・RCT 0・その他 12）

| # | PMID | DOI | 題名 | 年 | 雑誌 | 種類 |
|---|---|---|---|---|---|---|
| 1 | 32761509 | 10.1007/7854_2020_169 | Pharmacotherapy of Tinnitus. | 2021 | Curr Top Behav Neurosci | その他 |
| 2 | 18437865 | （記録になし） | [Tinnitus--classification, causes, diagnosis, treatment and prognosis]. | 2004 | MMW Fortschr Med | その他 |
| 3 | 7843999 | （記録になし） | [The lidocaine test in tinnitus. Determination of its current status]. | 1994 | HNO | その他 |
| 4 | 36383762 | 10.1002/14651858.CD013514.pub2 | Ginkgo biloba for tinnitus. | 2022 | Cochrane Database Syst Rev | SR |
| 5 | 41547415 | 10.1016/j.brainresbull.2026.111733 | Cell-type-specific reorganization of VGSCs in auditory cortex and therapeutic potential of Nav1.6 blockade for tinnitus. | 2026 | Brain Res Bull | その他 |
| 6 | 34566871 | 10.3389/fneur.2021.726803 | Treatment of Tinnitus in Children-A Systematic Review. | 2021 | Front Neurol | SR |
| 7 | 23213709 | （記録になし） | [Pharmacotherapy of acute and chronic tinnitus]. | 2012 | Med Monatsschr Pharm | その他 |
| 8 | 23076907 | 10.1002/14651858.CD004739.pub4 | Hyperbaric oxygen for idiopathic sudden sensorineural hearing loss and tinnitus. | 2012 | Cochrane Database Syst Rev | SR |
| 9 | 30589445 | 10.1002/14651858.CD013094.pub2 | Sound therapy (using amplification devices and/or sound generators) for tinnitus. | 2018 | Cochrane Database Syst Rev | SR |
| 10 | 33527333 | 10.1007/7854_2020_213 | Psychosocial Variables That Predict Chronic and Disabling Tinnitus: A Systematic Review. | 2021 | Curr Top Behav Neurosci | SR |
| 11 | 37792096 | 10.1007/s00106-023-01331-9 | Interventions against hearing loss as an integral component of successful tinnitus therapy. | 2024 | HNO | その他 |
| 12 | 16132881 | 10.1007/s00106-005-1292-4 | [Pharmacotherapy in acute tinnitis. The special role of hypoxia and ischemia in the pathogenesis of tinnitis]. | 2006 | HNO | その他 |
| 13 | 20811867 | 10.1007/s00106-010-2179-6 | [Pharmacotherapy of acute and chronic hearing loss]. | 2010 | HNO | その他 |
| 14 | 11270201 | 10.1007/s001060050716 | [Rheologic infusion therapy, neurotransmitter administration and lidocaine injection in tinnitus. A staged therapeutic concept]. | 2001 | HNO | その他 |
| 15 | 15602859 | （記録になし） | [Tinnitus: first symptom of chronic myeloid leukemia]. | 2004 | Rev Laryngol Otol Rhinol (Bord) | その他 |
| 16 | 22053947 | 10.1186/1472-6963-11-302 | Treatment options for subjective tinnitus: self reports from a sample of general practitioners and ENT physicians within Europe and the USA. | 2011 | BMC Health Serv Res | その他 |
| 17 | 37552280 | 10.1007/s00106-023-01333-7 | [Interventions against hearing loss are an integral component of successful tinnitus therapy. German version]. | 2023 | HNO | その他 |
| 18 | 40161477 | 10.1097/ONO.0000000000000067 | A Systematic Review of Psychometric Validation for Subjective Tinnitus Outcome Measures Assessing Acute Treatment Effects. | 2025 | Otol Neurotol Open | SR |
| 19 | 38317449 | 10.3346/jkms.2024.39.e49 | Consensus Statements on the Definition, Classification, and Diagnostic Tests for Tinnitus: A Delphi Study Conducted by the Korean Tinnitus Study Group. | 2024 | J Korean Med Sci | GL |

---

かかった時間：約 2 分（eutils の処理そのものは計 23 秒）／eutils 呼び出し回数：24 回（einfo 1・1 回目の検索 esearch 5＋esummary 5＋429 再試行 2・2 回目の検索 esearch 5＋esummary 5＋502 再試行 1）
