# gff_tools_box

This tool has been developed to modify, transforme or extract informations from genome annotation files (gff) without coding skills.
Gff tools box is a simple bash script that you can use in linux or macOS environment.
The usage of the script is quite easy, you have just to call a gff file in argument with it. (ex: bash gff_tools_box.sh my_gff_file.gff)

Before to start, this script is able to check its ability to work (control of the file and its structure).
All the new files generated by this script are created in the current directory.
Then, after a quite remind of the classical structure of gff file, the user can choose a specific tool to use on his file:


TOOL 1: Classical Human Chromosomes filter (Specific to human genome)
- This tool is able to recognise classical human chromosome names (NC_XXXXXX.X or chrX) in the SeqIDs column. 
You will have the choice to extract sequences with or without those names. 
If the file present both nomenclature, you will have the choice to homogenise chromosomes names by 'NC' or 'chr'.


TOOL 2: Promoter regions extractor (Specific to gene region)
- The tool extract promoter region in 3 steps:
	- First: the script check if all the types of region of each sequence are 'genes'. 
	If yes, you can check the different gene biotypes to extract promoters from a sub-fraction of gene (ex: coding_protein, pseudogene, tRNA, lncRNA, etc...)
	If not, please, make sure that the content of the gff is gene annotation.
	- Second: definition of the Transcription Start Site (TSS) depending of the strand of the gene. 
	For strand +, the TSS is the start point of the sequence, while for Strand -, the TSS is the end point of the sequence. 
	If the strand is not specify, the TSS is the start point of the sequence.
	- Third: Extraction of promoters around TSS depending of the interval answered by the user (ex: -2000bp to 2000bp)


TOOL 3: Extract lines with specific sources (column 2)
- If the file contain different sources (ex: RefSeq, BestRefSeq, Curated genomic, etc...), this tool can list it and you can choose to extract one of them.


TOOL 4: Extract lines with specific type of region (column 3)
- If the file contain different types of region (ex: gene, exon, tRNA, CDS, etc...), this tool can list it and you can choose to extract one of them.


TOOL 5: Attributes explorer (column 9) (specific to gff3 structure)
- First this tool is able to list all different kind of attributes and you can choose to extract the list of content of this attribute or extract all lines which present this attribute. (attribute exemple: ID=; gbkey=; name=; gene=; gene_biotype=; parental=; etc...)
- List extraction:
First, the tool will create a txt file with one content of a specific attribute per line.
	exemple: gene_biotype=coding_protein; gene_biotype=tRNA; gene_biotype=coding_protein; will give:
	
	coding_protein
	tRNA
	coding_protein

In a second part, you have the choice to create a second list with each unique sub-attribute
	exemple: gene_biotype=coding_protein; gene_biotype=tRNA; gene_biotype=coding_protein; will give:

	coding_protein
	tRNA

- Extraction of attribute:
If the attribute is not in all lines of the file, extraction of all lines which present this attribute.
If all lines present this attribute (ex: ID, gbkey, etc...), possibility to explore the sub-attribute. (gene_biotype=lncRNA)
	If the sub-attribute is not unique to each line, this tool can list it and you can choose to extract one of them.


TOOL 6: Sequence extender
- This tool is able to extend all sequences in the file depending of the user interval. You have the possibility to choose if it is strand specific or not.


TOOL 7: GFF to BED file
- This tool is able to transform the gff file in bed3 and/or bed6 file. If human chromosome are named with 'NC_XXXXXX.X', this tool correct it in 'chrX'.


Thank you to use GFF tools box!
If you got any problems when you used this script or if you have any comments on it, please feel free to contact mathias.boulanger.17@hotmail.com
