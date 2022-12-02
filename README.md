# Daily
## Nanopore
### 重复序列分析

微卫星标记（microsatellite），又被称为短串联重复序列（short tandem repeats, STRs）或简单重复序列（simple sequence repeats, SSRs），是均匀分布于真核生物基因组中的简单重复序列，由2～6个核苷酸的串联重复片段（核心序列）串联重复组成，其重复单位的重复次数在个体间呈高度变异性并且数量丰富。目前已发现重复序列和40多种神经肌肉和神经退行性疾病等疾病有关，包括众所熟知的精神发育迟滞疾病—脆性X染色体、神经退行性疾病—亨廷顿舞蹈症、脊髓小脑性共济失调症等，此外微卫星不稳定性MSI也是许多癌症基因组特征。由于重复序列的扩张引起的疾病称为重复序列扩张疾病，当然有些重复序列缩短也能引起疾病。其发病机制与这些重复的微卫星序列的重复次数相关。利用三代长读长数据，可用来检测卫星序列重复次数。

### HLA分型

主要组织相容性复合体MHC区域位于6号染色体的短臂上，是人类基因组上最复杂的区域之一（约4Mb），呈现出高度的多态性（有着超过10,000个等位）。其编码的分子参与抗原递呈，制约细胞间相互识别及诱导免疫应答。人类白细胞抗原（HLA）编码基因是 MHC 的一部分，是迄今已知基因中等位基因多态性最高的基因复合体，也是不同个体进行器官或组织细胞移植时发生排斥的主要成分。

与 HLA 相关的疾病多达100多种，涉及自身免疫性疾病、免疫缺陷性疾病、过敏性疾病、感染类疾病、代谢性疾病等，如糖尿病、类风湿性关节炎，银屑病、强直性脊柱炎、重症肌无力和哮喘等。同时，HLA在器官和骨髓等移植中起到至关重要的作用，也与许多药物的严重不良反应相关。因此，进行HLA 分型，有利于免疫相关疾病的研究、疫苗和药物靶向人群筛选、种族进化的研究、组织和器官移植等。

本次分析对样品的 HLA-A，HLA-B，HLA-C 基因进行单倍型鉴定。将测序的Nanopore reads与已知的HLA等位比对来识别候选的等位，接下来通过与候选等位的多重比对获取一致序列，最后通过将一致序列与参考数据库比对获取每个样品最终的单倍型。

## 测试call snp软件
### freebayes
```
freebayes -f /datapool/home/wangmc/project/genome/ucsc.hg19.fasta /datapool/home/wangmc/project/case_22BY12800/case_22BY12800.bam > case_22BY12800.vcf
```
freebayes参数意义<br>
freebayes结果过滤标准<br>

### deepvariant
#### 1 conda安装不可行 pass
#### 2 下载源码编译安装，依赖太多，需要管理员权限也不可行 pass
#### 3 singularity可以成功安装并使用
1 拉镜像：<br>
```
singularity build deepvariant.sif docker://google/deepvariant<br>
```
2 运行：<br>
```
singularity run -B /usr/lib/locale/:/usr/lib/locale/  /datapool/home/wangmc/software/deepvariant/deepvariant.sif /opt/deepvariant/bin/run_deepvariant --model_type=WES --ref=/datapool/home/wangmc/project/genome/ucsc.hg19.fasta --reads=/datapool/home/wangmc/project/case_22BY12800/case_22BY12800.bam  --output_vcf=case_22BY12800.vcf --output_gvcf=case_22BY12800.g.vcf case_22BY12800 --num_shards=30
```
bam和参考基因组fasta移动到一个磁盘下,docker调用系统文件的问题<br>
[SAMtools [E::hts_open_format] Failed to open file #1289](https://github.com/samtools/samtools/issues/1289)

### 不同call snp软件结果评估标准
#### 1 snp交集
