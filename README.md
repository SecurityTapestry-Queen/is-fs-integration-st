# InsightIDR + FreshService Helpdesk Integration Kit

## V2.0.7 - as of 6/17/23

## Status

[![CodeQL](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/github-code-scanning/codeql/badge.svg?branch=main)](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/github-code-scanning/codeql)

[![Pylint](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/pylint.yml/badge.svg)](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/pylint.yml)

[![Investigations](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/Investigations.yml/badge.svg)](https://github.com/SecurityTapestry-Queen/is-fs-integration-st/actions/workflows/Investigations.yml)

### Licensed under GPL v3.0

### Notice

> This is for use by the Security Tapestry Threat Hunting Team, and is written for compatibility with **InsightIDR** as an Alerts Platform, and **FreshService Helpdesk**.

## Important Files

1. [config.json](config.json) - Includes Configuration data for each client
    
    - 'enabled' - Denotes whether or not to activate alerts for this client.
    - 'api' - API Key symbol per client.
    - 'email' - Mail Email Address Alerts are to be directed to per client.
    - 'ccs' - Email Addresses to CC upon Investigation creation per client.
    - 'time' - Time in UTC of last bot check-in per client.

2. [functioncheck.py](functioncheck.py) - Used to check that environment currently is running Python 3.10+ and contains the 'FS_API' secret, otherwise exits.

3. [InsightFunctions.py](InsightFunctions.py) - Contains all Functions called by [Investigations.py](Investigations.py)

4. [Investigations.py](Investigations.py) - Main script to be run, contains statement:
```python
from InsightFunctions import *
```

5. [Investigations.yml](.github/workflows/Investigations.yml) - Main Workflow file for Github Actions, calls all API Keys, [functioncheck.py](functioncheck.py), and [Investigations.py](Investigations.py) every 15 minutes via cronjob.
