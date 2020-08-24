---
title: Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen
description: Hier erfahren Sie, wie Sie einen Dienstprinzipalnamen bei Active Directory registrieren. Diese Registrierung ist erforderlich, wenn Sie die Kerberos-Authentifizierung mit SQL Server verwenden.
ms.prod: sql
ms.prod_service: high-availability
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 08/12/2020
ms.openlocfilehash: 242b87166035c8ffc0e01272b5910f85a66620e7
ms.sourcegitcommit: bf5acef60627f77883249bcec4c502b0205300a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88200684"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a>Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 Damit die Kerberos-Authentifizierung mit SQL Server verwendet werden kann, müssen die beiden folgenden Bedingungen erfüllt sein:  

- Der Client- und der Servercomputer müssen Teil der gleichen Windows-Domäne sein oder sich in vertrauenswürdigen Domänen befinden.  

- Ein Dienstprinzipalname (Service Principal Name, SPN) muss in Active Directory registriert sein. Dieser Dienst nimmt die Rolle des Schlüsselverteilungscenters (KDC) in einer Windows-Domäne an. Der Dienstprinzipalname wird nach der Registrierung dem Windows-Konto zugeordnet, mit dem der SQL Server-Instanzdienst gestartet wurde. Wenn die Registrierung des Dienstprinzipalnamens fehlerhaft oder gar nicht erfolgt, kann die Windows-Sicherheitsebene das Konto nicht ermitteln, das dem Dienstprinzipalname zugewiesen ist. Die Kerberos-Authentifizierung wird dann nicht verwendet.

    > [!NOTE]  
    >  Wenn der Server den Dienstprinzipalnamen nicht automatisch registrieren kann, muss der Name manuell registriert werden. Siehe [Manuelle SPN-Registrierung](#Manual).  

Durch Abfragen der dynamischen Verwaltungssicht sys.dm_exec_connections können Sie überprüfen, ob eine Verbindung Kerberos verwendet. Führen Sie die folgende Abfrage aus, und überprüfen Sie den Wert der Spalte auth_scheme, der "KERBEROS" lautet, wenn Kerberos aktiviert ist.

```sql
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;
```

> [!TIP]
>  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for SQL Server** ist ein Diagnosetool zur Behebung Kerberos-bezogener Probleme mit der Verbindung mit SQL Server. Weitere Informationen finden Sie unter [Microsoft Kerberos-Konfigurations-Manager für SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  

##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> Die Rolle des Dienstprinzipalnamens bei der Authentifizierung  

Wenn eine Anwendung eine Verbindung öffnet und die Windows-Authentifizierung verwendet, übergibt der SQL Server Native Client den SQL Server-Computernamen, -Instanznamen und optional einen Dienstprinzipalnamen. Wenn die Verbindung einen Dienstprinzipalnamen übergibt, wird dieser ohne Änderungen verwendet.  

Wenn die Verbindung keinen Dienstprinzipalnamen übergibt, wird ein Standard-Dienstprinzipalname basierend auf verwendetem Protokoll, Servernamen und Instanzennamen erstellt.  

In beiden Szenarien wird der Dienstprinzipalname an das Schlüsselverteilungscenter gesendet, um ein Sicherheitstoken zum Authentifizieren der Verbindung abzurufen. Wenn kein Sicherheitstoken abgerufen werden kann, verwendet die Authentifizierung NTLM.  

Ein Dienstprinzipalname (SPN, Service Principal Name) ist der Name, über den ein Client eine Instanz eines Diensts eindeutig identifiziert. Der Kerberos-Authentifizierungsdienst kann einen SPN zum Authentifizieren eines Diensts verwenden. Wenn ein Client eine Verbindung zu einem Dienst herstellen möchte, sucht er eine Instanz des Diensts, verfasst einen SPN für diese Instanz, stellt eine Verbindung zum Dienst her und übergibt den SPN zur Authentifizierung an den Dienst.  
  
> [!NOTE]  
>  Die Informationen in diesem Thema gelten auch für SQL Server-Konfigurationen, die Clustering verwenden.  
  
Die bevorzugte Methode für die Authentifizierung von Benutzern bei SQL Server ist Windows-Authentifizierung. Clients, die Windows-Authentifizierung verwenden, werden mit NTLM oder Kerberos authentifiziert. In einer Active Directory-Umgebung wird immer zuerst Kerberos-Authentifizierung ausgeführt. Die Kerberos-Authentifizierung ist für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Clients, die Named Pipes verwenden, nicht verfügbar.  

##  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen

Beim Starten des Datenbank-Engine-Diensts versucht dieser, den Dienstprinzipalnamen zu registrieren. Nehmen wir einmal an, das Konto, das SQL Server startet, verfügt nicht über die Berechtigung, einen Dienstprinzipalnamen in Active Directory Domain Services zu registrieren. In diesem Fall tritt bei diesem Aufruf ein Fehler auf, und sowohl im Ereignisprotokoll der Anwendung als auch im SQL Server-Fehlerprotokoll wird eine Warnmeldung protokolliert. Um den Dienstprinzipalnamen zu registrieren, muss die Datenbank-Engine in einem integrierten Konto ausgeführt werden, z. B. einem lokalen System (nicht empfohlen), NETWORK SERVICE oder einem Konto mit Berechtigung zum Registrieren eines Dienstprinzipalnamens. Sie können einen Dienstprinzipalnamen mit einem Domänenadministratorkonto registrieren, dies wird in einer Produktionsumgebung jedoch nicht empfohlen. Unter Windows 7 oder Windows Server 2008 R2 können Sie SQL Server mit einem virtuellen Konto oder einem verwalteten Dienstkonto (Managed Service Account, MSA) ausführen. Sowohl virtuelle Konten als auch MSAs können einen SPN registrieren. Wird SQL Server nicht in einem dieser Konten ausgeführt, wird der Dienstprinzipalname beim Starten nicht registriert und muss vom Domänenadministrator manuell registriert werden.

> [!NOTE]  
>  Wenn die Windows-Domäne für die Ausführung auf einer niedrigeren Ebene als der Windows Server 2008 R2-Funktionsebene konfiguriert ist, verfügt das verwaltete Dienstkonto nicht über die notwendigen Berechtigungen zum Registrieren der Dienstprinzipalnamens für den [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Dienst. Ist die Kerberos-Authentifizierung erforderlich, muss der Domänenadministrator die Dienstprinzipalnamen für SQL Server manuell im verwalteten Dienstkonto registrieren.

Weitere Informationen sind unter [Implementieren von eingeschränkter Kerberos-Delegierung mit SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)verfügbar  

##  <a name="spn-formats"></a><a name="Formats"></a> SPN-Formate

In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]wurde das SPN-Format geändert, um die Kerberos-Authentifizierung unter TCP/IP, Named Pipes und Shared Memory zu unterstützen. Die folgenden SPN-Formate für benannte und Standardinstanzen werden unterstützt.  
  
**Benannte Instanz**  
  
-   **MSSQLSvc/\<FQDN>:[\<port> | \<instancename>]** , wobei:  
  
    -   **MSSQLSvc** der Dienst ist, der registriert wird.  
  
    -   **\<FQDN>** der vollqualifizierte Domänenname des Servers ist.  
  
    -   **\<port>** die TCP-Portnummer ist.  
  
    -   **\<instancename>** der Name der SQL Server-Instanz ist.  
  
**Standardinstanz**  
  
-   **MSSQLSvc/\<FQDN>:\<port>**  | **MSSQLSvc/\<FQDN>** , wobei:  
  
    -   **MSSQLSvc** der Dienst ist, der registriert wird.  
  
    -   **\<FQDN>** der vollqualifizierte Domänenname des Servers ist.  
  
    -   **\<port>** die TCP-Portnummer ist.  
  
    > [!NOTE]
    > Beim neuen Format für den Dienstprinzipalnamen ist keine Portnummer erforderlich. Somit können Server mit mehreren Ports oder Protokolle ohne Portnummern die Kerberos-Authentifizierung verwenden.  
   
|SPN-Format|BESCHREIBUNG|  
|-|-|  
|MSSQLSvc/\<FQDN>:\<port>|Der vom Anbieter erstellte Standard-SPN, wenn TCP verwendet wird. \<port> ist eine TCP-Portnummer.|  
|MSSQLSvc/\<FQDN>:|Der vom Anbieter erstellte Standard-SPN für eine Standardinstanz, wenn ein anderes Protokoll als TCP verwendet wird. \<FQDN> ist ein vollqualifizierter Domänenname.|  
|MSSQLSvc/\<FQDN>:\<instancename>|Der vom Anbieter erstellte Standard-SPN für eine benannte Instanz, wenn ein anderes Protokoll als TCP verwendet wird. \<instancename> ist der Name einer SQL Server-Instanz.|  

> [!NOTE]  
> Bei TCP/IP-Verbindungen, bei denen der TCP-Port im Dienstprinzipalnamen enthalten ist, muss SQL Server das TCP-Protokoll für einen Benutzer aktivieren, um mithilfe der Kerberos-Authentifizierung eine Verbindung herzustellen. 

##  <a name="automatic-spn-registration"></a><a name="Auto"></a> Automatische SPN-Registrierung  

Beim Starten einer Instanz der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] versucht SQL Server, den Dienstprinzipalnamen für den SQL Server-Dienst zu registrieren. Wenn die Instanz beendet wird, versucht SQL Server, die Registrierung des Dienstprinzipalnames wieder aufzuheben. Bei TCP/IP-Verbindungen wird der Dienstprinzipalname im folgenden Format registriert: *MSSQLSvc/\<FQDN>* : *\<tcpport>* . Sowohl benannte Instanzen als auch die Standardinstanz werden als *MSSQLSvc* registriert, und zur Unterscheidung der Instanzen wird der Wert *\<tcpport>* verwendet.  
  
Bei anderen Verbindungen, die Kerberos unterstützen, wird der SPN im Format *MSSQLSvc/\<FQDN>* / *\<instancename>* für eine benannte Instanz registriert. Die Standardinstanz wird im folgenden Format registriert: *MSSQLSvc/\<FQDN>* .  

Die Registrierung bzw. die Aufhebung der Registrierung eines SPN muss möglicherweise manuell durchgeführt werden, wenn der Dienst nicht über die Berechtigungen für diese Aktionen verfügt.  

##  <a name="manual-spn-registration"></a><a name="Manual"></a> Manuelle SPN-Registrierung  

Um den SPN manuell zu registrieren, muss der Administrator das Setspn.exe-Tool verwenden, das mit den Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] -Supporttools geliefert wird. Weitere Informationen finden Sie im KB-Artikel [Supporttools in Windows Server 2003 Service Pack 1](https://support.microsoft.com/kb/892777) .  

Setspn.exe ist ein Befehlszeilentool, mit dem Sie die SPN-Verzeichniseigenschaft lesen, ändern und löschen können. Mit diesem Tool können Sie auch die aktuellen SPN anzeigen, die Standard-SPN des Kontos zurücksetzen und zusätzliche SPN hinzufügen oder löschen.  

Das folgende Beispiel veranschaulicht die Syntax, die zur manuellen Registrierung eines SPN für eine TCP/IP-Verbindung unter Verwendung eines Domänenbenutzerkontos zu verwenden ist:  

```
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 redmond\accountname  
```

> [!NOTE]
> Wenn bereits ein SPN vorhanden ist, muss er gelöscht werden, um ihn erneut registrieren zu können. Verwenden Sie dafür den `setspn` -Befehl und den `-D` -Schalter. In den folgenden Beispielen wird veranschaulicht, wie Sie einen neuen instanzbasierten SPN manuell registrieren können. Verwenden Sie für eine Standardinstanz mit einem Domänenbenutzerkonto Folgendes:  

```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com redmond\accountname  
```  
  
Verwenden Sie für eine benannte Instanz Folgendes:  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename redmond\accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> Clientverbindungen  

Clienttreiber unterstützen vom Benutzer angegebene SPN. Wenn jedoch kein Dienstprinzipalname angegeben wurde, wird anhand des Clientverbindungstyps automatisch ein solcher erstellt. Bei einer TCP-Verbindung wird ein SPN im Format *MSSQLSvc*/*FQDN*:[*port*] sowohl für benannte als auch für Standardinstanzen verwendet.  
  
Für Verbindungen mit Named Pipes und gemeinsam genutzten Speicherbereichen wird für eine benannte Instanz ein SPN im Format *MSSQLSvc/\<FQDN>:\<instancename>* und für die Standardinstanz *MSSQLSvc/\<FQDN>* verwendet.  
  
**Verwenden eines Dienstkontos als SPN**  
  
Dienstkonten können als SPN verwendet werden. Sie werden durch das Verbindungsattribut für die Kerberos-Authentifizierung angegeben und liegen in den folgenden Formaten vor:  
  
- **Benutzername\@Domäne** oder **Domäne\Benutzername** für ein Domänenbenutzerkonto  

- **Computer$\@Domäne** oder **Host\FQDN** für ein Computerdomänenkonto, wie etwa Lokales System oder NETWORK SERVICES.  

Um die Authentifizierungsmethode einer Verbindung zu bestimmen, führen Sie die folgende Abfrage aus.  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
``` 

##  <a name="authentication-defaults"></a><a name="Defaults"></a> Authentifizierungsstandardwerte  

In der folgenden Tabelle werden die Authentifizierungsstandardwerte beschrieben, die auf Grundlage von SPN-Registrierungsszenarios verwendet werden.  
  
|Szenario|Authentifizierungsmethode|  
|--------------|---------------------------|  
|Der SPN ist dem richtigen Domänenkonto, virtuellen Konto, MSA oder integrierten Konto zugeordnet. Beispiel: Lokales System oder NETWORK SERVICE.|Lokale Verbindungen verwenden NTLM, Remoteverbindungen verwenden Kerberos.|  
|Der SPN entspricht dem richtigen Domänenkonto, virtuellen Konto, MSA oder integrierten Konto.|Lokale Verbindungen verwenden NTLM, Remoteverbindungen verwenden Kerberos.|  
|Der SPN ist einem falschen Domänenkonto, virtuellen Konto, MSA oder integrierten Konto zugeordnet.|Die Authentifizierung schlägt fehl.|  
|Bei der SPN-Suche tritt ein Fehler auf, oder der SPN ist nicht dem richtigen Domänenkonto, virtuellen Konto, MSA oder integrierten Konto zugeordnet bzw. entspricht nicht dem richtigen Domänenkonto, virtuellen Konto, MSA oder integrierten Konto.|Lokale Verbindungen und Remoteverbindungen verwenden NTLM.|  

> [!NOTE]
> "Richtig" bedeutet in diesem Fall, dass es sich bei dem Konto, das dem registrierten SPN zugeordnet ist, um das Konto handelt, unter dem der SQL Server-Dienst ausgeführt wird.  

##  <a name="comments"></a><a name="Comments"></a> Kommentare  

Die dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC) verwendet einen Dienstprinzipalnamen, der auf dem Instanznamen basiert. Die Kerberos-Authentifizierung kann mit einer DAC verwendet werden, wenn dieser SPN erfolgreich registriert wurde. Alternativ kann ein Benutzer den Kontonamen als SPN festlegen.

Wenn die SPN-Registrierung beim Starten nicht erfolgt, wird dieser Fehler im Fehlerprotokoll von SQL Server aufgezeichnet, und der Startvorgang wird fortgesetzt.  

Wenn beim Herunterfahren keine Aufhebung der SPN-Registrierung erfolgt, wird dieser Fehler im Fehlerprotokoll von SQL Server aufgezeichnet, und das Herunterfahren wird fortgesetzt.  

## <a name="see-also"></a>Siehe auch  
- [Unterstützung von Dienstprinzipalnamen &#40;SPN&#41; in Clientverbindungen](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)
- [Dienstprinzipalnamen (SPN) in Clientverbindungen (OLE DB)](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)
- [Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC)](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)
- [SQL Server Native Client-Funktionen](../../relational-databases/native-client/features/sql-server-native-client-features.md)
- [Behandeln von Problemen mit der Kerberos-Authentifizierung in einer Reporting Services-Umgebung](https://technet.microsoft.com/library/ff679930.aspx)
