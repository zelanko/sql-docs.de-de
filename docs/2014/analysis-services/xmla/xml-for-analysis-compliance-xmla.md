---
title: XML for Analysis-Kompatibilität (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc7a8da77b72f25a68764636fbe15bc2d9e4ae04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267086"
---
# <a name="xml-for-analysis-compliance-xmla"></a>XML for Analysis-Kompatibilität (XMLA)
  Die XML for Analysis 1.1-Spezifikation beschreibt einen offenen Standard, der Datenzugriff auf Datenquellen unterstützt, die im World Wide Web liegen. In diesem Thema werden den Grad der Kompatibilität mit der XML for Analysis 1.1-Spezifikation, die von unterstützt wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="compliant-items"></a>Kompatible Elemente  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist mit allen verbindlichen Elementen, die in der XML for Analysis 1.1-Spezifikation aufgelistet sind, kompatibel. Außerdem implementiert [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] das folgende optionale Element, das in der XML for Analysis 1.1-Spezifikation beschrieben ist.  
  
|Element|Spezifikation|Implementierung|  
|----------|-------------------|--------------------|  
|Session Support|Die SOAP-Headerelemente, die im Abschnitt "Support for Statefulness in XML for Analysis" der XML for Analysis 1.1-Spezifikation aufgelistet werden.|Alle aufgelisteten SOAP-Header-Elemente werden gemäß der Spezifikation von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt.|  
  
## <a name="extensions"></a>Erweiterungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verlängert außerdem die XML for Analysis 1.1-Spezifikation, um die folgenden weiteren Funktionen und Fähigkeiten zu unterstützen.  
  
|Element|Spezifikation|Implementierung|  
|----------|-------------------|--------------------|  
|Protokollaushandlung|Die XML for Analysis 1.1-Spezifikation enthält keine Informationen.|[ProtocolCapabilities](xml-elements-headers/protocolcapabilities-element-xmla.md) Header-Element hinzugefügt, indem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Aushandlung von Protokollfunktionen zu unterstützen.|  
|XML for Analysis-Befehle (XMLA) werden von der Discover-Methode unterstützt.|Die folgenden Befehle werden von der XML for Analysis 1.1-Spezifikation unterstützt:<br /><br /> -   [Statement-Element &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)|Die folgenden Befehle werden von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt:<br /><br /> -   [Alter-Element &#40;XMLA&#41;](xml-elements-commands/alter-element-xmla.md)<br />-   [Sichern des Elements &#40;XMLA&#41;](xml-elements-commands/backup-element-xmla.md)<br />-   [Batch-Element &#40;XMLA&#41;](xml-elements-commands/batch-element-xmla.md)<br />-   [BeginTransaction-Element &#40;XMLA&#41;](xml-elements-commands/begintransaction-element-xmla.md)<br />-   [Cancel-Element &#40;XMLA&#41;](xml-elements-commands/cancel-element-xmla.md)<br />-   [ClearCache-Element &#40;XMLA&#41;](xml-elements-commands/clearcache-element-xmla.md)<br />-   [CommitTransaction-Element &#40;XMLA&#41;](xml-elements-commands/committransaction-element-xmla.md)<br />-   [Create-Element &#40;XMLA&#41;](xml-elements-commands/create-element-xmla.md)<br />-   [Delete-Element &#40;XMLA&#41;](xml-elements-commands/delete-element-xmla.md)<br />-   [DesignAggregations-Element &#40;XMLA&#41;](xml-elements-commands/designaggregations-element-xmla.md)<br />-   [Drop-Element &#40;XMLA&#41;](xml-elements-commands/drop-element-xmla.md)<br />-   [INSERT-Element &#40;XMLA&#41;](xml-elements-commands/insert-element-xmla.md)<br />-   [Element sperren &#40;XMLA&#41;](xml-elements-commands/lock-element-xmla.md)<br />-   [MergePartitions-Element &#40;XMLA&#41;](xml-elements-commands/mergepartitions-element-xmla.md)<br />-   [NotifyTableChange-Element &#40;XMLA&#41;](xml-elements-commands/notifytablechange-element-xmla.md)<br />-   [Element verarbeiten &#40;XMLA&#41;](xml-elements-commands/process-element-xmla.md)<br />-   [Restore-Element &#40;XMLA&#41;](xml-elements-commands/restore-element-xmla.md)<br />-   [RollbackTransaction-Element &#40;XMLA&#41;](xml-elements-commands/rollbacktransaction-element-xmla.md)<br />-SetPasswordEncryptionKey Element<br />-   [Statement-Element &#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)<br />-   [Subscribe-Element &#40;XMLA&#41;](xml-elements-commands/subscribe-element-xmla.md)<br />-   [Synchronize-Element &#40;XMLA&#41;](xml-elements-commands/synchronize-element-xmla.md)<br />-   [Element Entsperren &#40;XMLA&#41;](xml-elements-commands/unlock-element-xmla.md)<br />-   [Update-Element &#40;XMLA&#41;](xml-elements-commands/update-element-xmla.md)<br />-   [UpdateCells-Element &#40;XMLA&#41;](xml-elements-commands/updatecells-element-xmla.md)|  
|Spaltenfehler in tabellarischen Rowsets|Nicht in der XML for Analysis 1.1-Spezifikation aufgelistet.|Die [Fehler](xml-elements-properties/error-element-xmla.md) Element dient der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] um Fehler in Spaltenelementen, die einem [Zeile](xml-elements-properties/error-element-xmla.md) Element.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis &#40;XMLA&#41; Verweis](xml-for-analysis-xmla-reference.md)  
  
  
