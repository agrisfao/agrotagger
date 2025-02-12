### System Requirements

- java >= 1.6 (mandatory)
- git >= 1.8.1.4 (to download the project from GitHub: other solutions may be adopted)
- maven >= 3.0.3 (to edit the code and build a new jar: you can also work with the provided command line application, without using Maven)
- linux environment (the provided command line application comes with some bash scripts to execute the code. A developer can replace the bash script with another one, as a bat script for Windows)

### Execute the command line application

The folder `executable` contains the command line application, including some bash scripts to run AgroTagger (note: if the bash can't interpret the scripts, try to run the `dos2unix` command). 

#### SCRIPTS  

**tagger.sh**  
It needs 4 mandatory parameters: 
* the path to a file with a list of URLs (or the output of a web crawler)
* the path to the output directory where to store results
* the type of the input file ("listURL" or "nutchOutput")
* the type of the output ("rdfnt" or "text"). 

> Example: ``./tagger.sh data/sources/crawler_result.txt data/documents nutchOutput rdfnt``  
  
There is also the possibility to express, as optional parameter, the name of the output file. Currently, the output file is a tar.gz file, but you don't need to define the extension, the system will automatically add the suffix .tar.gz to the filename.  
> Example: ``./tagger.sh data/sources/list_urls.txt data/documents listURL rdfnt myoutput``  
  
From v1.2.1, there is also the possibility to specify other two optional parameters: 
* the name of a new AGROVOC SKOS file
* the name of a new MAUI model
If names are not correct (i.e. the model and the voabulary are not in the application) the application stops. See the [online documentation](https://github.com/agrisfao/agrotagger/wiki/How-to-use-an-updated-AGROVOC-thesaurus) to know how to build a new model.  

> Example: ``./tagger.sh data/sources/crawler_result.txt data/documents listURL rdfnt myoutput new_agrovoc_name my_model``  
  
In this last scenario, the fifth parameter (output_filename) can be null.  

> Example: ``./tagger.sh data/sources/crawler_result.txt data/documents listURL rdfnt null new_agrovoc_name my_model``

The boolean flag to avoid the extraction of titles is not considered, but it is set to true by default. Thus, titles are always extracted by this script. To use the boolean flag, run [Java applications](https://github.com/fcproj/agrotagger/wiki/Java-Applications) indipendently.

**taggerDir.sh**  
It works as the previous one, but the first parameter is the path to a directory containing some input files.  

> Example: ``./taggerDir.sh ../work/splitted ../work/output nutchOutput rdfnt``  
  
From v1.2.1, there is the possibility to express a fifth and a sixth parameter: newAgrovocName; modelName

> Example: ``./taggerDir.sh data/sources/ data/documents listURL myoutput newAgrovocName modelName``
  
### Output
  
A TAR.GZ file containing the RDFNT ot TXT produced (An example of the output RDF file is available in the [RDF](https://github.com/agrisfao/agrotagger/wiki/Example-of-AgroTagger-output) page.)

### The Maven project

The folder `maven-source` contains the Maven source project. You can use it to edit the code or to build the "AgroTagger" distribution zip file (i.e. the command line application):

`cd maven-source/`   
`mvn clean install`  

You will find the created zip file in the directory `maven-source/target`. 

### License

GNU General Public License version 3 (GPL-3.0). See [Legal Code](https://github.com/fcproj/agrotagger/blob/master/agrotagger/LICENSE)
