---
title: Verwenden von Datenbankmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58e5e403bb33663654c3cd5f0f884c13957d04f2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711270"
---
# <a name="using-database-metadata"></a>Verwenden von Datenbankmetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Zum Abfragen einer Datenbank nach Informationen zu den unterstützten Funktionen ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts oder als Resultset zurückgeben.

Um ein SQLServerDatabaseMetaData-Objekt zu erstellen, können Sie mit der [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse Informationen über die verbundene Datenbank abrufen.

Im folgenden Beispiel eine offene Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die Funktion übergeben, die GetMetaData-Methode der SQLServerConnection-Klasse wird verwendet, um ein SQLServerDatabaseMetadata-Objekt, und klicken Sie dann die verschiedenen Methoden des Zurückgeben der SQLServerDatabaseMetaData-Objekt werden verwendet, um Informationen zu den Treiber, Treiberversion, Datenbankname und Datenbankversion angezeigt.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
