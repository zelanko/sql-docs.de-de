---
title: Arbeiten mit Datentypen (JDBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81a71bc89bf4dcf62bb5119bc8af60664f33a75a
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784066"
---
# <a name="working-with-data-types-jdbc"></a>Arbeiten mit Datentypen (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Die Hauptfunktion von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] liegt darin, Java-Entwicklern den Zugriff auf Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken zu ermöglichen. Der JDBC-Treiber sorgt dazu für die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen und Java-Typen und -Objekten.  
  
> [!NOTE]  
> Eine ausführliche Beschreibung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]- und JDBC-Treiberdatentypen, einschließlich deren Unterschiede und deren Konvertierung in Java-Datentypen, finden Sie unter [Understanding the JDBC Driver Data Types (Grundlegendes zu den Datentypen des JDBC-Treibers)](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Um SQL Server-Datentypen verarbeiten zu können, enthält der JDBC-Treiber get\<Type>- und set\<Type>-Methoden für die [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)- und [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klassen sowie get\<Type- und update\<Type>-Methoden für die [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse. Die verwendete Methode hängt vom Datentyp ab, der verarbeitet wird, sowie davon, ob Resultsets oder Abfragen verwendet werden.  
  
Die Themen in diesem Abschnitt beschreiben, wie Sie in Java-Anwendungen unter Verwendung von JDBC-Treiberdatentypen auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Daten zugreifen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                         | und Beschreibung                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Standarddatentypen – Beispiel](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Beschreibt, wie Werte von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standarddatentypen mithilfe von Abrufmethoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.                                             |
| [Beispiel für den SQLXML-Datentyp](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Beschreibt das Speichern von XML-Daten in einer relationalen Datenbank, das Abrufen von XML-Daten aus einer Datenbank sowie das Analysieren von XML-Daten mit dem Java-Datentyp **SQLXML**.                                                                                   |
| [Beispiel für räumliche Datentypen](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Beschreibt, wie zum Speichern von räumlichen Datentypen in SQL Server und diese Typen von SQL Server abzurufen. Außerdem erläutert, wie neu definierte Klassen **Geometrie** und **Geography** aus dem Treiber für die Verwaltung von Java-Referenz mit diesen Datentypen. |
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
