---
title: Schließen von nicht verwendeten Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f1f0c264a7752b296691f20f702ab345f18b1b37
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922585"
---
# <a name="closing-objects-when-not-in-use"></a>Schließen von nicht verwendeten Objekten
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie mit Objekten von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] arbeiten, insbesondere mit [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oder mit einem der Statement-Objekte wie [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oder [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), sollten Sie sie explizit mit den entsprechenden close-Methoden schließen, wenn sie nicht mehr benötigt werden. So wird die Leistung verbessert, da Treiber- und Serverressourcen so schnell wie möglich freigegeben werden und nicht erst darauf gewartet wird, dass dies durch den Garbage Collector der Java Virtual Machine erfolgt.  
  
 Das Schließen von Objekten ist besonders wichtig zum Erhalten der Parallelität auf dem Server, wenn Sie Rollen-Sperren verwenden. Rollen-Sperren im Fetchpuffer, auf den zuletzt zugegriffen wurde, werden beibehalten, bis das Resultset geschlossen wurde. Auf ähnliche Weise werden Handles für vorbereitete Anweisungen bis zum Schließen der Anweisung beibehalten. Wenn Sie eine Verbindung für mehrere Anweisungen wiederverwenden, führt das Schließen der Anweisungen, bevor sie den Bereich verlassen, dazu, dass der Server die vorbereiteten Handles früher bereinigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
