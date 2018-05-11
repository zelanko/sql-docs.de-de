---
title: BeginTransaction-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 452bf0463a073ec4033b9a0c62231838b8a7978a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="begintransaction-element-xmla"></a>BeginTransaction-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Startet eine Transaktion für die aktuelle Sitzung mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der **BeginTransaction** -Befehl startet eine aktive Transaktion auf der aktuellen Sitzung. Besteht bereits eine aktive Transaktion, inkrementiert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz den Verweiszähler der Transaktionen für die aktuelle Sitzung. Wenn nicht, startet die Instanz eine neue Transaktion und setzt den Verweiszähler der aktuellen Sitzung auf 1. Wenn eine aktive Transaktion explizit über den **BeginTransaction** -Befehl angegeben wird, werden alle folgenden Befehle innerhalb der explizit angegebenen Transaktion ausgeführt.  
  
 Wenn die aktuelle Sitzung beendet wird und der Verweiszähler der Transaktionen höher als null ist, wird für alle aktiven Transaktionen ein Rollback ausgeführt.  
  
 Wenn es in der aktuellen Sitzung keine explizit angegebenen aktiven Transaktionen gibt, wird jeder in der aktuellen Sitzung ausgegebene Befehl innerhalb einer implizit definierten Transaktion ausgeführt. Ein Commit wird für die implizite Transaktion ausgeführt, wenn der Befehl erfolgreich ist; bei einem Fehlschlagen des Befehls wird ein Rollback ausgeführt.  
  
## <a name="see-also"></a>Siehe auch  
 [Cancel-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [CommitTransaction-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [RollbackTransaction-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
