
**Get bams**

	isabl get-bams -fi projects 162 --verbose

in python api

        import isabl_cli as ii
        ii.get_experiments(system_id='my_sample_id')[0].bam_files.GRCh37.url

**Create cnacs pool**
	
	isabl apps-grch37 cnacs-pool-0.2.0-generate_pool \
		-fi system_id__in I-H-100534-N1-1-D1-2,I-H-100536-N1-1-D1-2,I-H-100540-N1-1-D1-2,I-H-100542-N1-1-D1-2,I-H-100543-N1-1-D1-2,I-H-100544-N1-1-D1-2 \
		--commit

**Get outdirs for CNACS**
	
	isabl get-outdirs -fi projects 162 -fi name CNACS

**Get Project Metadata**

       isabl get-metadata projects   -fi title.icontains 'Myeloma'   --field pk   --field title

**Get outdirs for BATTENBERG** 
	
	isabl get-outdirs -fi projects 220 -fi name BATTENBERG|awk '{print "rsync -aP "$1"/*.png ./"}' | bash

**Use force** 
	
	isabl apps-grch37 cnvkit-0.8.5_pooled -fi projects 162 -fi technique__name MYTYPE-V1 --force

**Get TSV and VCF for WGD from triple caller**

	isabl get-results -fi projects 220 -fi application__name ANNOT_SNVS -fi application__version 2.0.0 --result-key pass_tsv

	isabl get-outdirs -fi projects 220 -fi application__name ANNOT_SNVS|awk '{print "ls "$1"/merged/*pass.vcf.gz"}' | bash


**Get TSV for TGD from triple caller**

	isabl get-results -fi projects 162 -fi application__name ANNOT_SNVS -fi application__version 2.0.0 --result-key all_bed_tsv --verbose|cut -f2|grep "gz"

**If you want to know the available results for each pipeline you can type:**

	isabl get-results --app-results 33


