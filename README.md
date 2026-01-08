# llamafile-builder

A simple github actions script to build a llamafile from a given gguf file download url and uploads it to huggingface repo. This workflow runs on Debian 12 in a containerized environment.

llamafile lets you distribute and run LLMs with a single file. [announcement blog post](https://hacks.mozilla.org/2023/11/introducing-llamafile/)

## Inputs

### `model_url`

**Required** The url to the gguf file to download.

### `huggingface_repo`

**Required** The huggingface repo to upload the llamafile to.

Add your huggingface token with write access to the repo as a actions secret with the name `HF_TOKEN`.

## Usage

### Using GitHub Actions (Recommended)

This is the primary way to use this repository:

1. Head over to the actions tab.
2. Select the action `Build llamafile` 
3. Fill in the required inputs.
4. Click on `Run workflow` and wait for the action to complete.
5. Check your huggingface repo for the llamafile.

### Local Usage

If you want to use the `hf.py` script locally to upload an existing llamafile:

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Set your HuggingFace token:
   ```bash
   export HF_TOKEN=your_token_here
   ```

3. Run the script:
   ```bash
   python3 hf.py <model_url> <huggingface_repo> <llamafile_path>
   # Or, if the script has executable permissions:
   ./hf.py <model_url> <huggingface_repo> <llamafile_path>
   ```

   Example:
   ```bash
   ./hf.py https://huggingface.co/TheBloke/Llama-2-7B-GGUF username/my-llamafile model.llamafile
   ```

**Note:** The `.github/workflows/llamafile.yml` file is a GitHub Actions workflow configuration file and should not be executed directly. It is automatically run by GitHub Actions when you trigger the workflow through the GitHub UI.