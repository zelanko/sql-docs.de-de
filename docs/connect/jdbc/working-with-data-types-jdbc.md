---
title: Arbeiten mit Datentypen (JDBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
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
ms.openlocfilehash: cb8429fd5746369c080f7abb78f4a56adba7ad73
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456291"
---
# <a name="working-with-data-types-jdbc"></a>Arbeiten mit Datentypen (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Die Hauptfunktion von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] liegt darin, Java-Entwicklern den Zugriff auf Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbanken zu ermöglichen. Der JDBC-Treiber sorgt dazu für die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datentypen und Java-Typen und -Objekten.  
  
> [!NOTE]  
> Eine ausführliche Beschreibung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]- und JDBC-Treiberdatentypen, einschließlich deren Unterschiede und deren Konvertierung in Java-Datentypen, finden Sie unter [Understanding the JDBC Driver Data Types (Grundlegendes zu den Datentypen des JDBC-Treibers)](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Um SQL Server-Datentypen verarbeiten zu können, enthält der JDBC-Treiber get\<Type>- und set\<Type>-Methoden für die [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)- und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klassen sowie get\<Type- und update\<Type>-Methoden für die [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse. Die verwendete Methode hängt vom Datentyp ab, der verarbeitet wird, sowie davon, ob Resultsets oder Abfragen verwendet werden.  
  
Die Themen in diesem Abschnitt beschreiben, wie Sie in Java-Anwendungen unter Verwendung von JDBC-Treiberdatentypen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Daten zugreifen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Standarddatentypen – Beispiel](../../connect/jdbc/basic-data-types-sample.md)|Beschreibt, wie Werte von [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Standarddatentypen mithilfe von Abrufmethoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.|  
|[Beispiel für den SQLXML-Datentyp](../../connect/jdbc/sqlxml-data-type-sample.md)|Beschreibt das Speichern von XML-Daten in einer relationalen Datenbank, das Abrufen von XML-Daten aus einer Datenbank sowie das Analysieren von XML-Daten mit dem Java-Datentyp **SQLXML**.|  
|[Beispiel für räumliche Datentypen](../../connect/jdbc/spatial-data-types-sample.md)|Beschreibt, wie zum Speichern und Abrufen von Daten mit räumlichen Datentypen 'Geometry' und 'Geography' der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Datenbank mit **Geometrie** und **Geography** Java-Typen, die vom Microsoft JDBC-Treiber definiert.|

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Beispiele für JDBC-Treiberanwendungen](../../connect/jdbc/sample-jdbc-driver-applications.md)  
