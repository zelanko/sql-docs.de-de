---
title: Installieren von PolyBase unter Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase, installation
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e30cded830401c589c62d1e6301d5be78720c07f
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806750"
---
# <a name="install-polybase-on-windows"></a>Installieren von PolyBase unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Besuchen Sie [SQL Server Evaluierungsversionen](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016), um eine Testversion von SQL Server zu installieren. 
   
## <a name="prerequisites"></a>Voraussetzungen  
   
- Eine 64-Bit-Evaluierungs-Edition von SQL Server  
   
- Microsoft .NET Framework 4.5.  

- Oracle Java SE Runtime Environment (JRE). Version 7 (ab 7.51) und 8 werden unterstützt ([JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) oder [Server JRE](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html)). Wechseln Sie zu [Java SE-Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html). Das Installationsprogramm schlägt fehl, wenn JRE nicht vorhanden ist. JRE9 und JRE10 werden nicht unterstützt.

- Mindestens erforderlicher Arbeitsspeicher: 4 GB  
   
- Mindestfestplattenspeicher: 2 GB  
- **Empfohlen:** Mindestens 16 GB RAM
   
- TCP/IP muss für Polybase aktiviert sein, damit es ordnungsgemäß funktioniert. TCP/IP ist standardmäßig in allen Editionen von SQL Server aktiviert. Davon ausgenommen sind nur die Editionen Developer und Express SQL Server. Damit Polybase auch in den Developer- und Express-Edition ordnungsgemäß funktionieren kann, müssen Sie die TCP/IP-Konnektivität aktivieren (Informationen dazu finden Sie unter [Enable or Disable a Server Network Protocol (Aktivieren und -Deaktivieren eines Server-Netzwerkprotokolls](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)).

- MSVC++ 2012 

**Hinweis**  

PolyBase kann nur auf einer SQL Server-Instanz pro Computer installiert werden.

> **Wichtig**
>
> Wenn Sie die Berechnungsfunktionalität Pushdown für Hadoop verwenden möchten, müssen Sie sicherstellen, dass der Hadoop-Zielcluster über den Kernkomponenten von HDFS (Hadoop Distributed File System), Yarn/MapReduce mit einem aktivierten Jobhistory-Server verfügt. PolyBase reicht die Pushdown-Abfrage über MapReduce ein und ruft den Status aus dem JobHistory-Server ab. Die Abfrage wird ohne eine der Komponenten fehlschlagen.
  
## <a name="single-node-or-polybase-scaleout-group"></a>Einzelknoten oder PolyBase-Gruppe mit horizontaler Skalierung

Planen Sie vor der Installation von PolyBase auf Ihren SQL Server-Instanzen, ob Sie eine Einzelknoteninstallation oder eine [PolyBase-Erweiterungsgruppe](../../relational-databases/polybase/polybase-scale-out-groups.md) möchten.

Bei einer PolyBase-Erweiterungsgruppe müssen Sie sicherstellen, dass folgende Anforderungen erfüllt sind:

- Alle Computer befinden sich in derselben Domäne.
- Sie verwenden während der PolyBase-Installation dasselbe Dienstkonto und Kennwort.
- Ihre SQL Server-Instanzen können über das Netzwerk miteinander kommunizieren.
- Alle SQL Server-Instanzen weisen die gleiche Version von SQL Server auf.

Sobald PolyBase entweder eigenständig oder in einer Erweiterungsgruppe installiert wurde, können Sie diese Entscheidung nicht mehr rückgängig machen. Sie müssen die Funktion deinstallieren und wieder neu installieren, um diese Einstellung zu ändern.

## <a name="install-using-the-installation-wizard"></a>Installieren mithilfe des Installations-Assistenten  
   
1. Führen Sie das Setupprogramm von SQL Server aus.   
   
2. Klicken Sie auf **Installation**, dann auf **New Standalone SQL Server installation or add features**(Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen).  
   
3. Wählen Sie auf der Seite „Funktionsauswahl“ **PolyBase Query Service for External Data**(PolyBase-Abfragedienst für externe Daten).  

 ![PolyBase-Dienste](../../relational-databases/polybase/media/install-wizard.png "PolyBase services")  
   
4. Konfigurieren Sie auf der Seite „Serverkonfiguration“ die Dienste **SQL Server-PolyBase-Engine** und SQL Server-PolyBase-Datenverschiebungsdienst so, dass beide unter demselben Domänenkonto ausgeführt werden.  
   
 > **WICHTIG!** 
>
>In einer PolyBase-Erweiterungsgruppe müssen die Dienste PolyBase-Engine und PolyBase-Datenverschiebung auf allen Knoten unter dem gleichen Domänenkonto ausgeführt werden. Weitere Informationen finden Sie unter [PolyBase scale-out groups](#Enable) (PolyBase-Erweiterungsgruppen).
   
5. Wählen Sie auf der **PolyBase-Konfigurationsseite**eine der beiden Optionen aus. Weitere Informationen finden Sie unter [PolyBase scale-out groups](../../relational-databases/polybase/polybase-scale-out-groups.md) (PolyBase-Erweiterungsgruppen).  
   
   - Verwenden Sie die SQL Server-Instanz als eigenständige, für PolyBase aktivierte Instanz.  
   
     Wählen Sie diese Option aus, um die SQL Server-Instanz als eigenständigen Hauptknoten zu verwenden.  
   
   - Verwenden Sie die SQL Server-Instanz als Teil der PolyBase-Erweiterungsgruppe.  Durch die Auswahl dieser Option wird die Firewall für eingehende Verbindungen mit der SQL Server-Datenbank-Engine, SQL Server-PolyBase-Engine und dem SQL Server-PolyBase-Datenverschiebungsdienst sowie dem SQL-Browser geöffnet. Die Firewall wird für eingehende Verbindungen von anderen Knoten in einer PolyBase-Erweiterungsgruppe geöffnet.  
   
     Durch Auswahl dieser Option werden auch Firewallverbindungen des Microsoft Distributed Transaction Coordinator (MSDTC)-Diensts zugelassen und die MSDTC-Registrierungseinstellungen geändert.  
   
6. Geben Sie auf der Seite **PolyBase-Konfiguration**den Portbereich mit mindestens sechs Ports an. SQL Server-Setup wird die ersten sechs verfügbaren Ports aus diesem Bereich zuweisen.  

  > **WICHTIG!**
  >
  > Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).


##  <a name="installing"></a> Installieren mithilfe einer Eingabeaufforderung  

Verwenden Sie die Werte in dieser Tabelle, um Installationsskripte zu erstellen. Die beiden Dienste **SQL Server PolyBase-Engine** und **SQL Server PolyBase-Datenverschiebung** müssen unter demselben Konto ausgeführt werden. In einer PolyBase-Gruppe mit horizontaler Skalierung müssen PolyBase-Dienste auf allen Knoten unter demselben Domänenkonto ausgeführt werden.  
   
<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017"

|SQL Server-Komponente|Parameter und Werte|und Beschreibung|  
|--------------------------|--------------------------|-----------------|  
|SQL Server-Setupsteuerung|**Erforderlich**<br /><br /> /FEATURES=PolyBase|Wählt die PolyBase-Funktion aus.|  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCACCOUNT|Gibt das Konto für den Engine-Dienst an. Der Standardwert ist **NT Authority\NETWORK SERVICE**.|  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCPASSWORD|Gibt das Kennwort für das Engine-Dienstkonto an.|  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCSTARTUPTYPE|Gibt den Startmodus für den PolyBase-Engine-Dienst an: Automatisch (Standard), Deaktiviert und Manuell.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCACCOUNT|Gibt das Konto für den Datenverschiebungsdienst an. Der Standardwert ist **NT Authority\NETWORK SERVICE**.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCPASSWORD|Gibt das Kennwort für das Datenverschiebungskonto an.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCSTARTUPTYPE|Gibt den Startmodus für den Datenverschiebungsdienst an: Automatisch (Standard), Deaktiviert und Manuell.|  
|PolyBase|**Optional**<br /><br /> /PBSCALEOUT|Gibt an, ob die SQL Server-Instanz als Teil einer PolyBase-Erweiterungsgruppe aus Computeknoten verwendet wird. <br />Unterstützte Werte: **True**, **False**|  
|PolyBase|**Optional**<br /><br /> /PBPORTRANGE|Gibt einen Portbereich für PolyBase-Dienste mit mindestens sechs Ports an. Beispiel:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

|SQL Server-Komponente|Parameter und Werte|und Beschreibung|  
|--------------------------|--------------------------|-----------------|  
|SQL Server-Setupsteuerung|**Erforderlich**<br /><br /> /FEATURES=PolyBaseCore, PolyBaseJava, PolyBase | **PolyBaseCore** installiert Unterstützung für alle PolyBase-Features mit Ausnahme der Hadoop-Konnektivität. **PolyBaseJava** aktiviert die Hadoop-Konnektivität. **PolyBase** installiert beides. |  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCACCOUNT|Gibt das Konto für den Engine-Dienst an. Der Standardwert ist **NT Authority\NETWORK SERVICE**.|  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCPASSWORD|Gibt das Kennwort für das Engine-Dienstkonto an.|  
|SQL Server PolyBase-Engine|**Optional**<br /><br /> /PBENGSVCSTARTUPTYPE|Gibt den Startmodus für den PolyBase-Engine-Dienst an: Automatisch (Standard), Deaktiviert und Manuell.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCACCOUNT|Gibt das Konto für den Datenverschiebungsdienst an. Der Standardwert ist **NT Authority\NETWORK SERVICE**.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCPASSWORD|Gibt das Kennwort für das Datenverschiebungskonto an.|  
|SQL Server PolyBase-Datenverschiebungsdienst|**Optional**<br /><br /> /PBDMSSVCSTARTUPTYPE|Gibt den Startmodus für den Datenverschiebungsdienst an: Automatisch (Standard), Deaktiviert und Manuell.|  
|PolyBase|**Optional**<br /><br /> /PBSCALEOUT|Gibt an, ob die SQL Server-Instanz als Teil einer PolyBase-Erweiterungsgruppe aus Computeknoten verwendet wird. <br />Unterstützte Werte: **True**, **False**|  
|PolyBase|**Optional**<br /><br /> /PBPORTRANGE|Gibt einen Portbereich für PolyBase-Dienste mit mindestens sechs Ports an. Beispiel:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end

Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).



**Beispiel**

Hier wird ein Beispiel-Setupskript gezeigt.  

```cmd
   
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
   
```  

## <a id="enable"></a> Aktivieren von PolyBase

Nachdem Sie die Installation abgeschlossen haben, muss Polybase aktiviert werden, um auf die Funktionen zugreifen zu können. Zum Herstellen einer Verbindung mit SQL Server 2019 CTP 2.0 müssen Sie PolyBase nach der Installation mithilfe des folgenden Transact-SQL-Befehls aktivieren:


```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [ WITH OVERRIDE ]  ;
```
Anschließend muss die Instanz **neu gestartet werden**. 


## <a name="post-installation-notes"></a>Hinweise zur Installationsnachbereitung  

PolyBase installiert drei Benutzerdatenbanken, und zwar DWConfiguration, DWDiagnostics und DWQueue.   Diese sind für die Verwendung von PolyBase gedacht und dürfen nicht verändert oder gelöscht werden.  
   
### <a id="confirminstall"></a> Bestätigen der Installation  

Führen Sie den folgenden Befehl aus. Wenn PolyBase installiert ist, wird 1 zurückgegeben, andernfalls 0.  

```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  

### <a name="firewall-rules"></a>Firewallregeln  

SQL Server PolyBase-Setup erstellt die folgenden Firewallregeln auf dem Computer.  
   
- SQL Server PolyBase – Datenbank-Engine – \<SQL Server-Instanzname&gt; (eingehendes TCP)  
   
- SQL Server PolyBase – PolyBase-Dienste – \<SQL Server-Instanzname> (eingehendes TCP)  

- SQL Server-PolyBase – SQL-Browser – (eingehendes UDP)  
   
Wenn Sie auswählen, dass die SQL Server-Instanz als Teil einer PolyBase-Erweiterungsgruppe verwendet werden soll, werden diese Regeln bei der Installation aktiviert, und die Firewall wird für eingehende Verbindungen mit den der SQL Server-Datenbank-Engine, der SQL Server-PolyBase-Engine und dem SQL Server-PolyBase-Datenverschiebungsdienst sowie dem SQL-Browser geöffnet. Wenn der Firewalldienst des Computers während der Installation jedoch nicht ausgeführt wird, kann das SQL Server-Setup diese Regeln nicht aktivieren. In diesem Fall müssen Sie den Firewalldienst des Computers starten und diese Regeln nach der Installation aktivieren.  
   
#### <a name="to-enable-the-firewall-rules"></a>So aktivieren Sie die Firewallregeln  

- Öffnen Sie die **Systemsteuerung**.  

- Klicken Sie auf **System und Sicherheit**, und klicken Sie auf **Windows-Firewall**.  
   
- Klicken Sie auf **Erweiterte Einstellungen**und dann auf **Eingehende Regeln**.  
   
- Klicken Sie mit der rechten Maustaste auf die deaktivierte Regel, und klicken Sie dann **Regel aktivieren**.  
   
### <a name="polybase-service-accounts"></a>PolyBase-Dienstkonten

Deinstallieren Sie die PolyBase-Funktion, und installieren Sie sie erneut, um die Dienstkonten für die PolyBase-Engine und die PolyBase-Datenverschiebungsdienste zu ändern.

## <a name="next-steps"></a>Nächste Schritte  

Siehe [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).
