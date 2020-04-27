---
title: Zuordnung von MySQL und SQL Server Zeichensatz (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 20b3f22e-16a2-4a87-b4eb-c277be6bf5c8
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 32d5e23579b99b323da870d2608b2d197520f99f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67909025"
---
# <a name="mapping-mysql-and-sql-server-character-set-mysqltosql"></a>Zuordnen von MySQL- und SQL Server-Zeichensätzen (MySqlToSql)
Der Zeichensatz (CharSet) kann für MySQL-Zeichen Datentypen, Ausdrücke und Literale angegeben werden.  
  
## <a name="charset-mapping"></a>Charset-Zuordnung  
Die charset-Zuordnung wird für jedes MySQL-Zeichensatz definiert und bei der Konvertierung von Zeichen Datentypen verwendet. Gibt an, wie Zeichen folgen Datentypen eines bestimmten Zeichensatzes konvertiert werden:  
  
-   In nationale SQL Server Zeichen Typen (nchar/nvarchar) oder  
  
-   In reguläre SQL Server Zeichen Typen (char/varchar)  
  
1.  Datentypen der Daten Bank Zeichenfolge für das **nationale** Ziel  
  
    1.  **nchar**  
  
    2.  **nvarchar**  
  
2.  die Datentypen der **regulären** Ziel Daten Bank Zeichen lauten:  
  
    1.  **char**  
  
    2.  **varchar**  
  
3.  Die Typzuordnung ermöglicht nur die Zuordnung zu Datentypen von **nationalen** Zeichen. Nachdem der MySQL-Zeichen Datentyp entsprechend der Typzuordnung konvertiert wurde, wird die charset-Zuordnung angewendet.  
  
> [!NOTE]  
> Die Zeichensatz Zuordnung kann auf jeder Knotenebene des Metadatenobjekt-Explorers definiert werden und stellt alle aus MySQL gelesenen Zeichensätzen dar.  
  
## <a name="charset-mapping-on-different-node-levels"></a>Charset-Zuordnung auf verschiedenen Knoten Ebenen  
Die Zeichensatz Zuordnung variiert auf verschiedenen Knoten Ebenen, nämlich:  
  
1.  Auf Stamm-Metadatenknoten Ebene  
  
2.  Auf Datenbank-, Kategorie-und Objekt Knotenebene  
  
> [!NOTE]  
> Die Registerkarte, die zum Bearbeiten der Zeichensatz Zuordnung ausgewählt wurde, enthält drei Schaltflächen, unabhängig von der Zuordnung auf den verschiedenen Knoten Ebenen.  
>   
> Sie lauten wie folgt:  
>   
> 1.  **Anwenden:** Wendet vom Benutzer vorgenommene Änderungen an, die nur aktiviert werden, wenn die charset-Zuordnung bearbeitet und noch nicht gespeichert wurde.  
> 2.  **Abbrechen:** Bricht die vom Benutzer vorgenommenen Änderungen ab. Die Schaltfläche wird aktiviert, wenn die Zeichensatz Zuordnung bearbeitet, aber nicht gespeichert wird.  
> 3.  **Auf Standardwert zurücksetzen:** Setzt alle Zuordnungen auf die Standardwerte zurück.  
  
1.  **Auf Stamm-Metadatenknoten Ebene:**  Das Diagramm für die charset-Zuordnung enthält das CharSet-Raster mit einer separaten Spalte für jedes CharSet. Die Spalten des Rasters lauten:  
  
    1.  Die erste Spalte des Rasters namens **CharSet Name** enthält einen charset-Namen.  
  
    2.  Die zweite Beschreibung namens **CharSet Description** enthält eine Beschreibung des Zeichensatzes.  
  
    3.  Die dritte Spalte mit dem Titel **Ziel charset** enthält Zuordnungseinstellungen für bestimmte Zeichensätze. Die Werte für diese Spalte lauten:  
  
        -   char/varchar  
  
        -   nchar/nvarchar  
  
    > [!IMPORTANT]  
    > Die Standardwerte für einen bestimmten charset haben das Präfix "(Standard)" nach char/varchar oder nchar/nvarchar.  
  
    Die Zeichensatz Zuordnung zwischen der MySQL-Datenbank und der Zieldatenbank auf der Stamm-Metadatenknoten Ebene wird unten angegeben:  
  
    ||||  
    |-|-|-|  
    |**Charset-Name**|**Zeichensatz Beschreibung**|**Ziel Zeichensatz-Typ (Standard)**|  
    |Big5|Big5 traditionelles Chinesisch|Nchar/nvarchar (Standard)|  
    |dec8|Europa, Westen|Char/varchar (Standard)|  
    |CP850|DOS West europäisch|Char/varchar (Standard)|  
    |hp8|HP West europäisch|Char/varchar (Standard)|  
    |koi8r|KOI8-R Relcom Russisch|Char/varchar (Standard)|  
    |Lateinisch 1|cp1252 West europäisch|Char/varchar (Standard)|  
    |latin2|ISO 8859-2, mitteleuropäisch|Char/varchar (Standard)|  
    |swe7|7, Schwedisch|Char/varchar (Standard)|  
    |ascii|US-ASCII|Char/varchar (Standard)|  
    |ujis|EUC-JP Japanisch|Nchar/nvarchar (Standard)|  
    |sjis|Shift-JIS Japanisch|Nchar/nvarchar (Standard)|  
    |Hebräisch|ISO 8859-8 Hebrew|Char/varchar (Standard)|  
    |tis620|Tis620 Thai|Char/varchar (Standard)|  
    |eucKR|EUC-KR Koreanisch|Nchar/nvarchar (Standard)|  
    |koi8u|KOI8-U Ukrainisch|Char/varchar (Standard)|  
    |GB2312|GB2312 vereinfachtes Chinesisch|Nchar/nvarchar (Standard)|  
    |Griechisch|ISO 8859-7 Greek|Char/varchar (Standard)|  
    |CP 1250|Windows-zentral europäisch|Char/varchar (Standard)|  
    |GBK|Vereinfachtes Chinesisch (GBK)|Nchar/nvarchar (Standard)|  
    |latin5|ISO 8859-9 Turkish|Char/varchar (Standard)|  
    |armscii8|ARMSCII-8 Armenisch|Char/varchar (Standard)|  
    |utf8|UTF-8-Unicode|Nchar/nvarchar (Standard)|  
    |ucs2|UCS-2 Unicode|Nchar/nvarchar (Standard)|  
    |cp866|DOS Russisch|Char/varchar (Standard)|  
    |keybcs2|DOS Kamenicky, Tschechisch (slowakisch)|Char/varchar (Standard)|  
    |macce|Mac Central europäisch|Char/varchar (Standard)|  
    |MacRoman|Mac West europäisch|Char/varchar (Standard)|  
    |cp852|DOS Central europäisch|Char/varchar (Standard)|  
    |latin7|ISO 8859-13-Ostsee|Char/varchar (Standard)|  
    |CP 1251|Windows-Kyrillisch|Char/varchar (Standard)|  
    |CP 1256|Windows Arabisch|Char/varchar (Standard)|  
    |CP 1257|Windows-Ostsee|Char/varchar (Standard)|  
    |BINARY|Binäres Pseudo Zeichensatz|Char/varchar (Standard)|  
    |geostd8|GEOSTD8 Georgisch|Char/varchar (Standard)|  
    |cp932|SJIS für Windows Japanisch|Nchar/nvarchar (Standard)|  
    |eucjpms|Ujis für Windows Japanisch|Nchar/nvarchar (Standard)|  
  
2.  **Auf den Ebenen Datenbank, Kategorie oder Objekt Knoten:** Auf der Ebene der Datenbank, der Kategorie oder der Objekt Knoten enthält das Diagramm für die charset-Zuordnung die gleichen Zeilen wie die auf der Stamm-metadatenknotenebene (Viz):  
  
    1.  Die erste Spalte des Rasters mit dem Namen, der **Zeichensatz Name** enthält einen charset-Namen.  
  
    2.  Die zweite Spalte mit der **Bezeichnung Zeichensatz Beschreibung** enthält eine Beschreibung des Zeichensatzes.  
  
    3.  Der einzige Unterschied sind die Werte in der dritten Spalte des Rasters. Die dritte Spalte mit dem Namen **Target Data Type** enthält Zuordnungseinstellungen für bestimmte Zeichensätze. Die Werte für die Spalte lauten:  
  
        -   Geerbt (char/varchar oder nchar/nvarchar)  
  
        -   char/varchar  
  
        -   nchar/nvarchar  
  
> [!IMPORTANT]  
> -   In der Zeichensatz Zuordnung zwischen der MySQL-Datenbank und der Zieldatenbank auf Datenbank-, Kategorie-und Objekt Knotenebene sollten die Standardwerte für ein bestimmtes Zeichensatz auf jeder anderen Ebene als der root-Wert des Spalten **Ziel-Datentyps** "geerbt" lauten.  
> -   Im Raster wird für den **geerbten** Wert entweder ' (char/varchar) ' oder ' (nchar/nvarchar) ' angehängt, je nachdem, welcher Wert von diesem bestimmten charset vom übergeordneten Element geerbt wurde.  
  
