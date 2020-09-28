---
title: PDOStatement::getAttribute
description: API-Referenz für die PDOStatement::getAttribute-Funktion im Microsoft PDO_SQLSRV-Treiber für PHP für SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07cc46717dafe973dee05647f1d08134d858c58e
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646750"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft den Wert eines vordefinierten PDOStatement-Attributs oder ein benutzerdefiniertes Treiber-Attributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Parameter  
$*attribute:* Eine ganze Zahl, eine der Konstanten PDO::ATTR_* oder PDO::SQLSRV_ATTR_\*. Unterstützt werden die Attribute, die mithilfe von [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), PDO::SQLSRV_ATTR_DIRECT_QUERY (weitere Informationen unter [Direkte Anweisungsausführung und Ausführung von Prepared Statements im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO::ATTR_CURSOR und PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE ( weitere Informationen unter [Cursortypen (PDO_SQLSRV-Treiber)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)) festgelegt werden können.  
  
## <a name="return-value"></a>Rückgabewert  
Bei Erfolg wird ein (gemischter) Wert für ein vordefiniertes PDO-Attribut oder ein benutzerdefiniertes Treiber-Attribut zurückgegeben. Gibt bei einem Fehler NULL zurück.  
  
## <a name="remarks"></a>Bemerkungen  
Ein Beispiel hierzu finden Sie unter [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
