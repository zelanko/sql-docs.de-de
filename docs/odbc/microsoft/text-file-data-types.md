---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23416cb067507d821701e57255fdc6f81ee607c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633005"
---
# <a name="text-file-data-types"></a>Textdatei-Datentypen
Die folgende Tabelle zeigt, wie Text von Datentypen in ODBC-SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC-SQL-Datentypen, die durch den Text der ODBC-Treiber unterstützt werden.  
  
|Text-Datentyp|ODBC-Datentyp|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|GLEITKOMMAZAHL|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC-Datentypen zurückgegeben. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden für die SQL-Datentypen, die in der vorherigen Tabelle aufgeführten unterstützt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Datentypen Text.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|CHAR|Erstellen eine CHAR-Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 255-Bit-Spalte zurück.<br /><br /> In durch Trennzeichen getrennte Dateien wird eine CHAR-Spalte kann, oder Sie besitzen keine Trennzeichen doppelte Anführungszeichen, am Anfang und am Ende; in Dateien mit fester Länge sind die doppelten Anführungszeichen als Trennzeichen nicht verwendet.|  
|DATETIME|MM-DD-YY (z. B. 01-17-92)<br /><br /> MMM-JJ (z. B. Januar-17-92)<br /><br /> TT-MMM-JJ (z. B. 17 Jan. 92)<br /><br /> JJJJ-MM-TT (z. B. 1992-01-17)<br /><br /> JJJJ-MMM-TT (z. B. 1992-Januar-17)<br /><br /> Gemischte Datumstrennzeichen dürfen nicht in einer Tabelle.<br /><br /> Text-ISAM-Formate ein DATETIME-Feld in den Vereinigten Staaten oder in Europa-Format, je nach der internationalen Einstellung in der Windows-Systemsteuerung.|  
|GLEITKOMMAZAHL|Die maximale Breite enthält das Zeichen und ein Dezimaltrennzeichen. In Schema.ini wird die Breite wie folgt gekennzeichnet:<br /><br /> 14.083 ist "float" Breite 6<br /><br /> -14.083 ist "float" Breite 7<br /><br /> +14.083 ist "float" Breite 7<br /><br /> 14083. ist "float" Breite 6<br /><br /> ODBC gibt immer 8 für FLOAT-Spalten zurück.<br /><br /> FLOAT-Spalten können z. B. auch in der wissenschaftlichen Schreibweise sein:<br /><br /> -3.04E + 2 ist "float" Breite 8<br /><br /> 25E4 ist "float" Breite 4<br /><br /> **Beachten Sie** Decimal "und" wissenschaftliche Notation kann nicht in einer Spalte kombiniert werden.<br /><br /> NULL-Werte werden durch eine leere aufgefüllten Zeichenfolge fester Länge Dateien dargestellt, und in Dateien mit Trennzeichen ausgelassen werden.<br /><br /> Float-Daten werden mit führenden Leerzeichen aufgefüllt.|  
|INTEGER|Gültige Werte für Spalten sind-32766 32.767.<br /><br /> In Schema.ini wird die Breite wie folgt gekennzeichnet:<br /><br /> 14083 wird die ganze Zahl Breite 5<br /><br /> 0 ist, ganze Zahl Breite 1<br /><br /> ODBC gibt immer 4 für Spalten zurück.<br /><br /> Die maximale Breite enthält ein Zeichen. Die maximale Breite der Spalte mit ganzen Zahlen ist 11, obwohl die Breite aufgrund von Leerzeichen größer sein kann, die in Tabellen mit festem Format zulässig sind.|  
|LONGCHAR|Der theoretische beschränken auf der Breite einer Spalte LONGCHAR, entweder eine feste Länge aus, oder durch Trennzeichen getrennte Tabelle kann 65500K. Text-ISAM ist eher zuverlässig unterstützen bis zu ca. 32 KB.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
