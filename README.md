# Detektr

**Detektr** is a unified interface layer for file-based security and transformation engines.  
It provides a single, consistent entry point to interact with a variety of specialized services—such as antivirus scanners, data loss prevention, content disarm and reconstruction, file type detection, and more.

> **One interface. Any engine. Clean boundaries.**

---

## 🧠 Purpose

Modern file processing systems often rely on multiple specialized engines to secure, analyze, and transform content—each with its own interface, protocol, and quirks.  
**Detektr** abstracts those differences behind a single, normalized interface.

With Detektr, client systems no longer need to know *how* each engine works—just *what* they want to do.

---

## 🔗 What Detektr Connects

Detektr serves as a common access layer to a wide range of backend services, including:

- 🔍 **DLP Engines** (e.g., detecting PII, secrets)  
- 🧹 **CDR Engines** (e.g., scrubbing files of threats)  
- 🛡️ **Antivirus Engines** (e.g., ClamAV, Defender)  
- 📦 **Compression / Decompression Engines**  
- 🧰 **Extraction Engines** (e.g., ZIP, TAR)  
- 🔄 **File Conversion Engines** (e.g., DOCX → PDF)  
- 🧠 **File Type Detection Engines**  

---

## 🧩 Key Concepts

- **Engine ID**: Every engine Detektr exposes has a unique identifier (e.g., `dlp.fyltr`, `cdr.scrbbl`, `av.clamav`).
- **Uniform API**: Regardless of the underlying engine, Detektr presents a consistent request and response structure.
- **Isolation**: Client systems do not communicate with engines directly—only through Detektr.
- **Scalability**: Engines can be swapped, scaled, or relocated without impacting clients.
- **Simplicity**: No more dealing with engine-specific SDKs, protocols, or error formats.

---

## 🎯 Who Uses Detektr?

Any internal or external service that needs to:

- Scan uploaded files for threats
- Scrub or sanitize potentially dangerous documents
- Identify file formats and validate structure
- Detect and prevent sensitive data leakage
- Convert files between formats
- Unpack or compress archived content

Common examples:
- API gateways
- Upload validation pipelines
- Document processing services
- Threat analysis systems
- Compliance and security audit tools

---

## 🛠 Example Flow

1. A file upload service wants to check for malware.
2. It sends a request to Detektr: `"engine_id": "av.clamav"` with the file path.
3. Detektr routes the request to the ClamAV service.
4. It receives a normalized response and returns it to the caller.

No need to know how ClamAV works. No direct communication. Fully encapsulated.

---

## 🧱 Architecture Overview

```text
[ Client Services ]
        │
        ▼
    [ Detektr ]
        │
 ┌─────┼────────┬────────────┬────────────┐
 ▼     ▼        ▼            ▼            ▼
[DLP] [CDR]   [AV]         [Type]      [Extract]
````

---

## 🌍 Why Use Detektr?

* **Decoupling**: Your core business logic is never tied to a specific engine.
* **Standardization**: Unified API across disparate tools.
* **Flexibility**: Swap or scale engines independently.
* **Observability**: Centralized logging, auditing, and metrics.
* **Security**: Limit and isolate access to powerful file-processing tools.

---

## 📄 License

Detektr is released under the MIT License.

---

**Detektr** – The interface to everything under the hood.
