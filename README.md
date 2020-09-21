```
   ________  _________  ____     _______________(_)___  / /______
  / ___/ _ \/ ___/ __ \/ __ \   / ___/ ___/ ___/ / __ \/ __/ ___/
 / /  /  __/ /__/ /_/ / / / /  (__  ) /__/ /  / / /_/ / /_(__  ) 
/_/   \___/\___/\____/_/ /_/  /____/\___/_/  /_/ .___/\__/____/  
                                              /_/                
```
![v0.0.2-alpha](https://img.shields.io/badge/version-0.0.2--alpha-green)
                                                                                                     
# Personal recon framework for bug bounty hunting
Collection of reconnaissance scripts does the following to domains in a target:
- Enumerate subdomains using [Sublist3r](https://github.com/aboul3la/Sublist3r)
- Scan using Subdomainizer [Subdominizer](https://github.com/nsonaniya2010/SubDomainizer)
- Probe subdomains using [httpx](https://github.com/projectdiscovery/httpx)
- Check cloud buckets using [cloud_enum](https://github.com/initstring/cloud_enum) and [S3Scanner](https://github.com/OWASP/Amass)
- Scan webpages using [nuclei](https://github.com/projectdiscovery/nuclei)
- Take screenshots using [Aquatone](https://github.com/michenriksen/aquatone)
- Asset discovery using [hakrawler](https://github.com/hakluke/hakrawler) 
 - Notify for new URLs or JS files discovered via Slack

## Directory framework

This is the way I organize my recon loot. I just feed this directory to the tools here.

```
targets
├── target1
│   ├── screenshots/
│   ├── urls.txt
│   ├── js.txt
│   ├── githound.txt
│   ├── cloud_enum.txt
│   ├── httpx.txt
│   ├── domains.txt
│   └── subdomains.txt
├── target2
│   ├── screenshots/
│   ├── urls.txt
│   ├── js.txt
│   ├── cloud_enum.txt
│   ├── httpx.txt
│   ├── domains.txt
│   └── subdomains.txt
│
.
.
```

## Setup

```
git clone https://github.com/tedmdelacruz/recon-scripts.git
cd recon-scripts

# Initialize a vars.sh from vars.sh.example
cp vars.sh.example vars.sh
vim vars.sh
```

# Usage:
1. Clone this repository
2. Copy `vars.sh.example` into `vars.sh` and amend its values accordingly

```bash
cd recon_scripts
# Note: target_dir requires a domains.txt file
$ scans/recon_all.sh path/to/targets_dir
$ scans/recon.sh path/to/targets_dir/target
```

3. Or source `vars.sh` and `functions.sh` to access individual functions like so:
```
$ source vars.sh; source functions.sh;
$ enumerate_subdomains path/to/target
$ probe_subdomains path/to/target
$ cloud_bucket_enum path/to/target
$ nuclei_scan path/to/target
$ take_screenshots path/to/target
```

## TODO
- Monitor interesting files and web pages for changes
- Check for repository leaks using githound
- Show GitHub dorking links
