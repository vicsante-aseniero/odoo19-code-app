# Odoo 19 source code development with OpenEduCat ERP modules and tutorials

Odoo 19 community source code with additional 3rd party modules and tutorials.

Overview
- Main repo: odoo19-code-app (this project)
- Includes Odoo source submodule in `./odoo` (community edition) configured as a git submodule.
- Includes third-party OpenEduCat module in `./extra-addons/openeducat_erp` (git submodule).
- Includes Odoo developer tutorials under `./tutorials` (examples from Odoo docs).

Important directories
- ./odoo: Odoo community source (git submodule). Expected upstream: https://github.com/odoo/odoo.git (branch: 18)
- ./extra-addons/openeducat_erp: Third-party OpenEduCat education ERP modules. Upstream: https://github.com/openeducat/openeducat_erp
- ./tutorials: Odoo documentation tutorial modules. See: https://www.odoo.com/documentation/18.0/developer/tutorials/setup_guide.html

Quick setup
1. Clone the repo and init submodules:
   git clone --recurse-submodules https://github.com/vicsante-aseniero/odoo19-code-app.git
   cd odoo19-code-app
   git submodule update --init --recursive

2. Create a Python virtual environment (recommended):
   python3 -m venv .venv
   source .venv/bin/activate

3. Install requirements
   pip install -r odoo/requirements.txt

4. Start Odoo (example):
   odoo/odoo-bin -c config/odoo.conf -d mydb --dev=all --addons-path=odoo/addons,extra-addons,tutorials

Notes
- The `./odoo` directory is currently a git submodule on branch 18 (Odoo 18). There may be deliberate or accidental cross-version collocation: this repository is organized for testing and development with a mix of Odoo 18 files (submodule) and local customization for Odoo 19 community edition. Verify compatibility for any modules you plan to enable.
- `extra-addons/openeducat_erp` is a 3rd party submodule (OpenEduCat). Review OpenEduCat licensing and module compatibility before installing in your Odoo instance.
- `tutorials` contains example modules from Odoo docs and are useful for learning and experimentation.

Contributing and updates
- Update submodules:
  git submodule update --remote --merge
- To switch or update the `odoo` submodule branch, navigate to `odoo` and check out a new branch/tag per upstream release.

License
- Odoo Community is licensed under the LGPL; third-party modules may use different licenses—see upstream repositories for details.

Support
- For upstream Odoo issues, visit https://github.com/odoo/odoo
- For OpenEduCat issues, visit https://github.com/openeducat/openeducat_erp

Contact / Maintainers
- Refer to repository contributors and maintainers in the remote origin and submodules.


---
**Future Documentation Requests**
- To add docs, use `./.ai-prompts-prds/prompts/PROMPT-READ.md` and `./.ai-prompts-prds/prompts/PROMPT-ANALYSIS.md` templates.
- Request template: Short summary, area of repo to change, steps to reproduce or desired state.
- Response template: Summary, steps taken, files changed, and follow-ups.
