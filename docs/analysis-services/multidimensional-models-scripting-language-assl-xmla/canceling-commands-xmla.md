---
title: Abbrechen von Befehlen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: babdafaaa1c507a609760b02895f9438baf21581
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145016"
---
# <a name="canceling-commands-xmla"></a>Abbrechen von Befehlen (XMLA)
  Abhängigkeit von den Administrationsberechtigungen des Benutzers, der den Befehl ausgibt die [Abbrechen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) -Befehl in XML for Analysis (XMLA) einen Befehl, die sich auf eine Sitzung, eine Sitzung, eine Verbindung, einem Serverprozess oder einer zugeordneten Sitzung abbrechen können oder die Verbindung.  
  
## <a name="canceling-commands"></a>Abbrechen von Befehlen  
 Ein Benutzer kann den zurzeit ausgeführten Befehl innerhalb des Kontexts der aktuellen expliziten Sitzung abbrechen, indem Sie senden eine **Abbrechen** -Befehl ohne festgelegte Eigenschaften.  
  
> [!NOTE]  
>  Ein Befehl, der in einer impliziten Sitzung ausgeführt wird, kann von einem Benutzer nicht abgebrochen werden.  
  
### <a name="canceling-batch-commands"></a>Abbrechen von Batch-Befehlen  
 Wenn ein Benutzer abbricht eine **Batch** Befehl, und dann alle restlichen Befehle, die noch nicht ausgeführt wird, innerhalb der **Batch** Befehl abgebrochen werden. Wenn die **Batch** -Befehl transaktional war, werden alle Befehle, die ausgeführt wurden, bevor die **Abbrechen** Rollback-Befehl ausgeführt.  
  
## <a name="canceling-sessions"></a>Abbrechen von Sitzungen  
 Durch Angabe von eine Sitzungs-ID für eine explizite Sitzung in der [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) Eigenschaft der **Abbrechen** Befehl, ein Datenbank- oder Serveradministrator eine Sitzung abbrechen, einschließlich der derzeit ausgeführten Befehl. Ein Datenbankadministrator kann nur Sitzungen für Datenbanken abbrechen, für die er über Administratorberechtigungen verfügt.  
  
 Ein Datenbankadministrator kann die aktiven Sitzungen für eine festgelegte Datenbank abrufen, indem er das DISCOVER_SESSIONS-Schemarowset abruft. Zum Abrufen des DISCOVER_SESSIONS-Schemarowsets verwendet der Datenbankadministrator XMLA **Discover** Methode und gibt Sie den entsprechenden Datenbankbezeichner an für die Einschränkungsspalte session_current_database in der [Einschränkungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) Eigenschaft der **Discover** Methode.  
  
## <a name="canceling-connections"></a>Abbrechen von Verbindungen  
 Durch die Festlegung eines verbindungsbezeichners in der [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) Eigenschaft der **Abbrechen** Befehl, ein Server-Administrator kann alle von einer bestimmten Verbindung, einschließlich aller zugeordneten Sitzungen Abbrechen Ausführen von Befehlen, und der Verbindung.  
  
> [!NOTE]  
>  Wenn die Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht finden und eine Verbindung zugeordneten Sitzungen Abbrechen, wie z. B. wenn die Datapump mehrere Sitzungen gleichzeitig HTTP-Verbindung geöffnet wird, die Instanz die Verbindung nicht abbrechen. Wenn dieser Fall, während der Ausführung gefunden wird einer **Abbrechen** Befehls ein Fehler auftritt.  
  
 Ein Serveradministrator kann die aktiven Verbindungen für Abrufen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz, indem Sie mit dem XMLA DISCOVER_CONNECTIONS-Schemarowsets abrufen **Discover** Methode.  
  
## <a name="canceling-server-processes"></a>Abbrechen von Serverprozessen  
 Durch einen Serverprozessbezeichner (SPID) angeben, in der [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) Eigenschaft der **Abbrechen** Befehl, ein Serveradministrator kann einer bestimmten SPID zugeordneten Befehle Abbrechen.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Abbrechen von zugeordneten Sitzungen und Verbindungen  
 Sie können festlegen, die [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) Eigenschaft auf "true", um die Verbindungen, Sitzungen und die Verbindung, Sitzung oder SPID, die im angegebenen zugeordneten Befehle Abbrechen der **Abbrechen** Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Discover-Methode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
