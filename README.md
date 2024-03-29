# forge-template

Forge boilerplate repo.

# Getting started
## Prerequisites
### Install & Update Foundry
Install Forge with `curl -L https://foundry.paradigm.xyz | bash`. If you already have Foundry installed, run `foundryup` to update to the latest version. More detailed instructions can be found in the [Foundry Book](https://book.getfoundry.sh/getting-started/installation).

### Install & Update PNPM
Follow the instructions in the PNPM docs.

## Install Included Dependencies
Install the included dependencies with `forge install && pnpm install`.

# Adding dependencies
## With pnpm
If the dependency you would like to install has an NPM package, use `pnpm add [package]` where [package] is the package name. This will install the dependency to `node_modules`.

Tell forge to look for node libraries by adding `node_modules` to the `foundry.toml` by updating `libs` like so: `libs = ['lib', 'node_modules']`.

Add dependencies to `remappings.txt` by running `forge remappings >> remappings.txt`. For example, the NPM package `jbx-protocol` is remapped as `@jbx-protocol/=node_modules/@jbx-protocol/`.

## With Forge
If the dependency you would like to install does not have an up-to-date NPM package, use `forge install [dependency]` where [dependency] is the path to the dependency repo. This will install the dependency to `/lib`. Forge manages dependencies using git submodules.

Run `forge remappings > remappings.txt` to write the dependencies to `remappings.txt`. Note that this will overwrite that file. 

If nested dependencies are not installing, try this workaround `git submodule update --init --recursive --force`. Nested dependencies are dependencies of the dependencies you have installed. 

More information on remappings is available in the Forge Book.

# Updating dependencies
## With PNPM
Run `pnpm upgrade [package]`.

## With Forge
Run `foundryup` to update forge. 

Run `forge update` to update all dependencies, or run `forge update [dependency]` to 
