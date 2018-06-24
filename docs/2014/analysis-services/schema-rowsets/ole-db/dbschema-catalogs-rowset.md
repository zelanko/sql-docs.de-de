---
title: DBSCHEMA_CATALOGS-Rowset | Microsoft Docs
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df3b146d3e1015fd4a78254be0d8a7a6083991d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047488"
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS-Rowset
  Gibt die physischen Attribute an, die Katalogen zugeordnet sind, auf die über das Datenbankverwaltungssystem (Database Management System, DBMS) zugegriffen werden kann.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DBSCHEMA_CATALOGS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|Der Katalogname. Lässt keine NULL-Werte zu.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine lesbare Beschreibung der Tabelle.|  
|`ROLES`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Rollen, zu der der aktuelle Benutzer gehört.<br /><br /> Ein Sternchen (\*) als eine Rolle enthalten ist, wenn der aktuelle Benutzer ein Server- oder Datenbankadministrator ist.<br /><br /> `Username` angehängt `ROLES` Wenn einer der Rollen dynamische Sicherheit verwendet.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem der Katalog zuletzt geändert wurde.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DBSCHEMA_CATALOGS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](ole-db-schema-rowsets.md)  
  
  