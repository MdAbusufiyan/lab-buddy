# LAB Buddy

## Technical and Legal Documentation

### 1. Overview
LAB Buddy is a lightweight, offline-friendly desktop application designed for pharmaceutical and chemistry laboratories. The application enables users to search, view, and log chemical compound information sourced primarily from PubChem (NIH). It is built using Python and Tkinter, with a focus on stability, minimal resource usage, and suitability for low-specification laboratory computers.

The application operates in both online and offline environments. When internet access is available, LAB Buddy retrieves live data from PubChem. When offline, it relies on a locally stored cache to ensure uninterrupted functionality.

---

### 2. Intended Use
LAB Buddy is intended as an informational and record-keeping utility for laboratory personnel. It is not designed to replace official safety data sheets (SDS), regulatory documentation, or validated laboratory information management systems (LIMS).

The software provides summarized chemical data for reference purposes only.

---

### 3. Data Sources and Attribution
All chemical data displayed by LAB Buddy is sourced from:

- **PubChem**, National Center for Biotechnology Information (NCBI), National Institutes of Health (NIH)

The application accesses PubChem through its publicly available REST APIs. Structure images, hazard data, and chemical properties are retrieved directly from PubChem endpoints.

The application does not modify source data beyond formatting, truncation (e.g., top hazard statements), or caching for offline use.

---

### 4. Online and Offline Behavior

#### 4.1 Online Mode
When an active internet connection is detected:
- Chemical searches are performed directly against PubChem.
- Retrieved data is displayed in the user interface.
- Relevant data is stored in a local cache for future offline access.
- Missing or outdated cached fields (e.g., SMILES or GHS data) may be silently refreshed in the background without user interaction.

#### 4.2 Offline Mode
When no internet connection is available:
- Searches are performed against the local cache only.
- Cached data is displayed without attempting network access.
- Image retrieval may be unavailable if images were not previously cached.

---

### 5. Local Cache System
LAB Buddy maintains a local JSON-based cache to support offline functionality.

#### 5.1 Cache Contents
The cache may include:
- Chemical name (preferred name)
- PubChem CID
- CAS number (when available)
- Molecular formula
- Molecular weight
- Density (if available)
- IUPAC name
- SMILES notation
- Selected GHS hazard statements
- Structure image URL
- Timestamp of last update

#### 5.2 Cache Integrity
To ensure data integrity:
- A SHA-256 hash signature file is generated alongside the cache file.
- On application startup, the cache hash is verified.
- If verification fails, the cache is ignored and rebuilt as new data is retrieved.

#### 5.3 Search Optimization
The application maintains internal indices to allow case-insensitive lookup by:
- Chemical name
- CAS number
- IUPAC name
- SMILES string

---

### 6. Hazard Information
LAB Buddy displays limited hazard information based on PubChem’s GHS classification data.

- A maximum of selected pictograms may be displayed.
- Only a limited number of hazard statements are shown for clarity.

Hazard data is provided for reference only and should not be used as a substitute for official safety documentation.

---

### 7. Excel Logging Functionality
LAB Buddy allows users to log selected chemical data into Microsoft Excel (.xlsx) files.

#### 7.1 Log File Features
Users may:
- Create a new Excel log file with selectable columns
- Load an existing Excel log file
- Append new chemical records sequentially

Default and optional columns may include:
- Chemical name
- CAS number
- Molecular formula
- Molecular weight and units
- Density and units
- Quantity and equivalence fields
- IUPAC name
- SMILES notation
- Structure image link

LAB Buddy uses the `openpyxl` library for Excel file handling.

---

### 8. User Interface and Design Considerations
The user interface is intentionally minimal and function-focused.

Key design principles include:
- Low memory and CPU usage
- Clear labeling suitable for laboratory environments
- No unnecessary animations or background processes

A custom-generated header image is used solely for branding and visual separation. No third-party copyrighted images are embedded in the application.

---

### 9. Licensing
LAB Buddy is intended to be distributed under a permissive open-source license (e.g., MIT License).

Under such a license:
- The software may be used, modified, and redistributed free of charge
- No warranty or liability is provided by the author
- Proper attribution and inclusion of the license text are required in redistributions

The final license text is provided in the project repository.

---

### 10. Disclaimer
LAB Buddy is provided “as is”, without warranty of any kind, express or implied.

The author makes no guarantees regarding:
- Accuracy or completeness of chemical data
- Suitability for regulatory, clinical, or safety-critical use

Users are responsible for verifying all chemical information against authoritative sources before use in laboratory procedures.

---

### 11. Credits
- Chemical data and structure images: PubChem (NIH)
- Header image: Generated using OpenAI tools

---

### 12. Support and Maintenance
LAB Buddy is provided as a free and open-source utility. There is no obligation for ongoing support, updates, or maintenance.

Bug reports and improvements may be submitted through the project’s source repository, subject to availability and discretion of the author.

