# RAG - Retrieval-Augmented Generation Knowledge System for Insurellm

A comprehensive Retrieval-Augmented Generation (RAG) system built on a structured knowledge base containing company information, products, contracts, and employee records for **Insurellm**, an insurance technology platform.

## 📋 Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Knowledge Base](#knowledge-base)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Data Structure](#data-structure)
- [Contributing](#contributing)

## 🎯 Overview

This RAG system serves as an intelligent information retrieval and augmentation platform for querying comprehensive knowledge about Insurellm's operations, including:

- **Company Profile**: Organizational structure, locations, and business strategy
- **Product Information**: Detailed specifications of 8 insurance software products
- **Client Contracts**: 32 active contracts with pricing, terms, and SLAs
- **Employee Records**: HR data, compensation, career progression, and performance metrics

The system enables natural language queries to retrieve and synthesize relevant information from the structured knowledge base, making it ideal for:

- Stakeholder inquiries
- Business intelligence
- Client relationship management
- HR management
- Product documentation

## 📁 Project Structure

```
RAG/
├── README.md                          # Project documentation
├── test.ipynb                         # Jupyter notebook for testing and demonstrations
└── knowledge-base/
    ├── company/                       # Company information
    │   ├── overview.md               # Company overview and portfolio breakdown
    │   ├── about.md                  # Company background
    │   ├── careers.md                # Career opportunities
    │   └── culture.md                # Company culture
    ├── products/                      # Product specifications (8 products)
    │   ├── Bizllm.md                 # Commercial insurance platform
    │   ├── Carllm.md                 # Auto insurance platform
    │   ├── Claimllm.md               # AI-powered claims processing
    │   ├── Healthllm.md              # Health insurance platform
    │   ├── Homellm.md                # Home insurance platform
    │   ├── Lifellm.md                # Life insurance platform
    │   ├── Markellm.md               # Insurance marketplace
    │   └── Rellm.md                  # Reinsurance platform
    ├── contracts/                     # Client contracts (32 active)
    │   └── Contract with [Client] for [Product].md
    └── employees/                     # Employee records (32 employees)
        └── [Employee Name].md
```

## 📚 Knowledge Base

### Company (`knowledge-base/company/`)

Contains organizational information including:

- **Overview**: 32-employee team, founded 2015, offices in SF (HQ), NYC, Austin, Chicago, Denver
- **Portfolio**: 32 active contracts spanning all product lines
- **Mission**: Sustainable growth focused on operational excellence

### Products (`knowledge-base/products/`)

Eight comprehensive insurance technology solutions:

| Product       | Type        | Description                             | Pricing Tiers                       |
| ------------- | ----------- | --------------------------------------- | ----------------------------------- |
| **Carllm**    | Auto        | Personal & commercial auto insurance    | Essential, Professional, Enterprise |
| **Homellm**   | Home        | Property & home insurance management    | Standard, Professional, Enterprise  |
| **Lifellm**   | Life        | Life insurance with AI underwriting     | Growth, Standard, Enterprise        |
| **Healthllm** | Health      | Comprehensive health insurance platform | Essential, Professional, Enterprise |
| **Bizllm**    | Commercial  | Business insurance coverage management  | Professional, Enterprise            |
| **Claimllm**  | Claims      | AI-powered claims processing            | Core, Advanced, Enterprise          |
| **Markellm**  | Marketplace | Consumer-insurer matching platform      | Basic Listing + Performance-based   |
| **Rellm**     | Reinsurance | Enterprise reinsurance operations       | Professional, Enterprise            |

### Contracts (`knowledge-base/contracts/`)

32 active client contracts with:

- **Client information** and locations
- **Payment terms** ($4,500 - $64,000+/month)
- **Contract duration** (12-48 months)
- **Service specifications** (member coverage, policy volume, user licenses)
- **SLAs and performance guarantees**
- **Confidentiality and liability terms**
- **Renewal and termination conditions**

**Contract Value Breakdown:**

- **Healthllm**: 6 contracts (~$2.2M+ total)
- **Claimllm**: 7 contracts (~$1.8M+ total)
- **Lifellm**: 6 contracts (~$1.4M+ total)
- **Bizllm**: 7 contracts (~$0.8M+ total)
- **Carllm**: 3 contracts (~$0.7M+ total)
- **Homellm**: 4 contracts (~$1.0M+ total)
- **Rellm**: 2 contracts (~$2.4M+ total)
- **Markellm**: 2 contracts (~$0.5M+ total)

### Employees (`knowledge-base/employees/`)

32 comprehensive HR records including:

- **Personal Info**: DOB, location, contact
- **Job Title & Compensation**: Salary ranges from $82K-$225K
- **Career Progression**: Employment history and advancement
- **Performance**: Annual reviews and achievements
- **Compensation History**: Salary and benefit changes

**Key Roles:**

- CEO & Co-Founders
- Data Scientists & ML Engineers
- Full-Stack & Backend Engineers
- Product Managers
- Designers & UX Specialists
- DevOps & Infrastructure
- Sales & Business Development
- HR & Administration

## ⚙️ Features

### Core Capabilities

- 🔍 **Semantic Search**: Query knowledge base with natural language
- 📊 **Contract Analytics**: Extract pricing, terms, and SLA information
- 👥 **Employee Lookup**: Access HR records and organizational data
- 📦 **Product Information**: Retrieve detailed product specifications and pricing
- 🏢 **Company Insights**: Access organizational structure and strategy

### Data Organization

- Structured markdown documents for easy parsing
- Consistent formatting across all records
- Cross-referenced information (contracts linked to products and clients)
- Comprehensive metadata for each entry

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Required Python libraries (see below)

### Installation

1. Clone or download the repository:

```bash
cd RAG
```

2. Install required dependencies:

```bash
pip install jupyter pandas numpy
```

3. Optional: For advanced RAG capabilities, install:

```bash
pip install langchain openai chromadb sentence-transformers
```

### Running the System

1. Open the Jupyter notebook:

```bash
jupyter notebook test.ipynb
```

2. Load and explore the knowledge base data

3. Execute queries to retrieve information

## 💡 Usage

### Basic Query Examples

**Company Information:**

- "What is Insurellm's organizational structure?"
- "How many employees does Insurellm have and what are their locations?"
- "What is the company's founding date and history?"

**Product Information:**

- "Explain Healthllm's key features and pricing"
- "Compare the different insurance products offered"
- "What are the pricing tiers for Carllm?"

**Contract Insights:**

- "Which clients use Healthllm?"
- "What is the total contract value with United Healthcare Alliance?"
- "List all Enterprise Tier contracts"
- "Show contracts with automatic renewal clauses"

**Employee Queries:**

- "List all Data Scientists and their salaries"
- "Who are the engineers working on the platform?"
- "Show employee locations and compensation"

## 📊 Data Structure

### Knowledge Base Organization

Each document type follows a consistent structure:

**Company Files:**

```
# [Topic]
## Summary/Overview
[Content]
## Sections
[Detailed information]
```

**Product Files:**

```
# Product Name
## Summary
[Description]
## Features
[Feature list with details]
## Pricing
[Tier-based pricing model]
## Roadmap
[Future development plans]
```

**Contract Files:**

```
# Contract with [Client] for [Product]
## Terms
1. Parties Involved
2. Scope of Services
3. Payment Terms
4. Contract Duration
[Additional clauses...]
```

**Employee Files:**

```
# [Employee Name]
## Summary
[Personal info and current role]
## Insurellm Career Progression
[Career history]
## Annual Performance History
[Performance reviews]
## Compensation History
[Salary progression]
```

## 🔄 Workflow

### Adding New Information

1. **New Contract**: Add file to `knowledge-base/contracts/`
2. **New Employee**: Add file to `knowledge-base/employees/`
3. **Company Updates**: Update relevant files in `knowledge-base/company/`
4. **Product Changes**: Update product files in `knowledge-base/products/`

### Querying the System

1. Parse markdown files using Python
2. Load content into vector database (for semantic search)
3. Execute queries using RAG pipeline
4. Retrieve and synthesize results

## 📝 Contributing

To contribute to this knowledge base:

1. Maintain consistent formatting across documents
2. Update relevant cross-references
3. Keep information current and accurate
4. Follow the established structure for new documents
5. Include comprehensive metadata

## 📈 Metrics & KPIs

### Contract Portfolio

- **Total Contracts**: 32 active
- **Average Contract Value**: ~$75K per contract
- **Total ARR**: ~$12.5M+ annually
- **Longest Term**: 48 months (GlobalRe Partners, United Healthcare Alliance)

### Company Scale

- **Team Size**: 32 employees
- **Product Lines**: 8 solutions
- **Geographic Coverage**: 5 major offices (SF, NYC, Austin, Chicago, Denver)
- **Industry Focus**: Enterprise insurance technology

## 🎓 Use Cases

- **Sales Enablement**: Quick access to contract terms and client info
- **Business Intelligence**: Analytics on product adoption and revenue
- **HR Management**: Employee lookup and compensation analysis
- **Client Support**: Product specifications and feature documentation
- **Strategic Planning**: Portfolio analysis and market insights

## 📞 Support

For questions or issues:

1. Check existing documentation in the knowledge base
2. Review the test.ipynb notebook for examples
3. Ensure all markdown files are properly formatted

---

**Last Updated**: August 2026
**Knowledge Base Version**: 1.0
**Total Records**:

- Company Docs: 4
- Products: 8
- Contracts: 32
- Employees: 32
