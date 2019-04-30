---
title: Projekteinstellungen (Typzuordnung) (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e0a11a0b49589c3763b5af67623c9e819038c217
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231817"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Projekteinstellungen (Typzuordnung) (MySqlToSql)
Die projekteinstellungen Type Mapping können Sie die standardtypmappings für das SSMA-Projekt festgelegt.  

Zuordnung eines Typs ist in den Projekteinstellungen und Standardeinstellungen für die Projekt-Dialogfeldern verfügbar:  
  
-   Verwenden Sie das Dialogfeld "Projekteinstellungen", um das Festlegen von Konfigurationsoptionen für das aktuelle Projekt. Für den Zugriff auf Zuordnung die Einstellungen für den, auf das Menü "Extras", wählen Sie die Projekteinstellungen, und klicken Sie dann die Zuordnung eines Typs im linken Bereich auf.  
  
-   Verwenden Sie das Dialogfeld Projekt-Standardeinstellungen, um das Festlegen von Konfigurationsoptionen für alle Projekte. Wählen Sie auf die Zuordnung eines Typs Einstellungen, klicken Sie im Menü Extras, Projekteinstellungen Default, select Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden, **Migration Zielversion** Dropdown-Liste, und klicken Sie dann auf Die Zuordnung im linken Bereich.  
  
## <a name="options"></a>Optionen  
  
##### <a name="source-type"></a>Quelltyp  
Es ist der MySQL-Datentyp, der den Typ des Daten zugeordnet werden.  
  
##### <a name="target-type"></a>Zieltyp  
Die Datenbank Zieldatentyp für den angegebenen MySQL-Datentyp.  
  
##### <a name="add"></a>Hinzufügen  
Klicken Sie auf diese Option, um einen Datentyp der Zuordnungsliste hinzuzufügen.  
  
##### <a name="edit"></a>Bearbeiten  
Klicken Sie auf diese Option, um den ausgewählten Datentyp in der Zuordnungsliste zu bearbeiten.  
  
##### <a name="remove"></a>Entfernen  
Klicken Sie auf diese Option, um die ausgewählte Zuordnung von Datentypen aus der Zuordnungsliste zu entfernen.  
  
##### <a name="reset-to-default"></a>Standard wiederherstellen  
Klicken Sie auf diese Option, um die Liste ' datentypzuordnung ' der SSMA-Standardwerte zurückzusetzen.  
  
## <a name="type-mappings"></a>Datentypzuordnungen  
Die folgende Tabelle zeigt die Zuordnung zwischen Quelle und Ziel-Datentypen  
  
|||  
|-|-|  
|**MySQL-Datentyp**|**SQL Server-Datentyp**|  
|BIGINT|BIGINT|  
|bigint[*..255]|BIGINT|  
|BINARY|Binär [1]|  
|Binär [0.. 1]|Binär [1]|  
|Binär [2..255]|Binär [*]|  
|bit|Binär [1]|  
|Bit [0..8]|Binär [1]|  
|Bit [17..24]|Binär [3]|  
|Bit [25..32]|Binär [4]|  
|Bit [33..40]|Binär [5]|  
|Bit [41..48]|Binär [6]|  
|Bit [49..56]|Binär [7]|  
|Bit [57..64]|Binär [8]|  
|Bit [9..16]|Binär [2]|  
|Blob|varbinary(max)|  
|blob[0..1]|varbinary[1]|  
|BLOB [2..8000]|Varbinary [*]|  
|blob[8001..*]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|nchar[1]|  
|Char-byte|Binär [1]|  
|Char, Byte [0.. 1]|Binär [1]|  
|Byte [2..255] char|Binär [*]|  
|Char [0.. 1]|nchar[1]|  
|char[2..255]|NCHAR [*]|  
|character|nchar[1]|  
|Zeichen, die unterschiedliche [0.. 1]|nvarchar[1]|  
|Zeichen, die unterschiedliche [2..255]|NVARCHAR|  
|Zeichen [0.. 1]|nchar[1]|  
|Zeichen [2..255]|NCHAR [*]|  
|date|date|  
|DATETIME|datetime2 [0]|  
|dec|Decimal|  
|DEC [*... 65]|Dezimal [*] [0]|  
|DEC [*... 65] [\*... 30]|Dezimal [*] [\*]|  
|Decimal|Decimal|  
|Dezimal [*... 65]|Dezimal [*] [0]|  
|Dezimal [*... 65] [\*... 30]|Dezimal [*] [\*]|  
|double|float[53]|  
|mit doppelter Genauigkeit|float[53]|  
|Genauigkeit [*... 255] [\*... 30]|numeric[*][\*]|  
|Doppelte [*... 255] [\*... 30]|numeric[*][\*]|  
|behoben|NUMERIC|  
|feste [*... 65] [\*... 30]|numeric[*][\*]|  
|FLOAT|float[24]|  
|"float" [*... 255] [\*... 30]|numeric[*][\*]|  
|"float" [*... 53]|float[53]|  
|ssNoversion|ssNoversion|  
|Int [*... 255]|ssNoversion|  
|integer|ssNoversion|  
|ganze Zahl [*... 255]|ssNoversion|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|ssNoversion|  
|mediumint[*..255]|ssNoversion|  
|mediumtext|nvarchar(max)|  
|National char|nchar[1]|  
|National Char [0.. 1]|nchar[1]|  
|National Char [2..255]|NCHAR [*]|  
|nationale Zeichensätze|nchar[1]|  
|nationale Zeichensätze variieren.|nvarchar[1]|  
|nationale Zeichensätze, die unterschiedliche [0.. 1]|nvarchar[1]|  
|nationale Zeichensätze, die unterschiedliche [2..4000]|Nvarchar [*]|  
|nationale Zeichensätze zu unterschiedlichen [4001.. *]|nvarchar(max)|  
|nationale Zeichensätze [0.. 1]|nchar[1]|  
|nationale Zeichensätze [2..255]|NCHAR [*]|  
|National varchar|nvarchar[1]|  
|National Varchar [0.. 1]|nvarchar[1]|  
|National Varchar [2..4000]|Nvarchar [*]|  
|National Varchar [4001.. *]|nvarchar(max)|  
|NCHAR|nchar[1]|  
|Nchar, varchar|nvarchar[1]|  
|Nchar, Varchar [0.. 1]|nvarchar[1]|  
|Nchar, Varchar [2..4000]|Nvarchar [*]|  
|Nchar, Varchar [4001.. *]|nvarchar(max)|  
|NCHAR [0.. 1]|nchar[1]|  
|nchar[2..255]|NCHAR [*]|  
|NUMERIC|NUMERIC|  
|numerische [*... 65]|numerische [*] [0]|  
|numerische [*... 65] [\*... 30]|numeric[*][\*]|  
|NVARCHAR|nvarchar[1]|  
|nvarchar[0..1]|nvarchar[1]|  
|Nvarchar [2..4000]|Nvarchar [*]|  
|nvarchar[4001..*]|nvarchar(max)|  
|REAL|float[53]|  
|echte [*... 255] [\*... 30]|numeric[*][\*]|  
|serielle|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint[*..255]|SMALLINT|  
|text|nvarchar(max)|  
|Text [0.. 1]|nvarchar[1]|  
|Text [2..4000]|Nvarchar [*]|  
|text[4001..*]|nvarchar(max)|  
|time|time|  
|timestamp|DATETIME|  
|tinyblob|varbinary[255]|  
|TINYINT|SMALLINT|  
|tinyint[*..255]|SMALLINT|  
|tinytext|nvarchar[255]|  
|nicht signierte bigint|BIGINT|  
|nicht signierte Bigint [*... 255]|BIGINT|  
|nicht signierte Dez.|Decimal|  
|nicht signierte Dec [*... 65]|Dezimal [*] [0]|  
|nicht signierte Dec [*... 65] [\*... 30]|Dezimal [*] [\*]|  
|Dezimalzahl ohne Vorzeichen|Decimal|  
|Dezimalzahl ohne Vorzeichen [*... 65]|Dezimal [*] [0]|  
|Dezimalzahl ohne Vorzeichen [*... 65] [\*... 30]|Dezimal [*] [\*]|  
|Double-Wert ohne Vorzeichen|float[53]|  
|ohne Vorzeichen mit doppelter Genauigkeit|float[53]|  
|ohne Vorzeichen mit doppelten Genauigkeit [*... 255] [\*... 30]|numeric[*][\*]|  
|nicht signierte double [*... 255] [\*... 30]|numeric[*][\*]|  
|nicht signierte festen|NUMERIC|  
|nicht signierte festen [*... 65] [\*... 30]|numeric[*][\*]|  
|nicht signierte "float"|float[24]|  
|nicht signierte "float" [*... 255] [\*... 30]|numeric[*][\*]|  
|nicht signierte "float" [*... 53]|float[53]|  
|ganze Zahl ohne Vorzeichen|BIGINT|  
|ganze Zahl ohne Vorzeichen [*... 255]|BIGINT|  
|ganze Zahl ohne Vorzeichen|BIGINT|  
|ganze Zahl ohne Vorzeichen [*... 255]|BIGINT|  
|nicht signierte mediumint|ssNoversion|  
|nicht signierte Mediumint [*... 255]|ssNoversion|  
|ohne Vorzeichen, numerisch|NUMERIC|  
|nicht signierte numerische [*... 65]|numerische [*] [0]|  
|nicht signierte numerische [*... 65] [\*... 30]|numeric[*][\*]|  
|echte ohne Vorzeichen|float[53]|  
|nicht signierte echten [*... 255 [[\*... 30]|numeric[*][\*]|  
|nicht signierte smallint|ssNoversion|  
|nicht signierte Smallint [*... 255]|ssNoversion|  
|nicht signierte tinyint|TINYINT|  
|nicht signierte Tinyint [*... 255]|TINYINT|  
|Varbinary [0.. 1]|varbinary[1]|  
|Varbinary [2..8000]|Varbinary [*]|  
|Varbinary [8001.. *]|varbinary(max)|  
|varchar[0..1]|nvarchar[1]|  
|Varchar [2..4000]|Nvarchar [*]|  
|varchar[4001..*]|nvarchar(max)|  
|year|SMALLINT|  
|Jahr [2..2]|SMALLINT|  
|Jahr [4..4]|SMALLINT|  
  
##### <a name="add"></a>Hinzufügen  
Klicken Sie auf diese Option, um einen Datentyp der Zuordnungsliste hinzuzufügen.  
  
##### <a name="edit"></a>Bearbeiten  
Klicken Sie auf diese Option, um einen Datentyp aus der Zuordnung zu bearbeiten.  
  
##### <a name="remove"></a>Entfernen  
Klicken Sie auf diese Option, um die ausgewählte Zuordnung von Datentypen aus der Zuordnungsliste zu entfernen.  
  
##### <a name="reset-to-default"></a>Standard wiederherstellen  
Klicken Sie auf diese Option, um alle datentypzuordnungen der SSMA-Standardwerte zurückzusetzen.  
  
