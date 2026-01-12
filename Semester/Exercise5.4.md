*Task: Biological context of results/reporting of results:
Please discuss the significant metabolite-SNP pairs plotted in 3) regarding their biological
interpretation by investigating their functional relationships in appropriate public resources (e.g.
function of related gene, relevance for disease, known associations with further phenotypes,
biochemical function/metabolic pathway of metabolite etc. Taking all this information
together - what does the observed association mean biologically?). The provided publications
as well as metabolomics resources such as HMDB, PubChem or KEGG and databases hosting
gene related information such as dbSNP, GeneCards, EMBL-EBI GWAS Catalog and SNiPA
(www.snipa.org) might be helpful resources for this task.*

# Preprocessing (1c, 1d)


All metabolite values were log2 transformed to make their distributions less skewed and closer to what linear regression assumes. On this scale, effects reflect relative changes rather than changes in raw units.


Values that were more than three standard deviations away from a metabolite’s mean were set to missing. These extreme values are likely due to measurement error or very unusual samples, so keeping them would risk distorting the regression results.


# Association testing and multiple testing (2a, 2c)


Metabolite SNP pairs with data from fewer than 500 individuals were removed: this ensures that each regression is based on enough observations to produce stable estimates.


For the remaining pairs, we fitted a linear model with metabolite level as the outcome and genotype, age, and sex as predictors. The genotype coefficient describes how much the metabolite changes for each additional copy of the effect allele, after adjusting for age and sex.


Because thousands of tests were performed, p values were compared to a Bonferroni corrected threshold. This reduces the chance of false positives across all tests. Less strict alternatives include methods that control the false discovery rate, such as Benjamini Hochberg.


# Biological interpretation of the plotted SNP metabolite pairs


PC.aa.C42.5 is a phosphatidylcholine that is common in cell membranes and lipoproteins. In the plots for SNP rs9393903, median PC.aa.C42.5 levels increase slightly with the number of effect alleles. This suggests that the variant modestly raises levels of this phospholipid.


Gly is glycine, an amino acid involved in one carbon metabolism and antioxidant defense. For SNP rs2216405, glycine levels are higher in individuals with one or two effect alleles. This indicates that the SNP is associated with increased circulating glycine.


C4 is a short chain acylcarnitine that reflects aspects of mitochondrial fatty acid and amino acid oxidation. In the plots, especially for SNP rs2014355, higher genotype counts are associated with higher C4 levels. This pattern is consistent with a role for these variants in mitochondrial or branched chain amino acid metabolism.


lysoPC.a.C20.4 is a lysophosphatidylcholine containing a polyunsaturated C20 fatty acid. It is linked to membrane turnover and inflammation. For SNP rs174547, levels clearly decrease as the number of effect alleles increases. This suggests that the SNP lowers this lipid and is consistent with known effects of variants in the FADS region on polyunsaturated phospholipids.


Gln, or glutamine, is an amino acid important for nitrogen transport and energy metabolism. For SNP rs1043011, differences between genotype groups are small. This suggests a weaker genetic effect on glutamine compared with the other metabolites.

 
# Direction of effects and sex differences


Across the plots, median metabolite levels generally increase or decrease across genotype groups in the same direction as the regression coefficient. For example, effects are positive for glycine and C4 and negative for lysoPC.a.C20.4.


Male and female data points largely overlap within each genotype group. This suggests there are no strong sex specific genetic effects beyond the average sex difference already accounted for in the model. Detecting smaller sex specific effects would require formal interaction testing.
