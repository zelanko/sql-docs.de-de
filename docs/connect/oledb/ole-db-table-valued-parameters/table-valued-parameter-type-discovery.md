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
manager: jroth
ms.openlocfilehash: c45b5f6b00c15dee35d263447f5b95c8e31b986f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801110"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der Consumer, d.h. die Clientanwendung, die den OLE DB-Treiber für SQL Server verwendet, kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter weitergeleitet wurde. Nachdem der Typ des Tabellenwertparameters ermittelt wurde, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Tabellenwertparameters ermitteln.  
  
 Die Typinformationen für Prozedurparameter wird von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und der Einführung von benutzerdefinierten Typen und dem Datentyp **XML**  reichte die Methode „GetParameterInfo“ für diesen Zweck nicht mehr aus, da keine Informationen für benutzerdefinierte Typen (Name, Schema und Katalog) mit „ICommandWithParameters“ angegeben werden konnten. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Für Tabellenwertparameter verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der das Befehlsobjekt vorbereitet. Bei Tabellenwertparametern wird das Element *wType* der Struktur DBPARAMINFO der DBPARAMINFO vom Anbieter auf DBTYPE_TABLE festgelegt. Das Feld *ulParamSize* der Struktur DBPARAMINFO hat den Wert ~0.  
  
 Der Consumer fordert dann mithilfe des Parameters „ISSCommandWithParameters::GetParameterProperties“ zusätzliche Eigenschaften an (Katalogname, Schemaname und Name des Tabellenwertparameter-Typs, Spaltensortierung und Standardspalten).  
  
 Nachdem der Typname ermittelt wurde, muss der Consumer entweder „IOpenRowset::OpenRowsetor“ aufrufen oder das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen abrufen, um Informationen zu den einzelnen Spalten zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
