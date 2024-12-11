
[中文说明](README_CN.md) 

### Feature

- OneKey analysis from clean reads to variant VCF
- support multiple sample analysis
- parallel computing by default
- all analysis commands saved in files

### Notice

- No QC procedure, using Clean reads as input
- Servers with large memory recommended

### input file directory prepare
 
```mermaid
graph TB

analysisDir ---->fq
analysisDir-->sample.list.txt
fq-->*.R1.fq.gz
fq-->*.R2.fq.gz

analysisDir ---->genome
genome-->sequences.fa
genome-->genes.gtf

```

### Dependencies

install dependencies using conda:

```bash
mamba create -n WGS perl=5.26.2 gatk4=4.2.5  bwa=0.7.17  samtools=1.15  snpeff=5.1 python=3.8 parallel=20211222 bcftools=1.15 multiqc=1.12
```
### Usage


####  method 1

```bash
#activate environment 
conda activate WGS
```
Change the working directory to analysisDir 

ensure the onekeyReseq script and data files are present.


```bash
cd /mnt/d/workshop/analysisDir
bash onekeyReseq
```
#### method 2

```bash
#activate environment 
conda activate WGS
```

Ensure data files are in the workdir and the onekeyReseq script is in the current directory.

```bash
bash onekeyReseq   workdir
```

### Results

|directory|meaning|
|-|-|
|1.mapping|mapping results<br>`mapStat.html` is the analysis report|
|2.SNP|SNP/InDel Results<br>`2.SNP/4.anno/all.Variants.anno.vcf.gz` is the final variant file|
|commands|`.sh` is the detail commands <br>`.sh.ok` means the step is done normally|
|log|log files<br>`stdout.log` is the log of standard output，`stderr.log` is the log of standard error|

