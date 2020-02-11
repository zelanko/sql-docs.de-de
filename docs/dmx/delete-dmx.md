---
title: Delete (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c1c75a6ff18b26bee65365acbc068de87678a9c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070764"
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
  
 *Werks*  
 Ein Strukturbezeichner.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie kein **Mining Modell** oder keine **Mining Struktur**angeben, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sucht nach dem Objekttyp, der auf dem Namen basiert, und verarbeitet das richtige Objekt. Wenn der Server eine Miningstruktur und ein Miningmodell enthält, die denselben Namen haben, wird ein Fehler zurückgegeben.  
  
 In der folgenden Tabelle sind die Ergebnisse beschrieben, die sich ergeben, wenn verschiedene Formen der Syntax verwendet werden.  
  
|-Anweisung.|Ergebnis|  
|---------------|------------|  
|Aus Mining Struktur*\<Struktur löschen>*<br /><br /> oder<br /><br /> Aus Mining Struktur*\<Struktur löschen>*. Inhaltliche|Führt ProcessClear für die Mining Struktur aus. Der gesamte Inhalt wird aus der Miningstruktur sowie aus den dieser zugeordneten Miningmodellen gelöscht.|  
|Aus Mining Struktur*\<Struktur löschen>*. Denen|Führt ProcessClearStructureOnly in der Mining Struktur aus. Der gesamte Inhalt wird aus der Miningstruktur gelöscht, wogegen die der Struktur zugeordneten Miningmodelle erhalten bleiben. Drillthrough für die zugeordneten Miningmodelle erzeugt einen Fehler, nachdem der Inhalt der Miningstruktur gelöscht wurde.|  
|Aus Mining Modell*\<Modell löschen>*<br /><br /> oder<br /><br /> Aus Mining Modell*\<Modell>* löschen. Inhaltliche|Führt ProcessClear für das Mining Modell aus, lässt jedoch die Zustands Werte intakt. Statuswerte sind die möglichen Status einer Spalte. Beispielsweise sind die Statuswerte für eine Geschlecht-Spalte die Werte männlich und weiblich.|  
  
 Weitere Informationen zu Verarbeitungs Typen finden Sie unter [Type-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der gesamte Inhalt aus dem NB_Sample-Modell entfernt.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
