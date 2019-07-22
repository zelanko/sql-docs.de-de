---
title: Verwenden von Resultsetmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e41f52ed8296c46cfd7b167407b10fc9f0b285
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005939"
---
# <a name="using-result-set-metadata"></a>Verwenden von Resultsetmetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Zum Abfragen eines Resultsets nach Informationen zu den enthaltenen Spalten ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts zurückgeben.

Zum Erstellen eines SQLServerResultSetMetaData-Objekts können Sie die [GetMetadata](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) -Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) -Klasse verwenden.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die Funktion weitergegeben, die GetMetadata-Methode der SQLServerResultSet-Klasse wird verwendet, um ein SQLServerResultSetMetaData-Objekt zurückzugeben, und anschließend verschiedene Methoden des Das SQLServerResultSetMetaData-Objekt wird verwendet, um Informationen über den Namen und den Datentyp der im Resultset enthaltenen Spalten anzuzeigen.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
