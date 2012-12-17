# RHEVM Backup Windows

Procesos y scripts de backup de la base de datos RHEVM 2.2 bajo Windows 2008 Server R2.

## Ubicación de los backups
C:\Program Files(x86)\Microsoft SQL Server\MSSQL.1\MSSQL\Backup

## Scripts
### backup_vdc_db.sql
Ubicacion: C:\Program Files(x86)\RedHat\RHEVManager\Service\dbScripts\backup_vdc_db.sql
```sql
BEGIN
   BACKUP DATABASE [$(dbname)] TO DISK = N'$(backup_file)' WITH NOFORMAT, NOINIT,  NAME = N'$(dbname)-Full Database Backup', SKIP, NOREWIND, NOUNLOAD,  STATS = 10 
END
```

### backup_vdc_db.cmd
Ubicacion: C:\Program Files(x86)\RedHat\RHEVManager\Service\dbScripts\backup_vdc_db.sql
```text
@echo off

if "%1%" == "-h" goto Syntax
if "%1%" == "--help" goto Syntax

SET backup_file=%1%

SET sqlServer=%2%
if "%2%" == "" set sqlServer=.\sqlexpress

SET dbname=%3%
if "%3%" == "" set dbname=rhevm

for %%v in (%0) do set MyPath=%%~dpv
pushd "%MyPath%"

SET user=%4%
if "%4%" == "" set user=sa

SET pass=%5%
if "%5%" == "" set pass=RHEVMadmin2009!

echo server - %sqlServer%
echo dbname - %dbname%

echo backing up database ...
sqlcmd  -S %sqlServer% -U %user% -P %pass% -d %dbname% -i backup_vdc_db.sql
echo Done.

popd

goto:EOF

:Syntax
echo backup_vdc_db.cmd file_name [server] [dbname] [user] [pass]
echo   file_name - the backup file name
echo     server - the sql server to access (default = .\sqlexpress)
echo     dbname - the database name to access/create (default = rhevm)
echo	 user - the database administrator user name
echo	 pass - the database administrator password
goto:EOF
```

## Scheduling
Las tareas de backup de base de datos RHEVM 2.2 bajo Windows están programadas, mediante el Windows Task Scheduler, para correr diariamiente a las 00.20 hs.  
