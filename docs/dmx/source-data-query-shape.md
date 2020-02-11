---
title: Form (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c928d4c96917479f8c37415d5ebe2db9b7f9eb98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938118"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;Quelldaten Abfrage&gt; -Form
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Kombiniert Abfragen aus mehreren Datenquellen in einer hierarchischen Tabelle (eine Tabelle mit geschachtelten Tabellen), die zur Falltabelle für das Miningmodell wird.  
  
 Die gesamte Syntax des **Shape** -Befehls ist im [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK) dokumentiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumente  
 *Master Abfrage*  
 Die Abfrage, die die übergeordnete Tabelle zurückgibt.  
  
 *Abfrage für untergeordnete Tabellen*  
 Die Abfrage, die die geschachtelte Tabelle zurückgibt.  
  
 *Master Spalte*  
 Die Spalte in der übergeordneten Tabelle, die die untergeordneten Zeilen aus dem Ergebnis einer Abfrage der untergeordneten Tabelle (child table query) kennzeichnet.  
  
 *untergeordnete Spalte*  
 Die Spalte in der untergeordneten Tabelle, die die übergeordneten Zeilen aus dem Ergebnis einer Masterabfrage (master query) kennzeichnet.  
  
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
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
