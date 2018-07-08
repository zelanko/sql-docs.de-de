---
title: Abbrechen von Befehlen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77cf7fbc0d90571548bb28fde2dcce066c9151dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210150"
---
# <a name="canceling-commands-xmla"></a>Abbrechen von Befehlen (XMLA)
  Abhängigkeit von den Administrationsberechtigungen des Benutzers, der den Befehl ausgibt die [Abbrechen](../xmla/xml-elements-commands/cancel-element-xmla.md) -Befehl in XML for Analysis (XMLA) einen Befehl, die sich auf eine Sitzung, eine Sitzung, eine Verbindung, einem Serverprozess oder einer zugeordneten Sitzung abbrechen können oder die Verbindung.  
  
## <a name="canceling-commands"></a>Abbrechen von Befehlen  
 Ein Benutzer kann den zurzeit ausgeführten Befehl innerhalb der aktuellen expliziten Sitzung abbrechen, indem er einen `Cancel`-Befehl ohne festgelegte Eigenschaften sendet.  
  
> [!NOTE]  
>  Ein Befehl, der in einer impliziten Sitzung ausgeführt wird, kann von einem Benutzer nicht abgebrochen werden.  
  
### <a name="canceling-batch-commands"></a>Abbrechen von Batch-Befehlen  
 Wenn ein Benutzer einen `Batch`-Befehl abbricht, werden alle noch nicht ausgeführten Befehle innerhalb des `Batch`-Befehls abgebrochen. Wenn es sich bei dem `Batch`-Befehl um eine Transaktionsreplikation handelt, werden alle Befehle, die vor der Ausführung des `Cancel`-Befehls ausgeführt wurden, rückgängig gemacht.  
  
## <a name="canceling-sessions"></a>Abbrechen von Sitzungen  
 Durch Angabe von eine Sitzungs-ID für eine explizite Sitzung in der [SessionID](../xmla/xml-elements-properties/id-element-xmla.md) Eigenschaft der `Cancel` können Datenbankadministratoren oder Serveradministratoren kann eine Sitzung abbrechen, einschließlich des gerade ausgeführten Befehls . Ein Datenbankadministrator kann nur Sitzungen für Datenbanken abbrechen, für die er über Administratorberechtigungen verfügt.  
  
 Ein Datenbankadministrator kann die aktiven Sitzungen für eine festgelegte Datenbank abrufen, indem er das DISCOVER_SESSIONS-Schemarowset abruft. Zum Abrufen des DISCOVER_SESSIONS-Schemarowsets verwendet der Datenbankadministrator XMLA `Discover` Methode und gibt die entsprechende Datenbank-ID für die Einschränkungsspalte session_current_database in der [Einschränkungen](../xmla/xml-elements-properties/restrictions-element-xmla.md) Eigenschaft der `Discover` Methode.  
  
## <a name="canceling-connections"></a>Abbrechen von Verbindungen  
 Durch die Festlegung eines verbindungsbezeichners in der [ConnectionID](../xmla/xml-elements-properties/connectionid-element-xmla.md) Eigenschaft der `Cancel` Befehl, ein Serveradministrator kann alle zugeordneten eine angegebene Verbindung, einschließlich aller zurzeit ausgeführten Befehle, Sitzungen Abbrechen und Kündigen Sie die Verbindung ein.  
  
> [!NOTE]  
>  Wenn die Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht finden und eine Verbindung zugeordneten Sitzungen Abbrechen, wie z. B. wenn die Datapump mehrere Sitzungen gleichzeitig HTTP-Verbindung geöffnet wird, die Instanz die Verbindung nicht abbrechen. Wenn dies während der Ausführung eines `Cancel`-Befehls passiert, tritt ein Fehler auf.  
  
 Ein Serveradministrator kann die aktiven Verbindungen für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz abrufen, indem er das DISCOVER_CONNECTIONS-Schemarowset mithilfe der `Discover`-Methode von XMLA aufruft.  
  
## <a name="canceling-server-processes"></a>Abbrechen von Serverprozessen  
 Durch einen Serverprozessbezeichner (SPID) angeben, in der [SPID](../xmla/xml-elements-properties/spid-element-xmla.md) Eigenschaft der `Cancel` Befehl, ein Serveradministrator kann einer bestimmten SPID zugeordneten Befehle Abbrechen.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Abbrechen von zugeordneten Sitzungen und Verbindungen  
 Sie können festlegen, die [CancelAssociated](../xmla/xml-elements-properties/cancelassociated-element-xmla.md) Eigenschaft auf "true", um die Verbindungen, Sitzungen und die Verbindung, Sitzung oder SPID, die im angegebenen zugeordneten Befehle Abbrechen der `Cancel` Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Discover-Methode &#40;XMLA&#41;](../xmla/xml-elements-methods-discover.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
