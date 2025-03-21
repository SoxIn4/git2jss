# git2jss
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/d9d618c32e93436ea67102fd3d3f5b21)](https://www.codacy.com/app/adam-furbee/git2jss?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=BadStreff/git2jss&amp;utm_campaign=Badge_Grade)

A fast asynchronous python library for syncing your scripts in git with your JSS easily. This allows admins to keep their script in a version control system for easy updating rather than googling and copy-pasting from resources that they find online.

## Getting Started
1.  Fork the Project
2.  Install [Python version 3.11](https://www.python.org/downloads/). (this is because of the aiohttp requirements, if you already have a python 3.6 or higher with aiohttp installed, you can probably use that)
3.  Run `python3.11 -m pip install -r requirements.txt` to install required modules
4.  Run `python3.11 ./tools/download.py --url https://your.jss.url:8443 --username api_user` to download all scripts and extension attributes to the repository
5.  Run `python3.11 ./sync.py --url https://your.jss.url:8443 --username api_user` to sync all scripts back to your JSS

Optional flags for `download.py`:

-   `--password` for CI/CD (Will prompt for password if not set)
-   `--do_not_verify_ssl` to skip ssl verification
-   `--overwrite` to overwrite all scripts and extension attributes

Optional flags for `sync.py`:

-   `--password` for CI/CD (Will prompt for password if not set)
-   `--do_not_verify_ssl` to skip ssl verification
-   `--overwrite` to overwrite all scripts and extension attributes
-   `--limit` to limit max connections (default=25)
-   `--timeout` to limit max connections (default=60)
-   `--verbose` to add additional logging
-   `--update_all` to upload all resources in `./extension_attributes` and `./scripts`
-   `--jenkins` to write a Jenkins file:`jenkins.properties` with `$scripts` and `$eas` and compare `$GIT_PREVIOUS_COMMIT` with `$GIT_COMMIT`

### Prerequisites
git2jss requires [Python 3.11](https://www.python.org/downloads/) and the python modules listed in `requirements.txt`

## Deployment
The project can be run ad-hoc with the example listed above, but ideally you setup webhooks and integrate into a CI/CD pipeline so each time a push is made to the repo your scripts are re-uploaded to the JSS.

## Contributing
PR's are always welcome!
