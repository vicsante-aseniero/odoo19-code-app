# Analysis of Odoo 19 source code development with OpenEduCat ERP modules and tutorials

Summary
- This workspace contains an Odoo-based setup: core Odoo code in `./odoo` (as a git submodule), third-party OpenEduCat modules under `./extra-addons/openeducat_erp`, and tutorial/example addons under `./tutorials`.

Key findings
- Submodules:
  - `./odoo` is a submodule: https://github.com/odoo/odoo.git (branch 18). This indicates the actual runtime code is Odoo 18 while the repository name suggests Odoo 19. This mismatch is deliberate or historical and should be validated for compatibility of third party modules with the targeted Odoo version.
  - `./extra-addons/openeducat_erp` is a submodule: https://github.com/openeducat/openeducat_erp
  - `./tutorials` is a local copy of Odoo tutorial modules derived from Odoo documentation.

- Codebase size & structure: Large. The `odoo` submodule includes the full Odoo open-source codebase (core modules, test suite, tools, and CLI). The `extra-addons` folder contains modular third-party apps that extend Odoo functionality.

Compatibility & Risks
- Mixed Odoo versions risks:
  - If `odoo` submodule is on branch 18 while this repo intends to target Odoo 19, there will be compatibility problems with addons built for Odoo 19 APIs. Confirm the intended version and align submodules and local addons accordingly.
- Third-party module compatibility:
  - OpenEduCat is a community-driven module targeted at educational institutions and may target specific Odoo major versions. Check its manifest and tests to ensure the correct Odoo API mappings.
- Submodule updates:
  - Use `git submodule update --init --recursive` to fetch submodules and `git submodule update --remote` to track remotes. Use `--merge` with caution for non-trivial changes.

Recommended next steps
1. Confirm the desired Odoo runtime version (18 vs 19). Align `./odoo` submodule branch accordingly.
2. Run a smoke test with a fresh DB to check for breaking changes:
   - `python -m venv .venv` and `pip install -r odoo/requirements.txt`
   - `odoo/odoo-bin -d odoo_test --addons-path=odoo/addons,extra-addons,tutorials` and enable minimal installed modules.
3. Validate OpenEduCat compatibility by checking its `__manifest__` and running unit tests:
   - Navigate to `extra-addons/openeducat_erp` and run tests with a minimal Odoo test runner.
4. Consider aligning all modules to a single Odoo LTS release for consistency and safer testing.

Developer and maintenance notes
- Tests: Odoo's test suite is extensive. Use `pytest` or Odoo's built-in test runner. For addon tests, run with `odoo/odoo-bin -i <module> --test-enable`.
- CI: Implement CI that runs unit and smoke tests after updating submodules.



---
**Future Documentation Requests**
- To add docs, use `./.ai-prompts-prds/prompts/PROMPT-READ.md` and `./.ai-prompts-prds/prompts/PROMPT-ANALYSIS.md` templates.
- Request template: Short summary, area of repo to change, steps to reproduce or desired state.
- Response template: Summary, steps taken, files changed, and follow-ups.
