# Frequently Asked Questions

By Julius Technologies Inc (email: info@juliustech.co)

Julius is an auto-scaling, low-code and visual graph computing solution. It can builds and run sophisticated data and analytical pipelines as directed acyclic graphs (DAG) with very little coding. Readers are referred to [this blog](https://www.juliustech.co/blog/why-graph-computing-is-stellar) for the high level over view of the benefits of graph computing, and [this repo](https://github.com/JuliusTechCo/JuliusGraph) for tutorials(https://juliustechco.github.io/JuliusGraph) and instructions to sign up for free developer access.

This FAQ page answers some of the most common questions from our users and clients. They are organized by subjects if you want to jump to different areas.

### Graph Computing and RuleDSL

1. What are the benefits of graph computing and why we need computational DAG?  
Graph computing solves some of the most challenging problems in building complex data and analytical pipelines and systems. These challenges includes scalability, transparency, explainability, lineage, adaptability and reproducibility. These benefits comes from the fact that a computational DAG is an ideal representation to solve these problems.  Graph computing allows a small development team to build sophisticated, scalable and transparent systems with much less code. Please refer to [this blog](https://www.juliustech.co/blog/why-graph-computing-is-stellar) for more detailed explaination.

1. What are the `Atom` and RuleDSL in Julius?

    `Atom` and `RuleDSL` are the two fundamental constructs Julius uses to create and execute computational DAGs.

    `Atom` stands for atomic operation, it is the function being called at individual node in Julius' computational graph. Atom is the minimal unit of distribution and caching in Julius' computational DAG, it cannot broken apart further. 'Atom' is a generic base interface that can be inherited using any major programming languages, such as C++, Pyton, Java, Julia, .Net and R etc. Existing libraries written in these languages can be easily wrapped up under the `Atom` interface.

    'RuleDSL' is a high level declarative domain specific language (DSL) for creating computational DAGs. RuleDSL features an easy to use and low-code syntax that can connect individual `Atoms` (as nodes in the graph) to create the entire computational DAG.

    Please refer to Julius tutorials(https://juliustechco.github.io/JuliusGraph) for more detailed explaination and examples of using Atom and RuleDSL.

1. How does Julius Graph Engine access data?  
Julius Graph Engine creates application or systems in two stages:  
    * Build the data and analytical pipeline as a computational DAG (directed acyclic graph) from `RuleDSL` 
    * Run the pipeline to process data and produce the results, this step can run either in batch or streaming mode.    
 
  Both stages can access data. The data in step 1 is fed through binding data to the rule parameters in `RuleDSL`. The data in stage 2 are fed through individual `Atom`s, which can read data from any source, such as database, web URL, static files etc.
  
The key advantage of two stage data feeds is that the first stage usually require a very small amount of data for constructing the pipeline as a DAG. Once the pipeline is built, it can be distributed to multiple workers, so that the heavy lifting of data processing in stage 2 can be done in parallel, thus achieving much better performance in both graph creation and execution. A developer has full control over which types of data are fed at each stage through the `RuleDSL`. 

1. How does RuleDSL differ from ordinary programming languages such as Python/C++/Java? 

    The general purpose programming languages like Python, C/C++ and Java are low-level and imperative in that the developer has to specify the program's entire execution step by step, that requires a lot of coding! In comparison, the RuleDSL is a high level and declarative domain specific language (DSL) for constructing computational DAGs. In RuleDSL, a developer doesn't need to explicitly specify every step of a program's execution, instead he/she only need to declare the key business concepts and their dependencies. The Graph Engine then automatically create a runnable program in the form of a computational DAG from the RuleDSL. 
    
    Therefore, it requires much less code in RuleDSL to specify the same business logic compared to the traditional programming languages, as most of the boilerplate flow control code in the traditional programming languages are automatically generated by the Graph Engine. The RuleDSL doesn't have any of the complex flow control syntax in the traditional programming languages, such as variables, loops, functions, classes, or branches etc. It is much easier for non-programmers to learn use. Furthermore, its declarative syntax gives the Julius Graph Engine a lot more freedom to optimize the execution, especially the parallel distribution over multiple machines, resulting in great scalability and performance.

### Integration

1. What programming languages can I use with Julius Graph Engine?

    Atoms can be written in any major general-purpose programming language such as C/C++, Python, Java, .Net, R and Julia etc. The Julius Graph Engine also provides easy-to-use APIs that can be called from any programming languages. Existing data and analytical libraries written in these programming languages can be wrapped up as `Atoms` and used by Julius.

1. How to convert my Python/C++/Java/.Net/R/Julia/SQL applications to Julius, and get the benefits of Graph?
   
  The great news is that your existing data and analytical libraries built in these languages can be re-used. You don't have to abandon your battle tested production libraries and restart from scratch! The migration to Julius involves two easy steps:
    * wrap the existing data and analytical classes and functions using the Julius' `Atom` base class. Julius offers generic wrappers that works out of box for modern programming languages that support reflection, such as Python, Java, .Net and Julia etc. These generic reflection based Atom wrapper works automatically for any classes and functions written in these languages. For older languages that do not support reflection, such as C/C++, additional manual effort is required to write these wrappers for individual functions and classes, however this additional work is largely machanical and can be done rather quickly. 
    * declare the entire data and analytical pipeline using Julius RuleDSL, which can reference and use the existing libaries via the `Atom` wrappers. This step only require minimal efforts and a small amount of coding, thanks to the low-code nature of RuleDSL. A complex data and analytical pipeline with hundreds or thousands of nodes can be built with a few dozen lines of rules in RuleDSL, as shown in Julius' [tutorials](https://juliustechco.github.io/JuliusGraph).
  
   The conversion only require minimal efforts if the existing system is built in a modern language like Python, Java, .Net, R, Julia etc.  Our experience shows that a complex real world system can be fully converted in a few weeks, with some help from those who are knowledgeable about the business logic of the existing system. For C/C++ applications and systems, it would require more time and efforts for writing and testing the wrappers manually.

1. How to integrate Julius Graph Engine with an existing system or application?

   Existing systems and applications can easily access Julius' Graph Engine using Julius' easy-to-use APIs. Julius supports a low level API for Julia, C/C++ and Python clients, as well as a high level Rest API that can be called from any programming languages. The low-level API is faster and more performant, which is recommended for high performance system. The high-level API is easier to use and integrate, which is recommended for general usage.
   
1. What database and data sources Julius supports?

   Julius comes with a rich set of data connectors out of box, including relational databases, NoSQL databases (Hadoop/Spark etc), data files, web data sources etc. If you need additional data connections that Julius does not yet support, you can write your own connector as an Atom using Python, C++, Java or any other major programming language.
   
1. Can I use data visualization tools such Tableau and Qlik with Julius?

   Absolutely. Results from Julius graph can be fed into Tableau and Qlik for visualization and reporting.


### Features and Use Cases

1. Can the Julius Graph Engine support streaming and live use cases?

    Absolutely, the same computation DAG can run in either batch or streaming mode, without much code change. Please see the tutorials(https://juliustechco.github.io/JuliusGraph) for examples of streaming use cases.

1. What are the best use cases for graph computing and Julius Graph Engine? 

    The Julius Graph Engine is well suited for any data and analytics use case. However, Julius adds more value to enterprise systems with complex data and analytical pipelines, which often suffer from poor transparency, lineage, scalability and visibility. 
    
1. Can I use Julius for building machine learning applications and systems?

    Absolutely, actually machine learning is a great use case for Julius. Julius' computatoinal DAG offers tremendous transpraency, explanability and auditability for ML applications. It aslo offers automatic and complete persisting and recovery of past ML experiments. Please see our tutorials(https://juliustechco.github.io/JuliusGraph) for more details of ML use cases. 

### Installation
1. How to install Julius?

  Julius installation is super easy as Julius ships as a single docker image. A client can simply install this image on multiple computers in his computing environment, which can be either on public cloud or private on-premise cluster. Julius only require minimal configurations after installation, most of the orchistration and configuration are handled automatically by the Julius docker container.
  
1. What operating system does Julius Graph Engine support?

    The Rule /Engine supports both Linux and Windows operating systems.

1. What hardware environment can the Julius Graph Engine be deployed to?

    The Julius Graph Engine can be deployed to any cloud computer provider, or privae on-premise clusters in an organization.

1. How can a client protect its intellectual property when running the Julius Graph Engine in the cloud?

    The Julius Graph Engine can be integrated to clients' internal authentication process, so that only authorized personnel have access. Julius can be deployed in a single tenant environment on cloud, providing additional support. 

### Comparables
1. The Julius Graph Engine seems to be too good to be true, why hasn't anyone else done this before?

    The answer is twofold: the first is that there are a myriad of technological hurdles to overcome in designing/implementing such a generic graph computing solution; secondly the solution leverages new technologies that have only become widely available in recent years, such as the maturity of cloud computing.

1. What is the main difference between the Julius Graph Engine from a collaborative development solution like Beacon?

    Platform like Beacon offer an integrated and collaborative development/deployment environment so that firms can be more efficient in managing a complex code base. In contrast, the Julius Graph Engine attacks the root of the problem by dramatically reducing the amount of coding and efforts in building complex systems, by taking advantage of the graph computinga and low code RuleDSL.

1. How does Julius Graph Engine's RuleDSL and computation DAG differ from Excel's worksheet formula and its dependency graph?

    The RuleDSL is much more generic and expressive than Excel's worksheet formulae. The Rules support both type and value based polymorphism, while Excel formulas are hard coded for a given cell or range. As a result, Julius RuleDSL is a lot more expressive than Excel workbook formulae. An Excel workbook often has thousands of formulae created by copy/paste functions, which is error prone and is difficult to audit and validate. In comparison, similar logic can be implemented succinctly by a few rules in RuleDSL thanks to its expressivity and polymorphism.

    In addition, the Julius Graph Engine RuleDSL is much more performant and scalable than Excel, it can handle large volumen of data and computation by running in parallel on many computers. 

1. How does Julius Graph Engine differ from other software packages that also use DAGs, such as Dask, Tensorflow and Dagger.jl?

    Julius RuleDSL is specifically designed for efficient creation and execution of computational DAGs. It offers much better performance and scalability, as shown in this [benchmark](https://juliustechco.github.io/JuliusGraph/dev/pages/t007_benchmark.html). At the same time RuleDSL is also low-code, it takes much less code to achieve the same functionality from other tools.