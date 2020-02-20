---
title: Verwenden der Haltbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1c126385955ce6e9fa9098ec5a09ba115b94ffb0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026197"
---
# <a name="using-holdability"></a>Verwenden der Haltbarkeit

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Standardmäßig bleibt ein Resultset, das in einer Transaktion erstellt wurde, nach einem Commit der Transaktion in der Datenbank oder einem Rollback geöffnet. Bisweilen ist es aber von Nutzen, das Resultset nach einem Commit der Transaktion zu schließen. Zu diesem Zweck unterstützt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die Verwendung der Resultsethaltbarkeit.

Sie können die Resultsethaltbarkeit mit der [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse einstellen. Beim Einstellen der Haltbarkeit mit der setHoldability-Methode können für die Resultsethaltbarkeit die Konstanten `ResultSet.HOLD_CURSORS_OVER_COMMIT` oder `ResultSet.CLOSE_CURSORS_AT_COMMIT` verwendet werden.

Der JDBC-Treiber unterstützt auch das Festlegen der Haltbarkeit beim Erstellen eines der Statement-Objekte. Beim Erstellen der Statement-Objekte, die mit Parametern für die Resultsethaltbarkeit überladen sind, muss die Haltbarkeit des Statement-Objekts der Haltbarkeit der Verbindung entsprechen. Stimmen sie nicht überein, wird eine Ausnahme ausgelöst. Der Grund hierfür ist, dass SQL Server die Haltbarkeit nur auf Verbindungsebene unterstützt.

Bei der Haltbarkeit eines Resultsets handelt es sich um die Haltbarkeit eines SQLServerConnection-Objekts, das nur beim Erstellen von serverseitigen Cursorn dem Resultset zugeordnet wird. Dies gilt nicht für clientseitige Cursor. Alle Resultsets mit clientseitigen Cursorn besitzen immer den Haltbarkeitswert `ResultSet.HOLD_CURSORS_OVER_COMMIT`.

Wenn Servercursor mit SQL Server 2005 oder höher verbunden sind, wirkt sich das Festlegen der Haltbarkeit nur auf die Haltbarkeit neuer Resultsets aus, die erst noch für diese Verbindung erstellt werden. Das heißt, das Festlegen der Haltbarkeit hat keine Auswirkungen auf die Haltbarkeit von Resultsets, die zuvor erstellt wurden und für die Verbindung bereits geöffnet sind.

Im folgenden Beispiel wird die Resultsethaltbarkeit beim Ausführen einer lokalen Transaktion mit zwei getrennten Anweisungen im `try`-Block festgelegt. Die Anweisungen werden für die Production.ScrapReason-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank ausgeführt. Zunächst wird im Beispiel zum manuellen Transaktionsmodus gewechselt, indem die der automatische Commit auf `false` festgelegt wird. Sobald der automatische Commitmodus deaktiviert ist, wird ein Commit von SQL-Anweisungen erst ausgeführt, wenn die Anwendung die [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md)-Methode explizit aufruft. Der Code im catch-Block führt ein Rollback der Transaktion aus, wenn eine Ausnahme ausgelöst wird.

[!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Ausführen von Transaktionen mit dem JDBC-Treiber](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
