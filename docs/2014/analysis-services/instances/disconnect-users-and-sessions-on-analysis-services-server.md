---
title: Trennen von Benutzern und Sitzungen auf Analysis Services-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c1a974025e1f23cd5fa0a3b7824431d422bfe35
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080072"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Trennen von Benutzern und Sitzungen auf Analysis Services-Server
  Ein Administrator von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann die Benutzeraktivität als Teil der Arbeitsauslastungsverwaltung beenden. Hierzu werden Sitzungen und Verbindungen abgebrochen. Sitzungen können automatisch (implizit) erstellt werden, wenn eine Abfrage ausgeführt wird, oder sie können (explizit) durch den Administrator erstellt und dabei benannt werden. Bei Verbindungen handelt es sich um flexible Datenleitungen, über die Abfragen ausgeführt werden können. Sowohl Sitzungen als auch Verbindungen können beendet werden, während sie aktiv sind. Ein Administrator möchte z. B. die Verarbeitung einer Sitzung beenden, wenn diese zu lange dauert, oder wenn Zweifel bestehen, dass der ausgeführte Befehl richtig geschrieben wurde.  
  
## <a name="ending-sessions-and-connections"></a>Beenden von Sitzungen und Verbindungen  
 Sitzungen und Verbindungen können mithilfe von dynamischen Verwaltungssichten (DMVs) und XMLA verwaltet werden:  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Analysis Services-Instanz her.  
  
2.  Fügen Sie eine der folgenden DMV-Abfragen in ein MDX-Abfragefenster ein, um eine Liste aller momentan ausgeführten Sitzungen, Verbindungen und Befehle anzuzeigen:  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  Drücken Sie F5, um die Abfrage auszuführen.  
  
     Die DMV-Abfrage gibt Sitzungs- und Verbindungsinformationen in einem tabellarischen Resultset zurück, das einfacher zu lesen und zu kopieren ist.  
  
 Lassen Sie das Abfragefenster geöffnet. Im nächsten Schritt möchten Sie zu dieser Seite zurückkehren, um die SPIDs der Sitzung, die getrennt werden soll, zu kopieren.  
  
 Öffnen Sie zum Beenden einer Sitzung ein zweites XMLA-Abfragefenster.  
  
1.  Fügen Sie die folgende Syntax in ein MDX-Abfragefenster ein, und ersetzen Sie dabei den ConnectionID-, SessionID- oder den SPID-Platzhalter durch einen gültigen Wert, den Sie im vorherigen Schritt kopiert haben.  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Drücken Sie F5, um den cancel-Befehl auszuführen.  
  
 Beim Beenden einer Verbindung werden alle Sitzungen und SPIDs abgebrochen und somit die Hostsitzung geschlossen.  
  
 Beim Beenden einer Sitzung werden alle Befehle (SPIDs), die als Teil dieser Sitzung ausgeführt werden, beendet.  
  
 Beim Beenden einer SPID wird ein bestimmter Befehl abgebrochen.  
  
 In seltenen Fällen wird in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Verbindung nicht geschlossen, wenn nicht alle mit der Verbindung verknüpften Sitzungen und SPIDs nachverfolgt werden können, z.B. wenn mehrere Sitzungen in einem HTTP-Szenario geöffnet sind.  
  
 Weitere Informationen zu XMLA, auf die in diesem Thema verwiesen wird, finden Sie unter [Execute-Methode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) und [Cancel-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [BeginSession-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [EndSession-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Session-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
