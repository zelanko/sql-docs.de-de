---
title: Direkte - Anweisung Ausführung PDO_SQLSRV-Treiber für vorbereitete Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c721a32936bf39d91042d6b7ac89a03a5fd85d6
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "42783848"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber.
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Artikel wird erläutert, wie das PDO::SQLSRV_ATTR_DIRECT_QUERY-Attribut verwendet wird, um die direkte Anweisungsausführung anstelle des Standardwerts, der die Ausführung der vorbereiteten Anweisung darstellt, anzugeben. Mit einer vorbereiteten Anweisung kann in eine bessere Leistung führen, wenn die Anweisung ausgeführt wird, mehr als einmal mit der parameterbindung.  
  
## <a name="remarks"></a>Remarks  
Wenn Sie senden möchten eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung direkt an den Server ohne anweisungsvorbereitung vom Treiber, Sie können das PDO:: sqlsrv_attr_direct_query-Attribut mit festlegen [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) (oder eine Treiberoption übergebenen [PDO:: __construct](../../connect/php/pdo-construct.md)) oder beim Aufruf [PDO:: Prepare](../../connect/php/pdo-prepare.md). Der Wert des PDO:: sqlsrv_attr_direct_query wird standardmäßig "false" (verwenden Sie vorbereitete anweisungsausführung).  
  
Bei Verwendung von [PDO:: Query](../../connect/php/pdo-query.md), sollten Sie die direkte Ausführung. Vor dem Aufruf [PDO:: Query](../../connect/php/pdo-query.md), rufen Sie [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) und PDO:: sqlsrv_attr_direct_query auf "true" festgelegt.  Jeder Aufruf von [PDO:: Query](../../connect/php/pdo-query.md) mit einer anderen Einstellung für PDO:: sqlsrv_attr_direct_query ausgeführt werden kann.  
  
Bei Verwendung von [PDO:: Prepare](../../connect/php/pdo-prepare.md) und [pdostatement:: Execute](../../connect/php/pdostatement-execute.md) zum Ausführen einer Abfrage mehrere Male mit gebundenen Parametern, vorbereitete anweisungsausführung optimiert die Ausführung der Abfrage wiederholt.  In diesem Fall rufen [PDO:: Prepare](../../connect/php/pdo-prepare.md) mit PDO:: sqlsrv_attr_direct_query im Array Treiber Options-Parameter auf False festgelegt. Bei Bedarf können Sie die vorbereitete Anweisungen mit PDO:: sqlsrv_attr_direct_query auf "false" ausführen.  
  
Nach dem Aufruf von [PDO:: Prepare](../../connect/php/pdo-prepare.md), der Wert des PDO:: sqlsrv_attr_direct_query kann nicht geändert werden, wenn die vorbereitete Abfrage ausgeführt.  
  
Wenn eine Abfrage den Kontext, der in einer vorherigen Abfrage festgelegt wurde erfordert, führen Sie dann Ihre Abfragen mit PDO:: sqlsrv_attr_direct_query auf "true" festgelegt ist. Wenn Sie temporäre Tabellen in Ihren Abfragen verwenden, muss z. B. PDO:: sqlsrv_attr_direct_query auf "true" festgelegt werden.  
  
Das folgende Beispiel zeigt, dass wenn eine vorherige Anweisung Kontext erforderlich ist, Sie PDO:: sqlsrv_attr_direct_query auf "true" festlegen müssen.  Dieses Beispiel verwendet die temporäre Tabellen, die nur sind für nachfolgende Anweisungen in Ihrem Programm verfügbar, wenn Abfragen direkt ausgeführt werden.  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Programmierhandbuch für den Microsoft-Treiber für PHP für SQLServer](../../connect/php/programming-guide-for-php-sql-driver.md)
  
