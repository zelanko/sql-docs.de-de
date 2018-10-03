---
title: CommitTransaction-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CommitTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CommitTransaction
- urn:schemas-microsoft-com:xml-analysis#CommitTransaction
- microsoft.xml.analysis.committransaction
helpviewer_keywords:
- CommitTransaction command
ms.assetid: 1cd814dc-a0be-4305-b44d-faf15e843f7d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eff18a85bc33dfc47377f0613f0696811ff1389a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203200"
---
# <a name="committransaction-element-xmla"></a>CommitTransaction-Element (XMLA)
  Führt einen Commit für eine Transaktion für die aktuelle Sitzung mit einem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <CommitTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der `CommitTransaction`-Befehl führt für die aktuelle Sitzung einen Commit für eine aktive Transaktion aus, die explizit durch das `BeginTransaction`-Element definiert ist. Wenn keine aktive Transaktion vorhanden ist, tritt ein Fehler auf. Besteht bereits eine aktive Transaktion, reduziert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz den Verweiszähler der Transaktionen für die aktuelle Sitzung. Wenn der Verweiszähler explizit definierter aktiver Transaktionen NULL ist, erreicht der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz führt einen Commit der Transaktion.  
  
## <a name="see-also"></a>Siehe auch  
 [BeginTransaction-Element &#40;XMLA&#41;](begintransaction-element-xmla.md)   
 [Cancel-Element &#40;XMLA&#41;](cancel-element-xmla.md)   
 [RollbackTransaction-Element &#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
