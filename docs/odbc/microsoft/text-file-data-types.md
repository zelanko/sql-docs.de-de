---
description: Textdatei-Datentypen
title: Textdatei-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d14d98f7aa25c42ec6d121aa0819a1f3dcce5db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449102"
---
# <a name="text-file-data-types"></a>Textdatei-Datentypen
In der folgenden Tabelle wird gezeigt, wie Text Datentypen ODBC-SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC-SQL-Datentypen vom ODBC-Text Treiber unterstützt werden.  
  
|Text-Datentyp|ODBC-Datentyp|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|GLEITKOMMAZAHL|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmier Referenz* werden für die SQL-Datentypen unterstützt, die in der vorherigen Tabelle aufgeführt sind.  
  
 In der folgenden Tabelle sind die Einschränkungen für Text Datentypen aufgeführt.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|CHAR|Durch das Erstellen einer char-Spalte mit 0 (null) oder einer nicht angegebenen Länge wird tatsächlich eine 255-Bit-Spalte<br /><br /> In durch Trennzeichen getrennten Dateien kann eine char-Spalte am Anfang und am Ende doppelte Anführungszeichen enthalten. in Dateien mit fester Länge werden doppelte Anführungszeichen nicht als Trennzeichen verwendet.|  
|DATETIME|MM-dd-yy (z. b. 01-17-92)<br /><br /> Mmm-dd-yy (z. b. Jan-17-92)<br /><br /> DD-mmm-yy (z. b. 17-Jan-92)<br /><br /> Yyyy-mm-dd (z. b. 1992-01-17)<br /><br /> Yyyy-MMM-DD (z. b. 1992-Jan-17)<br /><br /> Trennzeichen für gemischte Datumsangaben sind innerhalb einer Tabelle nicht zulässig.<br /><br /> Der Text ISAM formatiert ein DateTime-Feld im USA-oder europäischen Format, abhängig von der internationalen Einstellung in der Windows-Systemsteuerung.|  
|GLEITKOMMAZAHL|Die maximale Breite umfasst das Vorzeichen und den Dezimaltrennzeichen. In Schema.ini wird die Breite wie folgt angegeben:<br /><br /> 14,083 ist float-Breite 6<br /><br /> -14,083 ist float-Breite 7<br /><br /> + 14,083 ist float-Breite 7<br /><br /> 14083. ist float-Breite 6<br /><br /> ODBC gibt immer 8 für float-Spalten zurück.<br /><br /> FLOAT-Spalten können sich auch in wissenschaftlicher Notation befinden, z. b.:<br /><br /> -3,04 e + 2 ist float-Breite 8<br /><br /> 25e4 ist float-Breite 4<br /><br /> **Hinweis** Die Dezimal-und wissenschaftliche Schreibweise können nicht in einer Spalte gemischt werden.<br /><br /> NULL-Werte werden in Dateien mit fester Länge durch eine leere, aufgefüllte Zeichenfolge dargestellt und in durch Trennzeichen getrennten Dateien ausgelassen.<br /><br /> Float-Daten können mit führenden Leerzeichen aufgefüllt werden.|  
|INTEGER|Gültige Werte für ganzzahlige Spalten sind 32767 bis 32766.<br /><br /> In Schema.ini wird die Breite wie folgt angegeben:<br /><br /> 14083 ist eine ganzzahlige Breite 5<br /><br /> 0 ist ganzzahlige Breite 1<br /><br /> ODBC gibt immer 4 für ganzzahlige Spalten zurück.<br /><br /> Die maximale Breite umfasst ein Vorzeichen. Die maximale Breite einer ganzzahligen Spalte ist 11, obwohl die Breite aufgrund von Leerzeichen, die in Tabellen mit festem Format zulässig sind, größer sein kann.|  
|LONGCHAR|Der theoretische Grenzwert für die Breite einer LONGCHAR-Spalte in einer Tabelle mit fester Länge oder einer durch Trennzeichen getrennten Tabelle ist 65500k. Der Text-ISAM bietet eine zuverlässige Unterstützung von bis zu etwa 32K.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).
