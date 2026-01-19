# Jupyter Notebook to Rmarkdown converter

This notebook converts a Jupyter notebook (.ipynb, JSON) to an Rmarkdown (.Rmd) file.

How it works (high level):
- Reads the notebook JSON into `data`. See [`Rmarkdown_convert.data`](Rmarkdown/jupyter-rmarkdown-converter/Rmarkdown_convert.ipynb).
- Detects the notebook language from `data["metadata"]["kernelspec"]["display_name"]`. See [`Rmarkdown_convert.programming_language`](Rmarkdown/jupyter-rmarkdown-converter/Rmarkdown_convert.ipynb).
- Extracts `cells` and iterates:
  - Markdown cells are appended as plain markdown.
  - Code cells are wrapped in fenced code blocks using the detected language.
- Prepends a YAML header (`yaml_config`) and writes the final string (`file_text`) to `converted_notebook.Rmd`.
- Output: a Rmarkdown file

Relevant file:
- [Rmarkdown/jupyter-rmarkdown-converter/Rmarkdown_convert.ipynb](Rmarkdown/jupyter-rmarkdown-converter/Rmarkdown_convert.ipynb)

Reference
1. https://towardsdatascience.com/how-to-convert-a-python-jupyter-notebook-into-an-rmarkdown-file-abf826bd36de/