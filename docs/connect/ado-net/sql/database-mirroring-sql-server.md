---
title: Datenbankspiegelung in SQL Server
description: Beschreibt die Daten Bank Spiegelungs Funktion.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 1c78f52f376ff6c333b952b8d013e17eefce45ea
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452274"
---
# <a name="database-mirroring-in-sql-server"></a>Datenbankspiegelung in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Mithilfe der Datenbankspiegelung in SQL Server können Sie eine Kopie, oder auch Spiegelbild, einer SQL Server-Datenbank auf einem Standbyserver speichern. Durch die Spiegelung wird sichergestellt, dass immer zwei separate Kopien der Daten vorhanden sind, was Hochverfügbarkeit und vollständige Datenredundanz gewährleistet. Der Microsoft-SqlClient-Anbieter für SQL Server stellt implizite Unterstützung für die Datenbankspiegelung bereit. Das Schreiben von Code oder Ausführen anderer Aktionen nach dem Konfigurieren für eine SQL Server-Datenbank ist daher seitens der Entwickler nicht erforderlich. Außerdem unterstützt das <xref:Microsoft.Data.SqlClient.SqlConnection> Objekt einen expliziten Verbindungs Modus, mit dem der Name eines Failover-Partner Servers im <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A> bereitgestellt werden kann.  
  
Die folgende vereinfachte Ereignis Sequenz tritt für ein <xref:Microsoft.Data.SqlClient.SqlConnection> Objekt auf, das eine für die Spiegelung konfigurierte Datenbank als Ziel hat:  
  
1. Die Client Anwendung stellt erfolgreich eine Verbindung mit der Prinzipal Datenbank her, und der Server sendet den Namen des Partner Servers zurück, der dann auf dem Client zwischengespeichert wird.  
  
2. Wenn der Server, der die Prinzipal Datenbank enthält, ausfällt oder die Konnektivität unterbrochen wird, gehen die Verbindungs-und der Transaktionsstatus verloren. Die Client Anwendung versucht, eine Verbindung mit der Prinzipal Datenbank wiederherzustellen, und schlägt fehl.  
  
3. Die Client Anwendung versucht dann transparent, eine Verbindung mit der Spiegel Datenbank auf dem Partner Server herzustellen. Wenn dies erfolgreich ist, wird die Verbindung an die Spiegel Datenbank umgeleitet, die dann zur neuen Prinzipal Datenbank wird.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Angeben des Failoverpartners in der Verbindungs Zeichenfolge  
Wenn Sie den Namen eines Failover-Partner Servers in der Verbindungs Zeichenfolge angeben, versucht der Client transparent, eine Verbindung mit dem Failoverpartner herzustellen, wenn die Prinzipal Datenbank nicht verfügbar ist, wenn die Client Anwendung zum ersten Mal eine Verbindung herstellt.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
Wenn Sie den Namen des Failover-Partner Servers weglassen und die Prinzipal Datenbank nicht verfügbar ist, wenn die Client Anwendung zum ersten Mal eine Verbindung herstellt, wird eine <xref:Microsoft.Data.SqlClient.SqlException> ausgelöst.  
  
Wenn ein <xref:Microsoft.Data.SqlClient.SqlConnection> erfolgreich geöffnet wird, wird der Name des Failoverpartners vom Server zurückgegeben und ersetzt alle Werte, die in der Verbindungs Zeichenfolge angegeben sind.  
  
> [!NOTE]
>  Sie müssen den ursprünglichen Katalog-oder Datenbanknamen in der Verbindungs Zeichenfolge für Datenbankspiegelungs-Szenarios explizit angeben. Wenn der Client Failover-Informationen zu einer Verbindung empfängt, für die nicht explizit ein Anfangskatalog oder eine Anfangsdatenbank angegeben wurde, werden die Failover-Informationen nicht zwischengespeichert und die Anwendung versucht auch nicht, bei einem Ausfall des Prinzipalservers einen Failover durchzuführen. Wenn eine Verbindungs Zeichenfolge einen Wert für den Failoverpartner, aber keinen Wert für den Anfangs Katalog oder die Anfangs Datenbank aufweist, wird eine `InvalidArgumentException` ausgelöst.  
  
## <a name="retrieving-the-current-server-name"></a>Abrufen des aktuellen Server namens  
Bei einem Failover können Sie den Namen des Servers, mit dem die aktuelle Verbindung tatsächlich verbunden ist, mit der <xref:Microsoft.Data.SqlClient.SqlConnection.DataSource%2A>-Eigenschaft eines <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts abrufen. Das folgende Code Fragment Ruft den Namen des aktiven Servers ab, wobei angenommen wird, dass die Verbindungs Variable auf eine geöffnete <xref:Microsoft.Data.SqlClient.SqlConnection> verweist.  
  
Wenn ein Failover-Ereignis eintritt und die Verbindung zum Spiegelserver wechselt, wird die **DataSource**-Eigenschaft aktualisiert, um den Namen des Spiegelservers wiederzugeben.  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient-Spiegelungs Verhalten  
Der Client versucht immer, eine Verbindung mit dem aktuellen Prinzipal Server herzustellen. Wenn ein Fehler auftritt, wird der Failoverpartner versucht. Wenn die Spiegel Datenbank bereits zur Prinzipal Rolle auf dem Partner Server gewechselt ist, wird die Verbindung erfolgreich hergestellt, und die neue Zuordnung des Prinzipal Spiegels wird an den Client gesendet und für die Lebensdauer der aufrufenden <xref:System.AppDomain> zwischengespeichert. Sie wird nicht im dauerhaften Speicher gespeichert und ist für nachfolgende Verbindungen in einer anderen **AppDomain** oder einem anderen Prozess nicht verfügbar. Sie ist allerdings für nachfolgende Verbindungen innerhalb derselben **AppDomain** verfügbar. Beachten Sie, dass eine andere **AppDomain** oder ein anderer Prozess, die oder der auf demselben oder einem anderen Computer ausgeführt wird, immer über einen eigenen Pool von Verbindungen verfügt, die nicht zurückgesetzt werden. Wenn in diesem Fall die primäre Datenbank ausfällt, wird jeder Prozess bzw. jede **AppDomain** einmal mit einem Fehler ausgeführt, und der Pool wird automatisch gelöscht.  
  
> [!NOTE]
>  Die Spiegelungs Unterstützung auf dem Server wird pro Datenbank konfiguriert. Wenn Daten Bearbeitungsvorgänge für andere Datenbanken ausgeführt werden, die nicht im Prinzipal-/Spiegelsatz enthalten sind, entweder mithilfe von mehrteiligen Namen oder durch Ändern der aktuellen Datenbank, werden die Änderungen an diesen anderen Datenbanken im Fall eines Fehlers nicht weitergegeben. Wenn Daten in einer nicht gespiegelten Datenbank geändert werden, wird kein Fehler generiert. Der Entwickler muss die möglichen Auswirkungen dieser Vorgänge auswerten.  
  
## <a name="next-steps"></a>Nächste Schritte
### <a name="database-mirroring-resources"></a>Ressourcen für die Datenbankspiegelung  
Die Begriffsdokumentation und Informationen zum Konfigurieren, Bereitstellen und Verwalten der Spiegelung finden Sie in den folgenden Ressourcen in der SQL Server-Dokumentation.  
  
|Ressource|und Beschreibung|  
|--------------|-----------------|  
|[Datenbankspiegelung](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)|Beschreibt, wie Spiegelung in SQL Server eingerichtet und konfiguriert wird.|  
