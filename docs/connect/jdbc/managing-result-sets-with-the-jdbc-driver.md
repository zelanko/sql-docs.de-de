---
title: Verwalten von Resultsets mit dem JDBC-Treiber legt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bb2f1743675f1ad381b9a5849cc395a5355d42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837718"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Verwalten von Resultsets mit dem JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Beim Resultset handelt es sich um ein Objekt, das die von einer Datenquelle zurückgegebenen Daten darstellt (normalerweise als Ergebnis einer Abfrage). Das Resultset enthält Zeilen und Spalten, die die angeforderten Datenelemente enthalten. Die Navigation erfolgt über einen Cursor. Ein Resultset kann aktualisiert werden, d. h., es besteht die Möglichkeit das Resultset zu ändern und diese Änderungen an die ursprüngliche Datenquelle zu übergeben. Ein Resultset kann auch unterschiedlich sensitiv gegenüber Änderungen in der zugrunde liegenden Datenquelle sein.  
  
 Der Typ des Resultset wird beim Erstellen der Anweisung bestimmt, d. h., wenn die [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse aufgerufen wird. Die grundlegende Aufgabe eines Resultsets besteht darin, Java-Anwendungen eine nutzbare Darstellung der Datenbankdaten bereitzustellen. Dies erfolgt normalerweise mit den typisierten Abruf- und Festlegungsmethoden der Datenelemente des Resultset.  
  
 Im folgenden Beispiel, das auf der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank basiert, wird durch Aufrufen der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse ein Resultset erstellt. Die Daten des Resultset werden anschließend mit der [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse angezeigt.  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 Die Themen in diesem Abschnitt beschreiben verschiedene Aspekte der Verwendung von Resultsets wie Cursortypen, Gleichzeitigkeit und Zeilensperren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Grundlegendes zu Cursortypen](../../connect/jdbc/understanding-cursor-types.md)|Beschreibt die verschiedenen Cursortypen, die von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt werden.|  
|[Grundlegendes zur Parallelitätssteuerung](../../connect/jdbc/understanding-concurrency-control.md)|Beschreibt, wie der JDBC-Treiber die Parallelitätssteuerung unterstützt.|  
|[Grundlegendes zu Zeilensperren](../../connect/jdbc/understanding-row-locking.md)|Beschreibt, wie der JDBC-Treiber Zeilensperren unterstützt.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
