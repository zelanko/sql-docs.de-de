---
title: Grundlegendes zu Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d5a6caa9c9bf1766b59aa813719d1461b6ef1aa
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027341"
---
# <a name="understanding-transactions"></a>Grundlegendes zu Transaktionen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei Transaktionen handelt es sich um Gruppen von Operationen, die in logische Arbeitseinheiten zusammengefasst sind. Damit wird die Konsistenz und Integrität der einzelnen Aktionen in einer Transaktion gesteuert und gewährleistet, falls im System Fehler auftreten sollten.

Mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ist eine lokale oder verteilte Transaktionsverarbeitung möglich. Transaktionen können auch Isolationsstufen verwenden. Weitere Informationen zu den vom JDBC-Treiber unterstützten Isolationsstufen finden Sie unter [Grundlegendes zu Isolationsstufen](../../connect/jdbc/understanding-isolation-levels.md).

Anwendungen sollten Transaktionen nur entweder mit Transact-SQL-Anweisungen oder den vom JDBC-Treiber bereitgestellten Methoden steuern. Wenn für die gleiche Transaktion sowohl Transact-SQL-Anweisungen als auch JDBC-API-Methoden verwendet werden, führt dies möglicherweise zu Problemen, z. B. kann der Commit einer Transaktion nicht wie erwartet durchgeführt werden, ein unerwarteter Commit oder Rollback der Transaktion wird durchgeführt und eine neue Transaktion gestartet, oder es treten Ausnahmen wie "Fehler beim Wiederaufnehmen der Transaktion" auf.

## <a name="using-local-transactions"></a>Verwenden von lokalen Transaktionen

Eine Transaktion wird als lokal angesehen, wenn es sich um eine Einphasentransaktion handelt, die von der Datenbank direkt verarbeitet wird. Der JDBC-Treiber unterstützt lokale Transaktionen über die Methoden der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse, wie z. B. [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md), [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md) und [rollback](../../connect/jdbc/reference/rollback-method.md). Lokale Transaktionen werden normalerweise explizit von der Anwendung oder automatisch vom Anwendungsserver für die Java-Plattform, Enterprise Edition (Java EE) verwaltet.

Im folgenden Beispiel wird eine lokale Transaktion mit zwei getrennten Anweisungen im`try`-Block ausgeführt. Die Anweisungen werden für die Production.ScrapReason-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank ausgeführt. Wenn keine Ausnahmen ausgegeben werden, wird ein Commit ausgeführt. Der Code im `catch`-Block führt ein Rollback der Transaktion aus, wenn eine Ausnahme ausgelöst wird.

[!code[JDBC#UnderstandingTransactions1](../../connect/jdbc/codesnippet/Java/understanding-transactions_1.java)]

## <a name="using-distributed-transactions"></a>Verwenden von verteilten Transaktionen

Eine verteilte Transaktion aktualisiert Daten in mindestens zwei vernetzten Datenbanken, wobei die wichtigen Eigenschaften der Transaktionsverarbeitung (unteilbar, konsistent, isoliert und dauerhaft) gewährleistet werden. Die Unterstützung verteilter Transaktionen wurde in der optionalen API-Spezifikation von JDBC 2.0 in die JDBC-API aufgenommen. Die Verwaltung verteilter Anwendungen wird normalerweise automatisch vom JTS-Transaktions-Manager (Java Transaction Service) in einer Java EE-Anwendungsserverumgebung ausgeführt. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt jedoch verteilte Transaktionen mit jedem JTA-kompatiblen (Java Transaction API) Transaktions-Manager.

Der JDBC-Treiber ist nahtlos in [!INCLUDE[msCoName](../../includes/msconame_md.md)] Distributed Transaction Coordinator (MS DTC) integriert, um eine echte Unterstützung von verteilten Transaktionen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu ermöglichen. Bei MS DTC handelt es sich um eine Funktion für verteilte Transaktionen, die von [!INCLUDE[msCoName](../../includes/msconame_md.md)] für [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows-Systeme bereitgestellt wird. MS DTC verwendet bewährte Transaktionsverarbeitungstechnologien von [!INCLUDE[msCoName](../../includes/msconame_md.md)], um XA-Funktionen wie das vollständige verteilte Protokoll für Zweiphasencommit und die Wiederherstellung von verteilten Transaktionen zu unterstützen.

Weitere Informationen zur Verwendung von verteilten Transaktionen finden Sie unter [Grundlegendes zu XA-Transaktionen](../../connect/jdbc/understanding-xa-transactions.md).

## <a name="see-also"></a>Weitere Informationen

[Ausführen von Transaktionen mit dem JDBC-Treiber](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
