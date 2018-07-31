---
title: Verwenden von Datenbankmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2f3e0a4e19b30eeb494f89281a01195cf98b7d9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982112"
---
# <a name="using-database-metadata"></a>Verwenden von Datenbankmetadaten
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Zum Abfragen einer Datenbank nach Informationen zu den unterstützten Funktionen ist in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Klasse implementiert. Diese Klasse enthält eine Vielzahl von Methoden, die Informationen in der Form eines einzelnen Werts oder als Resultset zurückgeben.  
  
 Um ein SQLServerDatabaseMetaData-Objekt zu erstellen, können Sie mit der [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse Informationen über die verbundene Datenbank abrufen.  
  
 Im folgenden Beispiel werden eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die Funktion übergeben, mit der -Methode der -Klasse ein -Objekt zurückgegeben und dann mit den verschiedenen Methoden des -Objekts Informationen zu Treiber, Treiberversion, Datenbankname und Datenbankversion angezeigt.  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verarbeiten von Metadaten mit dem JDBC-Treiber](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
