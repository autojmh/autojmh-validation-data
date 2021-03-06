# AutoJMH Validation
You have arrived to the AutoJMH validation repo. In this document you fill find instructions to reproduce our results.

##Experiment 1
The experiment 1 consisted in a comparison between the microbenchmarks generated by AutoJMH, an expert and those of 6 Java engineers.

This repo contains the all microbenchmarks used in the article, the ones generated automatically by AutoJMH and those manually writen by the expert and the six Java engineers participating in the experiment. They are separated in individual projects for each particiant: the expert and all six engineers, as well as another for AutoJMH.

In order to execute the microbenchmarks:

1. Clone this repo
2. Maven-package the parent project `validation-parent`. This will generate eight JARs one for each project containing the microbenchmarks generated by AutoJMH, the expert and the six engineers.
3. You must navigate to the *target* folder of each project and run the following command: 
	**`java -jar benchmark.jar -wf 1 -wi 5 -i 5 -f 1`**. 
This will give you the results for each project 
 


If you want to re-generate the microbenchmarks of the experiment using AutoJMH, you may:

1. Download and Maven-Install **AutoJMH** from its [sources](https://github.com/autojmh/autojmh-source-code)
2. Clone this repo to your machine, it contains the source code used by both AutoJMH and the participants to generate their microbenchmarks.
3. Locate the property file for `AutoJMHBase.properties` in the *src/main/resources* folder of the **AutoJMH** sources.
4. Set variable `projectDir` to the absolute path of the root *Samples* directory in your machine. (The root directory is the one containing the *pom.xml* file). 
   Set an output directory in `outputDir`, as well as a temporary working directory in `workingDir`. The working dir is for **AutoJMH** to store intermiediary results.
5. Execute AutoJMH using as entry point `fr.inria.autojmh.tool.AllTags.java`
6. The resulting microbenchmarks will be in the output directory you specified in variable `workingDir`.

The microbenchmarks by the expert are located in dir "expert" and for the engineers 1 to 6 in the directories "eng1" to "eng6". 
The estructure is the same for all engineers and the expert.

1. Microbenchmarks MB1a and MB1b for the different behaviors of SUA 1 are located in class `DifferentInheritors.java`
2. Microbenchmark M2 for SUA 2 in class `TransientStateListAdd.java`
3. Microbenchmark M3 for SUA 3 in class `TransientStateListSort.java`
4. Microbenchmarks M4 and M5 for SUA 4 and 5 are located in class `MathOperations.java`

***Attention***: If you want to execute the AutoJMH microbenchmarks used in the article, don't forget to change the value of the constant `DATA_ROOT_FOLDER` in the `fr.inria.diverse.autojmh.validation.autojmh.Main` class.

##Experiment 2
The experiment 2 was meant to evaluate the reach of AutoJMH in 5 real live projects. 

In order to reproduce this experiment:

1. You may find the code for all five projects in the *projects* directory of this repo. Uncompress them. 
2. Locate the property file for `AutoJMHBase.properties` in the *src/main/resources* folder of the **AutoJMH** sources.
3. Set variable `projectDir` to the root directory in your machine for the project you want to generate microbenchmarks.
(The root directory is the one containing the *pom.xml* file). Set an output directory in `outputDir`, as well as a temporary working directory in `workingDir`. The working dir is for **AutoJMH** to store intermiediary results.
4. Execute AutoJMH using as entry point `fr.inria.autojmh.tool.AllLops`
5. AutoJMH will print at the end of the process the results.
6. You may find the generated project in the `outputDir`.

##Questions
Any question regarding how to reproduce the results, you may leave an issue.

