---
title: Textdatei-Datentypen | Microsoft Docs
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
ms.openlocfilehash: 7864dc81eaa3dd37f3d0053b2329c8842e445c8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302658"
---
# <a name="text-file-data-types"></a>Textdatei-Datentypen
Die folgende Tabelle zeigt, wie Textdatentypen ODBC SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC SQL-Datentypen vom ODBC-Texttreiber unterstützt werden.  
  
|Textdatentyp|ODBC-Datentyp|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|GLEITKOMMAZAHL|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmierreferenz* werden für die in der vorherigen Tabelle aufgeführten SQL-Datentypen unterstützt.  
  
 Die folgende Tabelle zeigt Einschränkungen für Textdatentypen.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|CHAR|Beim Erstellen einer CHAR-Spalte mit Null oder nicht angegebener Länge wird tatsächlich eine 255-Bit-Spalte zurückgegeben.<br /><br /> In abgegrenzten Dateien kann eine CHAR-Spalte am Anfang und am Ende doppelte Anführungszeichentrennzeichen haben. in Dateien fester Länge werden doppelte Anführungszeichen nicht als Trennzeichen verwendet.|  
|DATETIME|MM-DD-YY (z.B. 01-17-92)<br /><br /> MMM-DD-YY (z. B. Jan-17-92)<br /><br /> DD-MMM-YY (z. B. 17-Jan-92)<br /><br /> YYYY-MM-DD (z.B. 1992-01-17)<br /><br /> YYYY-MMM-DD (z. B. 1992-Jan-17)<br /><br /> Gemischte Datumstrennzeichen sind in einer Tabelle nicht zulässig.<br /><br /> Der Text-ISAM formatiert ein DATETIME-Feld im Format USA oder Europa, abhängig von der Einstellung International in der Windows-Systemsteuerung.|  
|GLEITKOMMAZAHL|Die maximale Breite enthält das Vorzeichen und das Dezimalkomma. In Schema.ini wird die Breite wie folgt bezeichnet:<br /><br /> 14.083 ist FLOAT Breite 6<br /><br /> -14.083 ist FLOAT Breite 7<br /><br /> +14.083 ist FLOAT Breite 7<br /><br /> 14083. ist FLOAT Breite 6<br /><br /> ODBC gibt immer 8 für FLOAT-Spalten zurück.<br /><br /> FLOAT-Spalten können auch in wissenschaftlicher Notation sein, z. B.:<br /><br /> -3.04E+2 ist Float breite 8<br /><br /> 25E4 ist Float breite 4<br /><br /> **Hinweis** Dezimal- und wissenschaftliche Notation können nicht in einer Spalte gemischt werden.<br /><br /> NULL-Werte werden durch eine leere gepolsterte Zeichenfolge in Dateien fester Länge dargestellt und in Dateien mit Trennzeichen weggelassen.<br /><br /> Float-Daten können mit führenden Leerzeichen aufgepolstert werden.|  
|INTEGER|Gültige Werte für INTEGER-Spalten sind 32767 bis -32766.<br /><br /> In Schema.ini wird die Breite wie folgt bezeichnet:<br /><br /> 14083 ist INTEGER Breite 5<br /><br /> 0 ist INTEGER Breite 1<br /><br /> ODBC gibt immer 4 für INTEGER-Spalten zurück.<br /><br /> Die maximale Breite enthält ein Vorzeichen. Die maximale Breite einer INTEGER-Spalte beträgt 11, obwohl die Breite aufgrund von Leerzeichen, die in Tabellen mit festem Format zulässig sind, größer sein kann.|  
|LONGCHAR|Die theoretische Grenze für die Breite einer LONGCHAR-Säule in einer Tabelle mit fester Länge oder einer abgegrenzten Tabelle beträgt 65500K. Der Text-ISAM bietet eher zuverlässige Unterstützung bis zu etwa 32 K.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentypeinschränkungen](../../odbc/microsoft/data-type-limitations.md).
