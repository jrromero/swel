# SWEL - A Domain-Specific Language for Modelling Data-Intensive Workflows
_This page contains additional material to the paper entitled “SWEL: A Domain-Specific Language for Modelling Data-Intensive Workflows”, accepted in BISE journal (2023)_

## SWEL Technical Report

This [technical report](2023-01_SWEL_Technical_Report.pdf) defines the formal specification of SWEL (Scientific Workflow Execution Language) in terms of its meta-models and constraints, making this definition syntax-independent, according to the precepts of model-driven engineering. SWEL is a domain-specific modelling workflow language for defining data-intensive applications, which use advanced computing techniques with the aim of discovering valuable knowledge from huge amounts of data coming from real-world sources. The objective of SWEL is to provide a high-level, domain-independent definition language for the formulation of scientific workflows, hiding low-level computational aspects. SWEL is founded on a multi-layered structure that enables both the definition of workflows for different domains, the reuse of knowledge and the portability and interoperability among different workflow platforms.

## Tool Support

### JSON Concrete Syntax Validator

JSON is an IETF ([Internet Engineering Task Force](https://datatracker.ietf.org/doc/html/rfc8259)) standard language widely used as a data exchange format on the web via, e.g., REST APIs and services. JSON is also possible to use SWEL as a concrete textual notation for the serialisation of DIW models. To improve practicability, a syntactic validator is a useful tool to verify that the JSON document is well constructed and conforms to both the standard and the SWEL metamodel. To this end, a JSON schema has been generated in accordance with the declaration of the JSON-based concrete notation corresponding to the metamodel. The validation tool has been implemented in Java and it provides a command-line interface whose only argument is the path of the JSON file to be analysed. It reads and parses the input file in order to check if its content is according to the JSON scheme. If not compliant, the execution console reports the detected errors.

- Download JSON Validator ([Runnable JAR](./Tool_Support/JSON_Validator/validator-jar.zip))
- How to execute it:
```
java -jar validator.jar <path_to_workflow.json>
```
- Workflows: [Example1](./Tool_Support/JSON_Validator/example1-json.zip), [Example2](./Tool_Support/JSON_Validator/example2-json.zip), [Example3](./Tool_Support/JSON_Validator/example3-json.zip) (with errors)

#### Screenshoots:

_Validation of a valid SWEL workflow: Example2_

![Validation of a valid SWEL workflow: Example2](https://github.com/jrromero/swel/assets/16683876/2572521a-8e5b-4e0e-a879-d399b107c3ea)

_Output of an invalid SWEL workflow: Example3 (with errors)_

![Output of an invalid SWEL workflow: Example3 (with errors)](https://github.com/jrromero/swel/assets/16683876/0aeb3b60-ffd3-4e4f-bbd0-ea489cbf2474)

### Model-Based Workflow Management System

According to the user requirements, the need of facilitating the creation of workflows for data-intensive domains has led to the implementation of a workflow management system (WfMS). This is to define and execute data-intensive workflows for a wide range of domains, according to the user requirements. The tool which we have developed provides a set of domain-agnostic workflow components that can be configured and adapted to define domain-specific workflows at a high level of abstraction. The architecture of the tool is divided into two well-differentiated layers: a highly customisable user-centric graphical editor assisting domain experts to define domain-specific data-intensive applications, and a workflow engine intended to take advantage of available computational resources to execute the workflow activities in an effective and optimal way.

_Architecture of the model-based WfMS_:

![Architecture of the model-based WfMS](https://github.com/jrromero/swel/assets/16683876/8b56e7cb-980a-4a29-b83d-b6a96250d17a)

On the one hand, the editor layer uses a SWEL concrete syntax to represent workflows. The graphical editor is a design-oriented end-user environment that allows users to graphically define workflows and monitor their execution. With this purpose, users are provided with the necessary elements to draw and configure a data-intensive workflow that include: (1) a palette containing the set of available workflow components like data providers, processes or services; (2) a canvas area where the components can be inserted and connected defining their dependencies; and (3) a design assistance that helps users during the design of the workflow. Note that, due to the correspondence between the concrete syntax and the language metamodel, it is possible to directly verify its conformance. Furthermore, it is also possible to work at different levels of abstraction for the same workflow definition (graph execution, node representation, etc.). Once the workflow has been designed, the workflow repository manages the storage and retrieval of data-intensive workflows, as well as its exportation and importation to use in or from another compatible WfMS. Moreover, the workflow execution manager enables the management of the workflow execution and monitoring, gathering the execution traces and data that are shown to users on the own graphical editor. To graphically show the results generated during the execution, and depending on the data type, the data can be directly displayed on the canvas (e.g., numbers, strings) or delegated to an advanced data visualiser (e.g., images, video, data sets) using different kinds of graphics and tables.

The workflow execution engine interprets and executes the activities defined in the workflow. To this end, the engine provides all the features required for the invocation of services (both local and remote), the local execution of computing programs, and the management of data. Different elements are responsible for performing the workflow execution. Firstly, the scheduler analyses the high-level workflow definition according to the workflow language, and generates the corresponding low-level executable specification. This module coordinates and optimises the execution considering the computational constraints and the workload of the executor. Then, the executor module uses this low-level executable version to run the corresponding computing programs or services. The executor is flexible to integrate external tools and platforms (e.g., for grid and distributed computing), increasing the computational capabilities and reducing the execution time. Finally, the monitoring module logs the execution to provide information related to time, available memory and outcomes in order to monitor how resources are managed and consumed, and how resulting data are generated.

- Download ([Windows](./Tool_Support/WfMS/swel_editor_win32.win32.x86_64.zip), [Linux](./Tool_Support/WfMS/swel_editor_linux.gtk.x86_64.zip), [MacOS](./Tool_Support/WfMS/swel_editor_macosx.cocoa.x86_64.zip))

#### Videos

1. Executing a simple control-driven workflow composing by a Java process, a data input and a display, in order to perform an image transformation and visualize the result.

https://github.com/jrromero/swel/assets/16683876/706c0938-004e-48f8-aff2-987538acbc36

2. Creating a complex workflow, using existing workflows.


https://github.com/jrromero/swel/assets/16683876/041bd68e-0133-40a9-8c08-1be98844b9a9


3. Customizing the editor palette with ready-to-use processes to facilitate the definition of new workflows in a particular domain.


https://github.com/jrromero/swel/assets/16683876/7ffd2aa6-55f6-4287-8b0e-3fe06d4fb05e


4. Executing a workflow, showing the result in the WfMS and storing the workflow engine output in a local file.


https://github.com/jrromero/swel/assets/16683876/c850792e-379a-43dd-bc61-a8a0a81340ea


## Validation of SWEL

### Evaluation of Model Transformations

To evaluate the suitability of SWEL metamodel, it is used as a mechanism for interoperability between WfMS. We work with SCUFL and MoML, showing the possible reuse of workflows generated in Taverna towards Kepler. A second use case examines how SWEL can be used to facilitate the collective development of new pipelines in different tools like CWL. In this section, we provide the diferrent assets used in the model transformations process, such as metamodels, model-to-model transformations, text-to-model transformations and model-to-text transformations.

#### Metamodels:
- SWEL metamodel ([ecore](./Validation/1_Model_Transformations/EcoreMM_swel.zip))
- CWL metamodel ([ecore](./Validation/1_Model_Transformations/EcoreMM_cwl.zip))  
- MoML metamodel ([ecore](./Validation/1_Model_Transformations/EcoreMM_moml.zip))

_Diagram: MoML metamodel_

![image](https://github.com/jrromero/swel/assets/16683876/f208f950-bcee-4719-8730-0801213ffd7a)

- SCUFL metamodel ([ecore](./Validation/1_Model_Transformations/EcoreMM_scufl.zip))

_Diagram: Main elements of SCUFL_

![image](https://github.com/jrromero/swel/assets/16683876/6a2dfc60-be85-4789-9645-6276129ab1e9)

_Diagram: ConfigBeans-related elements_

![image](https://github.com/jrromero/swel/assets/16683876/c7827d2f-0e27-4265-88f3-dda147a45111)

#### Text-to-model Transformations:

- SCUFL T2M transformations ([XSL](./Validation/1_Model_Transformations/XSL_scufl.zip))
- CWL T2M transformations ([XSL](./Validation/1_Model_Transformations/XSL_cwl.zip))

#### Model-to-model Unidirectional Transformations:

- SCUFL to SWEL M2M transformations ([QVT](./Validation/1_Model_Transformations/QVT_M2M_scufl2swel.zip))
- SWEL to MoML M2M transformations ([QVT](./Validation/1_Model_Transformations/QVT_M2M_swel2moml.zip))

#### Model-to-model Bidirectional Transformations:

- CWL to SWEL (and vice versa) M2M transformations ([QVT](./Validation/1_Model_Transformations/QVT_M2M_cwl2swel.zip))

#### Model-to-Text Transformations:

- MoML M2T transformations ([MTL](./Validation/1_Model_Transformations/MTL_M2T_moml.zip))

### Demo Tool for Model Interoperability between WfMS

A demo tool has been developed to illustrate the complete transformation horseshoe process to enable interoperability between different WfMS. Currently, this tool supports both SCUFL and CWL workflows as input, in order to generate MoML workflows. During the transformation process, the output of each model transformation (text-to-model, model-to-model and model-to-text) is shown in the UI and stored in the local directory chosen by the user.

- Download demo tool ([Runnable JAR](./Validation/2_Model_Interoperability/demo-tool-jar.zip))
- How To Use it:
```
java -jar demo-tool.jar
```
- Source workflows ([SCUFL](./Validation/2_Model_Interoperability/example-SCUFL.zip), [CWL](./Validation/2_Model_Interoperability/example-CWL.zip))

#### Videos

1. Transforming a SCUFL workflow into a MoML workflow.


https://github.com/jrromero/swel/assets/16683876/2acb2db9-a4a7-4568-b524-6acffa02700c

2. Showing the intermediate models generated during transformation process and stored in a local directory.


https://github.com/jrromero/swel/assets/16683876/a482eb6e-4e56-4540-a9f0-5e7795aa21c1


3. Transforming a CWL workflow into a MoML workflow.


https://github.com/jrromero/swel/assets/16683876/d2ffe297-77c0-4283-a05f-30f13283de15


4. Opening the resulting MoML workflow in Kepler WfMS.


https://github.com/jrromero/swel/assets/16683876/fad81f0a-71aa-4705-9656-ed103bfd888b



## Experimentation: Survey

We conducted a human-based survey evaluation to assess the adequacy of SWEL as an intermediate model in the interoperability process between the Taverna and Kepler tools. We also analyse the suitability and comprehensibility of SWEL as a representation language for DIWs. For this purpose, a team of 11 experts, not involved in the prior design, development, and evaluation of SWEL, was selected. 5 of the experts work in academia in diverse areas of data science, while 6 are data scientists in industry. Both senior and junior profiles have been considered in both cases. These external experts have extensive knowledge of DI applications and were, therefore, well-suited to provide additional insights.

The experiment consisted of three exercises: (1) a first training transformation on a given workflow; (2) a transformation of a workflow chosen by the expert and downloaded from a public repository; and (3) an analysis of the adequacy and the comprehensibility of SWEL as a representation model for DIWs, as well as its accuracy in incorporating the concepts of the source (Taverna) and target (Kepler) models. Each expert responded to a total of 18 questions, rated on a scale of 1 (lowest) to 10 (highest).

We provide the __validation package__ ([ZIP](./Validation/3_Survey_Experiment/Q&A_experiment.zip)) containing the Q&A of the experiment with the following file structure:
- Expert evaluation form (```Expert_Evaluation_Form.pdf```)
- Experiment results (```Experiment_results.pdf```)
- Training exercise (```exercise1```)
  - Source workflow (```source```)
    - Taverna file (```Example.t2flow```)
    - Workflow representation (```source.jpg```)
  - Target workflow (```target```)
    - Kepler file (```Example.xml```)
    - Workflow representation (```target.jpg```)
  - Taverna model (```model_source.xmi```)
  - SWEL model (```model_swel.xmi```)
  - Kepler model (```model_target.xmi```)
