## Course Projects

For STAMPS 2018, we will have student projects to give you an opportunity
to practice the skills and perspectives you've learned, integrate them in
a project setting and work with course colleagues in small teams. 

We will provide a few datasets and the metadata and some context, and your
group will formulate questions to ask of the data, conduct analyses and
generate outcomes. You may use your own dataset or other publicly available data, but you must have it 
approved by Tracy or Mihai. There is often significant data preparation 
required before analysis, or a longer analysis, that may not be feasible for the length of the 
course.

### Project outline

- Step 1: Step one of your project will be getting to know your data. What kinds of things are interesting about your data? How many samples and permutations do you have? What kinds of questions can you ask and what are interesting?
- Step 2: Once you've identified one or a few questions, conceptually how are you going to approach it. Outline the project steps conceptually or in pseudocode.
- Step 3: Set up your project. You can do this in github, or Google drive, or some other collaborative sharing space. (Add links on how to set up a project)
- Step 4: Start your analyses or data exploration. Don't forget to document the steps you're taking! You likely will try out a few things. That's good! So, documenting won't be 'methods' quality yet, but you want to remember what you did. When you decide on the analysis path, add more notes and documentation. You want future you and your other group members to be able to replicate your results.
- Step 5: Think about your output. Does it make sense? How could you plot it to display the information? How could you think about describing results.
- Step 6: Iterate back through one to many of these steps

### Potential Datasets 

#### Replication and Refinement of a Vaginal Microbial Signature of Preterm Birth 
16S vaginal swab micorbiome data for two cohorts of pregnant women. The women were enrolled using the same study design, procedures, and methods at separate sites within the United States between 2013 and 2015, and analyzed under a case-control design. One cohort, the “Stanford” cohort, was enrolled from women presenting to the obstetrical clinics of the Lucille Packard Children’s Hospital at Stanford University for prenatal care. The underlying population is predominantly Caucasian and Asian and has a low risk for PTB (<10%); the Stanford cohort analyzed here was selected to enrich for PTB outcomes. Another cohort, the “UAB” cohort, was enrolled from women referred to the UAB for intramuscular 17α-hydroxyprogesterone caproate therapy due to a history of prior preterm delivery.  <br>
Data: https://purl.stanford.edu/yb681vm1809 <br>
Article: https://www.ncbi.nlm.nih.gov/pubmed/28847941

#### Enterotypes of the human gut microbiome 
Shotgun data from fecal samples from European, American and Japanese subjects. Some subjects had ulcerative colitis (UC) or Crohn’s disease (CD) <br>
Article: https://www.nature.com/articles/nature09944 <br>
Supplemental methods: https://media.nature.com/original/nature-assets/nature/journal/v473/n7346/extref/nature09944-s1.pdf <br>
Used as an example in the Callahan et al paper [Reproducible Research Workflow in R for the analysis of personalized human microbiome data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4873301/#R9) <br>
Code and data is in that paper: http://statweb.stanford.edu/~susan/papers/PSBRR.html
   can load data in R with: <br>
     >library("phyloseq") <br>
     >data(enterotypes)

#### Bacterial microbiome in the human oral cavity shaped by salivary flow
16S data for oral samples and oral and salivary flow metadata. Subjects were recruited into four cohorts: (1) 11 healthy adults were recruited into a “discovery cohort”; (2) 7 additional healthy adults were recruited into a “control cohort” for the validation data set; (3) 3 additional healthy adults were recruited into a “mucosal biogeography cohort”; and (4) 10 individuals who experienced low salivary flow due to the autoimmune disorder, SS, were recruited into a “low-flow cohort” for the validation data set. One individual in each of the discovery and validation cohorts also participated in the mucosal biogeography cohort. <br>
Data and scripts: https://purl.stanford.edu/xr749qy9885 <br>
Article: https://www.nature.com/articles/s41467-018-02900-1

