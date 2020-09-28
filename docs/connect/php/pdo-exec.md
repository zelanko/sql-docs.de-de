---
title: PDO::exec
description: API-Referenz für die PDO::exec-Funktion im Microsoft PDO_SQLSRV-Treiber für PHP für SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 989d1f6346f26292326c5b49e1675492cd4ee8de
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646160"
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bereitet eine SQL-Anweisung vor, führt diese in einem einzelnen Funktionsaufruf aus und gibt die Anzahl der von dieser Anweisung betroffenen Zeilen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Parameter  
*$statement*: Eine Zeichenfolge, die die auszuführende SQL-Anweisung enthält.  
  
## <a name="return-value"></a>Rückgabewert  
Eine ganze Zahl, die über die Anzahl der betroffenen Zeilen Auskunft gibt.  
  
## <a name="remarks"></a>Bemerkungen  
Wenn *$statement* mehrere SQL-Anweisungen enthält, wird nur die Anzahl der von der letzten Anweisung betroffenen Zeilen in der Zahl widergespiegelt.  
  
PDO::exec Gibt keine Ergebnisse für eine SELECT Anweisung zurück.  
  
Die folgenden Attribute beeinflussen das Verhalten der PDO::exec:  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Weitere Informationen finden Sie unter [PDO::setAttribute](../../connect/php/pdo-setattribute.md). 
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel löscht Zeilen in Tabelle 1, die in Spalte 1 „xxxyy“ aufweisen. Anschließend meldet das Beispiel, wie viele Zeilen gelöscht wurden.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
