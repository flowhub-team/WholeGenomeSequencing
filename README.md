# Whole Genome Sequencing

1. 实验准备：
在开始分析之前，需要准备样本和相关实验材料。样本可以是DNA的提取物，通常从血液、组织或细胞中提取。实验准备包括质量控制检查、DNA文库构建和测序芯片准备等。

2. DNA文库构建：
将样本的DNA片段转化为适合测序的文库。这通常包括以下步骤：
a. DNA片段切割：将长的DNA片段切割成较短的片段，通常为几百到几千碱基对。
b. 末端修复：修复DNA片段的末端，使其适合连接测序适配体。
c. 适配体连接：将测序适配体连接到DNA片段的末端，适配体包含与测序仪器兼容的序列。
d. PCR扩增：通过聚合酶链式反应（PCR）扩增适配体连接的DNA片段，以便在测序中产生足够的信号。

3. 测序：
将DNA文库放入测序仪器进行测序。有几种不同的测序技术可供选择，例如Illumina、Ion Torrent、PacBio和Oxford Nanopore等。这些技术使用不同的原理和方法来读取DNA序列。

4. 数据预处理：
从测序仪器中生成的原始测序数据称为"reads"。在进行进一步的分析之前，需要对这些数据进行预处理和质量控制，以去除低质量的reads和适配体序列。
   1. Trimmomatic：用于去除测序reads中的适配体序列、低质量碱基和低质量reads。你可以在 [Trimmomatic GitHub](https://github.com/timflutre/trimmomatic) 上找到更多信息和使用说明。

   2. FastQC：用于评估测序reads的质量分布和其他质量指标。它可以帮助检测测序过程中的潜在问题，如测序质量下降、适配体污染等。有关更多信息，请访问 [FastQC网站](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)。

   3. BWA-MEM：用于将测序reads比对到参考基因组上。BWA-MEM采用快速的seed-and-extend算法，能够高效地处理较长的reads。你可以在 [BWA-MEM GitHub](https://github.com/lh3/bwa) 上获取详细的文档和使用说明。

   4. Bowtie2：用于将reads比对到参考基因组。它结合了快速的seed-and-extend算法和最大可信权值路径算法，适用于短序列的比对。你可以在 [Bowtie2官方网站](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml) 上了解更多信息。

   5. SAMtools：用于处理比对结果的工具集，可以进行SAM/BAM格式文件的转换、排序、索引和过滤。此外，它还提供了一系列命令行工具，用于统计比对信息、检测SNPs和Indels等。你可以在 [SAMtools官方网站](http://www.htslib.org/) 上找到更多的文档和下载链接。

   6. GATK（Genome Analysis Toolkit）：是一个用于基因组数据的分析和变异检测的工具集。它提供了多种算法和工具，包括基因组重比对、SNP/Indel检测、变异过滤等。有关详细信息，请访问 [GATK官方网站](https://gatk.broadinstitute.org/hc/en-us)。

   7. Picard Tools：用于处理SAM/BAM文件的工具集，可以标记PCR重复、计算覆盖度、创建统计报告等。你可以在 [Picard Tools官方网站](https://broadinstitute.github.io/picard/) 上了解更多信息和使用说明。

   8. QualiMap：用于评估测序数据质量的工具，可以检测测序reads的覆盖度、GC含量、错误率等质量指标，并生成相应的统计图表和报告。有关更多信息，请访问 [QualiMap官方网站](https://gatk.broadinstitute.org/hc/en-us)。
5. 数据比对和基因组装：
将预处理后的reads与参考基因组进行比对或基因组装。比对是将reads与已知基因组序列进行比较，确定每个read在基因组中的位置。基因组装是将reads组合成更长的连续序列，以重建基因组的整体结构。
   1. 比对工具：
      1. BWA-MEM：用于将测序reads比对到参考基因组上。它采用快速的seed-and-extend算法，适用于处理较长的reads。你可以在[BWA-MEM GitHub](https://github.com/lh3/bwa)上获取详细的文档和使用说明。
      2. Bowtie2：用于将reads比对到参考基因组。它结合了快速的seed-and-extend算法和最大可信权值路径算法，适用于短序列的比对。了解更多信息，请访问[Bowtie2官方网站](https://www.ebi.ac.uk/~zerbino/velvet/)。
   2. 基因组装工具：
      1. SPAdes：用于从测序reads中进行基因组组装，包括单细胞测序数据。它结合了de Bruijn图算法和多种优化策略，适用于各种类型的测序数据。你可以在[SPAdes GitHub](https://github.com/ablab/spades)上找到更多信息和使用说明。
      2. Velvet：基于de Bruijn图的基因组组装工具，适用于短序列测序数据。它通过构建k-mer图来重建基因组序列。有关详细信息，请访问[Velvet官方网站](https://www.ebi.ac.uk/~zerbino/velvet/)。
      3. SOAPdenovo：一个用于基因组组装的快速和高效的工具。它基于de Bruijn图算法，适用于大规模基因组的组装。了解更多信息，请访问[SOAPdenovo官方网站](http://soap.genomics.org.cn/soapdenovo.html)。
6. 变异检测：
使用比对或基因组装的结果，识别和分析样本中的基因组变异。这些变异可能包括单核苷酸多态性（SNPs）、插入/缺失（indels）、基因重排等。变异检测的方法和工具会根据研究目的而有所不同。
   1. GATK（Genome Analysis Toolkit）：GATK是一个广泛使用的工具集，用于基因组数据的分析和变异检测。它提供了多种算法和工具，包括基因组重比对、SNP/Indel检测、变异过滤等。了解更多信息，请访问[GATK官方网站](https://gatk.broadinstitute.org/)。
   2. VarScan：VarScan是一种用于检测SNPs、Indels和结构变异的工具，特别适用于对比分析。它能够从比对数据中识别变异，并提供统计学过滤和注释。有关详细信息，请访问[VarScan官方网站](http://varscan.sourceforge.net/)。
   3. FreeBayes：FreeBayes是一个开源的SNP和Indel检测工具，能够从测序数据中检测变异。它采用贝叶斯统计方法进行变异检测，并提供了高灵敏度和准确性。了解更多信息，请访问[FreeBayes GitHub](https://github.com/ekg/freebayes)。
   4. MuTect：MuTect是一个专门用于检测肿瘤样本中的突变的工具。它可以分析肿瘤-正常对比数据，并鉴定出肿瘤样本中的突变。了解更多信息，请访问[MuTect官方网站](https://software.broadinstitute.org/cancer/cga/mutect)。
   5. Samtools：Samtools是一个用于处理比对数据（SAM/BAM格式）的工具集，同时也提供了一些变异检测功能。它可以进行SNP/Indel检测、过滤和注释等。有关详细信息，请访问[Samtools官方网站](http://www.htslib.org/)。
   6. Platypus：Platypus是一个灵活的变异检测工具，可以从WGS数据中检测SNPs、Indels和结构变异。它具有高度可配置性，并且支持多样本分析。了解更多信息，请访问[Platypus GitHub](https://github.com/andyrimmer/Platypus)。
7. 注释和功能分析：
对检测到的变异进行注释，确定其可能的功能和影响。注释可以包括变异在基因区域的位置、氨基酸改变的影响、潜在的功能通路等。
   1. ANNOVAR：ANNOVAR是一个用于注释基因组变异的工具，可以根据各种数据库提供详细的注释信息。它支持多种变异类型的注释，包括SNP、Indel、结构变异等。了解更多信息，请访问[ANNOVAR官方网站](https://annovar.openbioinformatics.org/en/latest/)。
   2. Variant Effect Predictor (VEP)：VEP是一个广泛使用的工具，用于注释和预测变异的功能影响。它能够提供详细的注释信息，包括变异的基因影响、功能改变、突变致病性预测等。了解更多信息，请访问[VEP官方网站](https://www.ensembl.org/info/docs/tools/vep/index.html)。
   3. SnpEff：SnpEff是一个用于注释和预测SNP和结构变异的功能影响的工具。它能够提供变异的注释、基因影响、功能改变以及通路分析等。有关详细信息，请访问[SnpEff官方网站](http://snpeff.sourceforge.net/)。
   4. dbNSFP：dbNSFP是一个基因组功能预测数据库，提供了大量的注释和预测信息。它包含了来自多个公共数据库的功能预测结果，并提供了丰富的注释信息，如SIFT、PolyPhen-2、GERP++等。有关详细信息，请访问[dbNSFP官方网站](https://sites.google.com/site/jpopgen/dbNSFP)。
   5. DAVID：DAVID（Database for Annotation, Visualization, and Integrated Discovery）是一个功能注释和富集分析工具，可以帮助用户理解基因组变异的功能和相关的生物学过程。它整合了多个公共数据库，提供了注释、功能分析和通路分析等功能。了解更多信息，请访问[DAVID官方网站](https://david.ncifcrf.gov/)。

8. 结果解读和报告：
根据分析的结果，对基因组测序数据进行解读，并形成报告。报告可能涵盖样本的遗传风险、潜在的致病变异、药物敏感性等信息。
