---
name: "COSMA CPU Compute Lab"
status: in-service
category: testbed
focus: open
focus-detail: "Prototyping and testing"
grouping: "COSMA"
funders:
- STFC
- Hypertec
- Dell
- AMD
partitions:
- name: Intel Sierra Forest
  nodes: 1
  accelerator: "Intel Xeon 6756E"
  accelerator-count: 2
  manufacturer: "Dell"
  scheduler: "Direct SSH"
- name: AMD Turin
  nodes: 1
  accelerator: "AMD EPYC 9755"
  accelerator-count: 2
  manufacturer: "Dell"
  scheduler: "Direct SSH"
- name: AMD Milan-X
  nodes: 1
  accelerator: "AMD EPYC 7773X"
  manufacturer: Dell
  scheduler: "Direct SSH"
- name: AMD Genoa
  nodes: 2
  accelerator: "AMD EPYC 9654"
  accelerator-count: 2
  manufacturer: "Dell"
  scheduler: "Slurm"
- name: Intel Cascade Lake
  nodes: 1
  accelerator: "Intel Xeon Platinum 8260L"
  accelerator-count: 2
  manufacturer: Intel
  scheduler: "Slurm"
interconnects: []
reference: https://cosma.readthedocs.io/en/latest/cpucomputelab.html
---

## COSMA CPU Compute Lab

COSMA (The Compute Optimised System for Modelling and Analysis) is a High Performance Computing facility hosted at Durham University, operated by the Institute for Computational Cosmology on behalf of DiRAC.

The following CPU testbed nodes are available within COSMA:

| Node/Partition | RAM | CPU | Access | Account | Limitations |
|------|-----|-----|--------|-------|-------|
| mad11 | 1TB | 256 cores (Intel Sierra Forest) | Direct SSH/Slurm | do025 | &mdash; |
| mad12 | 1.5TB | 256 cores (AMD EPYC Turin) | Direct SSH/Slurm | do025 | &mdash; |
| mad06 | 1TB | 128 cores (AMD EPYC Milan-X) | Direct SSH/Slurm | do025 | &mdash; |
| cosma5 | 1.5TB | 256 cores (AMD EPYC Bergamo) | Slurm | hpcicc | ICC collaborators only |
| cosma8-shm3 | 0.75TB | 192 cores (AMD EPYC Milan) | Slurm | do009 | &mdash; |
| cosma8-ska | 4TB | 56 cores (Intel Ice Lake) | Slurm | do011 | SKA users only |
| cosma8-milan | 1TB | 128 cores (AMD EPYC Milan) | Slurm | Any | DiRAC RAC users only |
| cosma8-rome | 1TB | 128 cores (AMD EPYC Rome) | Slurm | Any | DiRAC RAC users only |
| cosma7-shm2 | 5.8TB | 48 cores (Intel Cascade Lake) | Slurm | do025 | &mdash; |

Nodes marked "Direct SSH/Slurm"
have a hybrid setup where they can be used interactively during the day (8am&ndash;7pm),
but accept Slurm workloads overnight.

### Documentation

- <https://cosma.readthedocs.io/en/latest/cpucomputelab.html>
- <https://cosma.readthedocs.io/en/latest/cosma.html>

### Gaining access

Access requires a COSMA account, obtained via the [DiRAC SAFE portal](https://safe.epcc.ed.ac.uk/dirac/).

1. Create a SAFE account with an institutional email.
2. Upload an SSH public key on SAFE. If you do not have one, generate with `ssh-keygen -t ed25519`.
3. Request a login account. This requires selecting a project, either:
  - A specific project listed in the table above
  - The project code `do025` for nodes not tied to specific project 
  - A DiRAC project code for a given allocation (provided by a supervisor),
    if you are already associated with a DiRAC project
4. **Wait** for the account to be approved by the project manager. Keep an eye on your email!
5. Connect to COSMA via SSH: `ssh username@login8.cosma.dur.ac.uk` (Note: On first login you will be asked to change the password provided in your email)

Visit <https://cosma.readthedocs.io/en/latest/account.html> for more details.
Contact cosma-support@durham.ac.uk for any questions.

### Usage

For nodes marked "Direct SSH" above,
connect directly via SSH from a login node; for example, `ssh mad11`.
Otherwise,
jobs are submitted via Slurm.

### Restrictions

On nodes where there is no scheduler,
you are requested to monitor node usage
(for example,
using the `w` command)
to avoid trampling over other people's benchmarking work.
