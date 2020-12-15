---
title: Grundlegendes zur Parallelitätssteuerung
description: Erfahren Sie mehr über die Parallelitätssteuerung und über die Beibehaltung der Datenbankintegrität bei der Entwicklung einer Anwendung für mehrere Benutzer mit dem JDBC-Treiber für SQL Server.
ms.custom: ''
ms.date: 12/08/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 98b7dabe-9b12-4e1d-adeb-e5b5cb0c96f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c44f52697fa8048a8c7db2286c3e69114f658152
ms.sourcegitcommit: 7f76975c29d948a9a3b51abce564b9c73d05dcf0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96900943"
---
# <a name="understanding-concurrency-control"></a>Grundlegendes zur Parallelitätssteuerung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Als Parallelitätssteuerung werden unterschiedliche Verfahren beschrieben, mit denen die Integrität der Datenbank erhalten wird, wenn mehrere Benutzer gleichzeitig Zeilen aktualisieren. Falsche Parallelität kann zu Problemen führen, beispielsweise Dirty Reads, Phantomlesezugriffe und nicht wiederholbare Lesevorgänge. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stellt Schnittstellen für alle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendeten Parallelitätsverfahren bereit, um diese Probleme zu beheben.  
  
> [!NOTE]  
>  Weitere Informationen zu Parallelität in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Verwalten des parallelen Datenzugriffs](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#managing-concurrent-data-access).  
  
## <a name="remarks"></a>Bemerkungen  
 Der JDBC-Treiber unterstützt die folgenden Parallelitätstypen:  
  
|Parallelitätstyp|Merkmale|Anzahl von Zeilensperren|BESCHREIBUNG|  
|----------------------|---------------------|---------------|-----------------|  
|CONCUR_READ_ONLY|Nur Leseberechtigung|Nein|Updates über den Cursor sind nicht zulässig; es werden keine Sperren für die Zeilen aufrechterhalten, aus denen das Resultset besteht.|  
|CONCUR_UPDATABLE|Optimistic Read Write|Nein|Die Datenbank geht davon aus, dass Zeilenkonflikte unwahrscheinlich, aber möglich sind. Zeilenintegrität wird mit einem Timestampvergleich geprüft.|  
|CONCUR_SS_SCROLL_LOCKS|Pessimistic Read Write|Ja|Die Datenbank geht davon aus, dass Zeilenkonflikte wahrscheinlich sind. Zeilenintegrität wird mit Zeilensperren sichergestellt.|  
|CONCUR_SS_OPTIMISTIC_CC|Optimistic Read Write|Nein|Die Datenbank geht davon aus, dass Zeilenkonflikte unwahrscheinlich, aber möglich sind. Zeilenintegrität wird mit einem Timestampvergleich überprüft.<br /><br /> Bei [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher ändert der Server dies in CONCUR_SS_OPTIMISTIC_CCVAL, wenn die Tabelle keine timestamp-Spalte enthält.<br /><br /> Wenn in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] die zugrunde liegende Tabelle eine timestamp-Spalte aufweist, wird OPTIMISTIC WITH ROW VERSIONING selbst dann verwendet, wenn OPTIMISTIC WITH VALUES angegeben wurde. Wenn OPTIMISTIC WITH ROW VERSIONING angegeben wurde und die Tabelle keine Timestamps aufweist, wird OPTIMISTIC WITH VALUES verwendet.|  
|CONCUR_SS_OPTIMISTIC_CCVAL|Optimistic Read Write|Nein|Die Datenbank geht davon aus, dass Zeilenkonflikte unwahrscheinlich, aber möglich sind. Zeilenintegrität wird mit einem Zeilendatenvergleich geprüft.|  
  
## <a name="result-sets-that-are-not-updateable"></a>Nicht aktualisierbare Resultsets  
 Ein aktualisierbares Resultset ist ein Resultset, in dem Zeilen eingefügt, aktualisiert und gelöscht werden können. In den folgenden Fällen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keinen aktualisierbaren Cursor erstellen. Die generierte Ausnahme lautet "Das Resultset kann nicht aktualisiert werden".  
  
|Ursache|BESCHREIBUNG|Problembehandlung|  
|-----------|-----------------|------------|  
|Anweisung wurde nicht mit JDBC 2.0-Syntax (oder neuer) erstellt|In JDBC 2.0 wurden neue Methoden eingeführt, um Anweisungen zu erstellen. Bei der Verwendung von JDBC 1.0-Syntax ist das Resultset standardmäßig schreibgeschützt.|Geben Sie den Resultsettyp und die Parallelität beim Erstellen der Anweisung an.|  
|Anweisung wurde mit TYPE_SCROLL_INSENSITIVE erstellt|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt einen statischen Momentaufnahmencursor. Dieser ist von den zugrunde liegenden Tabellenzeilen getrennt, um den Cursor vor Zeilenudpates durch andere Benutzer zu schützen.|Verwenden Sie TYPE_SCROLL_SENSITIVE, TYPE_SS_SCROLL_KEYSET, TYPE_SS_SCROLL_DYNAMIC oder TYPE_FORWARD_ONLY mit CONCUR_UPDATABLE, um das Erstellen eines statischen Cursors zu vermeiden.|  
|Tabellenentwurf schließt einen KEYSET-Cursor oder einen DYNAMIC-Cursor aus|Die zugrunde liegende Tabelle weist keine eindeutigen Schlüssel auf, mit denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Zeile eindeutig identifizieren kann.|Fügen Sie der Tabelle eindeutige Schlüssel hinzu, um eine eindeutige Identifikation jeder Zeile bereitzustellen.|  
  
## <a name="see-also"></a>Weitere Informationen:  
 [Verwalten von Resultsets mit dem JDBC-Treiber](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
