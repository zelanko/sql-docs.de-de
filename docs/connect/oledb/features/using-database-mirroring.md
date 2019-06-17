---
title: Die Verwendung der Datenbankspiegelung | Microsoft-Dokumentation
description: Die Verwendung der datenbankspiegelung mit OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- OLE DB Driver for SQL Server, database mirroring
- data access [OLE DB Driver for SQL Server], database mirroring
- database mirroring [SQL Server], connecting clients to
- MSOLEDBSQL, database mirroring
- OLE DB Driver for SQL Server, database mirroring
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: eba70e8a4ee641b4bccb54f67f37015a0edbd434
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802898"
---
# <a name="using-database-mirroring"></a>Verwenden der Datenbankspiegelung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
 Die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführte Datenbankspiegelung ist eine Lösung zum Erhöhen der Datenbankverfügbarkeit und Datenredundanz. Der OLE DB-Treiber für SQL Server stellt implizite Unterstützung für die Datenbankspiegelung bereit, weshalb Entwickler weder Code schreiben noch andere Aktionen ausführen müssen, nachdem sie für die Datenbank konfiguriert wurde.  
  
 Bei einer Datenbankspiegelung, die für Datenbanken einzeln implementiert wird, befindet sich eine Kopie einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Produktionsdatenbank auf einem Standbyserver. Bei dem Server handelt es sich je nach Konfiguration und Status der Datenbankspiegelungs-Sitzung um einen unmittelbar betriebsbereiten oder einfach betriebsbereiten Standbyserver. Ein unmittelbar betriebsbereiter Standbyserver unterstützt schnelles Failover ohne Verlust von Transaktionen mit ausgeführtem Commit, und ein betriebsbereiter Standbyserver unterstützt das Erzwingen eines Diensts (bei möglichem Datenverlust).  
  
 Die Produktionsdatenbank wird *Prinzipaldatenbank* genannt. Die Standbykopie wird *Spiegeldatenbank* genannt. Die Prinzipaldatenbank und die Spiegeldatenbank müssen sich auf unterschiedlichen Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (Serverinstanzen) befinden und sollten sich nach Möglichkeit auch auf unterschiedlichen Computern befinden.  
  
 Die Produktionsserverinstanz, die als *Prinzipalserver* bezeichnet wird, kommuniziert mit der Standbyserverinstanz, dem so genannten *Spiegelserver*. Der Prinzipal- und der Spiegelserver agieren in einer Datenbankspiegelungs-*Sitzung* als Partner. Wenn der Prinzipalserver ausfällt, kann der Spiegelserver seine Datenbank über einen so genannten *Failover* als Prinzipaldatenbank bestimmen. Beispiel: Partner_A und Partner_B sind zwei Partnerserver. Die Prinzipaldatenbank befindet sich anfänglich auf dem Prinzipalserver Partner_A und die Spiegeldatenbank auf dem Spiegelserver Partner_B. Wenn Partner_A offline geht, kann die Datenbank auf Partner_B ein Failover ausführen, um zur aktuellen Prinzipaldatenbank zu werden. Sobald Partner_A wieder mit der Sitzung verbunden ist, übernimmt er wieder die Rolle des Spiegelservers und seine Datenbank wird zur Spiegeldatenbank.  
  
 Alternative Konfigurationen für die Datenbankspiegelung bieten unterschiedliche Leistungs- und Datensicherheitsstufen und unterstützen unterschiedliche Formen des Failover. Weitere Informationen finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Beim Angeben des Spiegeldatenbanknamens ist es möglich, einen Alias zu verwenden.  
  
> [!NOTE]  
>  Informationen über Versuche und Versuche der erneuten Herstellen einer Verbindung mit einer gespiegelten Datenbank finden Sie unter [Verbinden von Clients mit einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md).  
  
## <a name="programming-considerations"></a>Überlegungen zur Programmierung  
 Wenn auf dem Prinzipaldatenbankserver ein Fehler auftritt, empfängt die Clientanwendung als Antwort auf API-Aufrufe Fehlermeldungen. Dadurch wird angezeigt, dass die Verbindung zur Datenbank unterbrochen ist. Wenn dieser Fall eintritt, gehen alle Datenbankänderungen, für die kein Commit ausgeführt wurde, verloren und für die aktuelle Transaktion wird ein Rollback durchgeführt. Dann sollte die Anwendung die Verbindung beenden (oder das Datenquellobjekt freigeben) und erneut herstellen. Die Verbindung wird transparent zur Spiegeldatenbank umgeleitet, die jetzt als Prinzipalserver fungiert.  
  
 Wenn eine Verbindung hergestellt wurde, teilt der Prinzipalserver die Identität seines Failoverpartners, der bei einem Failover einspringt, dem Client mit. Wenn eine Anwendung versucht, nach dem Failover des Prinzipalservers eine Verbindung aufzubauen, kennt der Client die Identität des Failoverpartners nicht. Um Clients die Möglichkeit zu geben, in dieser Situation Abhilfe zu schaffen, können sie die Identität des Failoverpartners mithilfe einer Initialisierungseigenschaft und eines zugeordneten Schlüsselworts für die Verbindungszeichenfolge selbst angeben. Das Clientattribut wird nur in dieser Situation verwendet; wenn der Prinzipalserver verfügbar ist, wird es nicht verwendet. Wenn der vom Client angegebene Failoverpartnerserver nicht auf einen Server verweist, der als Failoverpartner fungiert, wird die Verbindung vom Server abgewiesen. Um es Anwendungen zu ermöglichen, sich an Konfigurationsänderungen anzupassen, kann die Identität des tatsächlichen Failoverpartners durch Überprüfung des Attributs nach dem Verbindungsaufbau bestimmt werden. Sie sollten die Partnerinformationen zwischenspeichern, um die Verbindungszeichenfolge zu aktualisieren, oder eine Wiederholungsstrategie für den Fall entwerfen, dass der erste Versuch des Verbindungsaufbaus fehlschlägt.  
  
> [!NOTE]  
>  Sie müssen die von einer Verbindung zu verwendende Datenbank explizit angeben, wenn Sie diese Funktion in einem DSN, einer Verbindungszeichenfolge oder einer/m Verbindungseigenschaft/-attribut verwenden möchten. OLE DB-Treiber für SQL Server versucht nicht, ein Failover zur Partnerdatenbank zu, wenn dies nicht erfolgt.  
>   
>  Die Spiegelung ist eine Funktion der Datenbank. Anwendungen, die mehrere Datenbanken verwenden, sind möglicherweise nicht in der Lage, diese Funktion zu nutzen.  
>   
>  Außerdem erfolgt bei den Servernamen keine Unterscheidung nach Groß-/Kleinschreibung, bei Datenbanknamen jedoch schon. Sie müssen daher auf die Übereinstimmung der Groß-/Kleinschreibung in DSNs und Verbindungszeichenfolgen achten.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server unterstützt die Datenbankspiegelung durch Attribute für Verbindungen und Verbindungszeichenfolgen. Die Eigenschaft SSPROP_INIT_FAILOVERPARTNER wurde dem DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz hinzugefügt, und das Schlüsselwort **FailoverPartner** ist ein neues Verbindungszeichenfolgen-Attribut für DBPROP_INIT_PROVIDERSTRING. Weitere Informationen finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit OLE DB-Treiber für SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Der Failovercache wird aufrechterhalten, solange der Anbieter geladen wird, also bis **CoUninitialize** aufgerufen wird, oder solange die Anwendung über einen Verweis auf ein vom OLE DB-Treiber für SQL Server verwaltetes Objekt, wie z.B. ein Datenquellobjekt, verfügt.  
  
 Weitere Informationen zu OLE DB-Treiber für SQL Server-Unterstützung für die datenbankspiegelung finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Verbinden von Clients mit einer Datenbank-Spiegelungssitzung (SQL Server)](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
