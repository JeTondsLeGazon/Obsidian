Running SharpHound/BloodHound is always a good idea on the target. It helps use see the paths that can be taken from our user to domain admins / domain controllers.

The results can be taken back locally on our machine and analysed.

#### Installation
Check [here](https://bloodhound.readthedocs.io/en/latest/installation/linux.html) for installation. Note you will need neo4j as a database to power it (`sudo apt-get install neo4j`, then run it, log in and **change the password**)

Simply run `./BloodHound --no-sandbox` to connect to the UI after you started `neo4j`.

#### Usage
To use bloodhound you first need to collect data from the target, which can be done with **sharphound** (uses windows API) or **bloodhound-python** on linux (available with ``sudo apt install bloodhound.py``)

Example:
```bash
bloodhound-python -ns <IP> -dc <domain-name> -u <username> -p <password> -c all
```
This will generate json files that can be drag-drop into bloodhound GUI