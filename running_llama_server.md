# Running the Llama Server

Before running, navigate to the directory where `llama-server` is located:
- **Windows:** `C:\llama.cpp\build\bin\Release`
- **Linux/macOS:** (Navigate to the directory above, then use the command below)

**Execution Command:**
Run the server using the following command. Adjust `path_to_model.gguf`, `ngl`, `c`, `host`, and `port` as needed.

\`\`\`bash
./llama-server -m path_to_model.gguf -ngl 999 -c 4096 --host 0.0.0.0 --port 8080
\`\`\`

**Expected Output:**
Upon successful execution, you should see the server initializing and loading the model onto your video card (CUDA0).

![Server running successfully](images/succes_run.png)
*Figure 1: Confirmation of Llama Server running successfully and loading the model onto CUDA0.*