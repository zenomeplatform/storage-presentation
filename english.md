## Zenome Storage System

### High-performance storage system for genomic data

* Works in both distributed systems and private networks
* Takes into account the specificity of big genomic data during their storage and processing
* Unlimited potential for customization through modularity
* The system components can be implemented in stages, as needed

Zenome Storage System is designed as a foundation for creating Genomics-IDE - an integrated environment for efficient work with genetic data.
For example, Zenome Storage System has the following features:

* Genomic data flow management and systematization
* Transparent use of containers for isolation of working environments
* Instant deployment of the desired runtime environment
* Access control system based on cryptographic evidence (optional)
* Support for standard containers for storing genetic data
* Data normalization: consideration of vendor-specific features of format subspecies

### Each data type needs a special approach

Working with genetic data includes operations with data of different types, which leads to significantly different requirements for both hardware and software that deals with data of a certain type.

1. Raw Sequence (fastq, uBAM): _data from DNA sequencing lab_

   * Starting point for primary analysis and reanalysis of data in the future
   * Significant data size (up to 500Gb)
   * Practically not used directly
   * Unable to recover when lost

    > **The priority in working with this type of data in the Zenome Storage System  --- is to ensure their safety.**  


2. Aligned sequence data (formats: SAM, BAM, CRAM)

   * Derived from raw data
   * Significant data size (up to 500Gb)
   * Can be used directly (e.g. visualizations of aligned reads)
   * Can be deleted and restored later if necessary

    > **Priority in dealing with this type of data in Zenome Storage System --- is to make them available if needed and minimize storage costs.**

3. Sequence variation data (formats: VCF, GVCF, TXT, etc)

    * Непосредственно характеризуют отличия в последовательности ДНК
    * Умеренный размер данных. Удаление для освобождения места не имеет смысла.
    * Используются для получения клинической интерпретации и еще много где.
    * Зачастую в задачах требуется лишь небольшая определенная часть данных.
    * Огромное количество несовместимых между собой разновидностей VCF.
    * Распространенная практика внесения в VCF данных из баз аннотаций усложняет обработку



### Zenome Storage System

Zenome Storage System представляет собой программно определеяемую систему хранения геномных данных. При разворачивании системы пользователь устанавливает управляющую программу на нескольких серверах, работающих под управлением Unix-совместимой операционной системы (рекомендуется использовать современные дистрибутивы Linux).

Затем с помощью специального скрипта формируется начальная конфигурация системы, в том числе и настраивается способ авторизации для администратора, число узлов, их сетевые адреса или имена. Система сгенерирует для каждого узла конфигурационный файл, а также приватный ключ для администратирования. Конфигурационные файлы применяются на соответствующих узлах при запуске управляющей программы, после чего (если есть сетевая доступность) сервера обнаруживают друг друга и формируют единый кластер.

После этого пользователь на каждом узле настраивает хранилище данных, указывая как и где узел может разместить данные. Каждый способ хранения представляет собой независимый модуль, который берет на себя реализацию взаимодействия с соответствующим бэкэндом. Поддержка локального хранения на сервере, а также популярных сетевых протоколов (FTP, SMB, iscsi и так далее) реализована в стандартных модулях, доступных по умолчанию. Кроме того существуют модули-адаптеры для интеграции популярных облачных сервисов как мест хранения данных.

После этого пользователю предлагается настроить политики хранения данных, настраивая либо с нуля (не рекомендуется для большинства пользователей), либо используя пресеты с популярными вариантами. Политики представляют собой декларативную конфигурацию для того, как будут распределяться данные в системе, какое должно использоваться число независимых дублирований данных, применяется ли шифрование, формируются группы для пользователей системы и настраиваются их права.

Затем создается ряд пользователей, которые получают возможность работать с системой одним из доступных способов: консольный клиент (Win/Linux/Mac), оконное приложение (Win/Linux/Mac) или же через Web interface (Win/Linux/Mac/Android/iOS/...). В простейшем случае авторизация пользователей происходит по паролю: при регистрации администратор рассылает одноразовые пароли для доступа, которые пользователь меняет на свой при первом входе.

### The incremental annotating

Zenome Storage System draws the line between sample-related data and data from annotation databases. By storing these two types of data separately we work around the common choice between constantly updating VCF and having to work with outdated annotations. After thoroughly researching the issue we propose the following solution, called **incremental annotating**. The very nature of it is applying annotation data on the fly while having a notion of **a virtual file with applied annotations**, which can be downloaded or used elsewhere in the system as a regular file.

Let's assume there are some samples and corresponding VCF files, which have to be annotated, for example, with information from the ClinVar database. Over time the new ClinVar releases are published and we used to rerun the annotating each time to get recent annotations and then check if there are important changes in the annotation. Zenome Storage System takes into account the exact semantic description of data to make the process incremental. It builds the difference between annotation databases of different versions and uses that information to infer the difference in annotations. Since the scope of such differences is limited, the process is very efficient. As a result, it becomes an easy task to determine if there is a substantial change in the annotation.

@import "figures/figure-virtual-annotations.md"

> In 2020 the following variant had been added to ClinVar database: `NM_003000.3(SDHB):c.332T>C (p.Leu111Pro)`. It had a `Likely pathogenic​` classification, making a huge difference to samples containing this variant. Zenome Storage System for each affected sample would efficiently update the corresponding virtual annotations, and would as well notify the user of the system or/and the owner of data of this significant change. The related message would appear on the sample's page in the desktop/web client and the warning also would appear on the main page. A console client simply warns that there are not yet reviewed changes in annotations and lists the sample ids. Optionally, the user may configure the additional means of notifications (such as notifying the doctor treating the patient).

To avoid being notified of insignificant changes, a user may specify which changes should be considered important. For instance, in the example above, this classification change from "pathogenicity is not determined" to "pathogenic" should be considered important, whereas the change from "likely benign" to "benign" is not that important. The system allows to simply specify important data fields to watch for changes. Also, there is experimental support of specifying an arbitrarily complex set of rules, which might be required in some special use cases.

### Accessing network content transparently (without necessarily storing it on hard drive)

On the modern versions of Linux and Mac (the support for Windows is being worked on), it's possible to work with files, located in the network, as if they are located locally on the disk of the user's computer. To make it happen, a user selects an empty folder using a console client application or a desktop client. Then the user selects files from the network to be shown inside that directory. Immediately after that, the files are emerged in that folder without consuming any disk space. The data is received from the network on-demand with a high level of granularity. It implies that only such parts of the file are transferred, which are being accessed. This is important when using genomic indexes to obtain a specific genomic interval.

Efficient accessing huge genetic databases is of particular interest. Zenome Storage System allows that too. While connected to the network (over LAN or the Internet) you may use databases as if they are stored locally on the computer. 

> For instance, Ensembl Variant Effect Predictor requires cache and resource files to do its work. The specific amount of data needed varies depending on the actual case and easily could be as high as a couple of terabytes (gnomAD v2.1.1 uses about 500 GB of disk space, while gnomAD v3.1.1 uses terabytes). Zenome Storage System enables using VEP with that databases without paying the costs of having them locally. While the data is only available when connected to the network, a temporary disconnect would not crash a running analysis. The analysis is simply paused until the connection is restored, and then continues as if there hasn't been any disconnect at all.

@import "figures/figure-vep-over-net.md"

### Managing information using metadata in Zenome Storage System

When new data is being added to the Zenome Storage System, the user is asked to provide additional metadata. Some metadata gets extracted from the data itself (for instance, from VCF header). Having rich metadata enables an enhanced capabilities of query processing. Also the grouping of entites in the system is based on metadata too.

> For example, all files and virtual files that refer to the same patient are grouped. So on every entity's page there is a list of related entities, referring to the same person.

@import "figures/figure-metadata.md"

> Metadata also includes information like the date or place of taking a DNA sample, the sequencer used, and so on. If there is a suspicion that the device is malfunctioning, producing incorrect genetic data, it's possible to quickly list all affected entities in the system and take the necessary actions.

### Making use of Zenome Storage System for controlled disclosure of genetic data

Zenome Storage System enables the data owners (mostly patients) to sign up and only partially disclosure their genetic data. _This requires special configuration. The following are some possible use cases._

> Genetic reports require some subset of the user's genetic data. So instead of uploading the whole data to the service provider, the user makes use of a special Zenome Storage System client. This piece of software may even be branded in the style of the service provider. Namely, the user registers the data in the system without even uploading it. After the user has chosen the desired report, the system asks him to allow access to the needed set of alleles. If the user agrees, this information is extracted from data and sent to the service provider. The user then gets its report based on the information provided.

> The data owner wants to take part in genetic research by providing access to the subset of its data. The user makes use of a special Zenome Storage System client (preconfigured by a research group) and registers his data in it. Optionally, the user completes a questionnaire. After that, the researchers are enabled to make a query that executes on the data owner's computer. Only the results of the computation are sent back to the research team. The user specifies a degree to which data are used when data is registered in the system.

### Virtually unlimited capabilities for customization

Zenome Storage System enables a flexible connection security policy that governs how new nodes enter the network. Both centralized systems and decentralized ones can be built using Zenome Storage System, depending on the policy used.

> The fully decentralized network enables the following use case of implementing a backup strategy. The nodes of said network store encrypted pieces of data and as such gain no access to it. When nodes are entering the network or leaving it, the system adjusts the number of replicas accordingly. For instance, the nodes may be just computers on the Internet, whose owners seek reward for providing their unutilized disk capacity.