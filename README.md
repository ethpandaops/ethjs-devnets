<div align="center"><img src="./docs/images/panda.png" width="300"/></div>
<h2 align="center">🐼 ❤️.oO<br>"Pandas love snap syncing"</h2>
<h1 align="center">Infrastructure code for EthJS Snap Sync Testnets</h1>

<p align="center">
<a href="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/ansible_lint.yaml"><img src="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/ansible_lint.yaml/badge.svg"></a>
<a href="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/terraform_lint.yaml"><img src="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/terraform_lint.yaml/badge.svg"></a>
<a href="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/helm_lint.yaml"><img src="https://github.com/ethpandaops/ethjs-testnets/actions/workflows/helm_lint.yaml/badge.svg"></a>
</p>

This repository contains the infrastructure code used to setup ~all~ dev/testnets. A lot of the code uses reusable components either provided by our [ansible collection](https://github.com/ethpandaops/ansible-collection-general) or our [helm charts for kubernetes](https://github.com/ethpandaops/ethereum-helm-charts/).

# Networks

Status   | Network    | Links   | Ansible                                                      | Terraform | Kubernetes
------   | --------   | ----     |  -----                                                       | -------   | ------
 🟢 Live | [devnet-0](https://dora.ethjs-devnet-0.ethpandaops.io/)   | [Network config](network-configs/devnet-0) / [Inventory](https://bootnode.srv.ethjs-devnet-0.ethpandaops.io/meta/api/v1/inventory.json) / [Validator ranges](https://bootnode.srv.ethjs-devnet-0.ethpandaops.io/meta/api/v1/validator-ranges.json)    | [🔗](ansible/inventories/devnet-0) | [🔗](terraform/devnet-0)

# Development
## Version management for tools

We're using [asdf](https://github.com/asdf-vm/asdf) to make sure that we all use the same versions across tools. Our repositories should contain versions defined in .tools-versions.

You can then use [`./setup.sh`](./asdf-setup.sh) to install all dependencies.

# Update all sops files
```
# Find all .sops.* and *.enc.* files and update their keys
find . -type d -name "vendor" -prune -o \( -type f \( -name "*.sops.*" -o -name "*.enc.*" \) \) -exec sops updatekeys {} -y \;
```

## Genesis allocation used:
Here's a table of where the keys are used

| Account Index | Component Used In | Private Key Used | Public Key Used | Comment                           |
|---------------|-------------------|------------------|-----------------|-----------------------------------|
| 0-15          | available         |                  |                 |                                   |