---
title: Tabellenwertparameter-Typermittlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf3f7b4d6754902ac38172ffa0e8fc392599d307
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62780319"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
  Der Consumer-d. h. der Clientanwendung mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter festgelegt wurde. Nachdem der Typ des Tabellenwertparameters ermittelt wurde, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Tabellenwertparameters ermitteln.  
  
 Die Typinformationen für Prozedurparameter wird von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], mit der Einführung von benutzerdefinierten Typen und die `xml` -Datentyp, die GetParameterInfo-Methode war nicht ausreichend, zu diesem Zweck da es nicht möglich, eine benutzerdefinierte Typinformationen bereitzustellen (Name, Schema und Katalogsichten Sie) durch ICommandWithParameters. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Für Tabellenwertparameter verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der das Befehlsobjekt vorbereitet. Bei Tabellenwertparametern wird das Element *wType* der Struktur DBPARAMINFO der DBPARAMINFO vom Anbieter auf DBTYPE_TABLE festgelegt. Das Feld *ulParamSize* der Struktur DBPARAMINFO hat den Wert ~0.  
  
 Der Consumer fordert dann mithilfe des Parameters „ISSCommandWithParameters::GetParameterProperties“ zusätzliche Eigenschaften an (Katalogname, Schemaname und Name des Tabellenwertparameter-Typs, Spaltensortierung und Standardspalten).  
  
 Nachdem der Typname ermittelt wurde, muss der Consumer entweder „IOpenRowset::OpenRowsetor“ aufrufen oder das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen abrufen, um Informationen zu den einzelnen Spalten zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
