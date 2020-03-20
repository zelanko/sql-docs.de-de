---
title: Problembehandlung bei der Bereitstellung im Active Directory-Modus
titleSuffix: SQL Server Big Data Cluster
description: In diesem Artikel erfahren Sie, wie Sie Probleme mit der Bereitstellung eines SQL Server-Big Data-Clusters in einer Active Directory-Domäne behandeln.
author: rl-msft
ms.author: rafidl
ms.reviewer: mikeray
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d887eadd021641241516a1478c6ac13e0d0bdec
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79191211"
---
# <a name="troubleshoot-sql-server-big-data-cluster-active-directory-mode-deployment"></a>Behandeln von Problemen mit der Bereitstellung von SQL Server-Big Data-Clustern im Active Directory-Modus

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel erfahren Sie, wie Sie Probleme mit der Bereitstellung eines SQL Server-Big Data-Clusters im Active Directory-Modus behandeln.

## <a name="check-deployment-progress"></a>Überprüfen des Bereitstellungsstatus

Die Bereitstellung kann einige Minuten dauern. Wenn der Cluster nicht innerhalb von 15 Minuten bereit ist, überprüfen Sie die Controllerprotokolle für weitere Informationen.

Überprüfen Sie die Pods, während der Cluster bereitgestellt wird.

```console
kubectl get pods -n mssql-cluster
```

Überprüfen Sie, ob die Liste der zurückgegebenen Pods Folgendes enthält:

- `compute-`$
- `data-`
- `storage-`

Wenn die Pods „compute“, „data“ und „storage“ nicht erstellt werden, überprüfen Sie die Protokolle, um herauszufinden, warum sie nicht erstellt wurden.

## <a name="check-logs"></a>Überprüfen der Protokolle

Überprüfen Sie die folgenden Protokolle, um zu ermitteln, wieso die Bereitstellung beendet wurde, ohne die Pods „compute“, „data“ und „storage“ zu erstellen: 

- Überprüfen Sie `controller.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\control-<suffix>\controller\controller\<date>\controller.log`). Suchen Sie nach dem folgenden Eintrag:

  `WARN | StatefulSet master is not ready with 0 ready pods and 3 unready pods `

- Überprüfen Sie `master-0` `provisioner.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\master-0\mssql-server\provisioner\provisioner.log`).

  ```
  ERROR | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
    Traceback (most recent call last):
      File "/opt/provisioner/bin/scripts/provisioningpool.py", line 214, in executeNonQueries
        connection.execute_non_query(command)
      File "src/_mssql.pyx", line 1033, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1061, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1634, in _mssql.check_and_raise
      File "src/_mssql.pyx", line 1683, in _mssql.maybe_raise_MSSQLDatabaseException
    _mssql.MSSQLDatabaseException: (15401, b"Windows NT user or group '<domain>.<top-level-domain>\\<domain-group>' not found. Check the name again.DB-Lib error message 20018, severity 16:\nGeneral SQL Server error: Check messages from the SQL Server\n")
  WARNING | [3/3] Provisioning exception occurred during provisioning step: ProvisioningMasterPool.
  WARNING | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
  WARNING | Retrying.
  ```

  Im obigen Beispiel schlägt das Erstellen eines Anmeldenamens für den Domänenbenutzer bei der Bereitstellung fehl, weil die Domänengruppe als domänenlokal eingestuft ist. Verwenden Sie Gruppen in den Bereichen „global“ oder „domain universal“. Informationen zu den Anforderungen von AD-Gruppenbereichen finden Sie unter [Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] im Active Directory-Modus](deploy-active-directory.md).

## <a name="check-the-scope-of-domain-groups"></a>Überprüfen des Bereichs der Domänengruppen

Überprüfen Sie den Bereich der Domänengruppe (<`domain-group`>). Verwenden Sie den Befehl [get-adgroup](/powershell/module/addsadministration/get-adgroup/).

Wenn der Gruppenbereich `<domain-group>` domänenlokal (`DomainLocal`) ist, schlägt die Bereitstellung fehl. 

Das folgende PowerShell-Skript überprüft den Bereich von zwei AD-Gruppen namens `bdcadmins` und `bdcusers`. Ersetzen Sie die Namen durch die Namen Ihrer Gruppen. 

```powershell
#Administrators and users AD groups
$Cluster_admins_group='bdcadmins'
$Cluster_users_group='bdcusers'

#Performing AD Group Checks...

#AD admin group Check
$ClusterAdminGroupScope_Result = New-Object System.Collections.ArrayList
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_admins_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterAdminGroupScope_Result.Add("Misconfiguration - $Cluster_admins_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal") 
    }
    else {
        [void]$ClusterAdminGroupScope_Result.Add("OK - $Cluster_admins_group Group scope is $GroupScope")
    }
}
catch {
    [void]$ClusterAdminGroupScope_Result.Add("Error - " + $_.exception.message)
}
#Ad users group check
$ClusterUsersGroupScope_Result = New-Object System.Collections.ArrayList
$GroupScope = ''
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_users_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterUsersGroupScope_Result.Add("Misconfiguration - $Cluster_users_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal")
    } 
    else 
    { [void]$ClusterUsersGroupScope_Result.Add("OK - $Cluster_users_group Group scope is $GroupScope") }
}
catch {
    [void]$ClusterUsersGroupScope_Result.Add("Error - " + $_.exception.message)
}

#Display the results
$ClusterUsersGroupScope_Result
```

## <a name="check-security-support-container"></a>Überprüfen des Containers „security-support“ 

Überprüfen Sie die Protokolle des Containers „security-support“.

Mit dem folgenden Befehl werden die security-support-Protokolle in einem Cluster unter den Namespace `mssql-cluster` erfasst.

```console
azdata bdc debug copy-logs -n mssql-cluster -c security-support
```

Extrahieren Sie die Protokolle, und suchen Sie nach `\mssql-cluster\control-<identifier>\controller\control-rts5t-controller-stdout.log`.

Suchen Sie im Protokoll nach den folgenden Einträgen:

```
ERROR    | Failed to create AD user account 'cntrl-controller'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=cntrl-controller,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'ldap-user'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=ldap-user,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'nginx-mgmtproxy'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=nginx-mgmtproxy,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform.
```

Diese Einträge können vorkommen, wenn der Reverse-DNS-Eintrag (PTR-Eintrag) im DNS-Server des Domänencontrollers fehlt.

## <a name="verify-reverse-lookup-ptr-record"></a>Überprüfen von Reverse-Lookup (PTR-Eintrag)
    
Führen Sie das folgende PowerShell-Skript aus, um zu überprüfen, ob Sie der Reverse-DNS-Eintrag (PTR-Eintrag) konfiguriert ist.

```powershell
#Domain Controller FQDN 'DCserver01.contoso.local'
$Domain_controller_FQDN = 'DCserver01.contoso.local'

#Performing Domain Controller DNS record, reverse PTR Checks...
$DcControllerDnsPtr_Result = New-Object System.Collections.ArrayList
try {
    $Domain_controller_DNS_Record = Resolve-DnsName $Domain_controller_FQDN -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop
    foreach ($ip in $Domain_controller_DNS_Record.IPAddress) {
        #resolving hostname by IP address to make sure we have reverse PTR record 
        if ((Resolve-DnsName $ip).NameHost -eq $Domain_controller_FQDN) {
            [void]$DcControllerDnsPtr_Result.add("OK - $Domain_controller_FQDN has an A record with an IP $ip, Reverse PTR record is in place") 
        }
        else {
            [void]$DcControllerDnsPtr_Result.add("Missing - $Domain_controller_FQDN has an A record with an IP $ip, But no reverse PTR record was found for the host")
        }
    }
}
catch {
    [void]$DcControllerDnsPtr_Result.add("Error - " + $_.exception.message)
}

#show the results 
$DcControllerDnsPtr_Result
```

[Überprüfen der Reverse-DNS-Einträge (PTR-Eintrag) für den Domänencontroller](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller)