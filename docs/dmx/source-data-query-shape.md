---
title: Form (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4d5d93d4236b3cf86719c416ba87517401e4b4f5
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970301"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;Quelldaten Abfrage &gt; -Form
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Kombiniert Abfragen aus mehreren Datenquellen in einer hierarchischen Tabelle (eine Tabelle mit geschachtelten Tabellen), die zur Falltabelle für das Miningmodell wird.  
  
 Die gesamte Syntax des **Shape** -Befehls ist im [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK) dokumentiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SHAPE {<primary query>}  
APPEND ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumente  
 *primäre Abfrage*  
 Die Abfrage, die die übergeordnete Tabelle zurückgibt.  
  
 *Abfrage für untergeordnete Tabellen*  
 Die Abfrage, die die geschachtelte Tabelle zurückgibt.  
  
 *primäre Spalte*  
 Die Spalte in der übergeordneten Tabelle, die die untergeordneten Zeilen aus dem Ergebnis einer Abfrage der untergeordneten Tabelle (child table query) kennzeichnet.  
  
 *untergeordnete Spalte*  
 Die Spalte in der untergeordneten Tabelle, um die übergeordnete Zeile aus dem Ergebnis einer primären Abfrage zu identifizieren.  
  
 *Spalten Tabellenname*  
 Der neu angefügte Spaltenname in der übergeordneten Tabelle für die geschachtelte Tabelle.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie müssen die Abfragen nach der Spalte sortieren, die die übergeordnete Tabelle und die untergeordnete Tabelle verknüpft.  
  
## <a name="examples"></a>Beispiele  
 Sie können das folgende Beispiel innerhalb einer [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md) -Anweisung verwenden, um ein Modell zu trainieren, das eine geschachtelte Tabelle enthält. Die beiden Tabellen innerhalb der **Shape** -Anweisung werden durch die **OrderNumber** -Spalte verknüpft.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#60;Quelldaten Abfrage&#62;](../dmx/source-data-query.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
