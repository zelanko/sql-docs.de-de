---
title: XML for Analysis (XMLA)-Kompatibilität | Microsoft-Dokumentation
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b618fdd8cca3faed72afb0276f18cd928a3f31f7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051588"
---
# <a name="xml-for-analysis-xmla-compliance"></a>XML for Analysis (XMLA)-Kompatibilität
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]  

  Die XML for Analysis 1.1-Spezifikation beschreibt einen offenen Standard, der Datenzugriff auf Datenquellen unterstützt, die im World Wide Web liegen. In diesem Thema werden den Grad der Kompatibilität mit der XML for Analysis 1.1-Spezifikation, die von Azure Analysis Services und SQL Server Analysis Services unterstützt wird.  
  
## <a name="compliant-items"></a>Kompatible Elemente  
Analysis Services ist mit allen verbindlichen Elementen, die in der XML for Analysis 1.1-Spezifikation aufgelistet. Analysis Services implementiert darüber hinaus das folgende optionale Element in der XML for Analysis 1.1-Spezifikation beschrieben.  
  
|Element|Spezifikation|Implementierung|  
|----------|-------------------|--------------------|  
|Session Support|Die SOAP-Headerelemente, die im Abschnitt "Support for Statefulness in XML for Analysis" der XML for Analysis 1.1-Spezifikation aufgelistet werden.|Alle aufgelisteten SOAP-Header-Elemente werden von Analysis Services unterstützt, wie in der Spezifikation beschrieben.|  
  
## <a name="extensions"></a>Erweiterungen  
 Analysis Services erweitert auch die XML for Analysis 1.1-Spezifikation zur Unterstützung der folgenden zusätzlichen Features und Funktionen.  
  
|Element|Spezifikation|Implementierung|  
|----------|-------------------|--------------------|  
|Protokollaushandlung|Die XML for Analysis 1.1-Spezifikation enthält keine Informationen.|ProtocolCapabilities-Header-Element hinzugefügt, die von Analysis Services für die Aushandlung von Protokollfunktionen zu unterstützen.|  
|XML for Analysis-Befehle (XMLA) werden von der Discover-Methode unterstützt.|Die folgenden Befehle werden von der XML for Analysis 1.1-Spezifikation unterstützt:<br /><br /> [Statement-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|Die folgenden Befehle werden von Analysis Services unterstützt:<br /><br /> [Alter-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Sichern des Elements &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Batch-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [BeginTransaction-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Cancel-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [ClearCache-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [CommitTransaction-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Create-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Delete-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [DesignAggregations-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Drop-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [INSERT-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Element sperren &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [MergePartitions-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [NotifyTableChange-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Element verarbeiten &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Restore-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [RollbackTransaction-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Statement-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Subscribe-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Synchronize-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Element Entsperren &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Update-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [UpdateCells-Element &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Spaltenfehler in tabellarischen Rowsets|Nicht in der XML for Analysis 1.1-Spezifikation aufgelistet.|Die [Fehler](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) Element werden von Analysis Services zum Melden von Fehlern Spaltenelementen, die einem [Zeile](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) Element.|  
  
## <a name="see-also"></a>Siehe auch
 [XML for Analysis-Referenz &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
