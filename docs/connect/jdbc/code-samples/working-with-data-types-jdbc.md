---
title: Arbeiten mit Datentypen (JDBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d05200ff0c634ea327e58e5288ff8e99c0ec9418
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922559"
---
# <a name="working-with-data-types-jdbc"></a>Arbeiten mit Datentypen (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Die Hauptfunktion von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] liegt darin, Java-Entwicklern den Zugriff auf Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken zu ermöglichen. Der JDBC-Treiber sorgt dazu für die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen und Java-Typen und -Objekten.  
  
> [!NOTE]  
> Eine ausführliche Beschreibung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]- und JDBC-Treiberdatentypen, einschließlich deren Unterschiede und deren Konvertierung in Java-Datentypen, finden Sie unter [Grundlegendes zu den Datentypen des JDBC-Treibers](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Um SQL Server-Datentypen verarbeiten zu können, enthält der JDBC-Treiber get\<Type>- und set\<Type>-Methoden für die [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)- und [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klassen sowie get\<Type- und update\<Type>-Methoden für die [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse. Die verwendete Methode hängt vom Datentyp ab, der verarbeitet wird, sowie davon, ob Resultsets oder Abfragen verwendet werden.  
  
Die Themen in diesem Abschnitt beschreiben, wie Sie in Java-Anwendungen unter Verwendung von JDBC-Treiberdatentypen auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten zugreifen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                         | BESCHREIBUNG                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Beispiel zu Standarddatentypen](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Beschreibt, wie Werte von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standarddatentypen mithilfe von Abrufmethoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.                                             |
| [Beispiel für den SQLXML-Datentyp](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Beschreibt das Speichern von XML-Daten in einer relationalen Datenbank, das Abrufen von XML-Daten aus einer Datenbank sowie das Analysieren von XML-Daten mit dem Java-Datentyp **SQLXML**.                                                                                   |
| [Beispiel für räumliche Datentypen](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | In diesem Thema wird beschrieben, wie Sie in SQL Server räumliche Datentypen speichern, und wie Sie diese aus SQL Server wieder abrufen. Außerdem wird darauf eingegangen, wie Sie die neu definierten Klassen **Geometrie** und **Geografie** aus dem Treiber verwenden, um Java-Verweise auf diese Datentypen zu verwalten. |
  
## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
