# Data-Management-and-Governance
![Screenshot (32)](https://github.com/user-attachments/assets/ec5d5caf-68fd-4a1d-9742-0b2a285f40aa)
# 🧩 Data Mesh Architecture Overview

**Data Mesh** is a modern decentralized data architecture approach that treats data as a product, with domain teams owning and managing their own data, while a centralized platform ensures governance, interoperability, and security.

## 🌐 Key Principles of Data Mesh

- **Decentralized Data Ownership**  
  Each domain team owns and manages its data as a product. This decentralization allows teams to build, maintain, and scale their data pipelines independently.

- **Centralized Governance Layer**  
  While ownership is decentralized, governance (such as security, lineage, and compliance) is enforced centrally through standardized policies and tooling—ensuring consistency and trust.

- **Domain-Oriented Architecture**  
  Data is organized around business domains (e.g., Marketing, Sales, Finance), aligning ownership with subject-matter expertise and promoting accountability.

- **Self-Serve Infrastructure as a Platform**  
  A central platform team provides reusable, self-serve tools (e.g., ingestion templates, CI/CD pipelines, data quality checks) so domain teams can build and manage data products efficiently.

- **Data as a Product**  
  Each dataset is treated like a product with well-defined SLAs, quality metrics, and discoverability—enhancing usability and trust across the organization.

- **Interoperability and Standardization**  
  Common standards for schemas, APIs, and data contracts enable domains to share and consume data easily without tight coupling.

## ✅ Advantages

- Scalable across large enterprises
- Promotes data democratization and agility
- Reduces bottlenecks from centralized data teams
- Improves data discoverability and productization

<img width="950" alt="image" src="https://github.com/user-attachments/assets/fd566da7-0e3c-4b79-b046-fce8bc5ac358" />
# 🔷 Google Cloud Dataplex Overview

**Dataplex** is an intelligent data fabric designed to unify and streamline data management across diverse environments—making it easier to govern, catalog, secure, and analyze data at scale.

## 🚀 Key Features

### 🔗 Unified Data Management
Seamlessly manage data across multiple storage environments such as data lakes, data warehouses, and databases.

### ⏳ Automated Data Lifecycle Management
Automate retention policies, archiving, and cleanup tasks to keep your data environment optimized and compliant.

### 📊 Integrated Analytics
Analyze data directly within Dataplex using built-in tools and integrations with BigQuery and Spark.

### 🛡️ Built-in Governance & Quality Monitoring
Combines data cataloging, lineage tracking, policy enforcement, and quality checks—all in a single platform.

### ✅ Simplified Governance Across the Organization
Enables consistent, centralized governance over distributed data systems, helping teams build reliable and trusted data products.
<img width="950" alt="image" src="https://github.com/user-attachments/assets/398524da-ae10-41ce-bffd-7db7a500c6bc" />
<img width="950" alt="image" src="https://github.com/user-attachments/assets/c9116f04-e418-4694-8a89-5a09ed257e44" />
<img width="950" alt="image" src="https://github.com/user-attachments/assets/20ed2a0a-361b-46ba-9aba-86c47a23587d" />
## 🧱 Dataplex Components

### 🔹 Lake
A **Lake** in Dataplex is the highest-level organizational construct. It typically represents a broad data domain or business unit within your organization (e.g., `marketing-lake`, `finance-lake`, `customer-analytics-lake`).

- Used to **group data logically** across zones and assets.
- Helps you **organize and isolate data** for different departments or domains.
- Enables **domain-specific access controls** and governance policies.

> 💡 Example: You can create a separate lake for each department—like Marketing, Sales, or Finance—to ensure that each team manages and accesses its own data independently, while still adhering to centralized governance policies.
<img width="950" alt="image" src="https://github.com/user-attachments/assets/3999b913-2d14-4e44-b389-4221f8c9b0e7" />
### 🔸 Zone

A **Zone** in Dataplex is a subdomain within a lake that helps further categorize data based on its lifecycle stage, usage, or access restrictions.

There are two main types of zones:

- **Raw Zone**  
  - Stores data in its original/raw format (e.g., files in GCS).
  - Typically used for staging or archiving unprocessed data.
  - Not subject to strict type-checking or schema enforcement.

- **Curated Zone**  
  - Contains data that has been cleaned, standardized, and made analytics-ready.
  - Often used for structured tables in BigQuery or other analytics tools.
  - Ideal for downstream consumption, reporting, and ML workflows.

> 📌 Tip: Structuring your data into raw and curated zones enables a clear separation between ingest and consumption layers, improving traceability, governance, and data quality.
<img width="956" alt="image" src="https://github.com/user-attachments/assets/b8163fac-b784-40b2-9227-b66283a23412" />
### 📦 Asset

An **Asset** in Dataplex represents the actual storage layer—such as Cloud Storage buckets or BigQuery datasets—that holds your data.

Assets are always linked to a specific **zone** within a lake, and they inherit the governance and access policies defined at the zone and lake level.

#### ✅ Supported Asset Types:
- **Cloud Storage Buckets** – for files like CSV, Parquet, JSON, etc.
<img width="950" alt="image" src="https://github.com/user-attachments/assets/4ef9b234-2c3c-4f51-8071-8199436cda55" />
### 🗑️ Deleting a Lake in Dataplex

To delete a lake, you must follow the proper hierarchy. Dataplex enforces dependency rules, so you need to clean up in reverse order:

#### 🧹 Deletion Workflow:

1. **Detach Assets**  
   Begin by detaching any Cloud Storage or BigQuery assets from their respective zones.

2. **Delete Zones**  
   Once assets are detached, delete each zone within the lake (both raw and curated).

3. **Delete the Lake**  
   After all zones are removed, you can safely delete the lake itself.

> 🔐 **Note:** Make sure you have the required IAM permissions (like `dataplex.admin`) to perform these operations.
<img width="950" alt="image" src="https://github.com/user-attachments/assets/d29c30ad-faf4-45db-bae5-7d95b4187741" />
# 🧪 Dataplex: Qwik Start – Command Line Lab

This lab provides hands-on experience using **Google Cloud Dataplex** to manage and organize data through the **command-line interface**. It walks through the process of creating a lake, zone, attaching a BigQuery dataset, and cleaning up resources.

---

## 📋 Lab Objectives

- Enable the **Dataplex API**
- Create a **Dataplex Lake**
- Add a **Zone** to the Lake
- Attach and detach **Assets** (BigQuery datasets)
- Delete the Zone and Lake

---

## 🧱 Concepts Overview

### 🔹 Lake
- The **highest organizational unit** in Dataplex.
- Represents a **data domain**


# 🚀 Dataplex Lab: Create and Manage a Lake, Zone, and Asset on GCP

This guide demonstrates how to use **Dataplex** to create a data mesh architecture by managing lakes, zones, and assets using `gcloud` and `bq` commands.

---

## 🌍 Step 2: Set Environment Variables

```bash
export PROJECT_ID=$(gcloud config get-value project)
export REGION=us-central1
```

---

## 🏞️ Step 3: Create a Lake

```bash
gcloud dataplex lakes create ecommerce \
  --location=$REGION \
  --display-name="Ecommerce" \
  --description="Ecommerce Domain"
```

---

## 🧭 Step 4: Create a Curated Zone

```bash
gcloud dataplex zones create orders-curated-zone \
  --location=$REGION \
  --lake=ecommerce \
  --display-name="Orders Curated Zone" \
  --resource-location-type=SINGLE_REGION \
  --type=CURATED \
  --discovery-enabled \
  --discovery-schedule="0 * * * *"
```

---

## 🗃️ Step 5: Create a BigQuery Dataset

```bash
bq mk --location=$REGION --dataset orders
```

---

## 🔗 Step 6: Attach BigQuery Dataset as an Asset

```bash
gcloud dataplex assets create orders-curated-dataset \
  --location=$REGION \
  --lake=ecommerce \
  --zone=orders-curated-zone \
  --display-name="Orders Curated Dataset" \
  --resource-type=BIGQUERY_DATASET \
  --resource-name=projects/$PROJECT_ID/datasets/orders \
  --discovery-enabled
```

---

## ❌ Step 7: Detach the Asset

```bash
gcloud dataplex assets delete orders-curated-dataset \
  --location=$REGION \
  --zone=orders-curated-zone \
  --lake=ecommerce
```

---

## 🧹 Step 8: Delete the Zone

```bash
gcloud dataplex zones delete orders-curated-zone \
  --location=$REGION \
  --lake=ecommerce
```

---

## 🗑️ Step 9: Delete the Lake

```bash
gcloud dataplex lakes delete ecommerce \
  --location=$REGION
```

---

## 🧩 Dataplex for Data Mesh

**Dataplex** supports Data Mesh Architecture principles:

- **Decentralized Data Ownership**: Each domain owns and manages its own data.
- **Centralized Governance**: Common policies and metadata control through Dataplex.
- **No Data Duplication**: Manages metadata directly—no need to move or copy data.
- **Unified Metastore**: Automatically registers both structured and unstructured data into a single secure metastore.
- **Native Integrations**: Seamlessly works with BigQuery, Data Catalog, Cloud Storage, and more.

---

✅ **Use Case**: This setup enables efficient, governed, and discoverable data lakes for analytics and cross-domain insights—all aligned with the **Data Mesh** philosophy.







