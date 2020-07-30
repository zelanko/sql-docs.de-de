---
title: Projekteinstellungen (Typzuordnung) (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7add1259778bf189c981d5b302e989bf7bc233c3
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396560"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Projekteinstellungen (Typzuordnung) (MySqlToSql)
Mit den Projekteinstellungen für die Typzuordnung können Sie Standardtypmappings für das SSMA-Projekt festlegen.  

Die Typzuordnung ist in den Dialogfeldern Projekteinstellungen und Standard Projekteinstellungen verfügbar:  
  
-   Verwenden Sie das Dialogfeld Projekteinstellungen, um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die typzuordnungseinstellungen zuzugreifen, wählen Sie im Menü Extras die Option Projekteinstellungen aus, und klicken Sie dann im linken Bereich auf Typzuordnung.  
  
-   Verwenden Sie das Dialogfeld Standard Projekteinstellungen, um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die typzuordnungseinstellungen zuzugreifen, wählen Sie im Menü Extras die Option Standard Projekteinstellungen aus, wählen Sie den Migrations Projekttyp, für den die Einstellungen angezeigt werden müssen/Changed in der Dropdown Liste **Migrations Ziel Version** aus, und klicken Sie im linken Bereich auf Typzuordnung.  
  
## <a name="options"></a>Optionen  
  
##### <a name="source-type"></a>Quellentyp  
Dabei handelt es sich um den MySQL-Datentyp, der dem Datentyp der Zieldatenbank zugeordnet werden muss.  
  
##### <a name="target-type"></a>Zieltyp  
Der Datentyp der Zieldatenbank für den angegebenen MySQL-Datentyp.  
  
##### <a name="add"></a>Hinzufügen  
Klicken Sie hier, um der Zuordnungsliste einen Datentyp hinzuzufügen.  
  
##### <a name="edit"></a>Bearbeiten  
Klicken Sie hierauf, um den ausgewählten Datentyp in der Liste Zuordnung zu bearbeiten.  
  
##### <a name="remove"></a>Remove (Entfernen)  
Klicken Sie hierauf, um die ausgewählte Datentyp Zuordnung aus der Liste Zuordnung zu entfernen.  
  
##### <a name="reset-to-default"></a>Standard wiederherstellen  
Klicken Sie hier, um die Liste Typzuordnung auf die SSMA-Standardwerte zurückzusetzen.  
  
## <a name="type-mappings"></a>Typzuordnungen  
Die folgende Tabelle zeigt die Standard Zuordnung zwischen Quell-und Ziel Datentypen.  
  
|MySQL-Datentyp|SQL Server-Datentyp|  
|-|-|  
|BIGINT|BIGINT|  
|bigint [*.. 255]|BIGINT|  
|BINARY|Binär [1]|  
|Binär [0.. 1]|Binär [1]|  
|Binär [2.. 255]|Binär [*]|  
|bit|Binär [1]|  
|Bit [0.. 8]|Binär [1]|  
|Bit [17.. 24]|Binär [3]|  
|Bit [25.. 32]|Binär [4]|  
|Bit [33.. 40]|Binär [5]|  
|Bit [41.. 48]|Binär [6]|  
|Bit [49.. 56]|Binär [7]|  
|Bit [57... 64]|Binär [8]|  
|Bit [9.. 16]|Binär [2]|  
|Blob|varbinary(max)|  
|BLOB [0.. 1]|varbinary [1]|  
|BLOB [2.. 8000]|varbinary [*]|  
|BLOB [8001.. *]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|NCHAR [1]|  
|char-Byte|Binär [1]|  
|char-Byte [0.. 1]|Binär [1]|  
|char-Byte [2.. 255]|Binär [*]|  
|Char [0.. 1]|NCHAR [1]|  
|Char [2.. 255]|NCHAR [*]|  
|character|NCHAR [1]|  
|Zeichen variiert [0.. 1]|nvarchar [1]|  
|Zeichen variierend [2.. 255]|NVARCHAR|  
|Zeichen [0.. 1]|NCHAR [1]|  
|Zeichen [2.. 255]|NCHAR [*]|  
|date|date|  
|datetime|datetime2 [0]|  
|dec|Decimal|  
|Dez [*... 65]|Dezimalzahl [*] [0]|  
|Dez [*... 65] [ \* .. 4.30|Dezimalzahl [*] [ \* ]|  
|Decimal|Decimal|  
|Dezimalzahl [*.. 65]|Dezimalzahl [*] [0]|  
|Dezimalzahl [*.. 65] [ \* .. 4.30|Dezimalzahl [*] [ \* ]|  
|double|float [53]|  
|double precision|float [53]|  
|doppelte Genauigkeit [*. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|Double [*. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|fixed|NUMERIC|  
|korrigiert [*.. 65] [ \* .. 4.30|numerisch [*] [ \* ]|  
|float|float [24]|  
|float [*. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|float [*. 53]|float [53]|  
|INT|INT|  
|int [*.. 255]|INT|  
|integer|INT|  
|Ganzzahl [*. 255]|INT|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|INT|  
|mediumschlag [*.. 255]|INT|  
|mediumtext|nvarchar(max)|  
|National Char|NCHAR [1]|  
|National Char [0.. 1]|NCHAR [1]|  
|National Char [2.. 255]|NCHAR [*]|  
|Länder Zeichen|NCHAR [1]|  
|unterschiedliches Zeichen|nvarchar [1]|  
|unterschiedliches Zeichen [0.. 1]|nvarchar [1]|  
|unterschiedliche Länder Zeichen [2.. 4000]|nvarchar [*]|  
|unterschiedliches Zeichen [4001.. *]|nvarchar(max)|  
|National Character [0.. 1]|NCHAR [1]|  
|Länder Zeichen [2.. 255]|NCHAR [*]|  
|National varchar|nvarchar [1]|  
|National varchar [0.. 1]|nvarchar [1]|  
|National varchar [2.. 4000]|nvarchar [*]|  
|National varchar [4001.. *]|nvarchar(max)|  
|NCHAR|NCHAR [1]|  
|NCHAR varchar|nvarchar [1]|  
|NCHAR varchar [0.. 1]|nvarchar [1]|  
|NCHAR varchar [2.. 4000]|nvarchar [*]|  
|NCHAR varchar [4001.. *]|nvarchar(max)|  
|NCHAR [0.. 1]|NCHAR [1]|  
|NCHAR [2.. 255]|NCHAR [*]|  
|NUMERIC|NUMERIC|  
|numerisch [*.. 65]|numerisch [*] [0]|  
|numerisch [*.. 65] [ \* .. 4.30|numerisch [*] [ \* ]|  
|NVARCHAR|nvarchar [1]|  
|nvarchar [0.. 1]|nvarchar [1]|  
|nvarchar [2.. 4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|real|float [53]|  
|Real [*. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|serial|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*.. 255]|SMALLINT|  
|text|nvarchar(max)|  
|Text [0.. 1]|nvarchar [1]|  
|Text [2.. 4000]|nvarchar [*]|  
|Text [4001.. *]|nvarchar(max)|  
|time|time|  
|timestamp|datetime|  
|tinyblob|varbinary [255]|  
|TINYINT|SMALLINT|  
|tinyint [*.. 255]|SMALLINT|  
|tinytext|nvarchar [255]|  
|nicht signiertes bigint|BIGINT|  
|nicht signiertes bigint [*. 255]|BIGINT|  
|nicht signierte Dec|Decimal|  
|nicht signierte Dec [*.. 65]|Dezimalzahl [*] [0]|  
|nicht signierte Dec [*.. 65] [ \* .. 4.30|Dezimalzahl [*] [ \* ]|  
|Dezimaltrennzeichen ohne Vorzeichen|Decimal|  
|unsigniertes Dezimaltrennzeichen [*. 65]|Dezimalzahl [*] [0]|  
|unsigniertes Dezimaltrennzeichen [*. 65] [ \* .. 4.30|Dezimalzahl [*] [ \* ]|  
|Double ohne Vorzeichen|float [53]|  
|doppelte Genauigkeit ohne Vorzeichen|float [53]|  
|doppelte Genauigkeit ohne Vorzeichen [*.. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|Ganzzahl ohne Vorzeichen Double [*.. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|nicht signiertes Fixed|NUMERIC|  
|nicht signiertes festes [*.. 65] [ \* .. 4.30|numerisch [*] [ \* ]|  
|Ganzzahl ohne Vorzeichen float|float [24]|  
|Ganzzahl ohne Vorzeichen float [*.. 255] [ \* .. 4.30|numerisch [*] [ \* ]|  
|Ganzzahl ohne Vorzeichen float [*.. 53]|float [53]|  
|unsigned int|BIGINT|  
|Ganzzahl ohne Vorzeichen int [*.. 255]|BIGINT|  
|Ganzzahl ohne Vorzeichen|BIGINT|  
|Ganzzahl ohne Vorzeichen [*. 255]|BIGINT|  
|nicht signiertes mediumschlag|INT|  
|nicht signiertes mediumschlag [*. 255]|INT|  
|nicht signierte numerische Werte|NUMERIC|  
|unsignierter numerischer Wert [*.. 65]|numerisch [*] [0]|  
|unsignierter numerischer Wert [*.. 65] [ \* .. 4.30|numerisch [*] [ \* ]|  
|Ganzzahl ohne Vorzeichen Real|float [53]|  
|Ganzzahl ohne Vorzeichen Real [*. 255 [[ \* ... 4.30|numerisch [*] [ \* ]|  
|smallint ohne Vorzeichen|INT|  
|smallint ohne Vorzeichen [*. 255]|INT|  
|nicht signiertes tinyint|TINYINT|  
|Ganzzahl ohne Vorzeichen tinyint [*. 255]|TINYINT|  
|varbinary [0.. 1]|varbinary [1]|  
|varbinary [2.. 8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [0.. 1]|nvarchar [1]|  
|varchar [2.. 4000]|nvarchar [*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|Jahr [2.. 2]|SMALLINT|  
|Jahr [4.. 4]|SMALLINT|  
  
##### <a name="add"></a>Hinzufügen  
Klicken Sie hier, um der Zuordnungsliste einen Datentyp hinzuzufügen.  
  
##### <a name="edit"></a>Bearbeiten  
Klicken Sie hierauf, um einen Datentyp in der Liste Zuordnung zu bearbeiten.  
  
##### <a name="remove"></a>Remove (Entfernen)  
Klicken Sie hierauf, um die ausgewählte Datentyp Zuordnung aus der Liste Zuordnung zu entfernen.  
  
##### <a name="reset-to-default"></a>Standard wiederherstellen  
Klicken Sie hier, um alle Datentyp Zuordnungen auf die SSMA-Standardwerte zurückzusetzen.  
  
