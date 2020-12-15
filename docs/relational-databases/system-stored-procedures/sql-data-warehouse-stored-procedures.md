---
description: Gespeicherte Prozeduren für die Azure Synapse-Analyse
title: Gespeicherte Prozeduren für die Azure Synapse-Analyse
ms.custom: ''
ms.date: 03/15/2017
ms.service: sql-data-warehouse
ms.subservice: design
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02e04dfe-d565-4e45-b427-b8e89c958ba3
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest
ms.openlocfilehash: 1ee858953867209a6686f1775c17e539d13aae2f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97410131"
---
# <a name="azure-synapse-analytics-stored-procedures"></a>Gespeicherte Prozeduren für die Azure Synapse-Analyse
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] stellt integrierte Prozeduren bereit, mit denen Sie Vorgänge im Zusammenhang mit Daten bankrollen ausführen können. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] umfasst die folgenden System Prozeduren:  
  
<a name="AggregateFunctions"></a>[sp_datatype_info_90 &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-datatype-info-90-sql-data-warehouse.md)  
  
 [sp_pdw_add_network_credentials &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
 [sp_pdw_database_encryption &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
 [sp_pdw_log_user_data_masking &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
 [sp_pdw_remove_network_credentials &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
 [sp_special_columns_100 &#40;Azure-Synapse-Analyse&#41;](../../relational-databases/system-stored-procedures/sp-special-columns-100-sql-data-warehouse.md)  
  
> [!NOTE]  
>  Einige zusätzliche gespeicherte System Prozeduren werden nur in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder über Client-APIs verwendet und sind nicht für die allgemeine Nutzung durch den Kunden vorgesehen. Diese Prozeduren werden unter [gespeicherte System Prozeduren (Transact-SQL)](./system-stored-procedures-transact-sql.md)aufgelistet. Diese Prozeduren unterliegen Änderungen, und die Kompatibilität ist nicht gewährleistet. Alle Prozeduren in der Liste sind in nicht verfügbar [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
