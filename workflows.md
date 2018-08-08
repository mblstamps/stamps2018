# Computing, automation, workflows, and publishing

[toc]

## NSF XSEDE and Jetstream in particular

[Link to Jetstream lesson](https://angus.readthedocs.io/en/2018/jetstream/boot.html)

## Automation with shell scripts

[This tutorial based partly on the ANGUS 2018 tutorial](https://hackmd.io/olmSyg4IR3m0EGDNhb9aaA)

Log into your class server (should be `class-XX`). Note, if you can't connect directly to `class-XX` you can connect in first to `class.mbl.edu` and then `ssh class-XX`.

Activate conda as before:
```
export PATH="/class/stamps-software/miniconda3/bin:$PATH"
```


```
mkdir ~/shell
cd ~/shell
```


Now, create a little shell script that contains the commands
from the assembly foo:
```
cat >assemble.sh <<EOF
curl -o sample.R1.fq.gz -L https://osf.io/mjs65/?action=download
curl -o sample.R2.fq.gz -L https://osf.io/7qybs/?action=download
megahit -1 sample.R1.fq.gz -2 sample.R2.fq.gz -o mystery.assembly -m 5e9

quast mystery.assembly/final.contigs.fa
cat quast_results/latest/report.txt
EOF
```

You can now run all of these commands at once by typing:

```
bash assemble.sh
```


## Automation with Snakemake workflows

Let's try working with snakemake instead. Snakemake is
focused on *recipes* rather than *scripts*.

```
mkdir ~/workflows
cd ~/workflows
```


First, let's define a bunch of recipes:
```
cat >Snakefile <<EOF

rule download_r1:
    shell:
        "curl -o sample.R1.fq.gz -L https://osf.io/mjs65/?action=download"

rule download_r2:
    shell:
        "curl -o sample.R2.fq.gz -L https://osf.io/7qybs/?action=download"

rule assemble:
    shell:
        "megahit -1 sample.R1.fq.gz -2 sample.R2.fq.gz -o mystery.assembly -m 5e9 -f"

rule run_quast:
    shell:
        "quast mystery.assembly/final.contigs.fa"
EOF
```
and run one of them:

```
snakemake download_r1
```
and you can see you end up with the R1 file in the directory.

But this seems like a lot of extra syntax over the shell script to just download files. What's the advantage?

One advantage is that you can annotate recipes with what they *produce* -- let's modify the rules above to have output information:

```
cat >Snakefile <<EOF

rule download_r1:
    output: "sample.R1.fq.gz"
    shell:
        "curl -o sample.R1.fq.gz -L https://osf.io/mjs65/?action=download"

rule download_r2:
    output: "sample.R2.fq.gz"
    shell:
        "curl -o sample.R2.fq.gz -L https://osf.io/7qybs/?action=download"

rule assemble:
    output: "mystery.assembly/final.contigs.fa"
    shell:
        "megahit -1 sample.R1.fq.gz -2 sample.R2.fq.gz -o mystery.assembly -m 5e9 -f"

rule run_quast:
    output: "quast/latest/report.txt"
    shell:
        "quast mystery.assembly/final.contigs.fa"
EOF
```

So now you can do

```
snakemake download_r1 download_r2
```

and it will only run that if the output files don't exist.

```
snakemake download_r1 download_r2
```

But wait! It gets even cooler! You can *chain* recipes --

```
cat >Snakefile <<EOF

rule download_r1:
    output: "sample.R1.fq.gz"
    shell:
        "curl -o sample.R1.fq.gz -L https://osf.io/mjs65/?action=download"

rule download_r2:
    output: "sample.R2.fq.gz"
    shell:
        "curl -o sample.R2.fq.gz -L https://osf.io/7qybs/?action=download"

rule assemble:
    input: "sample.R1.fq.gz", "sample.R2.fq.gz"
    output: "mystery.assembly/final.contigs.fa"
    shell:
        "megahit -1 sample.R1.fq.gz -2 sample.R2.fq.gz -o mystery.assembly -m 5e9 -f"

rule run_quast:
    input: "mystery.assembly/final.contigs.fa"
    output: "quast/latest/report.txt"
    shell:
        "quast mystery.assembly/final.contigs.fa"
EOF

```

## *What* to publish with your paper

1. Raw data
2. Intermediate files that take a long time to generate
3. Software versions
4. Software command line flags
5. Workflows and/or shell scripts
6. R, Python, etc. scripts and notebooks for analysis and figures

## *Where* to put stuff to publish

Big raw data - SRA/ENA. (This will generally be required by journal.)

Medium size raw data (between 500 MB and 5 GB) - Open Science Framework, osf.io

Small raw data (under 500 MB) - github & zenodo.

Scripts, notebooks, workflows, and shell scripts - github & zenodo.

