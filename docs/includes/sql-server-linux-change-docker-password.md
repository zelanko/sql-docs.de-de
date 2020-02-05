Das **SA**-Konto ist ein Systemadministrator für die SQL Server-Instanz, der während des Setups erstellt wird. Nach dem Erstellen Ihres SQL Server-Containers können Sie die von Ihnen festgelegte Umgebungsvariable `MSSQL_SA_PASSWORD` ermitteln, indem Sie `echo $MSSQL_SA_PASSWORD` im Container ausführen. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort:

1. Wählen Sie ein sicheres Kennwort für den SA-Benutzer aus.

1. Verwenden Sie `docker exec` zum Ausführen des Hilfsprogramms **sqlcmd**, um das Kennwort über eine Transact-SQL-Anweisung zu ändern. Ersetzen Sie `<YourStrong!Passw0rd>` und `<YourNewStrong!Passw0rd>` durch Ihre eigenen Kennwortwerte:

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourStrong!Passw0rd>' \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
