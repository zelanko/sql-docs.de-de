---
title: Verwenden von Resultsetmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d89e8130c897bbf7914b2d3d5d47cba8d38bd01
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661672"
---
# <a name="using-result-set-metadata"></a>Verwenden von Resultsetmetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Zum Abfragen eines Resultsets nach Informationen zu den enthaltenen Spalten ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts zurückgeben.

Um ein SQLServerResultSetMetaData-Objekt zu erstellen, können Sie die [GetMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) Klasse.

Im folgenden Beispiel eine offene Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die Funktion übergeben, die GetMetaData-Methode der SQLServerResultSet-Klasse wird verwendet, um ein SQLServerResultSetMetaData-Objekt, und klicken Sie dann die verschiedenen Methoden des Zurückgeben der SQLServerResultSetMetaData-Objekt werden verwendet, um Informationen zu den Namen und den Typ der im Resultset enthaltenen Spalten anzuzeigen.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
