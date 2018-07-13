---
title: DBSCHEMA_CATALOGS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2151d55ce06a8111ab1707e5673ee6d6982ef05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187047"
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS-Rowset
  Gibt die physischen Attribute an, die Katalogen zugeordnet sind, auf die über das Datenbankverwaltungssystem (Database Management System, DBMS) zugegriffen werden kann.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DBSCHEMA_CATALOGS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|Der Katalogname. Lässt keine NULL-Werte zu.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Tabelle.|  
|`ROLES`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Rollen, zu der der aktuelle Benutzer gehört.<br /><br /> Ein Sternchen (\*) als Rolle enthalten ist, wenn der aktuelle Benutzer ein Server- oder Datenbankadministrator ist.<br /><br /> `Username` wird angefügt `ROLES` Wenn einer der Rollen dynamische Sicherheit verwendet.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem der Katalog zuletzt geändert wurde.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DBSCHEMA_CATALOGS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](ole-db-schema-rowsets.md)  
  
  
