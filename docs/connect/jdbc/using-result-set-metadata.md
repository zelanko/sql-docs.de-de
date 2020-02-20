---
title: Verwenden von Resultsetmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ed0b1eedcafa1fab59d17f756523fc0fc189200
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026126"
---
# <a name="using-result-set-metadata"></a>Verwenden von Resultsetmetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Zum Abfragen eines Resultsets nach Informationen zu den enthaltenen Spalten ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts zurückgeben.

Sie können die [getMetaData-Methode](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse verwenden, um ein SQLServerResultSetMetaData-Objekt zu erstellen.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, mit der getMetaData-Methode der SQLServerResultSet-Klasse wird ein SQLServerResultSetMetaData-Objekt zurückgegeben, und verschiedene Methoden des SQLServerResultSetMetaData-Objekts werden zum Anzeigen von Informationen über den Namen und Datentyp der im Resultset enthaltenen Spalten verwendet.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
