# Labcorp Diagnostic Assistant (DxA) - Onboarding Process

This repository contains documentation and resources for the Labcorp Diagnostic Assistant (DxA) onboarding process architecture. The project focuses on streamlining and automating the customer onboarding workflow through DocuSign integration.

## Overview

The DxA onboarding process is a multi-phase workflow that manages customer contracts, validations, and documentation. This project documents both the current manual processes and proposed automated solutions to improve efficiency and reduce manual effort.

## Repository Contents

### 📊 Architecture Documentation
- **`onboarding-architecture-diagram.html`** - Interactive architecture diagram showcasing the complete onboarding process
  - Current process view (manual steps)
  - Proposed automated process view
  - Flowchart visualization
  - Searchable phases and steps
  - Export functionality (PDF, comparison reports)

### 📄 Process Documentation
- **`DxA Contracting Process - DocuSign for Automation.docx`** - Detailed DocuSign automation process documentation

## Process Phases

The onboarding workflow consists of 8 key phases:

| Phase | Name | Description |
|-------|------|-------------|
| **0** | Pre-Requisites | Access setup (DocuSign, Adobe Acrobat Pro, templates) |
| **1** | Information Receipt | Customer data collection and intake |
| **2** | Pre-Creation Validation | Data validation before document creation |
| **3** | DocuSign Creation | Contract document generation |
| **4** | Pre-Send Automation | Automated checks and configurations |
| **5** | Send DocuSign | Document distribution to customers |
| **6** | Post-Signature Automation | Processing signed documents |
| **7** | Pipeline Entry | Final integration into customer pipeline |

## Features

### Interactive Architecture Diagram
The HTML architecture diagram includes:
- **Toggle Views**: Switch between Current, Automated, and Flowchart views
- **Collapsible Phases**: Expand/collapse sections for focused viewing
- **Search Functionality**: Find specific steps, APIs, or tools
- **Color-Coded Legend**:
  - 🟡 Manual Process
  - 🟢 Automated Process
  - 🔵 Validation Step
  - 🔴 API/Integration Call
- **Export Options**: Generate PDF reports or comparison documents

## Getting Started

### Viewing the Architecture Diagram
1. Open `onboarding-architecture-diagram.html` in any modern web browser
2. Use the toggle buttons to switch between views
3. Click phase headers to expand/collapse sections
4. Use the search bar to find specific processes or tools

### Prerequisites for Implementation
- DocuSign account (request via IT Central)
- Adobe Acrobat Pro license (request via Emily Theriault)
- Access to pre-signed DxA agreement template PDF

## Use Cases

This documentation is intended for:
- **Process Owners**: Understanding current workflow and automation opportunities
- **Technical Teams**: Implementing automated solutions
- **Stakeholders**: Reviewing process efficiency improvements
- **Training**: Onboarding new team members to the DxA process

## Technology Stack

- HTML5/CSS3/JavaScript (architecture diagram)
- TailwindCSS (styling framework)
- DocuSign API integration
- Adobe Acrobat Pro (document management)

## Contributing

When updating the process documentation:
1. Update the HTML architecture diagram with new phases or steps
2. Keep the Word document synchronized with HTML changes
3. Test the interactive features in multiple browsers
4. Validate all links and dependencies

## Support

For questions or issues related to:
- **DocuSign Access**: Contact IT Central
- **Adobe Acrobat Pro**: Contact Emily Theriault
- **Process Questions**: Refer to the detailed process documentation

## License

Internal Labcorp documentation - Confidential and Proprietary