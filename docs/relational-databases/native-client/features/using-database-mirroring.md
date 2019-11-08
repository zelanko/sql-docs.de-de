---
title: Verwenden der Daten Bank Spiegelung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- SQL Server Native Client, database mirroring
- data access [SQL Server Native Client], database mirroring
- database mirroring [SQL Server], connecting clients to
- SQLNCLI, database mirroring
- SQL Server Native Client ODBC driver, database mirroring
- SQL Server Native Client OLE DB provider, database mirroring
ms.assetid: 71b15712-7972-4465-9274-e0ddc271eedc
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c2db9621490f4dc718516e5829f6704b20ee0e9
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761333"
---
# <a name="using-database-mirroring"></a>Verwenden der Datenbankspiegelung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
 Die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführte Datenbankspiegelung ist eine Lösung zum Erhöhen der Datenbankverfügbarkeit und Datenredundanz. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client stellt implizite Unterstützung für die Daten Bank Spiegelung bereit, sodass der Entwickler keinen Code schreiben oder andere Aktionen ausführen muss, nachdem er für die Datenbank konfiguriert wurde.  
  
 Bei einer Datenbankspiegelung, die für Datenbanken einzeln implementiert wird, befindet sich eine Kopie einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Produktionsdatenbank auf einem Standbyserver. Bei dem Server handelt es sich je nach Konfiguration und Status der Datenbankspiegelungs-Sitzung um einen unmittelbar betriebsbereiten oder einfach betriebsbereiten Standbyserver. Ein unmittelbar betriebsbereiter Standbyserver unterstützt schnelles Failover ohne Verlust von Transaktionen mit ausgeführtem Commit, und ein betriebsbereiter Standbyserver unterstützt das Erzwingen eines Diensts (bei möglichem Datenverlust).  
  
 Die Produktionsdatenbank wird *Prinzipaldatenbank* genannt. Die Standbykopie wird *Spiegeldatenbank* genannt. Die Prinzipaldatenbank und die Spiegeldatenbank müssen sich auf unterschiedlichen Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (Serverinstanzen) befinden und sollten sich nach Möglichkeit auch auf unterschiedlichen Computern befinden.  
  
 Die Produktionsserverinstanz, die als *Prinzipalserver* bezeichnet wird, kommuniziert mit der Standbyserverinstanz, dem so genannten *Spiegelserver*. Der Prinzipal- und der Spiegelserver agieren in einer Datenbankspiegelungs-*Sitzung* als Partner. Wenn der Prinzipalserver ausfällt, kann der Spiegelserver seine Datenbank über einen so genannten *Failover* als Prinzipaldatenbank bestimmen. Beispiel: Partner_A und Partner_B sind zwei Partnerserver. Die Prinzipaldatenbank befindet sich anfänglich auf dem Prinzipalserver Partner_A und die Spiegeldatenbank auf dem Spiegelserver Partner_B. Wenn Partner_A offline geht, kann die Datenbank auf Partner_B ein Failover ausführen, um zur aktuellen Prinzipaldatenbank zu werden. Sobald Partner_A wieder mit der Sitzung verbunden ist, übernimmt er wieder die Rolle des Spiegelservers und seine Datenbank wird zur Spiegeldatenbank.  
  
 Alternative Konfigurationen für die Datenbankspiegelung bieten unterschiedliche Leistungs- und Datensicherheitsstufen und unterstützen unterschiedliche Formen des Failover. Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Beim Angeben des Spiegeldatenbanknamens ist es möglich, einen Alias zu verwenden.  
  
> [!NOTE]  
>  Informationen zu anfänglichen Verbindungs versuchen und erneuten Verbindungs versuchen mit einer gespiegelten Datenbank finden Sie unter [Verbinden von Clients mit einer Datenbank &#40;-&#41;Spiegelungs Sitzung SQL Server](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md).  
  
## <a name="programming-considerations"></a>Überlegungen zur Programmierung  
 Wenn auf dem Prinzipaldatenbankserver ein Fehler auftritt, empfängt die Clientanwendung als Antwort auf API-Aufrufe Fehlermeldungen. Dadurch wird angezeigt, dass die Verbindung zur Datenbank unterbrochen ist. Wenn dieser Fall eintritt, gehen alle Datenbankänderungen, für die kein Commit ausgeführt wurde, verloren und für die aktuelle Transaktion wird ein Rollback durchgeführt. Dann sollte die Anwendung die Verbindung beenden (oder das Datenquellobjekt freigeben) und erneut herstellen. Die Verbindung wird transparent zur Spiegeldatenbank umgeleitet, die jetzt als Prinzipalserver fungiert.  
  
 Wenn eine Verbindung hergestellt wurde, teilt der Prinzipalserver die Identität seines Failoverpartners, der bei einem Failover einspringt, dem Client mit. Wenn eine Anwendung versucht, nach dem Failover des Prinzipalservers eine Verbindung aufzubauen, kennt der Client die Identität des Failoverpartners nicht. Um Clients die Möglichkeit zu geben, in dieser Situation Abhilfe zu schaffen, können sie die Identität des Failoverpartners mithilfe einer Initialisierungseigenschaft und eines zugeordneten Schlüsselworts für die Verbindungszeichenfolge selbst angeben. Das Clientattribut wird nur in dieser Situation verwendet; wenn der Prinzipalserver verfügbar ist, wird es nicht verwendet. Wenn der vom Client angegebene Failoverpartnerserver nicht auf einen Server verweist, der als Failoverpartner fungiert, wird die Verbindung vom Server abgewiesen. Um es Anwendungen zu ermöglichen, sich an Konfigurationsänderungen anzupassen, kann die Identität des tatsächlichen Failoverpartners durch Überprüfung des Attributs nach dem Verbindungsaufbau bestimmt werden. Sie sollten die Partnerinformationen zwischenspeichern, um die Verbindungszeichenfolge zu aktualisieren, oder eine Wiederholungsstrategie für den Fall entwerfen, dass der erste Versuch des Verbindungsaufbaus fehlschlägt.  
  
> [!NOTE]  
>  Sie müssen die von einer Verbindung zu verwendende Datenbank explizit angeben, wenn Sie diese Funktion in einem DSN, einer Verbindungszeichenfolge oder einer/m Verbindungseigenschaft/-attribut verwenden möchten. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client versucht sonst nicht, bei einem Fehler zur Partnerdatenbank zu wechseln.  
>   
>  Die Spiegelung ist eine Funktion der Datenbank. Anwendungen, die mehrere Datenbanken verwenden, sind möglicherweise nicht in der Lage, diese Funktion zu nutzen.  
>   
>  Außerdem erfolgt bei den Servernamen keine Unterscheidung nach Groß-/Kleinschreibung, bei Datenbanknamen jedoch schon. Sie müssen daher auf die Übereinstimmung der Groß-/Kleinschreibung in DSNs und Verbindungszeichenfolgen achten.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Daten Bank Spiegelung über Verbindungs-und Verbindungs Zeichen folgen Attribute. Die Eigenschaft SSPROP_INIT_FAILOVERPARTNER wurde dem DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz hinzugefügt, und das Schlüsselwort **FailoverPartner** ist ein neues Verbindungszeichenfolgen-Attribut für DBPROP_INIT_PROVIDERSTRING. Weitere Informationen finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungs Zeichenfolgen mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Der Failovercache wird so lange beibehalten, wie der Anbieter geladen wird. Dies ist der Zeitpunkt, zu dem die **Initialisierung** aufgerufen wird, oder solange die Anwendung einen Verweis auf ein Objekt hat, das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, wie z. b. einem Datenquellen Objekt, verwaltet wird.  
  
 Ausführliche Informationen zur Unterstützung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieters für die Daten Bank Spiegelung finden Sie unter [Initialisierungs-und Autorisierungs Eigenschaften](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt die Daten Bank Spiegelung über Verbindungs-und Verbindungs Zeichen folgen Attribute. Insbesondere wurde das SQL_COPT_SS_FAILOVER_PARTNER-Attribut für die Verwendung mit den Funktionen [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) hinzugefügt. und das **Failover_Partner** -Schlüsselwort wurde als neues Verbindungs Zeichenfolgen-Attribut hinzugefügt.  
  
 Der Failovercache wird beibehalten, solange der Anwendung mindestens ein Umgebungshandle zugeordnet ist. Umgekehrt geht er verloren, wenn die Zuordnung des letzten Umgebungshandles aufgehoben wird.  
  
> [!NOTE]  
>  Der ODBC-Treiber-Manager wurde verbessert, um die Spezifikation des Failoverservernamens zu unterstützen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Verbinden von Clients mit einer Datenbank-Spiegelungssitzung (SQL Server)](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
