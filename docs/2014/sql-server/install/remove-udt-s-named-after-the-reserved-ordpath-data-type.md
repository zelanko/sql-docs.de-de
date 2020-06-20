---
title: Entfernen Sie UDT-&#39;s, die nach dem reservierten ordpath-Datentyp benannt sind. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059132"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>UDT-&#39;s entfernen, die nach dem reservierten ordpath-Datentyp benannt sind
  Upgrade Advisor hat einen benutzerdefinierten Typ (UDT, User-Defined Type) erkannt, der nach einem Ausdruck benannt ist, der für den `ORDPATH`-Datentyp reserviert ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Die Ausdrücke, die für integrierte Datentypen verwendet werden, sollten nicht als Namen für die Common Language Runtime (CLR) oder Alias-UDTs genutzt werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie den UDT, der nach dem Datentyp benannt ist, und erstellen Sie den UDT mit einem nicht reservierten Namen neu.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
