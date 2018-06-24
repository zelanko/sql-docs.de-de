---
title: Tabellenwertparameter-Typermittlung | Microsoft Docs
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eea5d45c4c21b740a3ea91ee27023129b33719b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049946"
---
# <a name="table-valued-parameter-type-discovery"></a>Tabellenwertparameter-Typermittlung
  Der Consumer – d. h. die Clientanwendung mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter – können den Typ für jeden Befehlsparameter ermitteln, wenn der Befehlstext des OLE DB-Anbieters erhalten hat. Nachdem der Typ des einem Tabellenwertparameter bekannt ist, kann der Consumer die Metadateninformationen für jede einzelne der Tabellenwertparameter-Spalte ermitteln.  
  
 Die Typinformationen für Prozedurparameter wird von ICommandWithParameters:: GetParameterInfo für die meisten Parametertypen unterstützt. Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], mit der Einführung von benutzerdefinierten Typen und die `xml` Datentyp GetParameterInfo-Methode wurde nicht für diesen Zweck ausreichend, da es nicht möglich, einen benutzerdefinierten Typ der Anmeldeinformationen war (Name, Schema, und Katalogsichten Sie) durch ICommandWithParameters. Eine neue Schnittstelle, ISSCommandWithParameters, wurde definiert, um erweiterte Typinformationen bereitzustellen.  
  
 Für Tabellenwertparameter verwenden Sie auch die ISSCommandWithParameters-Schnittstelle, um ausführliche Informationen zu ermitteln. Der Client ruft ISSCommandWithParameters::GetParameterInfo nach der Vorbereitung der Command-Objekt. Für Tabellenwertparameter-Parameter der *wType* -Element der DBPARAMINFO-Struktur wird vom Anbieter auf DBTYPE_TABLE festgelegt. Die *UlParamSize* -Feld der DBPARAMINFO-Struktur hat einen Wert von ~ 0.  
  
 Der Consumer würde dann weitere Eigenschaften (Tabellenwertparameter Katalogname, Schemaname für Tabellenwertparameter-Typ Tabellenwertparameter Typname, Spaltenreihenfolge und Standardspalten) anzufordern, indem Sie ISSCommandWithParamters:: GetParameterProperties.  
  
 Nachdem der Typname bekannt ist, rufen Sie die einzelne Spalte-Informationen, die der Consumer entweder aufrufen muss IOpenRowset::OpenRowsetor erhalten das DBSCHEMA_TABLE_TYPE_COLUMNS-Rowset durch Festlegen des Tabellenwertparameter-Typnamens als Tabellennamen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  