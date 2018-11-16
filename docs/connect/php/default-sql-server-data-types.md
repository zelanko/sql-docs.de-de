---
title: Standardmäßige SQL Server-Datentypen | Microsoft-Dokumentation
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
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3ccdf7ffa8b5eaf01108ca0492b9b5db9ecc042
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51599862"
---
# <a name="default-sql-server-data-types"></a>SQL Server-Standarddatentypen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Beim Senden von Daten an den Server konvertiert der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Daten aus seinem PHP-Datentyp in einen SQL Server-Datentyp, wenn vom Benutzer kein SQL Server-Datentyp angegeben wurde. Die folgende Tabelle enthält den PHP-Datentyp (der Datentyp, der an den Server gesendet wird) und den SQL Server-Standarddatentyp (der Datentyp, in den die Daten konvertiert werden). Details zum Angeben von Datentypen beim Senden von Daten an den Server finden Sie unter [Gewusst wie: Angeben von SQL Server-Datentypen, wenn der SQLSRV-Treiber verwendet wird](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|PHP-Datentyp|SQL-Standardservertyp im SQLSRV-Treiber|SQL-Standardservertyp im PDO_SQLSRV-Treiber|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|nicht unterstützt|  
|Boolean|bit|bit|  
|Integer|ssNoversion|ssNoversion|  
|float|float(24)|nicht unterstützt|  
|Zeichenfolge (Länge kleiner als 8000 Bytes)|varchar(<string length>)|varchar(<string length>)|  
|Zeichenfolge (Länge größer als 8000 Bytes)|varchar(max)|varchar(max)|  
|Ressource|Wird nicht unterstützt.|Wird nicht unterstützt.|  
|Stream (Codierung: nicht binär)|varchar(max)|varchar(max)|  
|Stream (Codierung: binär)|varbinary|varbinary|  
|Array|Wird nicht unterstützt.|Wird nicht unterstützt.|  
|Objekt|Wird nicht unterstützt.|Wird nicht unterstützt.|  
|DatumUhrzeit (1)|DATETIME|Wird nicht unterstützt.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Konvertieren von Datentypen](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[PHP-Typen](https://php.net/manual/language.types.php)

[Datentypen (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/data-types/data-types-transact-sql)  
  
