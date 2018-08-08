# STAMPS 2018 - intro to shotgun metagenomes, and assembly

[toc]

## Outline, in brief

1. Introduction and welcome!
	* [Titus Brown](ivory.idyll.org/blog/)
	* Todd Treangen
2. Some terminology:
	* "metagenomics" == "shotgun metagenomics"
	* "16s sequencing" is a type of "amplicon sequencing" or "targeted sequencing"
4. Shotgun sequencing - an intro
5. Shotgun sequencing of metagenomes - why? why not?
	* Cons vs amplicon:
		* lower coverage / more expensive (good? bad? what are the tradeoffs?)
		* much more computationally challenging to analyze
	* Pros vs amplicon:
		* different bias (no primers)
		* virus/phage can be detected
		* function can be detected
		* recover (putative) genomes
6. What can we do with shotgun sequencing?
	* do taxonomic analysis directly on the reads - *(Tuesday!)*
	* search the reads for genes of interest (function, taxonomy)
	* assemble the reads into **contigs**, longer stretches of DNA - *(next few days)*
		* annotate contigs with taxonomy, function
		* (note distinction between de novo assembly and reference-based assembly)
		* cluster contigs together to extract **genome bins**, aka "metagenome assembled genomes" - *(Monday!)*
		* compare contig abundances across samples to look for differentially abundant sequences
	* (see [Mike Lee's diagram of All the Tools!](https://ndownloader.figshare.com/files/12367187))
7. Important notes on assembly:
	* assembly squashes abundance 8:
	* assembly ignores complicated regions :(
	* assembly is **surprisingly accurate** and (when using megahit, at least) **computationally tractable** :)
8. Important notes on quantifying assembled contigs:
	* it's not clear what tools to use for differential abundance analysis
		* we have a [tutorial for quantifying contig abundance with salmon](https://2017-ucsc-metagenomics.readthedocs.io/en/latest/salmon_tutorial.html) - see also [notebook](https://github.com/ngs-docs/2016-metagenomics-sio/blob/master/files/plot-quant.ipynb)
	* [mapping abundances look wavy](http://merenlab.org/2016/12/14/coverage-variation/)
9. Some open *computational* research questions:
	* right now assembly based approaches simply ...discard some proportion of the data. we should figure out a better way.
	* what is the value of long reads in shotgun metagenomics?


## Question 1!

[Question 1](https://docs.google.com/forms/d/e/1FAIpQLSeZ5KlYYWUFY9ZevHYzRcFJFxhnq01a2l4v-nD432QBlueG6g/viewform)

## Let's assemble something!


First, log in to the class server and activate the necessary software environment:

```
export PATH="/class/stamps-software/miniconda3/bin:$PATH"
```

Now, download some mystery data:
```
mkdir ~/mystery
cd ~/mystery
curl -o sample.R1.fq.gz -L https://osf.io/mjs65/?action=download
curl -o sample.R2.fq.gz -L https://osf.io/7qybs/?action=download
```

Assemble using the [megahit](https://github.com/voutcn/megahit) metagenome assembler:
```
megahit -1 sample.R1.fq.gz -2 sample.R2.fq.gz -o mystery.assembly -m 5e9
```

(Digression: where did this "megahit" software come from!? See: ["What is bioconda?"](https://angus.readthedocs.io/en/2018/jetstream-bioconda-config.html#what-is-bioconda) to learn about the magical software installation system known as "conda", and the amazing set of community-maintained packages that is "bioconda".)

After about 5 minutes, you should see output like this:

```
--- [STAT] 7774 contigs, total 4987609 bp, min 200 bp, max 8658 bp, avg 642 bp, N50 1049 bp
```

what does this mean?

Questions you might ask yourself at this point:

* what are the basic assembly metrics?
* is this a good assembly? (what does "good" mean?)
* what microbial genome(s) are present in this assembly?

We can get a preliminary set of metrics with [QUAST](http://quast.sourceforge.net/quast).
```
quast mystery.assembly/final.contigs.fa
cat quast_results/latest/report.txt
```

<!--
### So... what is it?

Try:
```
sourmash gather mystery.assembly/final.contigs.fa.sig /class/stamps-shared/sourmash-db/genbank-k31.sbt.json
```
-->

<!--
## Question 2!

[Question 2](https://docs.google.com/forms/d/e/1FAIpQLScwjqGp-juAUDvs_cv6Sef9CFyyKBKMcEetDy7yxrugx49ETA/viewform)
-->

## Open topics for discussion!

### How much should I sequence?

### How accurate/effective is functional classification on shotgun metagenome data?


