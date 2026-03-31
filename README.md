# sap-rap-sales-order-mgmt
Full-stack SAP RAP implementation of a Sales Order BO using an Unmanaged Save scenario with Draft enablement, custom transactional buffering, and OData V4 service exposure on S/4HANA.


# SAP RAP: Unmanaged Sales Order App with Custom Buffering

## 🚀 Technical Highlights
This project demonstrates a deep dive into the **ABAP RESTful Programming Model (RAP)** using an **Unmanaged Save** scenario. It transitions from legacy ABAP patterns to modern, Cloud-ready architecture.

### 🧠 The "Brain" of the App: Local Buffer & Saver
Unlike a standard Managed RAP app, I implemented a manual **Transactional Buffer** to handle the data lifecycle:
* **Interaction Phase:** Used a Local Class `lcl_buffer` to store state in-memory during `CREATE` and `UPDATE` calls.
* **ID Mapping:** Handled the critical mapping of `%cid` (Frontend ID) to `%pid` (Backend UUID) to ensure data consistency during the "Draft-to-Active" transition.
* **The Saver Class:** Redefined the `SAVE_MODIFIED` method to physically commit data from the buffer to transparent tables (`zotc_t_soh/soi`), simulating a legacy API integration.

### 🛠️ Tech Stack
* **Language:** ABAP Cloud (Strict Mode 2)
* **Data Modeling:** Core Data Services (CDS) View Entities
* **Framework:** SAP RAP (Unmanaged with Draft)
* **API:** OData V4
* **UI:** Fiori Elements (List Report / Object Page)
