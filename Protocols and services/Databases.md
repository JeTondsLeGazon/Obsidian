
## Oracle TNS

TNS: Transparent Network Substrate
Protocol for Oracle databases

Listens on port 1521 usually

Can support IPv6, TLS, etc.

Oracle DBSNMP service has default password `dbsnmp`

Configuration file for target database server in tnsnames.ora

Oracle manages database with SID: each database has unique identifier

### Attack tool
- ODAT: Oracle Database Attacking Tool
- nmap/hydra/ODAT: to brute force SID (oracle-sid-brute for nse)
- sqlplus: to connect

Table `sys.user$` contains password hashes
Can upload shell if webserver

### Error recovery
`sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory` -> see [here](https://stackoverflow.com/questions/27717312/sqlplus-error-while-loading-shared-libraries-libsqlplus-so-cannot-open-shared)
