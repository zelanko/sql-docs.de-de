---
title: Zuordnen von MySQL und SQL Server-Zeichen festgelegt (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 20b3f22e-16a2-4a87-b4eb-c277be6bf5c8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cebdf2ed28287a59ec9d4f0daaa1d0c200f8fe20
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312373"
---
# <a name="mapping-mysql-and-sql-server-character-set-mysqltosql"></a>Zuordnen von MySQL- und SQL Server-Zeichensätzen (MySqlToSql)
Zeichensatz (Charset) kann für die MySQL-Datentypen, Ausdrücke und Literale angegeben werden.  
  
## <a name="charset-mapping"></a>CharSet-Zuordnung  
CharSet-Zuordnung ist für die einzelnen MySQL-Zeichensatz definiert, während der datentypkonvertierung für Zeichen. Es gibt an, wie Zeichenfolgen-Datentypen von einem bestimmten Zeichensatz zu konvertieren:  
  
-   National SQL Server-Zeichen-Datentypen (NCHAR/NVARCHAR) oder  
  
-   Reguläre SQL Server-Zeichen-Datentypen (CHAR/VARCHAR)  
  
1.  **National** Ziel-Datenbank-Datentypen sind:  
  
    1.  **nchar**  
  
    2.  **nvarchar**  
  
2.  **reguläre** Ziel-Datenbank-Datentypen sind:  
  
    1.  **char**  
  
    2.  **varchar**  
  
3.  Typzuordnung lässt nur eine Zuordnung zu **national** Zeichendatentypen. Nachdem MySQL Zeichendatentyp gemäß der Zuordnung eines Typs konvertiert wurde, wird der Charset-Zuordnung angewendet.  
  
> [!NOTE]  
> CharSet-Zuordnung kann auf jeder Knotenebene des Objekt-Explorers Metadaten definiert werden und Darstellen von allen Zeichensätzen, die von MySQL zu lesen.  
  
## <a name="charset-mapping-on-different-node-levels"></a>CharSet-Zuordnung auf unterschiedlichen Knotenebenen  
Zuordnen von CharSet variiert auf unterschiedlichen Knotenebenen, nämlich:  
  
1.  Auf Ebene des Schemastammknotens Metadaten  
  
2.  Für Datenbank, Kategorie und Objektebene für Knoten  
  
> [!NOTE]  
> Die Registerkarte für die Bearbeitung der Charset-Zuordnung, ausgewählte enthält drei Schaltflächen, unabhängig von der Zuordnung für die unterschiedlichen Knotenebenen.  
>   
> Die Überladungen sind:  
>   
> 1.  **Gelten:** Wendet die Änderungen durch den Benutzer, die nur aktiviert, wenn Charset-Zuordnung bearbeitet und noch nicht gespeichert ist.  
> 2.  **Abbrechen:** Bricht die Änderungen, die vom Benutzer ab. Die Schaltfläche wird aktiviert, wenn Charset-Zuordnung bearbeitet, aber nicht gespeichert.  
> 3.  **Auf Standardwert zurücksetzen:** Setzt alle Zuordnungen auf Standardwerte zurück.  
  
1.  **Auf Metadaten Ebene des Schemastammknotens:**  CharSet-Zuordnungsraster enthält Charset-Raster mit einer separaten Spalte für jeden Zeichensatz. Die Spalten des Rasters sind:  
  
    1.  Die erste Spalte des Rasters mit dem Namen **Charset-Name** Charset-Namen enthält.  
  
    2.  Das zweite Argument, das mit dem Namen **Charset-Beschreibung** Charset-Beschreibung enthält.  
  
    3.  Die dritte Spalte mit dem Titel **Charset-Zieltyp** enthält Einstellungen für die Zuordnung für den bestimmten Zeichensatz. Werte für diese Spalte sind:  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
    > [!IMPORTANT]  
    > Die Standardwerte für einen bestimmten Zeichensatz haben das Präfix "(Default)" nach CHAR/VARCHAR oder NCHAR/NVARCHAR.  
  
    Die Charset-Zuordnung zwischen MySQL-Datenbank und die Zieldatenbank auf Ebene des Schemastammknotens Metadaten wird unten angezeigt:  
  
    ||||  
    |-|-|-|  
    |**CharSet-Name**|**CharSet-Beschreibung**|**Ziel-Charset-Typ (Standard)**|  
    |Big5|Chinesisch (traditionell) Big5|NCHAR/NVARCHAR (Standard)|  
    |dec8|DEC-West-Europäischen|CHAR/VARCHAR (Standard)|  
    |cp850|DOS-West-Europäischen|CHAR/VARCHAR (Standard)|  
    |hp8|HP West European|CHAR/VARCHAR (Standard)|  
    |koi8r|KOI8-R Relcom Russisch|CHAR/VARCHAR (Standard)|  
    |Latin 1|cp1252 West Europäischen|CHAR/VARCHAR (Standard)|  
    |Lateinisch-2|ISO 8859-2 Mitteleuropa|CHAR/VARCHAR (Standard)|  
    |swe7|7-Bit-Schwedisch|CHAR/VARCHAR (Standard)|  
    |ascii|US-ASCII|CHAR/VARCHAR (Standard)|  
    |ujis|EUC-JP-Japanisch|NCHAR/NVARCHAR (Standard)|  
    |SJIS|Shift-JIS-Japanisch|NCHAR/NVARCHAR (Standard)|  
    |Hebräisch|ISO 8859-8 Hebrew|CHAR/VARCHAR (Standard)|  
    |tis620|TIS620 Thai|CHAR/VARCHAR (Standard)|  
    |eucKR|EUC-KR Koreanisch|NCHAR/NVARCHAR (Standard)|  
    |koi8u|KOI8-U Ukrainisch|CHAR/VARCHAR (Standard)|  
    |gb2312|GB2312 Chinesisch (vereinfacht)|NCHAR/NVARCHAR (Standard)|  
    |Griechisch|ISO 8859-7 Greek|CHAR/VARCHAR (Standard)|  
    |CP-1250|Windows Central European|CHAR/VARCHAR (Standard)|  
    |gbk|Chinesisch vereinfacht, GBK|NCHAR/NVARCHAR (Standard)|  
    |latin5|ISO 8859-9 Turkish|CHAR/VARCHAR (Standard)|  
    |armscii8|ARMSCII-8-Armenisch|CHAR/VARCHAR (Standard)|  
    |utf8|UTF-8 Unicode|NCHAR/NVARCHAR (Standard)|  
    |ucs2|UCS-2-Unicode|NCHAR/NVARCHAR (Standard)|  
    |cp866|DOS-Russisch|CHAR/VARCHAR (Standard)|  
    |keybcs2|DOS Kamenicky Tschechisch-Slowakisch|CHAR/VARCHAR (Standard)|  
    |macce|Mitteleuropäisch für Mac|CHAR/VARCHAR (Standard)|  
    |MacRoman|Mac-West-Europäischen|CHAR/VARCHAR (Standard)|  
    |cp852|DOS-Central Europäischen|CHAR/VARCHAR (Standard)|  
    |latin7|ISO 8859-13 Baltic|CHAR/VARCHAR (Standard)|  
    |CP-1251|Windows Cyrillic|CHAR/VARCHAR (Standard)|  
    |cp 1256|Windows Arabic|CHAR/VARCHAR (Standard)|  
    |cp 1257|Windows Baltic|CHAR/VARCHAR (Standard)|  
    |BINARY|Binäre Pseudo-Zeichensatz|CHAR/VARCHAR (Standard)|  
    |geostd8|GEOSTD8 Georgian|CHAR/VARCHAR (Standard)|  
    |cp932|SJIS für Windows-Japanisch|NCHAR/NVARCHAR (Standard)|  
    |eucjpms|UJIS für Windows-Japanisch|NCHAR/NVARCHAR (Standard)|  
  
2.  **Für die Datenbank, Kategorie oder Objektebenen-Knoten:** Auf der Ebene des-Datenbank, Kategorie oder Objektknoten enthält Charset-Zuordnungsraster dieselben Zeilen wie die 1 auf Ebene des schemastammknotens Metadaten, viz.:  
  
    1.  Die erste Spalte des Rasters mit dem Titel **Zeichenname festgelegt** Charset-Namen enthält.  
  
    2.  Die zweite Spalte, die mit dem Titel **Beschreibung von Zeichen festlegen** Charset-Beschreibung enthält.  
  
    3.  Der einzige Unterschied ist die Werte in der dritten Spalte des Rasters. Die dritte Spalte mit dem Titel **Zieldatentyp** enthält Einstellungen für die Zuordnung für den bestimmten Zeichensatz. Die Werte für die Spalte sind:  
  
        -   Geerbt (CHAR/VARCHAR oder NCHAR/NVARCHAR)  
  
        -   CHAR/VARCHAR  
  
        -   NCHAR/NVARCHAR  
  
> [!IMPORTANT]  
> -   In der Charset-Zuordnung zwischen MySQL-Datenbank und die Zieldatenbank auf Datenbank-, Kategorie und Objekt-Knoten, die Standardwerte für einen bestimmten Zeichensatz für jede Ebene als Stammverzeichnis für die Spalte **Zieldatentyp** muss ' Geerbte ".  
> -   Im Raster des Werts **geerbte** ist, die entweder mit dem Suffix '(CHAR/VARCHAR)' oder '(NCHAR/NVARCHAR) "je nachdem, welcher Wert von diesem bestimmten Zeichensatz vom übergeordneten Element geerbt wurde.  
  
