---
title: Abbrechen von Befehlen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80bddac8f800c1b9394c1ed605007ab0f2137b88
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727464"
---
# <a name="canceling-commands-xmla"></a>Abbrechen von Befehlen (XMLA)
  Abhängig von den administrativen Berechtigungen des Benutzers, der den Befehl ausgibt, kann der [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) -Befehl in XML for Analysis (XMLA) einen Befehl für eine Sitzung, eine Sitzung, eine Verbindung, einen Server Prozess oder eine zugeordnete Sitzung oder Verbindung abbrechen.  
  
## <a name="canceling-commands"></a>Abbrechen von Befehlen  
 Ein Benutzer kann den zurzeit ausgeführten Befehl innerhalb der aktuellen expliziten Sitzung abbrechen, indem er einen `Cancel`-Befehl ohne festgelegte Eigenschaften sendet.  
  
> [!NOTE]  
>  Ein Befehl, der in einer impliziten Sitzung ausgeführt wird, kann von einem Benutzer nicht abgebrochen werden.  
  
### <a name="canceling-batch-commands"></a>Abbrechen von Batch-Befehlen  
 Wenn ein Benutzer einen `Batch`-Befehl abbricht, werden alle noch nicht ausgeführten Befehle innerhalb des `Batch`-Befehls abgebrochen. Wenn es sich bei dem `Batch`-Befehl um eine Transaktionsreplikation handelt, werden alle Befehle, die vor der Ausführung des `Cancel`-Befehls ausgeführt wurden, rückgängig gemacht.  
  
## <a name="canceling-sessions"></a>Abbrechen von Sitzungen  
 Wenn Sie in der [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) -Eigenschaft des `Cancel` Befehls eine Sitzungs-ID für eine explizite Sitzung angeben, kann ein Datenbankadministrator oder Server Administrator eine Sitzung abbrechen, einschließlich des aktuell ausgeführten Befehls. Ein Datenbankadministrator kann nur Sitzungen für Datenbanken abbrechen, für die er über Administratorberechtigungen verfügt.  
  
 Ein Datenbankadministrator kann die aktiven Sitzungen für eine festgelegte Datenbank abrufen, indem er das DISCOVER_SESSIONS-Schemarowset abruft. Zum Abrufen des DISCOVER_SESSIONS Schemarowsets verwendet der Datenbankadministrator die XMLA `Discover` -Methode und gibt den entsprechenden Daten Bank Bezeichner für die SESSION_CURRENT_DATABASE Einschränkungs Spalte in der Eigenschaft [Einschränkungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) der `Discover` Methode an.  
  
## <a name="canceling-connections"></a>Abbrechen von Verbindungen  
 Durch Angeben eines Verbindungs Bezeichners in der [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) -Eigenschaft `Cancel` des Befehls kann ein Server Administrator alle Sitzungen abbrechen, die einer bestimmten Verbindung zugeordnet sind, einschließlich aller Befehle, die ausgeführt werden, und die Verbindung abbrechen.  
  
> [!NOTE]  
>  Wenn die Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die einer Verbindung zugeordneten Sitzungen nicht finden und Abbrechen kann, z. b. wenn die Daten Verschiebung beim Bereitstellen von http-Konnektivität mehrere Sitzungen öffnet, kann die Instanz die Verbindung nicht abbrechen. Wenn dies während der Ausführung eines `Cancel`-Befehls passiert, tritt ein Fehler auf.  
  
 Ein Serveradministrator kann die aktiven Verbindungen für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz abrufen, indem er das DISCOVER_CONNECTIONS-Schemarowset mithilfe der `Discover`-Methode von XMLA aufruft.  
  
## <a name="canceling-server-processes"></a>Abbrechen von Serverprozessen  
 Durch Angeben eines Server Prozess Bezeichners (SPID) in der [SPID-](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) Eigenschaft `Cancel` des Befehls kann ein Server Administrator die Befehle abbrechen, die einer bestimmten SPID zugeordnet sind.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Abbrechen von zugeordneten Sitzungen und Verbindungen  
 Sie können die [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) -Eigenschaft auf true festlegen, um die Verbindungen, Sitzungen und Befehle abzubrechen, die der im `Cancel` Befehl angegebenen Verbindung, Sitzung oder SPID zugeordnet sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Discover-Methode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
