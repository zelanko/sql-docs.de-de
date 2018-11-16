---
title: PDOStatement::getAttribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e9f9a4e6af61eb507fa58f70b0aeb9060a16940
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605080"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft den Wert eines vordefinierten PDOStatement-Attributs oder ein benutzerdefiniertes Treiber-Attributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Parameter  
$*attribute:* Eine ganze Zahl, eine der Konstanten PDO::ATTR_* oder PDO::SQLSRV_ATTR_\*. Unterstützte Attribute sind die Attribute, die Sie festlegen können, mit [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md), PDO:: sqlsrv_attr_direct_query (Weitere Informationen finden Sie unter [direkte Anweisungsausführung und vorbereitete Anweisungsausführung im der PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO:: attr_cursor und sqlsrv_attr_cursor_scroll_type (Weitere Informationen finden Sie unter [Cursortypen (PDO_SQLSRV-Treiber)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Rückgabewert  
Bei Erfolg wird ein (gemischter) Wert für ein vordefiniertes PDO-Attribut oder ein benutzerdefiniertes Treiber-Attribut zurückgegeben. Gibt bei einem Fehler NULL zurück.  
  
## <a name="remarks"></a>Remarks  
Ein Beispiel hierzu finden Sie unter [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
