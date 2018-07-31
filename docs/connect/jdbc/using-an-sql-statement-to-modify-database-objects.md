---
title: Ändern von Datenbankobjekten mit SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b126fb0b5a72688c1801cf8854d8035763c8245f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040578"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Ändern von Datenbankobjekten mit SQL-Anweisungen
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Mit der [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbankobjekte über eine SQL-Anweisung ändern. Die executeUpdate-Methode übergibt die SQL-Anweisung zur Verarbeitung an die Datenbank und gibt anschließend den Wert 0 zurück, weil keine Zeilen betroffen sind.  
  
 Sie müssen dazu zuerst mit der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerStatement-Objekt erstellen.  
  
> [!NOTE]  
>  SQL-Anweisungen, die Objekte in einer Datenbank ändern, werden DDL-Anweisungen (Data Definition Language) genannt. Dazu gehören Anweisungen wie CREATE TABLE, DROP TABLE, CREATE INDEX und DROP INDEX. Weitere Informationen zu den von [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] unterstützten DDL-Anweisungen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Onlinedokumentation.  
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und eine SQL-Anweisung wird erstellt, die die einfache Testtabelle in der Datenbank erstellt. Anschließend wird die Anweisung ausgeführt, und der Rückgabewert wird angezeigt.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
