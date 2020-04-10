---
title: PHP-Standarddatentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3f5210d54fdd5a0a693f9cb7fdf8a7d4fc0f183
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928029"
---
# <a name="default-php-data-types"></a>PHP-Standarddatentypen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn vom Benutzer kein PHP-Datentyp angegeben wurde, werden die Daten beim Abrufen vom Server von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] in einen PHP-Standarddatentyp konvertiert.  
  
Wenn Daten mit dem Treiber PDO_SQLSRV zurückgegeben werden, wird als Datentyp entweder „int“ oder „string“ verwendet.  
  
Im weiteren Verlauf dieses Themas werden die Standarddatentypen erläutert, die den SQLSRV-Treiber verwenden.  
  
Die folgende Tabelle enthält den SQL Server-Datentyp (der Datentyp, der vom Server abgerufen wird), den PHP-Standarddatentyp (der Datentyp, in den Daten konvertiert werden) und die Standardcodierung für Datenströme und Zeichenfolgen. Weitere Informationen dazu, wie Sie Datentypen beim Abrufen von Daten vom Server festlegen, finden Sie unter [Vorgehensweise: Festlegen von PHP-Datentypen](../../connect/php/how-to-specify-php-data-types.md).  
  
|SQL Server-Typ|PHP-Standardtyp|Standardcodierung|  
|-------------------|--------------------|--------------------|  
|BIGINT|String|8-Bit-Zeichen<sup>1</sup>|  
|BINARY|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|bit|Integer|8-Bit-Zeichen<sup>1</sup>|  
|char|String|8-Bit-Zeichen<sup>1</sup>|  
|Datum<sup>4</sup>|Datetime|Nicht verfügbar|  
|datetime<sup>4</sup>|Datetime|Nicht verfügbar|  
|datetime2<sup>4</sup>|Datetime|Nicht verfügbar|  
|datetimeoffset<sup>4</sup>|Datetime|Nicht verfügbar|  
|Decimal|String|8-Bit-Zeichen<sup>1</sup>|  
|float|Float|8-Bit-Zeichen<sup>1</sup>|  
|geography|Datenstrom|Binär<sup>3</sup>|  
|Geometrie|Datenstrom|Binär<sup>3</sup>|  
|image<sup>5</sup>|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|INT|Integer|8-Bit-Zeichen<sup>1</sup>|  
|money|String|8-Bit-Zeichen<sup>1</sup>|  
|NCHAR|String|8-Bit-Zeichen<sup>1</sup>|  
|NUMERIC|String|8-Bit-Zeichen<sup>1</sup>|  
|NVARCHAR|String|8-Bit-Zeichen<sup>1</sup>|  
|nvarchar(Max)|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|ntext<sup>6</sup>|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|real|Float|8-Bit-Zeichen<sup>1</sup>|  
|smalldatetime|Datetime|8-Bit-Zeichen<sup>1</sup>|  
|SMALLINT|Integer|8-Bit-Zeichen<sup>1</sup>|  
|SMALLMONEY|String|8-Bit-Zeichen<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|8-Bit-Zeichen<sup>1</sup>|  
|text<sup>8</sup>|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|time<sup>4</sup>|Datetime|Nicht verfügbar|  
|timestamp|String|8-Bit-Zeichen<sup>1</sup>|  
|TINYINT|Integer|8-Bit-Zeichen<sup>1</sup>|  
|UDT|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|UNIQUEIDENTIFIER|String<sup>9</sup>|8-Bit-Zeichen<sup>1</sup>|  
|varbinary|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|varbinary(MAX)|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|varchar|String|8-Bit-Zeichen<sup>1</sup>|  
|varchar(MAX)|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|
|Xml|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
  

1.  Daten werden in 8-Bit-Zeichen gemäß der Codepage des im System eingestellten Windows-Gebietsschemas zurückgegeben. Alle Multi-Byte-Zeichen oder Zeichen, die nicht in dieser Codepage enthalten sind, werden durch ein aus einem einzelnen Byte bestehendes Fragezeichen (?) ersetzt.  
  
2.  Wenn [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) oder [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) verwendet wird, um Daten abzurufen, die den PHP-Standardtyp „Stream“ besitzen, werden die Daten als Zeichenfolge ausgegeben und genauso wie der Stream codiert. Wird z.B. einer der binären SQL Server-Datentypen über **sqlsrv_fetch_array** abgerufen, so wird als Standardrückgabetyp eine binäre Zeichenfolge verwendet.  
  
3.  Die Daten werden als uncodierter und nicht übersetzter Strom aus unbearbeiteten Bytes vom Server zurückgegeben.  

4.  Daten des Typs „Datum“ und „Uhrzeit“ können als Zeichenfolgen abgerufen werden. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Datums- und Uhrzeittypen mittels des SQLSRV-Treibers](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Dies ist ein veralteter Typ, der dem varbinary(max)-Typ zugeordnet ist.

6. Dies ist ein veralteter Typ, der dem nvarchar(max)-Typ zugeordnet ist.

7.  Der Typ sql_variant wird in bidirektionalen und Ausgabeparametern nicht unterstützt.

8.  Dies ist ein veralteter Typ, der dem varchar(max)-Typ zugeordnet ist.  
  
9.  Als „UNIQUEIDENTIFIER“ werden GUIDs bezeichnet, die den folgenden regulären Ausdruck aufweisen.  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Weitere neue Datentypen und Funktionen in SQL Server 2008  
Datentypen, die in SQL Server 2008 neu sind und die außerhalb von Spalten (z.B. Tabellenwertparameter) vorhanden sind, werden in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nicht unterstützt. Die folgende Tabelle fasst die PHP-Unterstützung für die neuen Features von SQL Server 2008 zusammen.  
  
|Funktion|PHP-Unterstützung|  
|-----------|---------------|  
|Tabellenwertparameter|Nein|  
|Spalten mit geringer Dichte|Teilweise|  
|NULL-Bit-Komprimierung|Ja|  
|Große benutzerdefinierte CLR-Typen (UDTs)|Ja|  
|Dienstprinzipalname|Nein|  
|MERGE|Ja|  
|FILESTREAM|Teilweise|  
  
Teilweise Unterstützung besagt, dass Sie den Spaltentyp nicht programmgesteuert abfragen können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Konvertieren von Datentypen](../../connect/php/converting-data-types.md)

[PHP-Typen](https://php.net/manual/en/language.types.php)

[Datentypen (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
