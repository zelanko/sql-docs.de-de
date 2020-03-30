---
title: Ändern von Datenbankobjekten mit SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de8e357328c151e3762f324dcbeba2525df53530
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026561"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Ändern von Datenbankobjekten mit SQL-Anweisungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]executeUpdate[-Methode der ](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)SQLServerStatement[-Klasse können Sie ](../../connect/jdbc/reference/sqlserverstatement-class.md)-Datenbankobjekte über eine SQL-Anweisung ändern. Die executeUpdate-Methode übergibt die SQL-Anweisung zur Verarbeitung an die Datenbank und gibt anschließend den Wert 0 zurück, weil keine Zeilen betroffen sind.

Sie müssen dazu zuerst mit der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerStatement-Objekt erstellen.

> [!NOTE]  
> SQL-Anweisungen, die Objekte in einer Datenbank ändern, werden DDL-Anweisungen (Data Definition Language) genannt. Dazu gehören Anweisungen wie `CREATE TABLE`, `DROP TABLE`, `CREATE INDEX` und `DROP INDEX`. Weitere Informationen zu den von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützten DDL-Anweisungen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine SQL-Anweisung wird erstellt, die die einfache Testtabelle in der Datenbank erstellt. Anschließend wird die Anweisung ausgeführt, und der Rückgabewert wird angezeigt.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)
