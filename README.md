# Artifact Cruncher
Parse forensic disk triage collection to supertimeline on Windows, using Plaso and MFTECmd. Maintains compatibility with Windows filesystem. Optional output ingest into local Docker Splunk instance. Tested on: `Windows 11`, `WSL2`, `Ubuntu 22.04 guest`, `Docker`

## Quick Install
From an `Ubuntu` guest inside `WSL2` on Windows 11 run the following code snippet as `root`.
```
git clone https://github.com/alexzorila/artifact-cruncher2.git
cd artifact-cruncher2
chmod +x ./setup.sh
./setup.sh
```
For WSL2 usage and Ubuntu install see [Cheat Sheet](#wsl-2-cheat-sheet).

## Usage
### Collect
```
PS> .\velociraptor_sans_triage.exe
```
Docs: [Velociraptor](https://docs.velociraptor.app/docs/offline_triage/#offline-collections), [KAPE](https://ericzimmerman.github.io/KapeDocs/#!Pages%5C5.-gkape.md), [CyLR](https://github.com/orlikoski/CyLR?tab=readme-ov-file#examples)

### Parse
```
WSL> parse -f DESKTOP-123.zip
```
Docs: [artifact-cruncher/parse](parse)

### Analyse
| Splunk        | Details |
|---------------|---------|
| CSV Ingest    | Copy CSV data to /artifact-cruncher2/splunk/splunk-data |
| Web GUI       | http://localhost:8000 |
| Web Login     | admin:Password! |

Docs: [artifact-cruncher/splunk](https://github.com/alexzorila/artifact-cruncher2/tree/main/splunk), [Splunk Quick Reference Guide](https://www.splunk.com/en_us/resources/splunk-quick-reference-guide.html)

## Docker Cheat Sheet
Using `WSL2` run one or more of the following `commands` to manage a Docker compose instance.
| Operation       | Command |
|-----------------|---------|
| Show running    |	docker compose ps |
| Stop			      |	docker compose stop |
| Restart		      |	docker compose restart |
| Execute		      |	docker compose exec |
| Destroy	      	|	docker compose down |

Docs: [Docker Compose](https://docs.docker.com/reference/cli/docker/compose/)

## WSL 2 Cheat Sheet
Using Windows `Terminal` run one or more of the following `commands` to manage an Ubunt guest install.
| Operation                      | Command |
| -------------------------------|---------|
| List distro install options    | `wsl -l -o` |
| Install Ubuntu distro          | `wls --install Ubuntu` |
| List installed distros         | `wsl -l` |
| Restart all distros            | `wsl --shutdown` |
| Stop Ubuntu distr              | `wsl --terminate Ubuntu` |
| Uninstall Ubuntu distro        |  `wls --unregister Ubuntu` |

Docs: [WSL Basic Commands](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)

## Previous Version
**Date**: `Jan 10, 2023`  
**About**: VM built using Vagrant and VirtualBox. Parse forensic triage images collected with CyLR, using MFTECmd and CDQR. Ingest into Splunk.  
**Reference**: https://github.com/alexzorila/artifact-cruncher.
