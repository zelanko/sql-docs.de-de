---
description: DELETE (DMX)
title: Delete (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eafe865a5d997b0f01a510fc0fad30646a732825
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726241"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
|Anweisung|Ergebnis|  
|---------------|------------|  
|aus Mining Struktur löschen*\<structure>*<br /><br /> oder<br /><br /> aus Mining Struktur löschen *\<structure>* . Inhaltliche|Führt ProcessClear für die Mining Struktur aus. Der gesamte Inhalt wird aus der Miningstruktur sowie aus den dieser zugeordneten Miningmodellen gelöscht.|  
|aus Mining Struktur löschen *\<structure>* . Denen|Führt ProcessClearStructureOnly in der Mining Struktur aus. Der gesamte Inhalt wird aus der Miningstruktur gelöscht, wogegen die der Struktur zugeordneten Miningmodelle erhalten bleiben. Drillthrough für die zugeordneten Miningmodelle erzeugt einen Fehler, nachdem der Inhalt der Miningstruktur gelöscht wurde.|  
|aus Mining Modell löschen*\<model>*<br /><br /> oder<br /><br /> aus Mining Modell löschen *\<model>* . Inhaltliche|Führt ProcessClear für das Mining Modell aus, lässt jedoch die Zustands Werte intakt. Statuswerte sind die möglichen Status einer Spalte. Beispielsweise sind die Statuswerte für eine Geschlecht-Spalte die Werte männlich und weiblich.|  
  
 Weitere Informationen zu Verarbeitungs Typen finden Sie unter [Type-Element &#40;XMLA&#41;](/analysis-services/xmla/xml-elements-properties/type-element-xmla).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der gesamte Inhalt aus dem NB_Sample-Modell entfernt.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
