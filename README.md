# Docs

![Build and Deploy](https://github.com/jwblangley/docs/actions/workflows/publish.yml/badge.svg)

https://jwblangley.github.io/docs/

---

**Time-saving Answers to Infrequent, but Annoyingly Specific Tasks**
My personal notes covering small bits and pieces that may be needed relatively uncommon, but are a time-suck when they do come up without this collection!

## Adding docs
This repo is fully automated. To add or edit any documentation, simply create/edit a file within the `docs` directory. Do not add documentation to the `img` or `stylesheets` directories as these have special usage.

Directory hierarchy is preserved and reflected in the generated docs, which are automatically built and published on each commit to the master branch.

## Development
This repo uses [mkdocs](https://www.mkdocs.org/), incorporating [material for mkdocs](https://squidfunk.github.io/mkdocs-material/). Local development can be done by creating and activating a virtual environment.

```bash
python3 -m venv venv
source venv/bin/activate
```

Installing the dependencies.

```bash
pip install -r requirements.txt
```

And serving a build to [localhost:8000](http://localhost:8000)
```bash
mkdocs serve
```
