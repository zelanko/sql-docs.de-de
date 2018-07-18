---
title: LÖSCHEN (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5b11bda21fe877af419442cb8b98acd4d29c21b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989912"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  LGöscht abhängig von den verwendeten DMX-Klauseln (Data Mining-Erweiterungen) ein Miningmodell, eine Miningstruktur oder eine Miningstruktur samt allen ihr zugeordneten Miningmodellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Argumente  
 *model*  
 Ein Modellbezeichner.  
  
 *Struktur*  
 Ein Strukturbezeichner.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie keinen angeben **MININGMODELL** oder **MININGSTRUKTUR**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sucht nach den Objekttyp, der anhand des Namens, und verarbeitet das richtige Objekt. Wenn der Server eine Miningstruktur und ein Miningmodell enthält, die denselben Namen haben, wird ein Fehler zurückgegeben.  
  
 In der folgenden Tabelle sind die Ergebnisse beschrieben, die sich ergeben, wenn verschiedene Formen der Syntax verwendet werden.  
  
|-Anweisung.|Ergebnis|  
|---------------|------------|  
|DELETE FROM MINING STRUCTURE*\<Struktur >*<br /><br /> oder<br /><br /> DELETE FROM MINING STRUCTURE*\<Struktur >*. INHALT|Führt ProcessClear für die Miningstruktur an. Der gesamte Inhalt wird aus der Miningstruktur sowie aus den dieser zugeordneten Miningmodellen gelöscht.|  
|DELETE FROM MINING STRUCTURE*\<Struktur >*. FÄLLEN|Die Miningstruktur führt ' ProcessClearStructureOnly '. Der gesamte Inhalt wird aus der Miningstruktur gelöscht, wogegen die der Struktur zugeordneten Miningmodelle erhalten bleiben. Drillthrough für die zugeordneten Miningmodelle erzeugt einen Fehler, nachdem der Inhalt der Miningstruktur gelöscht wurde.|  
|Löschen von MINING MODEL*\<Modell >*<br /><br /> oder<br /><br /> Löschen von MINING MODEL*\<Modell >*. INHALT|Führt ProcessClear für das Miningmodell, bleiben jedoch intakt die Statuswerte. Statuswerte sind die möglichen Status einer Spalte. Beispielsweise sind die Statuswerte für eine Geschlecht-Spalte die Werte männlich und weiblich.|  
  
 Weitere Informationen zur Verarbeitung von Typen finden Sie unter [Typelement &#40;XMLA&#41;](../analysis-services/xmla/xml-elements-properties/type-element-xmla.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der gesamte Inhalt aus dem NB_Sample-Modell entfernt.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
