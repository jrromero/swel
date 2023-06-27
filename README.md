# SWEL - A Domain-Specific Language for Modelling Data-Intensive Workflows
_This page contains additional material to the paper entitled “SWEL: A Domain-Specific Language for Modelling Data-Intensive Workflows”, accepted in BISE journal (2023)_

## SWEL Technical Report

This [technical report](2023-01_SWEL_Technical_Report.pdf) defines the formal specification of SWEL (Scientific Workflow Execution Language) in terms of its meta-models and constraints, making this definition syntax-independent, according to the precepts of model-driven engineering. SWEL is a domain-specific modelling workflow language for defining data-intensive applications, which use advanced computing techniques with the aim of discovering valuable knowledge from huge amounts of data coming from real-world sources. The objective of SWEL is to provide a high-level, domain-independent definition language for the formulation of scientific workflows, hiding low-level computational aspects. SWEL is founded on a multi-layered structure that enables both the definition of workflows for different domains, the reuse of knowledge and the portability and interoperability among different workflow platforms.

## Tool Support

### JSON Concrete Syntax Validator

JSON is an IETF ([Internet Engineering Task Force](https://datatracker.ietf.org/doc/html/rfc8259)) standard language widely used as a data exchange format on the web via, e.g., REST APIs and services. JSON is also possible to use SWEL as a concrete textual notation for the serialisation of DIW models. To improve practicability, a syntactic validator is a useful tool to verify that the JSON document is well constructed and conforms to both the standard and the SWEL metamodel. To this end, a JSON schema has been generated in accordance with the declaration of the JSON-based concrete notation corresponding to the metamodel. The validation tool has been implemented in Java and it provides a command-line interface whose only argument is the path of the JSON file to be analysed. It reads and parses the input file in order to check if its content is according to the JSON scheme. If not compliant, the execution console reports the detected errors.

- Download JSON Validator (Runnable JAR)
- How to execute it:
```
java -jar validator.jar <path_to_workflow.json>
```
- Workflows: Example1, Example2, Example3 (with errors)

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

- Download (Windows, Linux, MacOS)

#### Videos

1. Executing a simple control-driven workflow composing by a Java process, a data input and a display, in order to perform an image transformation and visualize the result.


