# Define the README content
readme_content = """
# 🧬 Variant Analysis Pipeline using Whole Exome Sequencing (WES)

This project implements a complete bioinformatics workflow for variant discovery and annotation starting from raw FASTQ files.

---

## 🚀 Pipeline Overview

### Step 1: Environment Setup
- Created structured directories for organizing data and results
- Installed essential tools: FastQC, BWA, GATK, SAMtools, bcftools

### Step 2: Raw Data Processing
- Performed quality control of raw `.fastq` files using **FastQC**
- Indexed human reference genome (hg38)
- Aligned reads using **BWA-MEM**
- Sorted, converted, and indexed BAM files with **SAMtools**

### Step 3: Variant Calling
- Called variants using **GATK HaplotypeCaller**
- Compressed and indexed VCF output

---

## 🧬 Variant Annotation with ANNOVAR

- Converted `.vcf` to ANNOVAR input format
- Annotated using `table_annovar.pl` against:
  - `refGene` (gene annotations)
  - `ClinVar` (clinical significance)
  - `dbnsfp` (predicted functional impact)
- Produced multi-annotation output: `output.hg38_multianno.txt`

---

## 🎯 Variant Prioritization

Filtered for high-confidence exonic variants:
- `Func.refGene = exonic`
- Focused on coding changes like nonsynonymous SNVs, stopgains, etc.
- Looked at:
  - `ExonicFunc.refGene`
  - `CLNSIG` (e.g., pathogenic)
  - `CADD_phred` ≥ 20

Saved filtered data to: `filtered_exonic_variants.xlsx`

---



