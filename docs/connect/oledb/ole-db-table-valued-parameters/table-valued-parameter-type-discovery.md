---
title: Tabellenwertparameter-Typermittlung | Microsoft-Dokumentation
description: Table-Valued Parameter-Typermittlung mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 8e4da9d25a5d23e81e1d5dd44becd17e26263338
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558317"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der Consumer, d.h. die Clientanwendung, die den OLE DB-Treiber für SQL Server verwendet, kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter weitergeleitet wurde. Nachdem der Typ des Tabellenwertparameters ermittelt wurde, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Tabellenwertparameters ermitteln.  
  
 Die Typinformationen für Prozedurparameter wird von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und der Einführung von benutzerdefinierten Typen und dem Datentyp **XML**  reichte die Methode „GetParameterInfo“ für diesen Zweck nicht mehr aus, da keine Informationen für benutzerdefinierte Typen (Name, Schema und Katalog) mit „ICommandWithParameters“ angegeben werden konnten. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Für Tabellenwertparameter verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der das Befehlsobjekt vorbereitet. Bei Tabellenwertparametern wird das Element *wType* der Struktur DBPARAMINFO der DBPARAMINFO vom Anbieter auf DBTYPE_TABLE festgelegt. Das Feld *ulParamSize* der Struktur DBPARAMINFO hat den Wert ~0.  
  
 Der Consumer fordert dann mithilfe des Parameters „ISSCommandWithParameters::GetParameterProperties“ zusätzliche Eigenschaften an (Katalogname, Schemaname und Name des Tabellenwertparameter-Typs, Spaltensortierung und Standardspalten).  
  
 Nachdem der Typname ermittelt wurde, muss der Consumer entweder „IOpenRowset::OpenRowsetor“ aufrufen oder das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen abrufen, um Informationen zu den einzelnen Spalten zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
