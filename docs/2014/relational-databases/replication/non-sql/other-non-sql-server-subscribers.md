---
title: Andere Nicht-SQL Server-Abonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e6a01bfc16041db89ea6160c36af1a7536290ef
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068553"
---
# <a name="other-non-sql-server-subscribers"></a>Andere Nicht-SQL Server-Abonnenten
  Eine Liste der von[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützten Nicht- [!INCLUDE[msCoName](../../../includes/msconame-md.md)]-Abonnenten finden Sie unter [Non-SQL Server Subscribers](non-sql-server-subscribers.md). Dieses Thema enthält Informationen zu den Anforderungen für ODBC-Treiber und OLE DB-Anbieter.  
  
## <a name="odbc-driver-requirements"></a>Anforderungen für ODBC-Treiber  
 Der ODBC-Treiber muss folgende Voraussetzungen erfüllen:  
  
-   Er muss ODBC Level-1-kompatibel sein.  
  
-   Er muss threadsicher sein und sich für die Prozessorarchitektur (Intel oder Alpha) und die Plattform (32 Bit oder 64 Bit) eignen, auf der der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verteiler ausgeführt wird.  
  
-   Er muss in der Lage sein, Transaktionen zu verarbeiten.  
  
-   Er muss die Datendefinitionssprache (Data Definition Language, DDL) unterstützen.  
  
-   Er darf nicht schreibgeschützt sein.  
  
-   Er muss lange Tabellennamen unterstützen, wie z. B. **MSreplication_subscriptions**.  
  
## <a name="replicating-using-ole-db-interfaces"></a>Replikation mithilfe von OLE DB-Schnittstellen  
 OLE DB-Anbieter müssen folgende Objekte für die Transaktionsreplikation unterstützen.  
  
-   **DataSource** -Objekt  
  
-   **Session** -Objekt  
  
-   **Command** -Objekt  
  
-   **Rowset** -Objekt  
  
-   **Error** -Objekt  
  
### <a name="datasource-object-interfaces"></a>Schnittstellen für DataSource-Objekte  
 Die folgenden Schnittstellen sind erforderlich, um eine Verbindung mit einer Datenquelle herzustellen:  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 Wenn der Anbieter die Schnittstelle **IDBInfo** unterstützt, wird sie von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet, um Informationen wie den Bezeichner in Anführungszeichen, die maximale Länge einer SQL-Anweisung und die maximale Anzahl von Zeichen in Tabellen- und Spaltennamen abzurufen.  
  
### <a name="session-object-interfaces"></a>Schnittstellen für Session-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Schnittstellen für Command-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** ist zum Erstellen von Parameterzugriffen erforderlich. Wenn der Anbieter **IColumnRowset**unterstützt, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet diese Schnittstelle, um zu bestimmen, ob eine Spalte eine Identitäts Spalte ist.  
  
### <a name="rowset-object-interfaces"></a>Schnittstellen für Rowset-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Eine Anwendung sollte ein Rowset für eine replizierte Tabelle öffnen, das in der Abonnementdatenbank erstellt wird. **IColumnsInfo** und **IAccessor** werden zum Zugreifen auf Daten im Rowset benötigt.  
  
### <a name="error-object-interfaces"></a>Schnittstellen für Error-Objekte  
 Verwenden Sie die folgenden Schnittstellen zur Verwaltung von Fehlern:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Verwenden Sie **ISQLErrorInfo** , wenn diese Schnittstelle vom OLE DB-Anbieter unterstützt wird.  
  
 Weitere Informationen zum OLE DB-Anbieter finden Sie in der Dokumentation zum jeweiligen OLE DB-Anbieter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)  
  
  
