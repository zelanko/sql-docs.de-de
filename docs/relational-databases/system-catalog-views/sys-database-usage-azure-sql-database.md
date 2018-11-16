---
title: Sys. database_usage (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f17e34de7c230b111652ea57a3baa072a442a6a5
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656739"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Hinweis: Dies gilt nur für Azure SQL-Datenbank V11.**  
  
 Listet Anzahl, Typ und Dauer der Datenbanken auf dem [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server.  
  
 Die **Sys. database_usage** -Ansicht enthält die folgenden Spalten.  
  
|Spaltenname|Description|  
|-----------------|-----------------|  
|Uhrzeit|Das Datum, an dem die Verwendungsereignisse eingetreten sind.|  
|sku|Der Typ der Dienstebene für die Datenbank: **Web**, **Business**, **grundlegende**, **Standard**, **Premium**|  
|quantity|Die maximale Anzahl von Datenbanken eines SKU-Typs, der an diesem Tag vorhanden war.|  
  
## <a name="permissions"></a>Berechtigungen  
 Nur-Lese Zugriff auf diese Sicht wird für alle Benutzer mit Berechtigungen zum Herstellen einer Verbindung mit der **master** Datenbank.  
  
## <a name="remarks"></a>Hinweise  
 Die **Sys. database_usage** Sicht gibt eine Zeile für jeden Tag des Ihrem Abonnement zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Preisdetails – SQL-Datenbank](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Konten und Abrechnung in Windows Azure SQL-Datenbank](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
