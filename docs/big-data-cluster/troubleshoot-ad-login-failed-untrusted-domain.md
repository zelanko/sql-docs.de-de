---
title: 'Fehler beim Anmelden im AD-Modus: nicht vertrauenswürdige Domäne'
titleSuffix: SQL Server Big Data Cluster
description: 'Korrektur des Verhaltens: Bei der Authentifizierung von Clients tritt ein Fehler auf, wenn die DNS-Einträge der Endpunkte als CNAME-Einträge konfiguriert sind, die auf einen Aliasnamen verweisen.'
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 05/01/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 669d8f050c3dd86d733c33741eb6fc846245aff2
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891040"
---
# <a name="symptom-ad-mode-login-fails---untrusted-domain-big-data-clusters"></a>Symptom: Fehler beim Anmelden im AD-Modus: nicht vertrauenswürdige Domäne (Big Data-Cluster)

Bei einem SQL Server-Big Data-Cluster (BDC) im Active Directory-Modus schlagen Verbindungsversuche möglicherweise fehl, und der folgende Fehler wird zurückgegeben:

`Login failed. The login is from an untrusted domain and cannot be used with Integrated authentication.`

Dies kann passieren, wenn Sie DNS-Einträge als CNAME-Einträge konfiguriert haben, die auf einen Aliasnamen eines Reverseproxys verweisen, der den Datenverkehr auf Kubernetes-Knoten verteilt.

## <a name="root-cause"></a>Grundursache

Folgendes passiert, wenn die Endpunkte mit CNAME-Einträgen als DNS-Einträge konfiguriert sind, die auf einen Aliasnamen eines Reverseproxys verweisen, der den Datenverkehr auf Kubernetes-Knoten verteilt:

- Der Kerberos-Authentifizierungsprozess sucht nach einem Dienstprinzipalnamen (Service Principal Name, SPN), der mit dem CNAME-Eintrag übereinstimmt, und nicht nach dem richtigen SPN, der vom BDC in Active Directory registriert wurde.
- Bei der Authentifizierung tritt ein Fehler auf. 

## <a name="confirm-root-cause"></a>Überprüfen der Grundursache

Wenn bei der Authentifizierung ein Fehler aufgetreten ist, überprüfen Sie den Kerberos-Ticketcache. 

Verwenden Sie den Befehl `klist`, um den Ticketcache zu überprüfen. 

Suchen Sie nach einem Ticket mit einem SPN, der dem des Endpunkts entspricht, mit dem Sie eine Verbindung herstellen wollten.

Das gesuchte Ticket ist nicht vorhanden.

Im folgenden Beispiel handelt es sich bei dem DNS-Eintrag für den Masterendpunkt `bdc-sql` um einen CNAME-Eintrag mit dem Reverseproxy `ServerReverseProxy`.

```PowerShell
Resolve-DnsName bdc-sql
```

Der folgende Abschnitt zeigt die Ergebnisse für den obigen Befehl.

```
Name                           Type   TTL   Section    NameHost
----                           ----   ---   -------    --------
bdc-sql.mydomain.com           CNAME  3600  Answer     ReverseProxyServer.mydomain.com

Name       : ReverseProxyServer.mydomain.com
QueryType  : A
TTL        : 3600
Section    : Answer
IP4Address : 193.168.5.10
```

>[!NOTE]
>Der folgende Abschnitt bezieht sich auf [`tshark`](https://www.wireshark.org/docs/man-pages/tshark.html). Bei `tshark` handelt es sich um ein Befehlszeilen-Hilfsprogramm, das als Teil des Hilfsprogramms [Wireshark](https://www.wireshark.org/docs/) für Netzwerkablaufverfolgung installiert ist.

Verwenden Sie `tshark`, um den von Active Directory angeforderten SPN anzuzeigen. Mit dem folgenden Befehl wird bei der Netzwerkablaufverfolgung nur die Kerberos-Protokollkommunikation erfasst, und nur Meldungen mit `krb-error (30)` werden angezeigt. Diese Meldungen sollten SPN-Anforderungsnachrichten enthalten, bei denen ein Fehler aufgetreten ist.

```bash
tshark -Y "kerberos && kerberos.msg_type == 30" -T fields -e kerberos.error_code -e kerberos.SNameString
```

Versuchen Sie, über eine andere Befehlsshell eine Verbindung mit dem Masterpod herzustellen:

```bash
klist purge

sqlcmd -S bdc-sql.mydomain.com,31433 -E
```

Sehen Sie sich die folgende Beispielausgabe an.

```bash
klist purge

Current LogonId is 0:0xf6b58
        Deleting all tickets:
        Ticket(s) purged!

sqlcmd -S bdc-sql.mydomain.com,31433 -E
sqlcmd: Error: Microsoft ODBC Driver 17 for SQL Server : Login failed. The login is from an untrusted domain and cannot be used with Integrated authentication.
```

Überprüfen Sie die `tshark`-Ausgabe. 

```bash
Capturing on 'Ethernet 3'
25      krbtgt,RLAZURE.COM
7       MSSQLSvc,ReverseProxyServer.mydomain.com:31433
2 packets captured
```

Beachten Sie, dass der Client den `SPN MSSQLSvc,ReverseProxyServer.mydomain.com:31433` anfordert, der nicht existiert. Der Verbindungsversuch schlägt schließlich mit dem Fehler 7 fehl. Fehler 7 bedeutet `KRB5KDC_ERR_S_PRINCIPAL_UNKNOWN Server not found in Kerberos database` (KRB5KDC_ERR_S_PRINCIPAL_UNKNOWN: Der Server wurde in der Kerberos-Datenbank nicht gefunden.).

Bei richtiger Konfiguration fordert der Client den vom BDC registrierten SPN an. Bei diesem Beispiel wäre der richtige SPN `MSSQLSvc,bdc-sql.mydomain.com:31433`.

>[!NOTE]
>Fehler 25 bedeutet `KDC_ERR_PREAUTH_REQUIRED`. Eine zusätzliche Vorauthentifizierung ist erforderlich. Diesen Fehler können Sie ruhig ignorieren. `KDC_ERR_PREAUTH_REQUIRED` wird bei der anfänglichen Kerberos-AD-Anforderung zurückgegeben. Der Windows-Kerberos-Client erfasst in dieser ersten Anforderung standardmäßig keine Vorauthentifizierungsinformationen.

Führen Sie `setspn -L mssql-master` aus, um die Liste der vom BDC für den Masterendpunkt registrierten SPNs anzuzeigen. 

Sehen Sie sich die folgende Beispielausgabe an:

```bash
Registered ServicePrincipalNames for CN=mssql-master,OU=bdc,DC=mydomain,DC=com:
        MSSQLSvc/bdc-sqlread.mydomain.com:31436
        MSSQLSvc/-sqlread:31436
        MSSQLSvc/bdc-sqlread.mydomain.com
        MSSQLSvc/bdc-sqlread
        MSSQLSvc/bdc-sql.mydomain.com:31433
        MSSQLSvc/bdc-sql:31433
        MSSQLSvc/bdc-sql.mydomain.com
        MSSQLSvc/bdc-sql
        MSSQLSvc/master-p-svc.mydomain.com:1533
        MSSQLSvc/master-p-svc:1533
        MSSQLSvc/master-p-svc.mydomain.com:1433
        MSSQLSvc/master-p-svc:1433
        MSSQLSvc/master-p-svc.mydomain.com
        MSSQLSvc/master-p-svc
        MSSQLSvc/master-svc.mydomain.com:1533
        MSSQLSvc/master-svc:1533
        MSSQLSvc/master-svc.mydomain.com:1433
        MSSQLSvc/master-svc:1433
        MSSQLSvc/master-svc.mydomain.com
        MSSQLSvc/master-svc
```

In den obigen Ergebnissen sollte die Reverseproxyadresse nicht registriert sein.

## <a name="resolve"></a>Beheben

In diesem Abschnitt werden zwei Möglichkeiten gezeigt, dieses Problem zu beheben. Führen Sie in Ihrem Client `ipconfig -flushdns` und `klist purge` aus, nachdem Sie die entsprechenden Änderungen vorgenommen haben. Versuchen Sie dann noch mal, eine Verbindung herzustellen.

### <a name="option-1"></a>Option 1:

Entfernen Sie im DNS alle CNAME-Einträge für BDC-Endpunkte, und ersetzen Sie sie durch mehrere `A`-Einträge, die auf jeden Kubernetes-Knoten oder jeden Kubernetes-Master verweisen, wenn Sie über mehr als einen Master verfügen.

>[!TIP]
>Das nachstehende Skript verwendet PowerShell. Weitere Informationen finden Sie unter [Installieren von PowerShell unter Linux](/powershell/scripting/install/installing-powershell-core-on-linux).

Sie können die DNS-Einträge der Endpunkte mithilfe des folgenden PowerShell-Skripts aktualisieren. Führen Sie das Skript auf allen Computern aus, die mit derselben Domäne verbunden sind:

```powershell
#Specify the DNS server, example contoso.local
$Domain_DNS_name=mydomain.com'

#DNS records for bdc endpoints
$Controller_DNS_name = 'bdc-control'
$Managment_proxy_DNS_name= 'bdc-proxy'
$Master_Primary_DNS_name = 'bdc-sql'
$Master_Secondary_DNS_name = 'bdc-sqlread'
$Gateway_DNS_name = 'bdc-gateway'
$AppProxy_DNS_name = 'bdc-appproxy'

#Performing Endpoint DNS records Checks..

#Build array of endpoints 
$BdcEndpointsDns = New-Object System.Collections.ArrayList

[void]$BdcEndpointsDns.Add($Controller_DNS_name)
[void]$BdcEndpointsDns.Add($Managment_proxy_DNS_name)
[void]$BdcEndpointsDns.Add($Master_Primary_DNS_name)
[void]$BdcEndpointsDns.Add($Master_Secondary_DNS_name)
[void]$BdcEndpointsDns.Add($Gateway_DNS_name)
[void]$BdcEndpointsDns.Add($AppProxy_DNS_name)

#Build arrary for results 
$BdcEndpointsDns_Result = New-Object System.Collections.ArrayList

foreach ($DnsName in $BdcEndpointsDns) {
    try {
        $endpoint_DNS_record = Resolve-DnsName $DnsName -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop 
        foreach ($ip in $endpoint_DNS_record.IPAddress) {
            [void]$BdcEndpointsDns_Result.Add("OK - $DnsName is an A record with an IP $ip")
        }
    }
    catch {
        [void]$BdcEndpointsDns_Result.Add("MisConfiguration - $DnsName is not an A record or does not exists")
    }  
}

#show the results 
$BdcEndpointsDns_Result
```

### <a name="option-2"></a>Option 2:

Alternativ können Sie das Problem umgehen, indem Sie den CNAME-Eintrag so ändern, dass er auf die IP-Adresse des Reverseproxys statt auf dessen Namen verweist.

## <a name="confirm-resolution"></a>Überprüfen der Behebung

Wenn Sie eine der oben dargestellten Problemlösungsstrategien angewendet haben, überprüfen Sie, ob der Fehler behoben wurde, indem Sie eine Verbindung mit dem Big Data-Cluster über Active Directory herstellen.

## <a name="next-steps"></a>Nächste Schritte

[Überprüfen der Reverse-DNS-Einträge (PTR-Eintrag) für den Domänencontroller](active-directory-deploy.md#verify-reverse-dns-entry-for-domain-controller)
