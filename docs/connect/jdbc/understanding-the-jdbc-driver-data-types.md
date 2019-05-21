---
title: Grundlegendes zu den Datentypen des JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c3712370fef840e8bf265850d9ad4dbd946a52b
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905011"
---
# <a name="understanding-the-jdbc-driver-data-types"></a>Grundlegendes zu den Datentypen in JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt die Verwendung von einfachen und erweiterten JDBC-Datentypen in einer Java-Anwendung, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Datenbank verwendet.  
  
Das JDBC-Typsystem vermittelt die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen und Java-Typen und -Objekten. Die JDBC-Typen beruhen auf den SQL-92- und SQL-99-Typen. Der JDBC-Treiber befolgt die JDBC-Spezifikation und stellt eine optimale Balance zwischen Vorhersehbarkeit und Flexibilität bereit.  
  
Die Themen in diesem Abschnitt beschreiben die Verwendung der grundlegenden und erweiterten Datentypen sowie das Konvertieren der Datentypen in andere Datentypen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                                                                            | Beschreibung                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Verwenden von Standarddatentypen](../../connect/jdbc/using-basic-data-types.md)                                                                           | Beschreibt die grundlegenden JDBC-Datentypen. Umfasst Beispiele zum Arbeiten mit den Datentypen mithilfe von Resultsets, parametrisierten Abfragen und gespeicherten Prozeduren.                                                                                                        |
| [Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md) | Beschreibt die Generierung von Datumsangaben durch den JDBC-Treiber.                                                                                                                                                                                                                       |
| [Verwenden von erweiterten Datentypen](../../connect/jdbc/using-advanced-data-types.md)                                                                     | Beschreibt die erweiterten JDBC-Datentypen.                                                                                                                                                                                                                              |
| [Grundlegendes zu den Unterschieden von Datentypen](../../connect/jdbc/understanding-data-type-differences.md)                                                 | Beschreibt Unterschiede zwischen den verschiedenen Datentypen des JDBC-Treibers.                                                                                                                                                                                                    |
| [Grundlegendes zu Datentypkonvertierungen](../../connect/jdbc/understanding-data-type-conversions.md)                                                 | Beschreibt, wie die Datentypkonvertierung bei der Verwendung von Methoden zum Festlegen und Abrufen behandelt wird.                                                                                                                                                                                  |
| [Unterstützung für nationale Zeichensätze](../../connect/jdbc/national-character-set-support.md)                                                           | Beschreibt die Unterstützung der Typen für nationale Zeichensätze.                                                                                                                                                                                                          |
| [Unterstützen von XML-Daten](../../connect/jdbc/supporting-xml-data.md)                                                                                 | Beschreibt die SQLXML-Schnittstelle. Beschreibt außerdem, wie Sie XML-Daten mit dem **SQLXML**-Java-Datentyp in bzw. aus einer relationalen Datenbank schreiben und lesen.                                                                                                             |
| [Wrapper und Schnittstellen](../../connect/jdbc/wrappers-and-interfaces.md)                                                                         | Behandelt die Schnittstellen, die über die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-spezifischen Methoden und Konstanten verfügen und es einem Anwendungsserver ermöglichen, einen Proxy der Klasse zu erstellen. Behandelt außerdem Unterstützungen für die `java.sql.Wrapper`-Schnittstelle. |
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
