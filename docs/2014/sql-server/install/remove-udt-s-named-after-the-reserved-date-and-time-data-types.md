---
title: Entfernen Sie UDTS,&#39;s mit dem Namen nach den reservierten Datentypen für Datum und Uhrzeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9692bcc5b3c7685e247730b0f203d273f585f1de
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092991"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>Entfernen Sie UDTS,&#39;s, die nach den reservierten Datum und Uhrzeit-Datentypen benannt sind
  Der Upgrade Advisor hat einen benutzerdefinierten Typ (UDT, User-Defined Type) erkannt, der nach einem Ausdruck benannt ist, der entweder für den `date`-Datentyp oder den `time`-Datentyp reserviert ist.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die Ausdrücke, die für Datentypen verwendet werden, sollten nicht als Namen für die Common Language Runtime (CLR) oder Alias-UDTs genutzt werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie den UDT, der nach dem Datentyp benannt ist, und erstellen Sie den UDT mit einem nicht reservierten Namen neu.  
  
  
