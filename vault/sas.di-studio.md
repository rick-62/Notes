---
id: ffdqeTkAWCsk8kombKmrr
title: DI Studio
desc: ''
updated: 1644423904103
created: 1644226413431
---

# Introduction

- DI Studio is still a SAS 9 platform
- Possible SAS vIYA version of DI Studio

## SAS Platform Architecture

- **Clients:** SAS EG and VIYA
- **Middle tier:** all web accessed tools and services
- **SAS Servers:** SAS session running in the background
- **Data Sources:** Any data, in any format

Make use of meta data server and workspace server to run some of the DI Studio jobs. Preparing the data for the analysts.

## Metadata
- All about the metadata
- Must be registered as a piece of data or job or process etc
- types of Metadata:
    - tables
    - jobs
    - libraries (to access tables)
    - users
    - etc...
- All stored in SAS folders, which we can create to store metadata
- Can create _SAS package_ to store metadata objects

## Core primary tasks
1. Define metadata for source data (register required source tables)
2. Define metadata for target tables (input)
3. Define jobs (build jobs using input tables)

## Course Star Schema
![](/assets/images/2022-02-07-10-25-59.png)

## Change management
- All using the same folder so working in same folders at the same time
- Possibility of overwriting changes by others
- change management comes in here
- allows us to lock metadata, by checking out any metadata
- Use checkouts tab represents own personal repo
- To load stuff into checkout folder, drag and drop metadata into `Checkouts`
- Tick mark will appear next to metadata
- Check back in once changes made
- Note: Not version control
- Ensure metadata is checked back in once complete, or cleared

# Creating metadata for source data
Note: the process is very similar for varying data sources e.g. Oracle, CAS, Hadoop, Flat files etc

1. Create new folder, specifically for the project source data (good practise)
2. Right click folder and create `New` > `library...`
3. Right click folder and click `Register Tables...`
4. Repeat accordingly

![Example: source data](/assets/images/2022-02-07-13-44-49.png)

*Example: Source Data*


# Creating metadata for target data
1. Create new folder, specifically for the project target data (good practise)
2. Right click folder and create `New` > `Table...`
3. Can define library within the `New Table` wizard
4. Columns can be defined manually or from existing data
5. At this stage indices can also be defined
4. Repeat accordingly

![Example: target data](/assets/images/2022-02-07-15-35-42.png)

*Example: Target Data*


## Importing metadata
Industry standard is **Common Warehouse Metamodel format (CWM)**, whereas SAS package is SAS specific internal storage solution for metadata.

1. Right click folder and select `Import` > `Metadata...`
2. Select appropriate CWM (usually XML file)
3. Change data definitions as appropriate, ensuring names, formats etc are correct


# Creating metadata for jobs

![Example Process Flow](/assets/images/2022-02-07-16-04-22.png)

*Example Process Flow*

1. Create new folder, specifically for the job metadata (good practise)
2. Right click folder and create `New` > `Job...`
3. Create a job flow accordingly, dragging in source/target data and transformations
4. Test by running & click save

- Other jobs can be dragged into a new job to create a process flow
- Can use `Control Flow` tab to prioritise order of jobs

## Intermediate tables
- Rename `Physical name` using the `Physical Storage` tab
- Ensure intermediate tables are data views if only used once (memory saving)

### Transformation: Splitter
Splits a table according to `Selection Conditions` in `Row Selection` tab

### Transformation: File Reader
For reading in flat files based on metadata

### Transformation: Table Loader
For column selection and how to feed data into target data e.g. insert, append or replace

### Transformation: Join
- Supports SQL pass-through
- Allows for fine tuning the individual clauses of the SQL query
- For **inner join** only must use where clause to indicate where columns match
- Must ensure all data is mapped on the `Select` clause
- Computed columns can be defined in the `Select` clause

### Transformation: Extract
For applying filters, grouping or/and sorting

### Transformation: Summary Statistics
For applying tailored summary statistics such as averages and percentiles etc, to be output as a report or as data

### Transformation: Data Validation
- Used to identify invalid, missing or duplicate values
- Has ability to `Move row to error table`, `Change value to` or `Abort job`
- Outputs a table of valid rows, invalid rows and an exceptions report


# Additional features of jobs

## Propagation & Mapping
- Copying and pasting of Metadata definitions
- Automatic propagation only occurs for temporary tables (can be switched off)

!Propagation Tools](/assets/images/2022-02-08-14-12-16.png)

*Propagation Tools*

- Numeric/character conversions will occur automatically
- Automatic mapping will occur if length is not less
- Automatic & manual propagation can be defined at transformations/global/job level
- Can use `PROC Metalib` to update Metadata to match source data

## Status
- Dependent on status of job, can output message or add log to data
- Can be found in properties of transformations and jobs
- Messages are so far impenetrable to code injection

## Importing SAS code
SAS code wizard:
- Executes the programs
- Analyses the results
- Saves analysis to a file

Do the following:
1. Right click folder where want to import SAS code
2. Click `Import...` > `Import SAS Code`
3. Follow wizard and select SAS9 code

Recommended to test first in DI Studio, using `Tools` > `Code Editor`, then `File` > `Open` > `SAS Code`.

## Outputting to CAS/VIYA
1. Create library to connect to existing CAS library & database
2. Use `Cloud Analytics Services Transfer` transformation in a job
3. Specify the CAS library to output data to

## Impact Analysis
- Can right click `Analyze` to review dependencies
- Reveal where a metadata object is dependent on other metadata objects
- Reveal where an metadata object is depended upon by other metadata objects

# The Scheduling Process
Requirements Scheduling Manager to schedule jobs and scheduling server to create triggers.

(Similar to AWS Step functions or batching and Eventbridge for triggering)

In this case the `SAS application` is **DI Studio**.

![](/assets/images/2022-02-09-14-43-00.png)

*https://documentation.sas.com/doc/en/bicdc/9.4/scheduleug/n1f7xolpdktgjkn18aiem5lchkxl.htm*

## Steps

Right click the job to schedule and click `Scheduling` > `Deploy...`

![](/assets/images/2022-02-09-14-48-22.png)


Once complete a new job will appear in the specified folder, with scheduled job icon

![](/assets/images/2022-02-09-14-49-25.png)


This can be done in batch by highlighting multiple jobs at once

![](/assets/images/2022-02-09-14-51-16.png)


Navigate to SAS Management Console

![](/assets/images/2022-02-09-14-53-34.png)


Right click`Schedule Manager` > `New Flow...`

![](/assets/images/2022-02-09-14-55-16.png)


Add OR/AND gates to define dependencies of jobs

![](/assets/images/2022-02-09-14-56-09.png)

![](/assets/images/2022-02-09-14-58-32.png)

Once complete right click schedule job and click `Schedule Flow...`

![](/assets/images/2022-02-09-15-00-42.png)

![](/assets/images/2022-02-09-15-01-18.png)


Finally navigate to scheduling server to schedule (e.g. IBM Flow Manager)

![](/assets/images/2022-02-09-15-03-10.png)





















