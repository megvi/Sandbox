# Simulation Model Interface Standard

## 8. Model Failure Handling

Simulation models may implement **failure handling** and/or **logging mechanisms** to detect and manage runtime errors that occur during execution.

Implementing failure handling allows the **simulation control entity** to:

- **Monitor failures** and react accordingly.
- **Reset or shut down the simulation safely** to prevent cascading errors.

While failure handling is **not mandatory**, it is **strongly recommended** to ensure simulation stability and maintainability.

There are two possible approaches for implementing model failure handling:

1. **Dedicated Global Parameter (`R_ERROR`)**
2. **Failure Handling API**

---

### 8.1 Model Error Parameter (`R_ERROR`)

To facilitate **error detection and management**, a **Model Control Variable (`R_ERROR`)** is defined to provide a standardized mechanism for reporting errors to the **simulation environment**.

#### Error Reporting Mechanism (`R_ERROR`)

| **Value** | **Meaning** |
|-----------|------------|
| `0` | The model code is **not responding** to any simulation mode execution request. |
| `-1` | The model code is **executing the required simulation mode correctly**. |
| Any positive value | Indicates an **error or warning** during the execution of the simulation mode. |

> **Note:**  
> All **positive values** of `R_ERROR`, along with their corresponding error/warning descriptions, **must** be documented in the **Model Specification**. This may include a predefined set of errors and warnings to ensure consistency.