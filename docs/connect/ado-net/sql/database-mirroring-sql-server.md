---
title: Datenbankspiegelung in SQL Server
description: Beschreibt die Funktionsweise der Datenbankspiegelung.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 38481625645a7d2a70b7d3212cdf9ef765ca9c1f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928868"
---
# <a name="database-mirroring-in-sql-server"></a>Datenbankspiegelung in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Mithilfe der Datenbankspiegelung in SQL Server können Sie eine Kopie, oder auch Spiegelbild, einer SQL Server-Datenbank auf einem Standbyserver speichern. Die Spiegelung stellt sicher, dass jederzeit zwei getrennte Kopien der Daten vorhanden sind, was Hochverfügbarkeit und vollständige Datenredundanz gewährleistet. Der Microsoft-SqlClient-Anbieter für SQL Server stellt implizite Unterstützung für die Datenbankspiegelung bereit. Das Schreiben von Code oder Ausführen anderer Aktionen nach dem Konfigurieren für eine SQL Server-Datenbank ist daher seitens der Entwickler nicht erforderlich. Zusätzlich unterstützt das <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekt einen expliziten Verbindungsmodus, der es erlaubt, den Namen eines Failoverpartnerservers in <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A> anzugeben.  
  
Die folgende vereinfachte Ereignissequenz erfolgt für ein <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekt, das eine für Spiegelung konfigurierte Datenbank als Ziel hat:  
  
1. Die Clientanwendung verbindet sich erfolgreich mit der Prinzipaldatenbank, und der Server sendet den Namen des Partnerservers zurück, der dann auf dem Client zwischengespeichert wird.  
  
2. Wenn der Server mit der Prinzipaldatenbank ausfällt oder die Verbindung unterbrochen wird, gehen Verbindung und Transaktionsstatus verloren. Die Clientanwendung versucht, wieder eine Verbindung mit der Prinzipaldatenbank herzustellen, und schlägt fehl.  
  
3. Die Clientanwendung versucht dann auf transparente Weise, eine Verbindung mit der Spiegeldatenbank auf dem Partnerserver herzustellen. Bei Erfolg wird die Verbindung zur Spiegeldatenbank umgeleitet, die dann zur neuen Prinzipaldatenbank wird.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Angeben des Failoverpartners in der Verbindungszeichenfolge  
Wenn Sie den Namen eines Failoverpartnerservers in der Verbindungszeichenfolge angeben, versucht der Client transparent eine Verbindung mit dem Failoverpartner herzustellen, sofern die Prinzipaldatenbank beim ersten Verbindungsversuch der Clientanwendung nicht verfügbar ist.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
Wenn Sie den Namen des Failoverpartnerservers weglassen und die Hauptdatenbank beim ersten Verbindungsversuch der Clientanwendung nicht verfügbar ist, wird eine <xref:Microsoft.Data.SqlClient.SqlException> ausgelöst.  
  
Wenn <xref:Microsoft.Data.SqlClient.SqlConnection> erfolgreich geöffnet wird, wird der Failoverpartnername vom Server zurückgegeben und ersetzt alle in der Verbindungszeichenfolge angegebenen Werte.  
  
> [!NOTE]
>  In Szenarien mit Datenbankspiegelung müssen Sie den Ausgangskatalog oder Datenbanknamen explizit in der Verbindungszeichenfolge angeben. Wenn der Client Failover-Informationen zu einer Verbindung empfängt, für die nicht explizit ein Anfangskatalog oder eine Anfangsdatenbank angegeben wurde, werden die Failover-Informationen nicht zwischengespeichert und die Anwendung versucht auch nicht, bei einem Ausfall des Prinzipalservers einen Failover durchzuführen. Wenn eine Verbindungszeichenfolge einen Wert für den Failoverpartner, aber keinen Wert für den Ausgangskatalog oder die Datenbank hat, wird eine `InvalidArgumentException` ausgelöst.  
  
## <a name="retrieving-the-current-server-name"></a>Abrufen des aktuellen Servernamens  
Bei einem Failover können Sie den Namen des Servers abrufen, mit dem die aktuelle Verbindung tatsächlich besteht, indem Sie die <xref:Microsoft.Data.SqlClient.SqlConnection.DataSource%2A>-Eigenschaft eines <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts verwenden. Das folgende Codefragment ruft den Namen des aktiven Servers ab, wobei angenommen wird, dass die Verbindungsvariable auf eine geöffnete <xref:Microsoft.Data.SqlClient.SqlConnection> verweist.  
  
Wenn ein Failover-Ereignis eintritt und die Verbindung zum Spiegelserver wechselt, wird die **DataSource**-Eigenschaft aktualisiert, um den Namen des Spiegelservers wiederzugeben.  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient-Spiegelungsverhalten  
Der Client versucht stets, eine Verbindung mit dem aktuellen Prinzipalserver herzustellen. Bei Misserfolg wird der Failoverpartner versucht. Wenn die Spiegeldatenbank bereits auf die Prinzipalrolle auf dem Partnerserver umgestellt wurde, ist die Verbindung erfolgreich. Die neue Zuordnung zwischen Prinzipal und Spiegel wird an den Client gesendet und für die Lebensdauer des Aufrufs von <xref:System.AppDomain> zwischengespeichert. Sie wird nicht im dauerhaften Speicher gespeichert und ist für nachfolgende Verbindungen in einer anderen **AppDomain** oder einem anderen Prozess nicht verfügbar. Sie ist allerdings für nachfolgende Verbindungen innerhalb derselben **AppDomain** verfügbar. Beachten Sie, dass eine andere **AppDomain** oder ein anderer Prozess, die oder der auf demselben oder einem anderen Computer ausgeführt wird, immer über einen eigenen Pool von Verbindungen verfügt, die nicht zurückgesetzt werden. Wenn in diesem Fall die primäre Datenbank ausfällt, wird jeder Prozess bzw. jede **AppDomain** einmal mit einem Fehler ausgeführt, und der Pool wird automatisch gelöscht.  
  
> [!NOTE]
>  Die Unterstützung der Spiegelung auf dem Server wird datenbankbezogen konfiguriert. Wenn Datenbearbeitungsvorgänge auf andere, nicht im Prinzipal-/Spiegelsatz enthaltene Datenbanken angewendet werden, entweder durch Verwendung mehrteiliger Namen oder durch Änderung der aktuellen Datenbank, werden die Änderungen an diesen anderen Datenbanken bei einem Fehler nicht weitergegeben. Wenn Daten in einer nicht gespiegelten Datenbank geändert werden, wird kein Fehler ausgegeben. Der Entwickler muss die möglichen Auswirkungen solcher Vorgänge einschätzen.  
  
## <a name="next-steps"></a>Nächste Schritte
### <a name="database-mirroring-resources"></a>Ressourcen für die Datenbankspiegelung  
Die Begriffsdokumentation und Informationen zum Konfigurieren, Bereitstellen und Verwalten der Spiegelung finden Sie in den folgenden Ressourcen in der SQL Server-Dokumentation.  
  
|Resource|BESCHREIBUNG|  
|--------------|-----------------|  
|[Datenbankspiegelung](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)|Beschreibt, wie Spiegelung in SQL Server eingerichtet und konfiguriert wird.|  
