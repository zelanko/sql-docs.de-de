---
title: LINKEDSERVERS-Rowset (OLE DB) | Microsoft Docs
description: LINKEDSERVERS-Rowset (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ff4c35178b5cc047fb711821b332f43cf0094fc8
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611725"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Schemarowsets - LINKEDSERVERS-Rowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **LINKEDSERVERS** Rowset listet organisationsdatenquellen beteiligt sein können, die auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilte Abfragen.  
  
 Das **LINKEDSERVERS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Name eines Verbindungsservers|  
|SVR_PRODUCT|DBTYPE_WSTR|Hersteller oder ein anderer Name, der den Typ des Datenspeichers identifiziert, der durch den Namen des Verbindungsservers repräsentiert wird.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Der Anzeigename des OLE DB-Anbieters, der Daten vom Server verwendet.|  
|SVR_DATASOURCE|DBTYPE_WSTR|OLE DB DBPROP_INIT_DATASOURCE-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|OLE DB DBPROP_INIT_PROVIDERSTRING-Wert, der verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
|SVR_LOCATION|DBTYPE_WSTR|OLE DB DBPROP_INIT_LOCATION-Zeichenfolge, die verwendet wird, um eine Datenquelle vom Anbieter abzurufen.|  
  
 Das Rowset wird nach SRV_NAME sortiert, und eine einzelne Einschränkung wird für SRV_NAME unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemarowset-Unterstützung &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
