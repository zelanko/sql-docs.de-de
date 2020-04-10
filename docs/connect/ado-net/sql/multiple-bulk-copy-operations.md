---
title: Mehrere Massenkopiervorgänge
description: Beschreibt das Ausführen mehrerer Massenkopiervorgänge von Daten in eine SQL Server-Instanz mithilfe der SqlBulkCopy-Klasse
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a0a1f24970801698eedc8971f0db54bd08589945
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924299"
---
# <a name="multiple-bulk-copy-operations"></a>Mehrere Massenkopiervorgänge

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Mithilfe einer einzelnen Instanz einer <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse können Sie mehrere Massenkopiervorgänge ausführen. Wenn sich die Parameter für den Vorgang zwischen den Ausführungen ändern (z. B. der Name der Zieltabelle), müssen Sie sie vor allen nachfolgenden Aufrufen einer der **WriteToServer**-Methoden ändern, wie im folgenden Beispiel gezeigt. Sofern sie nicht explizit geändert werden, bleiben alle Eigenschaftswerte die gleichen wie beim letzten Massenkopiervorgang für eine bestimmte Instanz.  
  
> [!NOTE]
>  Das Ausführen mehrerer Massenkopiervorgänge mithilfe der gleichen Instanz von <xref:Microsoft.Data.SqlClient.SqlBulkCopy> ist normalerweise effizienter als die Verwendung einer separaten Instanz für jeden Vorgang.  
  
Wenn Sie mehrere Massenkopiervorgänge mithilfe des gleichen <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Objekts ausführen, bestehen normalerweise keine Einschränkungen hinsichtlich der Gleichheit oder Verschiedenheit der Quell- und Zielinformationen für die einzelnen Vorgänge. Sie müssen jedoch sicherstellen, dass die Informationen zur Spaltenzuordnung bei jedem Schreibvorgang auf dem Server ordnungsgemäß festgelegt sind.  

## <a name="example"></a>Beispiel

> [!IMPORTANT]
>  Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Massenkopierbeispiel-Einrichtung](bulk-copy-example-setup.md) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von **SqlBulkCopy**. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
[!code-csharp[DataWorks SqlBulkCopy_._ColumnMappingOrdersDetails#1](~/../sqlclient/doc/samples/SqlBulkCopy_ColumnMappingOrdersDetails.cs#1)]
  
## <a name="next-steps"></a>Nächste Schritte
- [Massenkopiervorgänge in SQL Server](bulk-copy-operations-sql-server.md)
