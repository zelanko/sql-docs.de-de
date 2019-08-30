---
title: sys. database_usage (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0a0789ebd9a5aa4bd10605d69afa59a586ce75b2
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155537"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Hinweis: Dies gilt nur für Azure SQL-Datenbank v11.**  
  
 Listet die Anzahl, den Typ und die Dauer der Datenbanken [!INCLUDE[ssSDS](../../includes/sssds-md.md)] auf dem Server auf.  
  
 Die **sys. database_usage** -Sicht enthält die folgenden Spalten.  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|time|Das Datum, an dem die Verwendungsereignisse eingetreten sind.|  
|sku|Der Typ der Dienst Ebene für die Datenbank: **Web**, **Business**, **Basic**, **Standard**, **Premium**|  
|quantity|Die maximale Anzahl von Datenbanken eines SKU-Typs, der an diesem Tag vorhanden war.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der schreibgeschützte Zugriff auf diese Ansicht ist für alle Benutzer verfügbar, die über Berechtigungen zum Herstellen einer Verbindung mit der **Master** -Datenbank verfügen.  
  
## <a name="remarks"></a>Hinweise  
 Die **sys. database_usage** -Sicht gibt eine Zeile für jeden Tag Ihres Abonnements zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Preis Details zur SQL-Datenbank](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Konten und Abrechnung in Azure SQL-Datenbank](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
