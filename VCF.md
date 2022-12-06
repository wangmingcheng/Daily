(VCF格式说明)[http://samtools.github.io/hts-specs/#:~:text=VCFv4.3.tex%20is%20the%20canonical%20specification%20for%20the%20Variant,of%20VCF%20format%20and%20is%20under%20active%20revision]

RMS Mapping Quality（Root Mean Square of the mapping quality of reads across all samples） 默认值：SNP>= 40

QUAL：Phred格式(Phred_scaled)的质量值，表示在该位点存在variant的可能性；该值越高，则variant的可能性越大；计算方法：Phred值 = -10 * log (1-p) p为variant存在的概率; 通过计算公式可以看出值为10的表示错误概率为0.1，该位点为variant的概率为90%。<br>
GQ：基因型的质量值(Genotype Quality)。Phred格式(Phred_scaled)的质量值，表示在该位点该基因型存在的可能性；该值越高，则Genotype的可能性越大；计算方法：Phred值 = -10 * log (1-p) p为基因型存在的概率。<br>
