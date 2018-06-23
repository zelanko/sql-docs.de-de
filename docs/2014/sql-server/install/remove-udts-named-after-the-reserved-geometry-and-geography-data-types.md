---
title: Entfernen Sie UDTs, die nach den reservierten Datentypen GEOMETRY und GEOGRAPHY benannt | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d772f880e1ad88c6423d0a34f71d1a75205169f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061541"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a>Entfernen von UDTs, die nach den reservierten Datentypen GEOMETRY und GEOGRAPHY benannt sind
  Der Upgrade Advisor hat einen benutzerdefinierten Typ (UDT, User-Defined Type) erkannt, der nach einem Ausdruck benannt ist, der entweder für den `geometry`-Datentyp oder den `geography`-Datentyp reserviert ist. Die Datentypen `geometry` und `geography` sind Teil der Funktion für räumliche Daten.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die Ausdrücke, die für räumliche Datentypen verwendet werden, sollten nicht als Namen für die Common Language Runtime (CLR) oder Alias-UDTs genutzt werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie den UDT, der nach dem Datentyp benannt ist, und erstellen Sie den UDT mit einem nicht reservierten Namen neu.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [Übersicht über räumliche Datentypen](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  