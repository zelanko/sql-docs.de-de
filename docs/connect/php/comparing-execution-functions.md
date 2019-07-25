---
title: Vergleichen von Ausführungs Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2b4d6c85c399589aae4eedbaade4bbdc4f70609
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993742"
---
# <a name="comparing-execution-functions"></a>Vergleichen von Ausführungsfunktionen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] bietet mehrere Optionen zum Ausführen von Funktionen.  

## <a name="sqlsrv-execution-functions"></a>SQLSRV-Ausführungs Funktionen  
Wenn Sie den SQLSRV-Treiber verwenden, verwenden Sie [sqlsrv_query](../../connect/php/sqlsrv-query.md) zum Ausführen einer einzelnen Abfrage und [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) mit [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) zur mehrfachen Ausführung einer vorbereiteten Anweisung mit verschiedenen Parameterwerten für jede Ausführung.  

## <a name="pdosqlsrv-execution-functions"></a>PDO_SQLSRV-Ausführungs Funktionen 
Wenn Sie den PDO_SQLSRV-Treiber verwenden, können Sie eine Abfrage mit einer der folgenden Methoden ausführen:  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) und [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Referenz zum Treiber PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
