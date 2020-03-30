---
title: SQL Server Service Broker | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 11dc9169ec88928c893d875b7051bfbf551c95fd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68034519"
---
# <a name="service-broker"></a>Service Broker
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSB](../../includes/sssb-md.md)] bieten native Unterstützung für Messaging und Warteschlangen in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [verwalteten Azure SQL-Datenbank-Instanzen](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index). Entwickler können problemlos anspruchsvolle Anwendungen erstellen, die die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Komponenten verwenden, um zwischen verschiedenen Datenbanken zu kommunizieren und verteilte und zuverlässige Anwendungen zu erstellen.  
  
## <a name="when-to-use-service-broker"></a>Einsatz von Service Broker

 Verwenden Sie Service Broker-Komponenten, um native, datenbankinterne asynchrone Nachrichtenverarbeitungsfunktionen zu implementieren. Anwendungsentwickler, die [!INCLUDE[ssSB](../../includes/sssb-md.md)] verwenden, können Datenarbeitsauslastungen zwischen mehreren Datenbanken verteilen, ohne komplizierte Besonderheiten von Kommunikation und Messaging programmieren zu müssen. Service Broker reduziert die Entwicklungs- und die Testarbeit, da [!INCLUDE[ssSB](../../includes/sssb-md.md)] die Kommunikationspfade im Kontext einer Konversation behandelt. Außerdem wird die Leistung verbessert. Front-End-Datenbanken, die Websites unterstützen, können z. B. Informationen aufzeichnen und prozessintensive Tasks an die Warteschlange von Back-End-Datenbanken senden. [!INCLUDE[ssSB](../../includes/sssb-md.md)] stellt sicher, dass alle Tasks im Kontext von Transaktionen verwaltet werden, um die Zuverlässigkeit und technische Konsistenz zu gewährleisten.  
  
## <a name="overview"></a>Übersicht

  Service Broker ist ein Nachrichtenübermittlungsframework, das das Erstellen nativer, datenbankinterner dienstorientierter Anwendungen ermöglicht. Im Gegensatz zu den klassischen Funktionen der Abfrageverarbeitung, die während des Abfragelebenszyklus ständig Daten aus den Tabellen lesen und verarbeiten, stehen Ihnen in der dienstorientierten Anwendung Datenbankdienste zur Verfügung, die Nachrichten austauschen. Jeder Dienst verfügt über eine Warteschlange, in der Nachrichten bis zu ihrer Verarbeitung platziert werden.
  
![Service Broker](media/service-broker.png)
  
  Die Nachrichten in den Warteschlangen können mit dem Transact-SQL-Befehl `RECEIVE` oder durch das Aktivierungsverfahren abgerufen werden, das aufgerufen wird, wenn die Nachricht in der Warteschlange eingeht.
  
### <a name="creating-services"></a>Erstellen von Diensten
 
  Datenbankdienste werden mit der Transact-SQL-Anweisung [CREATE SERVICE](../../t-sql/statements/create-service-transact-sql.md) erstellt. Der Dienst kann mit der Anweisung [CREATE QUEUE](../../t-sql/statements/create-queue-transact-sql.md) der erstellten Nachrichtenwarteschlange zugeordnet werden:
  
```sql
CREATE QUEUE dbo.ExpenseQueue;
GO
CREATE SERVICE ExpensesService
    ON QUEUE dbo.ExpenseQueue; 
```

### <a name="sending-messages"></a>Senden von Nachrichten
  
  Nachrichten werden für die Konversation zwischen den Diensten mit der Transact-SQL-Anweisung [SEND](../../t-sql/statements/send-transact-sql.md) gesendet. Eine Konversation ist ein Kommunikationskanal, der zwischen den Diensten mit der Transact-SQL-Anweisung `BEGIN DIALOG` eingerichtet wird. 
  
```sql
DECLARE @dialog_handle UNIQUEIDENTIFIER;

BEGIN DIALOG @dialog_handle  
FROM SERVICE ExpensesClient  
TO SERVICE 'ExpensesService';  
  
SEND ON CONVERSATION @dialog_handle (@Message) ;  
```
   Die Nachricht wird an `ExpenssesService` gesendet und in `dbo.ExpenseQueue` platziert. Da dieser Warteschlange kein Aktivierungsverfahren zugeordnet ist, verbleibt die Nachricht in der Warteschlange, bis sie gelesen wird.

### <a name="processing-messages"></a>Verarbeiten von Nachrichten

   Die Nachrichten, die in die Warteschlange gestellt werden, können mit einer Standardabfrage `SELECT` ausgewählt werden. Die `SELECT`-Anweisung ändert die Warteschlange nicht und entfernt die Nachrichten nicht. Um die Nachrichten aus der Warteschlange zu lesen und abzurufen, können Sie die Transact-SQL-Anweisung [RECEIVE](../../t-sql/statements/receive-transact-sql.md) verwenden.

```sql
RECEIVE conversation_handle, message_type_name, message_body  
FROM ExpenseQueue; 
```

  Nachdem Sie alle Nachrichten aus der Warteschlange verarbeitet haben, sollten Sie die Konversation mit der Transact-SQL-Anweisung [END CONVERSATION](../../t-sql/statements/end-conversation-transact-sql.md) schließen.

## <a name="where-is-the-documentation-for-service-broker"></a>Wo finde ich die Dokumentation für Service Broker?  
 Die Referenzdokumentation für [!INCLUDE[ssSB](../../includes/sssb-md.md)] ist in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Dokumentation enthalten. Diese Referenzdokumentation enthält die folgenden Abschnitte:  
  
-   [Anweisungen &#40;Transact-SQL&#41; für Datendefinitionssprache &#40;DDL&#41;](../../t-sql/statements/statements.md) für CREATE-, ALTER- und DROP-Anweisungen  
  
-   [Service Broker-Anweisungen](../../t-sql/statements/service-broker-statements.md)  
  
-   [Service Broker-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)  
  
-   [Dynamische Verwaltungssichten in Verbindung mit Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
-   [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 Informationen zu [-Konzepten sowie Entwicklungs- und Verwaltungsaufgaben finden Sie in der](https://go.microsoft.com/fwlink/?LinkId=231312) zuvor veröffentlichten Dokumentation [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Diese Dokumentation ist aufgrund der geringen Anzahl von Änderungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssSB](../../includes/sssb-md.md)] nicht in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Dokumentation enthalten.  
  
## <a name="whats-new-in-service-broker"></a>Neues in Service Broker  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wurden keine wesentlichen Änderungen eingeführt.  Für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]wurden die folgenden Änderungen eingeführt.  

### <a name="service-broker-and-azure-sql-database-managed-instance"></a>Service Broker und verwaltete Azure SQL-Datenbank-Instanz

- Ein instanzenübergreifender Service Broker wird nicht unterstützt. 
 - `sys.routes` – Voraussetzung: Wählen Sie die Adresse aus sys.routes. Die Adresse muss für jede Route LOCAL sein. Informationen hierzu finden Sie unter [sys.routes](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md).
 - `CREATE ROUTE`: `CREATE ROUTE` kann ausschließlich mit dem Wert `ADDRESS` für `LOCAL` verwendet werden. Informationen hierzu finden Sie unter [CREATE ROUTE](https://docs.microsoft.com/sql/t-sql/statements/create-route-transact-sql).
 - `ALTER ROUTE` kann `ALTER ROUTE` mit keiner anderen `ADDRESS` als `LOCAL` verwenden. Informationen hierzu finden Sie unter [ALTER ROUTE](../../t-sql/statements/alter-route-transact-sql.md).  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a>Nachrichten können an mehrere Zieldienste gesendet werden (Multicast)  
 Die Syntax der [SEND &#40;Transact-SQL&#41;](../../t-sql/statements/send-transact-sql.md)-Anweisung wurde erweitert, um mehrere Konversationshandles zu unterstützen und so die Multicastübermittlung zu ermöglichen.  
  
### <a name="queues-expose-the-message-enqueued-time"></a>Warteschlangen machen die Nachrichtenwartezeit verfügbar  
 Warteschlangen verfügen über eine neue **message_enqueue_time**-Spalte, in der angezeigt wird, wie lange eine Nachricht in der Warteschlange war.  
  
### <a name="poison-message-handling-can-be-disabled"></a>Behandlung nicht verarbeitbarer Nachrichten kann deaktiviert werden  
 Die Anweisungen [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md) und [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md) bieten nun die Möglichkeit, die Behandlung von nicht verarbeitbaren Nachrichten zu aktivieren oder deaktivieren, indem die Klausel `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` hinzugefügt wird. Die **sys.service_queues** -Katalogsicht enthält jetzt eine **is_poison_message_handling_enabled** -Spalte, in der angezeigt wird, ob die Behandlung nicht verarbeitbarer Nachrichten aktiviert oder deaktiviert ist.  
  
### <a name="always-on-support-in-service-broker"></a>AlwaysOn-Unterstützung in Service Broker  
 Weitere Informationen finden Sie unter [Service Broker mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).  
  
  

