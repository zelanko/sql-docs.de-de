---
description: EXPORT (DMX)
title: Export (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2c7f2f5e8e3f46fc8e6301cf2e93afa709207dd0
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726199"
---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Extrahiert ein Miningmodell- oder Miningstrukturobjekt aus dem Server in eine ABF-Datei (Analysis Services Backup File).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Argumente  
 *Objekttyp*  
 Optional. der Typ des zu exportierenden Objekts (entweder Mining Modell oder Mining Struktur).  
  
 *Objektname*  
 Optional. Der Name des zu exportierenden Objekts.  
  
 *filename*  
 Die Zeichenfolge, die den Namen und den Speicherort der Datei angibt, in die exportiert werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist in der Anweisung ein Miningmodell angegeben, enthält die sich ergebende Datei auch eine zugeordnete Miningstruktur. Wenn die-Anweisung **with-Abhängigkeiten**angibt, sind alle-Objekte, die zum Verarbeiten des Objekts erforderlich sind (z. b. die Datenquelle und die Datenquellen Sicht), in der ABF-Datei enthalten.  
  
 Sie müssen Datenbank-oder Server Administrator sein, um Objekte aus einer Datenbank exportieren oder importieren zu können [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="export-mining-structure-example"></a>Beispiel zum Exportieren einer Miningstruktur  
 Im folgenden Beispiel werden die Miningstrukturen Targeted Mailing und Forecasting sowie das Association-Miningmodell in eine Datei exportiert. Da das Association-Modell zur Market Basket-Miningstruktur gehört, wird in dem Beispiel auch die Market Basket-Struktur exportiert. Alle anderen Mining Modelle, die möglicherweise als Teil der Market Basket-Mining Struktur vorhanden sind, werden nicht exportiert, da das Association-Modell mithilfe des **Mining Modells**exportiert wurde, nicht mit der **Mining Struktur**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Beispiel zum Exportieren eines Miningmodells  
 Im folgenden Beispiel wird das Association-Miningmodell in die angegebene Datei exportiert. Da die-Anweisung **with-Abhängigkeiten**angibt, sind auch die Datenquellen-und Datenquellen Sicht-Objekte in der ABF-Datei enthalten.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Importieren &#40;DMX-&#41;](../dmx/import-dmx.md)   
 [Exportieren und Importieren von Data Mining-Objekten](/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
