# vcf2phylip
Convert SNPs in VCF format to PHYLIP for phylogenetic analysis

## _Brief description_
The script converts a collection of SNPs in VCF format into a PHYLIP file for phylogenetic analysis. In case of heterozygous SNPs the IUPAC ambiguity code is used to construct the final DNA sequence. The code is optimized for large VCF files, in our tests it processed a 20GB VCF (~3 million SNPs x 650 individuals) in ~27 minutes. Once the PHYLIP file is obtained, conversion to other alignment formats (e.g. FASTA) is trivial with other software like [_Aliview_](http://ormbunkar.se/aliview/).

A minimum number of samples per SNP can also be specified so you won't need to run again the software that created your VCF file just to increase this threshold. Lastly, if you specify an OUTGROUP the sequence of that sample will be written first in the alignment (phylogenetic software usually root the trees on the first taxon in the alignment).

The script has been tested with VCF files produced by [_pyrad v.3.0.66_](https://github.com/dereneaton/pyrad), [_ipyrad v.0.7.x_](http://ipyrad.readthedocs.io/), and [_Stacks v.1.47_](http://catchenlab.life.illinois.edu/stacks/).

## _Usage_
Simply specify the name of the VCF input file and optionally the minimum of samples per SNP (default 4 for phylogenetics):

_Example 1:_ Using the default minimum of samples per SNP of 4:
```bash
python vcf2phylip.py myfile.vcf
# This command will create a PHYLIP called myfile_min4.phy
```

_Example 2:_ Using a custom minimum of samples per SNP of 63:
```bash
python vcf2phylip.py myfile.vcf 63
# This command will create a PHYLIP called myfile_min63.phy
```

_Example 3:_ Using a custom minimum of samples per SNP of 35 and setting outgroup to "sample1":
```bash
python vcf2phylip.py myfile.vcf 35 sample1
# This command will create a PHYLIP called myfile_min35.phy with sample1 as the first sequence
```
