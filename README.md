### Introduction: Bioinformatics seminars at Skoltech

**Disclaimer:** the entire repository is forked from Aleksandra Galitsyna with her permission. 

We're going through the course on Bioinformatics held by Prof. Mikhail Gelfand, and I (Anna Rybina) will be your TA for the Seminar 4 on 
sequence alignments and motif search. 

All materials for this seminar,including slides and datasets, can be found at [the github repo](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/)

The datasets are deposited [here](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/tree/master/data). 

For the home assignments and table with files distribution, check out Canvas. 


## Seminar 4. Multiple Alignments

Anna Rybina 12/11/2022

### Location of the files

The files for this hometask are located at this github repository: 

https://github.com/rybinaanya/2021_Skoltech_Bioinformatics_course_seminar_4/tree/master/data/

If you need to view the file, the link will be: 

https://github.com/encent/2021_Skoltech_Bioinformatics_course_seminar_4/blob/master/data/upstreams.fasta

To download a raw file, there are 2 options:

a) `right click` the `Raw` button at the top of the file, select `Save Link As…` (or depending on the version of your Internet browser, `Download Linked File As...`), choose the location on your computer where you want to save the file, and select `Save`. 

b) press `Raw` in GitHub window with file, copy the link from the browser and use `wget` to download as in an example below: 

```
wget https://raw.githubusercontent.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/master/data/peaks.fasta
```

### Task 1. Multiple alignment

In this part of the task you will work with alignments with three popular aligners: MUSCLE, ClustalW and T-COFFEE. 


1.1. Download the file with upstream regions of bacterial orthologs (`upstreams.fasta`).
 
1.1. To download the files on the local computer, follow the links, e.g.:

https://raw.githubusercontent.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/master/data/upstreams.fasta 


1.2. Select one of the aligners to run on these sequences. Your aim is to find small (up to 16 bp) regulatory regions of DNA in the 
upstream sequences of bacterial genes. To improve the quality of the alignment, you can try to vary the parameters. 
Please, note these parameters, you will be asked to report them in the assignment.

Helpful links:

| Aligner  | Web server link                            | CLI manual                                                               | Original paper |  Type |
|----------|------------------------------------------|--------------------------------------------------------------------------|----------------|---|
| MUSCLE   | https://www.ebi.ac.uk/Tools/msa/muscle   | [`muscle` manual](https://www.drive5.com/muscle/manual/options.html)                       |     [Edgar 2004](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-5-113)           | Global alignment  |
| ClustalW | https://www.genome.jp/tools-bin/clustalw | [`clustalw` manual](http://manpages.ubuntu.com/manpages/bionic/man1/clustalw.1.html)          |     [Thompson et al. 1994](https://academic.oup.com/nar/article-abstract/22/22/4673/2400290?redirectedFrom=fulltext)           | Global alignment  |
| T-COFFEE | http://tcoffee.crg.cat/                  | [`t_coffee` manual](https://tcoffee.readthedocs.io/en/latest/tcoffee_main_documentation.html) |     [Notredame et al. 2000](https://www.sciencedirect.com/science/article/abs/pii/S0022283600940427?via%3Dihub)           |  Global and local alignment |

1.2.a. If you select web server interface, follow the instructions on the website, for example: 

![Web Server Instructions 1](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/blob/master/images/Figure1.png)


![Web Server Instructions 2](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/blob/master/images/Figure2.png)


Check the output of these commands. What is the file format of the output? 

> Hint: typically the output is represented in [FASTA](https://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=BlastHelp) 
>or [CLUSTAL](http://scikit-bio.org/docs/0.2.1/generated/skbio.io.clustal.html#:~:text=Format%20Specification,in%20the%20alignment%20%5BR152%5D.) format. 

1.3. Download the output files with alignments, or copy full alignments to the clipboard. 

1.4. Visualize **the alignment** using MView provided by EMBL-EBI: [https://www.ebi.ac.uk/Tools/msa/mview/](https://www.ebi.ac.uk/Tools/msa/mview/)

This tool allow you to paste your alignment and highlight it based on sequence conservation. 

**Pay extra attention to**: 
- Type of sequence you upload/paste (DNA)
- Input format of your alignment. The full list of MView-accepted formats can be found [here](https://www.ebi.ac.uk/seqdb/confluence/display/JDSAT/MView+Help+and+Documentation#MViewHelpandDocumentation-informat). 
The examples of different formats can be found [here](https://www.hiv.lanl.gov/content/sequence/HelpDocs/SEQsamples.html)

> Do not paste the original upstreams.fasta at this step! Your alignment should contain gaps ("-" symbols). 

1.5. Propose a region that might be conserved regulatory sequence of DNA in the alignment of gene upstreams of bacteria. 
There is no ultimately right answer, so concentrate on the best candidate you observe and describe your conclusion. 

Consider the following criteria for conserved regulatory sequence: 
- Should it be present in all the sequences? (probably yes)
- Should it contain the gaps? (probably no)
- Should it be located close to the gene start? (probably yes)

1.6. Try another aligner. Has the result changed? 

Try all three aligners, select the one that results in most full and realistic regulatory sequences. 

Visualize the best aligner output at the location of the best candidate regulatory sequence alignment. 
You may highlight the candidate regulatory sequence by graphics editor.

Save the information about the aligner and the image. **This will be part of your home assignment (Task 1).**

1.7. Copy the best candidate regulatory sequence alignment only and manually convert it into FASTA file. 
Use text editor for this task to save the selected block of the alignment as a separate file. 
You may use Word, Notepad/TextEdit to create only the alignment; 
advanced users might use `vim` block-selection opportunity (see below). 

The resulting file should contain something like:

```
>1
GGTCAATTCACTGCCTT
>2
GGCCAATTTACGGCCTT
>3
GGTCAGTTCACGGCATT
>4
TCCTAATTTACAGCAGC
>5
GGTCAGTTCACGGCATT
>6
GGCCAATTTACTGCGTT
>7
AACCAGCTTGAGACAGC
```

Save this file and download it to your local computer. **This will be your input for the construction of PWM (Task 2).**

### Task 2. Construction of position weight matrix (PWM)
 
You will use the output of Task 1 (1.7) for the construction of consensus sequence and PWM. 

2.1. Do the following steps:
- Go to RSAT web tool: http://embnet.ccg.unam.mx/rsat/ 
- Click -> `"Matrix tools"` from left menu 
- -> `"convert matrix"`
- Select matrix format `“sequences”`
- Paste alignment of conserved sequences in FASTA format to the field, or upload the file
- Check the boxes "consensus", "counts", "frequencies", "weights", "profile" and "Compute reverse complement" (if they are not selected). 
Set all other parameters to default. Press “GO”. 

2.2. In the RSAT output you can observe the transition from alignment to nucleotides counts matrix, 
frequencies matrix, then to weights, profile and logo. 

Save the forward logo to your local computer. **This will be part of your home assignment (Task 2).**

### Task 3. Automated search of motifs in the sequences with MEME. 

3.1. Now let’s switch to some more automated tool, Multiple Expression motifs for Motif Elicitation (MEME, http://meme-suite.org/tools/meme). 

- Upload the upstreams.fasta file
- Select `"One occurence per sequence"` for `"Select the site distribution"`
- Press “Advanced options”, set “How wide can motifs be?” **from 5 to 15**. **Don't forget this step, otherwise you will wait for your results for quite some time (Why?)**
- Submit and wait for results
- Go to `"MEME HTML output"` and check the result

The initial submission form should look similar to this one: 

![MEME Instructions](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/blob/master/images/Figure3.png)


Are any of the found motifs similar to your result obtained manually in Task 2? 
Try to submit the most significant motif to Tomtom program to find similar motifs in public libraries (click `Submit/Download`, select `Tomtom`, click `Submit`, adjust parameters to the **prokaryotes** search).
Save the resulting report to your local computer. **This will be part of your home assignment (Task 3).**

### Task 4. Motif search in ChIP-Seq data

Now you will use MEME-ChIP for search of motifs in ChIP-Seq dataset. 
Your input is the peaks from ChIP-Seq experiment on _Gallus gallus_ (chicken) for CTCF protein. 
We will use this knowledge for a test run of MEME-ChIP. 

- Download ChIP-Seq peaks ([peaks.fasta](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/blob/master/data/peaks.fasta)). 
- Go to MEME-ChIP web interface: http://meme-suite.org/ -> MEME-ChIP
- Do not change the options, submit the `peaks.fasta` file

The result will look as following: 

![MEME ChIP output](https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/blob/master/images/Figure4.png)

To interpret this result, take a look at:
- Number of found motifs
- E-values of the hits (What would you consider significant?)
- Discrepancy between E-value of the best hit and E-values of suboptimal hits (Do you expect high discrepancy for meaningful hits?)
- Known or similar motifs to the hit obtained by TOMTOM tool 
(You can press the links in this field to learn more. Are the TOMTOM hits significant?)
- Complexity and the length of the logo. 
(Can you expect the motif to too short or contain only 2-4 informational positions?) 
- Distribution of the possible binding sites around the centers of the peaks 

> Hint on how to select the best motif. 
> You work with ChIP-Seq peaks, which represent the DNA sequences bound by CTCF protein.
> In ChIP-Seq, the protein is bound preferentially at the center of peaks. 
> If you observe some motif in the peaks sequences with good E-value and central enrichment, 
> this is a sign of true motif of the binding protein of interest.
> Even more, if you observe significant similarity to other vertebrates' CTCF, you must be sure you've found the right motif.

> If you observe some other motifs significantly enriched in your peaks, it might be the co-occuring binding of chromatin factors. 

Now, as you've learned to work with MEME-ChIP, you can download your own file with ChIP-Seq. You do not have the information 
about the factor or species. You need to derive this information from MEME-ChIP output. 

4.1. Find your name and corresponding file in the table provided in Files section for this seminar in **Canvas**

4.2. Download your file with peaks from the "data/unknown_peaks" folder from this repository: 

https://github.com/rybinaanya/2022_Skoltech_Bioinformatics_course_seminar_4/tree/master/data/unknown_peaks

4.3. Run MEME-ChIP and **answer to the questions in the Assignements (Task 4)**. You may need to download the MEME-ChIP report for that. 

### Home assignments

Your home task will be in Canvas "Assignments" section. 
The assignments will test your understanding of the topic. 
You are expected to learn how to use T-COFFEE, Muscle and ClustalW, 
build global and local alignments (and tell the difference between them), 
build the motifs from the given alignment and perform _de novo_ search of the motifs.
The home assignment will test the correct output of the tools in your hand, your ability to observe and interpret the results, 
and express your opinion on the results. 

The deadline for submitting the home task is 12:00 on Wednesday, November 23. 

### Afterword from TA

I hope it was fun to learn about alignments, motifs search and analysis of ChIP-Seq peaks. :) 
Write me at Skoltech e-mail, search it in Outlook by Anna Rybina.

### Acknowledgement

Special thanks to Dr. Aleksandra Galitsyna for the materials and discussion.
