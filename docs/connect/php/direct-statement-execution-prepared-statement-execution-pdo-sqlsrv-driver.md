---
title: 'Direkte Anweisung: vorbereitete Anweisungs Ausführung PDO_SQLSRV Treiber | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa9e544fb7b79009d86a5742946a722d5adc18f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993618"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber.
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Artikel wird erläutert, wie das PDO::SQLSRV_ATTR_DIRECT_QUERY-Attribut verwendet wird, um die direkte Anweisungsausführung anstelle des Standardwerts, der die Ausführung der vorbereiteten Anweisung darstellt, anzugeben. Die Verwendung einer vorbereiteten Anweisung kann zu einer besseren Leistung führen, wenn die Anweisung mehrmals mithilfe der Parameter Bindung ausgeführt wird.  
  
## <a name="remarks"></a>Remarks  
Wenn Sie eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung ohne Anweisungs Vorbereitung durch den Treiber direkt an den Server senden möchten, können Sie das PDO:: SQLSRV_ATTR_DIRECT_QUERY-Attribut mit [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) festlegen (oder als Treiber Option an [PDO:: __construct ](../../connect/php/pdo-construct.md)) oder wenn Sie [PDO::p repare aufgerufen haben](../../connect/php/pdo-prepare.md). Standardmäßig ist der Wert von PDO:: SQLSRV_ATTR_DIRECT_QUERY false (verwenden Sie die vorbereitete Anweisungs Ausführung).  
  
Wenn Sie [PDO:: Query](../../connect/php/pdo-query.md)verwenden, möchten Sie möglicherweise direkt ausführen. Bevor Sie [PDO:: Query](../../connect/php/pdo-query.md)aufrufen, rufen Sie [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) auf, und legen Sie PDO:: SQLSRV_ATTR_DIRECT_QUERY auf true fest.  Jeder Aufrufe von [PDO:: Query](../../connect/php/pdo-query.md) kann mit einer anderen Einstellung für PDO:: SQLSRV_ATTR_DIRECT_QUERY ausgeführt werden.  
  
Wenn Sie [PDO::p repare](../../connect/php/pdo-prepare.md) und [PDOStatement:: Execute](../../connect/php/pdostatement-execute.md) verwenden, um eine Abfrage mehrmals mit gebundenen Parametern auszuführen, wird die Ausführung der wiederholten Abfrage durch die vorbereitete Anweisungs Ausführung optimiert.  Nennen Sie in diesem Fall [PDO::p repare](../../connect/php/pdo-prepare.md) mit PDO:: SQLSRV_ATTR_DIRECT_QUERY im Parameter "Driver Options Array" auf "false" festgelegt ist. Bei Bedarf können Sie vorbereitete Anweisungen ausführen, bei denen PDO:: SQLSRV_ATTR_DIRECT_QUERY auf "false" festgelegt ist.  
  
Nachdem Sie [PDO::p repare](../../connect/php/pdo-prepare.md)aufgerufen haben, kann der Wert von PDO:: SQLSRV_ATTR_DIRECT_QUERY beim Ausführen der vorbereiteten Abfrage nicht geändert werden.  
  
Wenn eine Abfrage den Kontext erfordert, der in einer vorherigen Abfrage festgelegt wurde, führen Sie die Abfragen mit PDO:: SQLSRV_ATTR_DIRECT_QUERY Set auf true aus. Wenn Sie z. b. temporäre Tabellen in Ihren Abfragen verwenden, muss PDO:: SQLSRV_ATTR_DIRECT_QUERY auf true festgelegt werden.  
  
Das folgende Beispiel zeigt, dass Sie PDO:: SQLSRV_ATTR_DIRECT_QUERY auf true festlegen müssen, wenn der Kontext aus einer vorherigen-Anweisung erforderlich ist. In diesem Beispiel werden temporäre Tabellen verwendet, die nur für nachfolgende Anweisungen in Ihrem Programm verfügbar sind, wenn Abfragen direkt ausgeführt werden.  
  
> [!NOTE]
> Wenn die Abfrage eine gespeicherte Prozedur aufrufen soll und temporäre Tabellen in dieser gespeicherten Prozedur verwendet werden, verwenden Sie stattdessen [PDO:: exec](../../connect/php/pdo-exec.md) .

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
  
## <a name="see-also"></a>Weitere Informationen  
[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
