---
title: Verwenden von Daten Bank Metadaten | Microsoft-Dokumentation
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
ms.openlocfilehash: fbe290c558dd8c64605bad0a977657904582c696
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916258"
---
# <a name="using-database-metadata"></a>Verwenden von Datenbankmetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Zum Abfragen einer Datenbank nach Informationen zu den unterstützten Funktionen ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts oder als Resultset zurückgeben.

Um ein SQLServerDatabaseMetaData-Objekt zu erstellen, können Sie mit der [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse Informationen über die verbundene Datenbank abrufen.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die-Funktion weitergegeben, die GetMetadata-Methode der SQLServerConnection-Klasse wird verwendet, um ein SQLServerDatabaseMetaData-Objekt zurückzugeben, und anschließend verschiedene Methoden des Das SQLServerDatabaseMetaData-Objekt wird verwendet, um Informationen zu Treiber, Treiber Version, Datenbankname und Datenbankversion anzuzeigen.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
