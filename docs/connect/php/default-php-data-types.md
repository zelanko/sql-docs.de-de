---
title: Default PHP Data Types | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01f611e0c11d6a2f3671c8911d41b4c0cfeef83c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801481"
---
# <a name="default-php-data-types"></a>PHP-Standarddatentypen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Wenn vom Benutzer kein PHP-Datentyp angegeben wurde, werden die Daten beim Abrufen vom Server von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] in einen PHP-Standarddatentyp konvertiert.  
  
Wenn Daten mit dem Treiber PDO_SQLSRV zurückgegeben werden, wird als Datentyp entweder „int“ oder „string“ verwendet.  
  
Im weiteren Verlauf dieses Themas werden die Standarddatentypen erläutert, die den SQLSRV-Treiber verwenden.  
  
Die folgende Tabelle enthält den SQL Server-Datentyp (der Datentyp, der vom Server abgerufen wird), den PHP-Standarddatentyp (der Datentyp, in den Daten konvertiert werden) und die Standardcodierung für Datenströme und Zeichenfolgen. Weitere Informationen dazu, wie Sie Datentypen beim Abrufen von Daten vom Server festlegen, finden Sie unter [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
|SQL Server-Typ|PHP-Standardtyp|Standardcodierung|  
|-------------------|--------------------|--------------------|  
|BIGINT|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|BINARY|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|bit|Integer|8-Bit-Zeichen<sup>1</sup>|  
|char|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|Datum<sup>4</sup>|DATETIME|Nicht verfügbar|  
|datetime<sup>4</sup>|DATETIME|Nicht verfügbar|  
|datetime2<sup>4</sup>|DATETIME|Nicht verfügbar|  
|datetimeoffset<sup>4</sup>|DATETIME|Nicht verfügbar|  
|Decimal|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|FLOAT|float|8-Bit-Zeichen<sup>1</sup>|  
|geography|Datenstrom|Binär<sup>3</sup>|  
|Geometrie|Datenstrom|Binär<sup>3</sup>|  
|Image<sup>5</sup>|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|ssNoversion|Integer|8-Bit-Zeichen<sup>1</sup>|  
|money|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|NCHAR|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|NUMERIC|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|NVARCHAR|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|nvarchar(Max)|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|ntext<sup>6</sup>|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|REAL|float|8-Bit-Zeichen<sup>1</sup>|  
|smalldatetime|DATETIME|8-Bit-Zeichen<sup>1</sup>|  
|SMALLINT|Integer|8-Bit-Zeichen<sup>1</sup>|  
|SMALLMONEY|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|sql_variant<sup>7</sup>|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|text<sup>8</sup>|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
|time<sup>4</sup>|DATETIME|Nicht verfügbar|  
|timestamp|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|TINYINT|Integer|8-Bit-Zeichen<sup>1</sup>|  
|UDT|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|UNIQUEIDENTIFIER|String<sup>9</sup>|8-Bit-Zeichen<sup>1</sup>|  
|varbinary|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|varbinary(MAX)|Datenstrom<sup>2</sup>|Binär<sup>3</sup>|  
|varchar|Zeichenfolge|8-Bit-Zeichen<sup>1</sup>|  
|varchar(MAX)|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|
|xml|Datenstrom<sup>2</sup>|8-Bit-Zeichen<sup>1</sup>|  
  

1.  Daten werden in 8-Bit-Zeichen gemäß der Codepage des im System eingestellten Windows-Gebietsschemas zurückgegeben. Alle Multi-Byte-Zeichen oder Zeichen, die nicht in dieser Codepage enthalten sind, werden durch ein aus einem einzelnen Byte bestehendes Fragezeichen (?) ersetzt.  
  
2.  Wenn [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) oder [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) verwendet wird, um Daten abzurufen, die den PHP-Standardtyp „Stream“ besitzen, werden die Daten als Zeichenfolge ausgegeben und genauso wie der Stream codiert. Wird z.B. einer der binären SQL Server-Datentypen über **sqlsrv_fetch_array** abgerufen, so wird als Standardrückgabetyp eine binäre Zeichenfolge verwendet.  
  
3.  Die Daten werden als uncodierter und nicht übersetzter Strom aus unbearbeiteten Bytes vom Server zurückgegeben.  

4.  Daten des Typs „Datum“ und „Uhrzeit“ können als Zeichenfolgen abgerufen werden. Weitere Informationen finden Sie unter [So wird's gemacht: Datums- und Uhrzeittypen mittels des SQLSRV-Treibers als Zeichenfolgen abrufen](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Dies ist ein veralteter Typ, der dem varbinary(max)-Typ zugeordnet ist.

6. Dies ist ein veralteter Typ, der dem nvarchar(max)-Typ zugeordnet ist.

7.  Sql_variant wird in bidirektionalen oder Output-Parameter nicht unterstützt.

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

[Converting Data Types](../../connect/php/converting-data-types.md)

[PHP-Typen](https://php.net/manual/en/language.types.php)

[Datentypen (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
