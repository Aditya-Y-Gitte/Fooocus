# Fooocus on Google Colab

This guide is for this repository's Colab notebook and its tested Google Colab environment: **Python 3.10.21** with a GPU runtime. It runs this fork, including its current prompt-handling behavior.

## Start Fooocus

1. Open [fooocus_colab.ipynb](fooocus_colab.ipynb) in Google Colab, or use the Colab badge below.
2. Select **Runtime -> Change runtime type -> T4 GPU** (or another available NVIDIA GPU).
3. Run the notebook's only cell. The first launch installs the required packages, downloads Fooocus models, and prints a public Gradio URL.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Aditya-Y-Gitte/Fooocus/blob/main/fooocus_colab.ipynb)

The notebook verifies that the runtime is Python 3.10.x and is specifically tested with Python 3.10.21. No Python-version change is needed when Colab reports `Python 3.10.21`.

## Notebook command

The launch cell clones this repository and starts the shared Gradio interface:

```python
%pip install pygit2==1.15.1
%cd /content
!git clone --depth 1 https://github.com/Aditya-Y-Gitte/Fooocus.git
%cd /content/Fooocus
!python entry_with_update.py --share --always-high-vram
```

`--always-high-vram` is a good default for a T4. If the runtime has less available VRAM or disconnects during model loading, remove that argument and run the final command again.

## Presets and persistence

Append `--preset anime` or `--preset realistic` to the final command to start in that preset. Colab's `/content` storage is temporary: downloaded models, outputs, and settings disappear when the runtime is reset. Copy files you want to keep to Google Drive before ending the session.

## Troubleshooting

- **Wrong Python version:** use a Colab runtime that reports Python 3.10.21 (or another Python 3.10.x release), then rerun the cell.
- **The clone folder already exists:** run `!rm -rf /content/Fooocus` only if you do not need files from the current runtime, then rerun the cell.
- **No public URL:** confirm that the final command includes `--share` and wait for the initial model downloads to finish.
- **Out of memory:** remove `--always-high-vram`, restart the runtime, and try again.
