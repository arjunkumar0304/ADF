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


