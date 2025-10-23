# Running Your Own Generative AI on Minisforum: The 70B Parameter Manual

## **Dedicated to the Minisforum MS-S1 Max: Your Local AI Workstation**

This manual provides a step-by-step guide to installing and utilizing the powerful **Llama 3 70B Instruct** Large Language Model (LLM) on your Minisforum MS-S1 Max, leveraging its massive **128GB Unified Memory Architecture (UMA)** for superior, private performance.

-----

## **SECTION 1: HARDWARE & SOFTWARE FOUNDATION**

### **1.1 The Minisforum Advantage**

Your **128GB LPDDR5x UMA** is the key component. It allows the model (which typically requires up to 75GB of high-speed memory) to run directly on your fast system RAM and integrated AMD GPU/NPU cores, avoiding the cost and complexity of high-end dedicated graphics cards.

| Component | Specification on MS-S1 Max | Recommended Requirement |
| :--- | :--- | :--- |
| **LLM Model** | Llama 3 70B Instruct (GGUF) | The highest-performing model you can run privately. |
| **RAM (UMA)** | **128GB LPDDR5x** | More than sufficient for the most demanding quantized versions. |
| **Storage** | NVMe SSD | **$\mathbf{150\text{ GB}+}$** of free space is highly recommended for models, data, and software. |
| **Recommended OS** | **Windows (for GUI Simplicity) or Linux (for AMD Performance)** | The GUI guide below uses the cross-platform tool **LM Studio**. |

### **1.2 Key Terminology**

  * **LLM:** Large Language Model (The AI itself, e.g., Llama 3 70B).
  * **GGUF:** The efficient file format that allows the model to run on CPU + RAM + Integrated GPU.
  * **Quantization:** The process of compressing the model (e.g., Q5\_K\_M) to fit into limited memory with minimal loss of quality.
  * **RAG:** Retrieval-Augmented Generation (The method for feeding your documents).

-----

## **SECTION 2: SETUP GUIDE (The GUI Path - LM Studio)**

This method prioritizes ease-of-use and a familiar graphical interface for managing your LLM.

### **STEP 1: Install LM Studio**

1.  **Download:** Navigate to the **LM Studio official website** and download the application for your operating system (Windows or Linux AppImage).
2.  **Install:** Run the downloaded file and follow the simple installation instructions.

### **STEP 2: Download the Llama 3 70B Model**

*The Llama 3 70B model file is large ($\approx 40\text{ GB}$ to $50\text{ GB}$) and requires a strong internet connection.*

1.  **Search:** Open LM Studio. In the top search bar, type **`Llama 3 70B Instruct GGUF`**.
2.  **Select Source:** Click on a result from a reputable source like **"TheBloke"** or **"lmstudio-community"** to open the file list.
3.  **Choose Quality:** In the right-hand panel, find the GGUF file list. Look for the **Q5\_K\_M** or **Q4\_K\_M** version.
4.  **Download:** Click the **Download** button next to your chosen file.

### **STEP 3: Start Chatting (Inference)**

1.  **Load:** Go to the **Chat** tab (the chat bubble icon).
2.  **Select Model:** In the upper-middle dropdown menu, select the **Llama 3 70B Instruct** model you just downloaded.
3.  **Wait:** The model will take **30 seconds to 2 minutes** to load from your SSD into your 128GB of UMA RAM. The output log will confirm when it is ready.
4.  **Test:** Type a complex request, such as: *"Explain the historical relationship between the Roman Republic and Carthage, focusing on the economic motivations for the Punic Wars."*

-----

## **SECTION 3: PROFESSIONAL USE (Writing & Rephrasing)**

To use the 70B model for high-stakes tasks like proposals and letters, you must control its behavior using the settings in the right-hand panel of the LM Studio **Chat** interface.

### **3.1 Set the Professional Persona (System Prompt)**

The **System Prompt** defines the model's role and style for the entire conversation.

1.  Find the **System Prompt** box at the top of the settings panel.
2.  Paste this text (or a customized version):
    ```
    "You are an expert Proposal Writer and Executive Assistant. Your tone must be formal, professional, confident, and highly persuasive. You will use perfect grammar and always structure outputs with clear headings and bullet points unless explicitly told otherwise."
    ```

### **3.2 Tune Generation Parameters**

| Setting | Use Case (Proposals & Letters) | Recommended Value |
| :--- | :--- | :--- |
| **Temperature** | Controls creativity. Must be low for factual, professional writing. | **0.2 - 0.5** (Lower prevents the model from "hallucinating" or being overly informal). |
| **Context Length** | How many tokens (words) the model remembers for the conversation. | **8192** (or the model's highest available setting). Crucial for long proposals to maintain tone and consistency. |
| **Max Tokens** | The maximum length of a single response. | **2048 - 4096** (Ensures the model doesn't cut off a detailed paragraph or section midway). |

-----

## **SECTION 4: LEARNING & DEVELOPMENT (RAG)**

RAG is the method for making your Llama 3 70B "read" and answer questions about your private files (PDFs, course materials, style guides). This keeps your data local and secure.

### **4.1 Recommended RAG Tool**

The most beginner-friendly GUI tool is **AnythingLLM**.

### **4.2 The RAG Process (How to Teach Your AI)**

1.  **Install AnythingLLM:** Download and install the AnythingLLM desktop application.
2.  **Start Local Server:** Ensure LM Studio is running, and its **Local Inference Server** is active (you may need to switch to Ollama if using a specific RAG app like Open WebUI).
3.  **Connect:** In AnythingLLM, link the application to your local LLM (it should auto-detect or allow you to enter `http://localhost:1234/v1`).
4.  **Create a Workspace:** Create a new "Workspace" (e.g., "M.S. Research Papers").
5.  **Upload Documents:** Upload your PDF research papers, private notes, and internal proposals into the Workspace.
6.  **Indexing:** The RAG tool will automatically perform the following steps locally:
      * **Chunking:** Break the large files into small, searchable text snippets.
      * **Embedding:** Convert those snippets into numerical vectors (meaning) using a small, fast local embedding model.
      * **Storage:** Save the vectors in a local, private database.
7.  **Query:** Now, chat with the model within that workspace. Ask questions like: *"Summarize the key findings on UMA from the 'AMD Architecture Whitepaper.pdf' that I uploaded."*

**Result:** The Llama 3 70B model will retrieve the exact relevant text and generate an accurate, private, high-quality answer.
