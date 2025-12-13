# Odoo 19 Community — Code + OpenEducat + Tutorials

Overview

This repository contains a development workspace for Odoo 19 Community Edition with the following components:

- Odoo 19 (Community): located at `./odoo` as a git submodule (branch 19.0).
- OpenEducat ERP (third-party): located at `./extra-addons/openeducat_erp` as a git submodule (branch 19.0). See https://openeducat.org and https://github.com/openeducat/openeducat_erp.
- Odoo Tutorials module: located at `./tutorials` as a git submodule. These are useful example modules from the Odoo developer tutorials (https://www.odoo.com/documentation/19.0/developer/tutorials/setup_guide.html).

Quick Start (development)

1. Clone the repo and initialize submodules:

```bash
# If not cloned yet
git clone --recurse-submodules <repo-url>
# Or, update submodules after cloning
git submodule update --init --recursive
```

2. Set up a Python virtual environment and install dependencies:

```bash
python3 -m venv venv
. venv/bin/activate
pip install -r odoo/requirements.txt
```

3. Run Odoo (example):

```bash
# Run the server with addons path including extra-addons
./odoo/odoo-bin -d mydb --addons-path=odoo/addons,extra-addons
```

Notes

- The `odoo` directory is a submodule that tracks branch `19.0`.
- The `extra-addons/openeducat_erp` is a third-party submodule for OpenEducat and matches Odoo 19.0 compatibility.
- `tutorials` provides example modules useful for learning and experimentation.

Testing

- Odoo contains an integrated test framework. You can run module tests using Odoo's CLI test options or run core tests as documented in Odoo developer docs.

Submodule Maintenance

- To update submodules:

```bash
git submodule update --remote --merge --init --recursive
```

- To add/update a submodule explicitly (example):

```bash
# Add Odoo 19 from official repo (if needed)
git submodule add -b 19.0 https://github.com/odoo/odoo.git odoo
```

Contributing

- Code: follow Odoo's contribution and module guidelines.
- For bugs/security/vulnerability disclosures, use the standard repository process.

License

This repository includes Odoo Community Edition and third-party modules. Check the `odoo` and `openeducat_erp` LICENSE files for specific licensing details.

