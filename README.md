## Publication
R. Barbudo, A. Ramírez, F. Servant and J.R. Romero*. ["GEML: A grammar-based evolutionary machine learning approach for design-pattern detection"](https://doi.org/10.1016/j.jss.2021.110919). *Journal of Systems and Software*, 110919. 2021.

## Abstract
Design patterns (DPs) are recognised as a good practice in software development. However, the lack of appropriate documentation often hampers traceability, and their benefits are blurred among thousands of lines of code. Automatic methods for DP detection have become relevant but are usually based on the rigid analysis of either software metrics or specific properties of the source code. We propose GEML, a novel detection approach based on evolutionary machine learning using software properties of diverse nature. Firstly, GEML makes use of an evolutionary algorithm to extract those characteristics that better describe the DP, formulated in terms of human-readable rules, whose syntax is conformant with a context-free grammar. Secondly, a rule-based classifier is built to predict whether new code contains a hidden DP implementation. GEML has been validated over five DPs taken from a public repository recurrently adopted by machine learning studies. A second experiment increases this number up to 15 diverse DPs, showing its effectiveness and robustness in terms of detection capability. An initial parameter study served to tune a parameter setup whose performance guarantees the general applicability of this approach without the need to adjust complex parameters to a specific pattern. Finally, a demonstration tool is also provided.

## Additional material
### Experiment 1
#### **Results of statistical tests**
Analysis of *coverage threshold* ([ZIP](/experiment1/coverage.zip), 27KB)

Analysis of *support*, *confidence* and *classification strategy*:
- Adapted grammar ([ZIP](/experiment1/adapted.zip), 65KB)
- Full grammar ([ZIP](/experiment1/full.zip), 64KB)

Analysis of full grammar vs. adapted grammar ([ZIP](/experiment1/comparison.zip), 35KB)

### Experiment 3
#### **Repository for training**
For this experiment, a repository has been built for training. It contains implementations of 15 design patterns, as well as negative samples. Here we describe how the samples are generated:

*Positive samples*
1. Instances available from the [P-Mart repository](http://www.ptidej.net/tools/designpatterns/index_html#2) (v1.2) are added, since they have been peer-reviewed.
2. Pieces of code for which both SSA and Ptidej tools agree in that they implement a design pattern are identified. The code belongs to the same Java projects considered in P-Mart.
3. Instances from step 2 are automatically processed and manually revised to match roles, since each tool provides different information and level of granularity.

*Negative samples*
1. The VF2 algorithm, available in the [VFLib graph matching library](https://mivia.unisa.it/vflib/), is executed to find group of classes that are structurally similar to the design pattern.
2. For each design pattern, we define heuristics to filter out instances. This process is required because the VF2 algorithm might return a high number of results. The heuristics check the type of relationship between classes playing roles, which is not taken into account in the previous step.
3. For each positive sample, a maximum of three negative samples are randomly selected from the project in which the positive sample was found.

The resulting repository is available for reproducibility purposes. It is provided for each design pattern separately:
- [Abstract factory](/experiment3/repository/AbstractFactory.xml)
- [Adapter](/experiment3/repository/Adapter.xml)
- [Bridge](/experiment3/repository/Bridge.xml)
- [Command](/experiment3/repository/Command.xml)
- [Composite](/experiment3/repository/Composite.xml)
- [Decorator](/experiment3/repository/Decorator.xml)
- [Factory method](/experiment3/repository/FactoryMethod.xml)
- [Iterator](/experiment3/repository/Iterator.xml)
- [Observer](/experiment3/repository/Observer.xml)
- [Proxy](/experiment3/repository/Proxy.xml)
- [Singleton](/experiment3/repository/Singleton.xml)
- [State](/experiment3/repository/State.xml)
- [Strategy](/experiment3/repository/Strategy.xml)
- [Template method](/experiment3/repository/TemplateMethod.xml)
- [Visitor](/experiment3/repository/Visitor.xml)

#### **Detection rules generated by GEML**
The following files contain the detection rules for each design pattern. These rules correspond to the best detection model generated by the G3P algorithm after applying the pruning method (database coverage).
- [Abstract factory](/experiment3/rules/AbstractFactory.txt)
- [Adapter](/experiment3/rules/Adapter.txt)
- [Bridge](/experiment3/rules/Bridge.txt)
- [Command](/experiment3/rules/Command.txt)
- [Composite](/experiment3/rules/Composite.txt)
- [Decorator](/experiment3/rules/Decorator.txt)
- [Factory method](/experiment3/rules/FactoryMethod.txt)
- [Iterator](/experiment3/rules/Iterator.txt)
- [Observer](/experiment3/rules/Observer.txt)
- [Proxy](/experiment3/rules/Proxy.txt)
- [Singleton](/experiment3/rules/Singleton.txt)
- [State](/experiment3/rules/State.txt)
- [Strategy](/experiment3/rules/Strategy.txt)
- [Template method](/experiment3/rules/TemplateMethod.txt)
- [Visitor](/experiment3/rules/Visitor.txt)

#### **Outcomes of GEML, SSA and Ptidej**

The next table shows the number of design pattern implementations found by each tool for the project [DPExample](https://essere.disco.unimib.it/marple-2/). For each design pattern and tool, a file with the information of the implementations can be downloaded by clicking on the cell number. Symbol '-' stands for non-supported design patterns.

| Design pattern | GEML | SSA | Ptidej |
| --- | --- | --- | --- |
| *Abstract factory* | [99](/experiment3/results/geml/GEML-DPExample-AbstractFactory.txt) | - | - |
| *Adapter* | [12](/experiment3/results/geml/GEML-DPExample-Adapter.txt) | [54](/experiment3/results/ssa/SSA-DPExample-Adapter.xml) | [128](/experiment3/results/ptidej/Ptidej-DPExample-Adapter.txt) |
| *Bridge* | [41](/experiment3/results/geml/GEML-DPExample-Bridge.txt) | [3](/experiment3/results/ssa/SSA-DPExample-Bridge.xml) | - |
| *Command* | [79](/experiment3/results/geml/GEML-DPExample-Command.txt) | [4](/experiment3/geml/results/ssa/SSA-DPExample-Command.xml) | [36](/experiment3/results/ptidej/Ptidej-DPExample-Command.txt) |
| *Composite* | [30](/experiment3/results/geml/GEML-DPExample-Composite.txt) | [7](/experiment3/results/ssa/SSA-DPExample-Composite.xml) | [29](/experiment3/results/ptidej/Ptidej-DPExample-Composite.txt) |
| *Decorator* | [5](/experiment3/results/geml/GEML-DPExample-Decorator.txt) | [19](/experiment3/results/ssa/SSA-DPExample-Decorator.xml) | - |
| *Factory method* | [26](/experiment3/results/geml/GEML-DPExample-FactoryMethod.txt) | [1](/experiment3/results/ssa/SSA-DPExample-FactoryMethod.xml) | [44](/experiment3/results/ptidej/Ptidej-DPExample-FactoryMethod.txt) |
| *Iterator* | [5](/experiment3/results/geml/GEML-DPExample-Iterator.txt) | - | - |
| *Observer* | [2](/experiment3/results/geml/GEML-DPExample-Observer.txt) | [4](/experiment3/results/ssa/SSA-DPExample-Observer.xml) | - |
| *Proxy* | [5](/experiment3/results/geml/GEML-DPExample-Proxy.txt) | [2](/experiment3/results/ssa/SSA-DPExample-Proxy.xml) | [127](/experiment3/results/ptidej/Ptidej-DPExample-Proxy.txt) |
| *Singleton* | [21](/experiment3/results/geml/GEML-DPExample-Singleton.txt) | [22](/experiment3/results/ssa/SSA-DPExample-Singleton.xml) | [82](/experiment3/results/ptidej/Ptidej-DPExample-Singleton.txt) |
| *State* | [57](/experiment3/results/geml/GEML-DPExample-State.txt) | [41](/experiment3/results/ssa/SSA-DPExample-State.xml) | [104](/experiment3/results/ptidej/Ptidej-DPExample-State.txt) |
| *Strategy* | [46](/experiment3/results/geml/GEML-DPExample-Strategy.txt) | [6](/experiment3/results/ssa/SSA-DPExample-Strategy.xml) | 0 |
| *Template method* | [11](/experiment3/results/geml/GEML-DPExample-TemplateMethod.txt) | [20](/experiment3/results/ssa/SSA-DPExample-TemplateMethod.xml) | [234](/experiment3/results/ptidej/Ptidej-DPExample-TemplateMethod.txt) |
| Visitor | [33](/experiment3/results/geml/GEML-DPExample-Visitor.txt) | [11](/experiment3/results/ssa/SSA-DPExample-Visitor.xml) | [2](/experiment3/results/ptidej/Ptidej-DPExample-Visitor.txt) |

Note: For SSA and Ptidej, the number of DP implementations might not coincide with the number of raw results in the corresponding file. The reason is that each tool follows a different strategy to group the classes that implement each role. More specifically, we observe that SSA defines one instance for each combination of roles (only one class per role), while Ptidej puts together all classes implementing a multiple role (e.g. subclasses in a hierarchy).


### Demonstration tool

#### **How to install this tool**:

1. Download the demonstration tool ([ZIP](/tool/geml.zip), 31.7 MB)
   - *Note*: This tool has been tested for Java 8, in both Ubuntu 18.04 and Windows 10.
   - The full set of DP samples used in the experimentation are contained in the */data* folder.
2. Unzip the file.
   - *Note:* Please do not write special characters or white spaces in the location path. Their use is restricted by the third-party library [ckjm](https://www.spinellis.gr/sw/ckjm/doc/faq.html).
3. Download the VFLib graph matching library ([ZIP](/tool/vf2.zip), 216 KB)
   - *Note*: This tool uses the C++ implementation of the VF2 algorithm to generate the candidates. This folder should be located in the root folder of the tool. Follow the next steps to compile the library:
   - Run *make*
   - Execute *g++ -c -I include/ designPattern.cc*
   - Execute *g++ -o designPattern designPattern.o -L lib -lvf -lstdc++ -lm*
4. Download the example repository ([ZIP](/tool/repo.zip), 70.9 MB)
   - These projects can be directly downloaded from the [MARPLE website](http://essere.disco.unimib.it/wiki/marple) or the [P-Mart repository](http://www.ptidej.net/tools/designpatterns/index_html#2) (with the exception of DPExample).
   - Unzip the file into the */repo* folder.
5. (Optionally) In case you want to skip Step 1 (*Generation of candidates*) and 2 (Learning of the detection model), please download the set of candidates, computed metrics and generated rules of the running example ([ZIP](/tool/gExample-jrefactory-singleton.zip), 26.4kB)
   - *Note*: Unzip this file into the root folder of the GEML application.

#### **How to execute a running example**:
1. Execute the launch script.
   - *Note*: Depending on your OS, please run *dpdtool.bat* for Windows, or *dpdtool.sh* for GNU/Linux
2. Move to the "**DP Candidates (project path)**" tab:
   1. Under the "**Set a new project path**" label, select the Singleton pattern and click the ![button](https://www.uco.es/grupos/kdis/wp-content/uploads/open.png) button.
   2. Set the path of the target project, i.e., the project for which you want to detect the Singleton pattern instances.
      - *Note*: For this example, please select *JRefactory*, which is part of the DPB repository. It should be noted that the project folder requires a specific structure: (1) a */bin* folder containing the ".class" files; (2) a */src* folder containing the ".java" files; and (3) a */lib* directory containing any external dependency in form of ".jar" files.
   3. GEML will automatically generate the list of candidates potentially implementing the Singleton pattern. This step depends on an external library (ckjm) and can take a few minutes, especially if you are running on Windows. When finished, the number of candidates will be reported.
      - *Note*: Click the ![save button](https://www.uco.es/grupos/kdis/wp-content/uploads/save.png) button to save the set of pattern candidates and the computed software metrics, respectively. For reproducibility, notice that both files could be loaded later by clicking the ![open button](https://www.uco.es/grupos/kdis/wp-content/uploads/open.png) button located under the label "*Load an existing set of candidates*".
3. Move to the "*DPD Model (repository)*" tab:
   1. Click the ![open button](https://www.uco.es/grupos/kdis/wp-content/uploads/open.png) button, located under the label "*Learn set of detection rules*", to load the *singleton.xml* file, which contains the full parametrisation of the G3P4DPD algorithm.
      - *Note*: For those interested, notice that this file could be modified to set the values of some additional, internal-specific parameters. Nevertheless, the GUI allows the user to set the values of the support and confidence thresholds after loading this file.
   2. Click the ![project button](https://www.uco.es/grupos/kdis/wp-content/uploads/project.png) button and deselect the *JRefactory* project to indicate that you are not interested in using it anymore for the generation of the DPD detection model. Click then *Apply* and *Close*.
   3. Select the set of properties to be used to characterise the design pattern implementations.
      - *Note*: In this example, select the common properties describing the Singleton pattern (explained in Section 6.2 of the paper): *isFinal*, *isSubclass*, *controlledExcep*, *controlledInit*, *conglomeration*, *returns*, *receives*, *createObject*, *ctorVisibility*, *aggregation*, *redirectInFamily*, *NOM*, *NOC*, *DIT* and *RFC*.
   4. Click ![run button](https://www.uco.es/grupos/kdis/wp-content/uploads/run.png) to launch the G3P4DPD algorithm. When finished, the rules composing the detection model will be reported.
      - *Note*: Click ![save button](https://www.uco.es/grupos/kdis/wp-content/uploads/save.png) to save the detection rules. For reproducibility, notice that this file could be loaded later by clicking the ![open button](https://www.uco.es/grupos/kdis/wp-content/uploads/open.png) button, located under the label "*Load an existing set of detection rules*".
4. Select a classification strategy and click ![run button](https://www.uco.es/grupos/kdis/wp-content/uploads/run.png), located to the right of the label "*Detection strategy*".
   - *Note*: For this example, please select the DFML_lap.
5. Finally, after completing the execution, the detected design patterns will be reported.

#### **How to execute GEML with the DPB samples (from experimentation):**
DPB samples (positives and negatives) for the Singleton pattern ([ZIP](/samples/repo-candidates-singleton.zip), 5.5kB). This file contains 9 XML files, one per project, including both positive and negative samples of the Singleton pattern, as used for the experimentation.
1. Unzip the DPB samples in the root folder of the *GEML* project.
2. Load the file containing the Singleton samples of the project we are interested in.
   - *Note*: For this example, please select *jrefactory.xml file*, which contains 10 samples (6 positives and 4 negatives).
3. Load the file */data/metrics.csv* containing the metrics of all the projects from the DPB repository.
4. Generate a detection model for the Singleton pattern excluding the JRefactory project.
5. Execute the detection process selecting any classification strategy.
