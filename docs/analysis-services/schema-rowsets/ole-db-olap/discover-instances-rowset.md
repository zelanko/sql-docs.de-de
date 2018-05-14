---
title: DISCOVER_INSTANCES-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0acc45eb2ea114a8d1c685aa6b3e867a4eaa967d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="discoverinstances-rowset"></a>DISCOVER_INSTANCES-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die Instanzen auf dem Server.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_INSTANCES** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**INSTANZNAME**|**DBTYPE_WSTR**||Der Name der Instanz.|  
|**INSTANCE_PORT_NUMBER**|**DBTYPE_I4**||Die Portnummer, die die Instanz überwacht.|  
|**INSTANCE_STATE**|**DBTYPE_I4**||Der Status der Serverinstanz.<br /><br /> **Schritte**<br /><br /> **Beendet**<br /><br /> **Starten**<br /><br /> **Beenden**<br /><br /> **Angehalten**|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_INSTANCES** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**INSTANZNAME**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
