---
title: Trennen von Benutzern und Sitzungen auf Analysis Services-Server | Microsoft-Dokumentation
ms.date: 07/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 696c6548dadda2412566acf7fae1e2cff2b28095
ms.sourcegitcommit: 9af07bd57b76a34d3447e9e15f8bd3b17709140a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624399"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Trennen von Benutzern und Sitzungen auf Analysis Services-Server
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  Als Administrator sollten Sie auf die Benutzeraktivität als Teil der arbeitsauslastungsverwaltung beenden. Hierzu werden Sitzungen und Verbindungen abgebrochen. Sitzungen können automatisch (implizit) erstellt werden, wenn eine Abfrage ausgeführt wird, oder sie können (explizit) durch den Administrator erstellt und dabei benannt werden. Bei Verbindungen handelt es sich um flexible Datenleitungen, über die Abfragen ausgeführt werden können. Sowohl Sitzungen als auch Verbindungen können beendet werden, während sie aktiv sind. Beispielsweise empfiehlt es sich zum Beenden einer Sitzung verarbeitet werden, wenn es sich bei die Verarbeitung zu lange dauert oder wenn Zweifel bestehen, gibt an, ob der ausgeführte Befehl richtig geschrieben wurde.  
  
## <a name="ending-sessions-and-connections"></a>Beenden von Sitzungen und Verbindungen  
 Verwenden Sie zum Verwalten von Sitzungen und Verbindungen, Dynamic Management Views (DMVs) und XMLA ein:  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer Analysis Services-Instanz her.  
  
2.  Fügen Sie eine der folgenden DMV-Abfragen in ein MDX-Abfragefenster ein, um eine Liste aller momentan ausgeführten Sitzungen, Verbindungen und Befehle anzuzeigen:  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  (Diese Abfrage gilt nicht für Azure Analysis Services)
  
     `Select * from $System.Discover_Commands`  
  
3.  Drücken Sie F5, um die Abfrage auszuführen.  
  
     Die DMV-Abfrage gibt Sitzungs- und Verbindungsinformationen in einem tabellarischen Resultset zurück, das einfacher zu lesen und zu kopieren ist.  
  
 Lassen Sie das Abfragefenster geöffnet. Im nächsten Schritt möchten Sie zu dieser Seite zurückkehren, um die SPIDs der Sitzung, die getrennt werden soll, zu kopieren.  
  
 Öffnen Sie zum Beenden einer Sitzung ein zweites XMLA-Abfragefenster.  
  
1.  Fügen Sie die folgende Syntax in ein MDX-Abfragefenster ein, und ersetzen Sie dabei den ConnectionID-, SessionID- oder den SPID-Platzhalter durch einen gültigen Wert, den Sie im vorherigen Schritt kopiert haben.  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Drücken Sie F5, um den cancel-Befehl auszuführen.  

SPID/SessionID Abbrechen, wird aktive Befehle, die unter der Sitzung, die für die SPID/SessionID abgebrochen. Abbrechen einer Verbindungs identifiziert die Sitzung, die der Verbindung zugeordnet, und aktive Befehle, die unter dieser Sitzung abbrechen. In seltenen Fällen wird eine Verbindung nicht geschlossen, wenn die Engine alle Sitzungen und SPIDs, die der Verbindung zugeordnete nachverfolgt werden kann; beispielsweise, wenn mehrere Sitzungen in einem HTTP-Szenario geöffnet sind.   
  
Weitere Informationen zu XMLA, die in diesem Thema verwiesen wird, finden Sie unter [Execute-Methode &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) und [Cancel-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [BeginSession-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [EndSession-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Session-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
