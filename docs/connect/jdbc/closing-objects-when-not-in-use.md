---
title: Schließen von Objekten bei Nichtverwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47ad0a6d69ccf19b34ff0e15e7afa39b2dfcce41
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687422"
---
# <a name="closing-objects-when-not-in-use"></a>Schließen von nicht verwendeten Objekten
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie mit Objekten von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] arbeiten, insbesondere mit [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oder mit einem der Statement-Objekte wie [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oder [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), sollten Sie sie explizit mit den entsprechenden close-Methoden schließen, wenn sie nicht mehr benötigt werden. So wird die Leistung verbessert, da Treiber- und Serverressourcen so schnell wie möglich freigegeben werden und nicht erst darauf gewartet wird, dass dies durch den Garbage Collector der Java Virtual Machine erfolgt.  
  
 Das Schließen von Objekten ist besonders wichtig zum Erhalten der Parallelität auf dem Server, wenn Sie Rollen-Sperren verwenden. Rollen-Sperren im Fetchpuffer, auf den zuletzt zugegriffen wurde, werden beibehalten, bis das Resultset geschlossen wurde. Auf ähnliche Weise werden Handles für vorbereitete Anweisungen bis zum Schließen der Anweisung beibehalten. Wenn Sie eine Verbindung für mehrere Anweisungen wiederverwenden, führt das Schließen der Anweisungen, bevor sie den Bereich verlassen, dazu, dass der Server die vorbereiteten Handles früher bereinigt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
