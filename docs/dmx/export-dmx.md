---
title: EXPORT (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2cf3cf85b0efb024d65744f6eea0f5eea47ead83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074855"
---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrahiert ein Miningmodell- oder Miningstrukturobjekt aus dem Server in eine ABF-Datei (Analysis Services Backup File).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Argumente  
 *Objekttyp*  
 Optional den Typ des Objekts (entweder Miningmodell oder Miningstruktur) zu exportieren.  
  
 *Objektname*  
 Optional. Der Name des zu exportierenden Objekts.  
  
 *Dateiname*  
 Die Zeichenfolge, die den Namen und den Speicherort der Datei angibt, in die exportiert werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Ist in der Anweisung ein Miningmodell angegeben, enthält die sich ergebende Datei auch eine zugeordnete Miningstruktur. Wenn die Anweisung gibt **WITH DEPENDENCIES**, alle Objekte, die erforderlich sind, zum Verarbeiten des Objekts (z. B. die Datenquelle und Datenquellensicht) in die ABF-Datei enthalten sind.  
  
 Müssen Sie eine Datenbank oder Server-Administrator zu exportierenden oder importierenden Objekte aus einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank.  
  
## <a name="export-mining-structure-example"></a>Beispiel zum Exportieren einer Miningstruktur  
 Im folgenden Beispiel werden die Miningstrukturen Targeted Mailing und Forecasting sowie das Association-Miningmodell in eine Datei exportiert. Da das Association-Modell zur Market Basket-Miningstruktur gehört, wird in dem Beispiel auch die Market Basket-Struktur exportiert. Alle anderen Miningmodelle, die als Teil der Market Basket-Miningstruktur wird nicht exportiert werden, da das Association-Modell mit exportiert wurde möglicherweise bestehen **MININGMODELL**, nicht **MININGSTRUKTUR**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Beispiel zum Exportieren eines Miningmodells  
 Im folgenden Beispiel wird das Association-Miningmodell in die angegebene Datei exportiert. Da die Anweisung gibt **WITH DEPENDENCIES**, die Datenquelle und Datenquellensicht-Objekte auch in die ABF-Datei enthalten sind.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [IMPORT &#40;DMX&#41;](../dmx/import-dmx.md)   
 [Exportieren und Importieren von Data Mining-Objekten](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
