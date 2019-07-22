---
title: Tabellenwert Parameter-typantermittlung | Microsoft-Dokumentation
description: Tabellenwert Parameter-typanmittlung mithilfe OLE DB Treibers für SQL Server
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
ms.openlocfilehash: 4e824e39a44985dc2f46a1a27c7b5b4e8d05a6dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015309"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der Consumer, d.h. die Clientanwendung, die den OLE DB-Treiber für SQL Server verwendet, kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter weitergeleitet wurde. Nachdem der Typ des Tabellenwertparameters ermittelt wurde, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Tabellenwertparameters ermitteln.  
  
 Die Typinformationen von Prozedur Parametern werden von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und der Einführung von benutzerdefinierten Typen und dem Datentyp **XML**  reichte die Methode „GetParameterInfo“ für diesen Zweck nicht mehr aus, da keine Informationen für benutzerdefinierte Typen (Name, Schema und Katalog) mit „ICommandWithParameters“ angegeben werden konnten. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Bei Tabellenwert Parametern können Sie auch die ISSCommandWithParameters-Schnittstelle verwenden, um ausführliche Informationen zu ermitteln. Der Client ruft nach der Vorbereitung des Befehls Objekts ISSCommandWithParameters:: GetParameterInfo auf. Bei Tabellenwertparametern wird das Element *wType* der Struktur DBPARAMINFO der DBPARAMINFO vom Anbieter auf DBTYPE_TABLE festgelegt. Das Feld *ulParamSize* der Struktur DBPARAMINFO hat den Wert ~0.  
  
 Der Consumer fordert dann mithilfe des Parameters „ISSCommandWithParameters::GetParameterProperties“ zusätzliche Eigenschaften an (Katalogname, Schemaname und Name des Tabellenwertparameter-Typs, Spaltensortierung und Standardspalten).  
  
 Nachdem der Typname ermittelt wurde, muss der Consumer entweder „IOpenRowset::OpenRowsetor“ aufrufen oder das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen abrufen, um Informationen zu den einzelnen Spalten zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
