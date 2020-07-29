---
title: Tabellenwertparameter-Typermittlung | Microsoft-Dokumentation
description: Tabellenwertparameter-Typermittlung mithilfe des OLE DB-Treibers für SQL Server
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
ms.openlocfilehash: 06e0de0ad5fb0b4b8b7fd90144769ca9f9133928
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003338"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der Consumer, d.h. die Clientanwendung, die den OLE DB-Treiber für SQL Server verwendet, kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter weitergeleitet wurde. Nachdem der Typ des Tabellenwertparameters ermittelt wurde, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Tabellenwertparameters ermitteln.  
  
 Die Typinformationen für Prozedurparameter werden von ICommandWithParameters::GetParameterInfo für die meisten Parametertypen unterstützt. Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und der Einführung von benutzerdefinierten Typen und dem Datentyp **XML**  reichte die Methode „GetParameterInfo“ für diesen Zweck nicht mehr aus, da keine Informationen für benutzerdefinierte Typen (Name, Schema und Katalog) mit „ICommandWithParameters“ angegeben werden konnten. Es wurde eine neue Schnittstelle, ISSCommandWithParameters, definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Bei Tabellenwertparametern verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der Vorbereitung des Befehlsobjekts auf. Bei Tabellenwertparametern wird das Element *wType* der Struktur DBPARAMINFO der DBPARAMINFO vom Anbieter auf DBTYPE_TABLE festgelegt. Das Feld *ulParamSize* der Struktur DBPARAMINFO hat den Wert ~0.  
  
 Der Consumer fordert dann mithilfe des Parameters „ISSCommandWithParameters::GetParameterProperties“ zusätzliche Eigenschaften an (Katalogname, Schemaname und Name des Tabellenwertparameter-Typs, Spaltensortierung und Standardspalten).  
  
 Nachdem der Typname ermittelt wurde, muss der Consumer entweder „IOpenRowset::OpenRowsetor“ aufrufen oder das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen abrufen, um Informationen zu den einzelnen Spalten zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
