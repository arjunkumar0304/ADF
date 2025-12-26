# ADF


## 1. Key Features and Services

### 1.1 Global Data Centers

Azure operates data centers across multiple countries and regions. These data centers ensure high availability, low latency, data security, and disaster recovery. Regions may also contain Availability Zones to protect applications from failures.   

---

### 1.2 Azure Subscription and Resource Groups

**Azure Subscription** is required to access Azure services. It helps manage billing, usage, and permissions.

**Resource Group** is a logical container that holds related Azure resources such as virtual machines, storage accounts, and databases.

#### 1.2.1 Creating Azure Subscription

Steps:

1. Sign in to the Azure Portal
2. Navigate to **Subscriptions**
3. Click **Add**
4. Select subscription type and complete setup

#### 1.2.2 Managing Resources in Resource Groups

* Organizes related resources together
* Allows easy deployment, monitoring, and deletion
* Resources can share the same lifecycle

---

## 1.3 Azure Workspace and UI

### 1.3.1 Navigating the Azure Portal

The Azure Portal is a web-based interface used to create, configure, and manage Azure resources. It provides access to all services, resource groups, and settings.

---

### 1.3.2 Dashboard and Resource Management

The dashboard provides a customizable view of resources. Users can pin services, monitor performance metrics, and track alerts for better resource management.

---

### 1.3.3 Azure CLI and PowerShell

Azure offers command-line tools for managing resources efficiently:

* **Azure CLI**: Cross-platform tool with simple commands
* **Azure PowerShell**: Script-based tool using PowerShell cmdlets



| **Command**               | **Purpose (Why we use it)**               |
| ------------------------- | ----------------------------------------- |
| `az login`                | Sign in to Azure account                  |
| `az account list`         | View all Azure subscriptions              |
| `az account set`          | Select the active subscription            |
| `az group create`         | Create a resource group                   |
| `az group list`           | List all resource groups                  |
| `az group delete`         | Delete a resource group and its resources |
| `az vm list`              | View all virtual machines                 |
| `az vm start`             | Start a virtual machine                   |
| `az vm stop`              | Stop a virtual machine to save cost       |
| `az storage account list` | View storage accounts                     |
| `az help`                 | Get help for Azure CLI commands           |
| `az version`              | Check Azure CLI version                   |

---

### 1.3.4 Command-Line Interface Options for Azure

* Azure CLI
* Azure PowerShell
* Azure Cloud Shell (runs in browser)

These tools help automate tasks and manage resources faster than the portal.

---

### 1.3.5 Scripting with PowerShell

PowerShell allows automation of Azure operations such as creating resources, configuring services, and managing access using reusable scripts.






## 1.4 Azure Storage Account (Types)

An **Azure Storage Account** is a container that holds different types of storage services. It provides **secure, scalable, and highly available cloud storage**.

### Why Azure Storage?

* Store data in the cloud
* Highly scalable and cost‑effective
* Secure with access control and encryption
* Used by almost all Azure services

---

### 1.4.1 Blob Storage

**What it is:**
Blob Storage is used to store **unstructured data**.

**Examples of unstructured data:**

* Images
* Videos
* PDFs
* Text files
* Backup files

**Real‑time use case:**

* Store website images
* Store large CSV files for analytics
* Data lake for big data processing

**Why use Blob Storage?**

* Very cheap for large data
* Supports big data and analytics tools (ADF, Synapse)

---

### 1.4.2 File Storage

**What it is:**
File Storage provides **cloud file shares**, similar to a local file system.

**Real‑time use case:**

* Share files between multiple virtual machines
* Lift‑and‑shift on‑premise file servers to Azure

**Why use File Storage?**

* Supports SMB protocol
* Easy migration from traditional file servers

---

### 1.4.3 Table Storage

**What it is:**
Table Storage is a **NoSQL key‑value storage** for structured data.

**Real‑time use case:**

* Store user profiles
* Store application configuration data
* Store logs or metadata

**Why use Table Storage?**

* Fast access
* Schema‑less design
* Cost‑effective for large datasets

---

### 1.4.4 Queue Storage

**What it is:**
Queue Storage is used for **message storage** between applications.

**Real‑time use case:**

* Order processing systems
* Background job processing
* Decoupling applications

**Why use Queue Storage?**

* Improves application reliability
* Supports asynchronous communication

---

## 1.5 Azure Data Factory (ADF)

### Introduction to ADF

Azure Data Factory is a **cloud‑based ETL/ELT service** used to **move and transform data**.

**ADF is mainly used for:**

* Data ingestion
* Data integration
* Data orchestration


> Azure Data Factory is a cloud ETL service used to extract data from different sources, transform it, and load it into a destination.

---

### Key Components of ADF

#### 1. Pipelines

**What it is:**
A pipeline is a **logical container** that groups multiple activities.

**Example:**

* Copy data from Blob Storage to Azure SQL Database

---

#### 2. Activities

**What it is:**
Activities define **what action to perform**.

**Examples:**

* Copy activity
* Data flow activity
* Lookup activity

---

#### 3. Datasets

**What it is:**
Datasets represent the **data structure** inside a data store.

**Example:**

* A CSV file in Blob Storage
* A table in Azure SQL Database

---

#### 4. Linked Services

**What it is:**
Linked Services are **connection strings** to external resources.

**Example:**

* Connection to Blob Storage
* Connection to SQL Database

---

## 1.6 Azure Key Vault

Azure Key Vault is a service used to **securely store and manage sensitive information**.

### 1.6.1 Securely Store and Manage Sensitive Information

**What can be stored?**

* Secrets (passwords, connection strings)
* Keys (encryption keys)
* Certificates (SSL/TLS)

**Why use Azure Key Vault?**

* Improves security
* Prevents hard‑coding passwords
* Centralized secret management

**Real‑time use case:**

* Store database passwords
* Store API keys
* Secure access for ADF, VMs, and applications


| Service            | Purpose                   |
| ------------------ | ------------------------- |
| Blob Storage       | Store unstructured data   |
| File Storage       | Cloud file shares         |
| Table Storage      | NoSQL structured data     |
| Queue Storage      | Message handling          |
| Azure Data Factory | Data integration and ETL  |
| Azure Key Vault    | Secure secrets management |


# 1.7 Integration with Azure Services (ADF)

## 1.7.1 Dataset and Linked Service

### Linked Service

A **Linked Service** defines the connection information to external resources such as databases, storage accounts, or web services.

* Stores authentication details and connection strings
* Acts like a **connection configuration**
* Used by datasets and activities

**Examples:**

* Azure Blob Storage linked service
* Azure SQL Database linked service
* Azure Data Lake linked service

---

### Dataset

A **Dataset** represents the data structure within a linked service.

* Points to specific data (table, file, folder, container)
* Describes data format (CSV, JSON, Parquet, table, etc.)
* Used as **input (source)** or **output (sink)** in activities

**Examples:**

* CSV file inside a Blob container
* Table inside Azure SQL Database

**Relationship:**

* Linked Service → where the data is
* Dataset → what the data is

---

## 1.7.2 Integration Runtimes (IR)

An **Integration Runtime (IR)** is the compute infrastructure used by ADF to move and process data.

### Types of Integration Runtimes

1. **Azure Integration Runtime**

   * Used for cloud-to-cloud data movement
   * Fully managed by Azure

2. **Self-hosted Integration Runtime**

   * Used for on-premises or private network data sources
   * Installed on local machines or VMs

3. **Azure-SSIS Integration Runtime**

   * Used to run SSIS packages in Azure

**Purpose of IR:**

* Data movement
* Data transformation
* Activity execution

---

## 1.7.3 Triggers and Monitoring

### Triggers

Triggers define **when a pipeline runs**.

Types of triggers:

* **Schedule Trigger** – runs at a specific time or interval
* **Tumbling Window Trigger** – runs in fixed time windows
* **Event-based Trigger** – runs based on events (e.g., file arrival)

---

### Monitoring

ADF provides built-in monitoring to track pipeline executions.

Monitoring features:

* Pipeline run status (Success, Failed, In Progress)
* Activity-level details
* Error messages and execution time
* Trigger history

---

# 1.8 Activities in Azure Data Factory

Activities are the **building blocks of pipelines**. Each activity performs a specific task.

---

## 1.8.1 Data Movement Activity

Data movement activities are used to **copy data** from a source to a destination.

### Copy Activity

* Reads data from a source dataset
* Writes data to a sink dataset
* Supports multiple data formats and stores

---

### 1.8.1.1 Azure Blob Storage Source / Sink

**Azure Blob Storage as Source:**

* Reads files such as CSV, JSON, Parquet
* Used for ingestion scenarios

**Azure Blob Storage as Sink:**

* Stores processed or copied data
* Commonly used for staging and archival

---

### 1.8.1.2 Azure SQL Database Source / Sink

**Azure SQL Database as Source:**

* Reads structured data from tables or queries

**Azure SQL Database as Sink:**

* Writes data into tables
* Supports insert, upsert, and stored procedures

---

## 1.8.2 Execution Control Activities

Execution control activities manage **pipeline flow and logic**.

---

### 1.8.2.1 Execute Pipeline Activity

* Calls another pipeline from the current pipeline
* Enables pipeline reuse and modular design
* Passes parameters between pipelines

---

### 1.8.2.2 If Condition Activity

* Executes activities based on a condition
* Supports **true** and **false** paths
* Uses expressions for decision-making

---

### 1.8.2.3 ForEach Activity

* Repeats activities for each item in a collection
* Supports sequential and parallel execution
* Commonly used for file or table iteration

---

### 1.8.2.4 Web Activity

* Calls REST APIs or web endpoints
* Supports GET, POST, PUT methods
* Used for external system integration and automation

---



## 1.8.3 Control Flow Activities

Control Flow Activities **control how a pipeline runs** (order, conditions, looping, waiting, checks). They do not move data themselves.

### 1.8.3.1 Wait Activity

**Purpose:** Pause pipeline execution for a fixed time.

**Key Points:**

* Time is given in **seconds**
* Used to delay next activity

**Practical Scenario:**

* Wait 10 minutes before checking if a file arrives

**Example:**

* Wait = 600 seconds → then run Copy Activity

---

### 1.8.3.2 Until Activity

**Purpose:** Repeat activities **until a condition becomes true**.

**Key Points:**

* Works like a loop
* Stops when condition = TRUE

**Practical Scenario:**

* Keep checking a folder until a file is available

**Example Condition:**

```
@equals(activity('Get Metadata').output.exists, true)
```

---

### 1.8.3.3 Get Metadata Activity

**Purpose:** Get information about a file or folder.

**What it can return:**

* exists
* size
* lastModified
* childItems

**Practical Scenario:**

* Check whether a file exists before copying it

**Common Use:**

* Used with **If Condition** or **Until** activity

---

### 1.8.3.4 Lookup Activity

**Purpose:** Read data from a database or file (small data).

**Key Points:**

* Returns rows (JSON output)
* Used for parameters, conditions, validation

**Practical Scenario:**

* Get control table values
* Get list of tables to load

**Example Use:**

* Lookup → ForEach → Copy data

---

### 1.8.3.5 Stored Procedure Activity

**Purpose:** Execute a stored procedure in a database.

**Key Points:**

* Works with Azure SQL / SQL Server
* Can pass input & output parameters

**Practical Scenario:**

* Update audit table after load
* Perform data validation

**Example:**

* Execute `sp_Update_Load_Status`

---

## 1.8.4 Pipelines and Triggers

### Pipelines

**Definition:**
A pipeline is a **group of activities** that performs a task.

**Example:**

* Get Metadata → If Condition → Copy Data → Stored Procedure

---

### Triggers

**Purpose:** Decide **when** a pipeline runs.

**Types of Triggers:**

1. **Schedule Trigger** – Run at fixed time (daily, hourly)
2. **Tumbling Window Trigger** – Time‑based batches
3. **Event Trigger** – Run when file arrives

**Practical Scenario:**

* Run pipeline every day at 2 AM
* Trigger pipeline when a file is uploaded

---


---

## Summary Table

| Activity         | Use Case                  |
| ---------------- | ------------------------- |
| Wait             | Pause execution           |
| Until            | Loop until condition true |
| Get Metadata     | Check file/folder info    |
| Lookup           | Read small reference data |
| Stored Procedure | Run DB logic              |

---



## 1. Azure Databricks Notebooks


### 1.1 Notebook Integration Overview

Azure Databricks integrates with key Azure services:

* **Azure Data Factory (ADF)** – orchestration
* **Azure Blob Storage / ADLS Gen2** – data storage
* **Azure DevOps / GitHub** – version control and CI/CD

**Basic Flow:**
Storage → Databricks Notebook → Processed Data → ADF / Jobs

---

### 1.2 Notebook Orchestration

Notebook orchestration means controlling the order and execution of notebooks using **ADF Databricks Notebook Activity** or **Databricks Jobs**.

**Example:**

* Notebook 1: Data ingestion
* Notebook 2: Data cleaning
* Notebook 3: Data transformation

ADF ensures sequential execution and monitoring.

---

## 2. Azure DevOps – CI/CD Integration

Azure DevOps is used to automate notebook development and deployment.

### 2.1 Continuous Integration and Development

**CI/CD Flow:**

1. Notebooks are stored in **Azure Repos (Git)**
2. Code changes are committed and validated
3. Pipelines deploy notebooks to Databricks workspace

**Benefits:**

* Faster deployment
* Reduced manual errors
* Better team collaboration
==========================================================================================================================================================


“I created an Azure Data Factory pipeline with a Databricks Notebook activity.
I configured an Azure Databricks linked service using an access token and existing interactive cluster.
The pipeline successfully triggered the Databricks notebook and executed Python code.
I monitored the execution in ADF and validated the success in Databrick



<img width="1899" height="1068" alt="Screenshot 2025-12-23 171459" src="https://github.com/user-attachments/assets/37e0de16-7cd6-4aa1-a1a7-66da46c6301f" />



<img width="1884" height="1077" alt="Screenshot 2025-12-23 173013" src="https://github.com/user-attachments/assets/790bb171-d373-448c-b101-0aaffab0dbf7" />




<img width="1883" height="1031" alt="Screenshot 2025-12-23 172009" src="https://github.com/user-attachments/assets/da2e6629-ea10-4d87-b74a-9e1187c6b71f" />



## 1. Copy Data from ADLS (Using Azure Data Factory)

### Objective

Copy files from **ADLS Gen2** to a target location (another ADLS folder / Blob / SQL DB).

### Steps

1. Create **Azure Data Factory**
2. Open **ADF Studio → Author**
3. Create **Linked Service** for ADLS Gen2
4. Create **Dataset** pointing to source ADLS path
5. Create target **Dataset** (sink)
6. Create a **Pipeline**
7. Drag **Copy Data Activity**
8. Select source dataset and sink dataset
9. Validate → Debug → Publish


### Use Case

Used when moving raw data from landing zone to processed zone.

---

## 2. Copy Different File Formats from ADLS Gen2

### Supported File Formats

* CSV
* JSON
* Parquet
* Avro
* TXT

### Objective

Copy multiple file formats from ADLS using a **single pipeline**.

### Steps

1. Create datasets for each file format
2. Use **Parameterization** in dataset (file name / folder path)
3. Use **ForEach Activity** in pipeline
4. Inside ForEach, use **Copy Data Activity**
5. Pass file format and path dynamically
6. Validate and Debug pipeline

### Output

* Multiple file formats copied successfully

### Use Case

Useful when a data lake contains mixed data formats from different sources.

---

## 3. Creating Pipelines and Jobs in Azure Databricks

### Objective

Process data using Databricks notebooks and automate execution using jobs.

### 3.1 Create Databricks Notebook

1. Open **Azure Databricks Workspace**
2. Create **Notebook** (Python / SQL)
3. Read data from ADLS using DBFS or ABFS path
4. Perform transformations
5. Save output back to ADLS

### 3.2 Create Databricks Job

1. Go to **Workflows → Jobs**
2. Click **Create Job**
3. Select notebook
4. Attach cluster (existing or new)
5. Configure parameters (optional)
6. Run job

### 3.3 Orchestrate Databricks from ADF

1. Open ADF Pipeline
2. Drag **Databricks Notebook Activity**
3. Connect Databricks Linked Service
4. Select notebook path
5. Debug and trigger pipeline

### Output

* Databricks notebook executed successfully
* Transformed data stored in ADLS

### Use Case

Used for large‑scale data processing and transformations.

---

