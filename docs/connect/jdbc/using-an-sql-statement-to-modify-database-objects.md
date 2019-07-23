---
title: Ändern von Datenbankobjekten mit SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28c71784f8e51600aef111649b12f81b5878b324
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916385"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Ändern von Datenbankobjekten mit SQL-Anweisungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Mit der [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankobjekte über eine SQL-Anweisung ändern. Die executeUpdate-Methode übergibt die SQL-Anweisung zur Verarbeitung an die Datenbank und gibt anschließend den Wert 0 zurück, weil keine Zeilen betroffen sind.

Sie müssen dazu zuerst mit der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerStatement-Objekt erstellen.

> [!NOTE]  
> SQL-Anweisungen, die Objekte in einer Datenbank ändern, werden DDL-Anweisungen (Data Definition Language) genannt. Dazu zählen Anweisungen `CREATE TABLE`wie, `DROP TABLE`, `CREATE INDEX`und `DROP INDEX`. Weitere Informationen zu den von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten DDL-Anweisungen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine SQL-Anweisung wird erstellt, die die einfache Testtabelle in der Datenbank erstellt. Anschließend wird die Anweisung ausgeführt, und der Rückgabewert wird angezeigt.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)
