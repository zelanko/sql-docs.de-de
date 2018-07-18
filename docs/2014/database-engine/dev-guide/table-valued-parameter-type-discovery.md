---
title: Tabellenwertparameter-Typermittlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 021109d32ceed7055348aea0bb0cb9ac32a4c7c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231950"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
  Der Consumer – d. h. der Clientanwendung mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter – kann den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext an den OLE DB-Anbieter festgelegt wurde. Nachdem Sie der Typ des einem Tabellenwertparameter bekannt ist, kann der Consumer die Metadateninformationen für jede einzelne Spalte des Table-valued Parameters ermitteln.  
  
 Die Typinformationen für Prozedurparameter wird von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], mit der Einführung von benutzerdefinierten Typen und die `xml` -Datentyp, die GetParameterInfo-Methode war nicht ausreichend, zu diesem Zweck da es nicht möglich, eine benutzerdefinierte Typinformationen bereitzustellen (Name, Schema und Katalogsichten Sie) durch ICommandWithParameters. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Für Tabellenwertparameter verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der das Befehlsobjekt vorbereitet. Für die Table-valued Parameter die *wType* Mitglied der DBPARAMINFO-Struktur wird durch den Anbieter auf DBTYPE_TABLE festgelegt. Die *UlParamSize* -Feld der DBPARAMINFO-Struktur hat einen Wert von ~ 0.  
  
 Der Consumer würde dann weitere Eigenschaften (Table-tabellenwertparametertyps Katalogname, Schemaname für Tabellenwertparameter-Typ, Tabellenwertparameter-Typnamen, spaltensortierung und Standardspalten) fordern Sie mithilfe von ISSCommandWithParamters:: GetParameterProperties.  
  
 Nachdem der Typname bekannt ist, zum Abrufen der einzelnen Spalte-Informationen, die der Consumer entweder aufrufen muss IOpenRowset::OpenRowsetor erhalten das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen der Tabellenwertparameter-Typnamens als den Namen der Tabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
