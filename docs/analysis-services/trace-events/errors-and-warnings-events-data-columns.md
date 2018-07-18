---
title: Fehler- und Warnungsereignis-Datenspalten | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84a1f21e5556efcf64e1ff1b7c6d5ab2208d1038
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043094"
---
# <a name="errors-and-warnings-events-data-columns"></a>Fehler- und Warnungsereignis-Datenspalten
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die Ereigniskategorie Sicherheitsüberwachung enthält die folgenden Ereignisklassen:  
  
-   Fehlerklasse  
  
 In der folgenden Tabelle sind die Datenspalten für diese Ereignisklasse aufgeführt.  
  
## <a name="error-event-classdata-columns"></a>Fehler-Ereignisklasse – Datenspalten  
  
|**Spaltenname**|**Spalten-ID**|**Spaltentyp**|**Spaltenbeschreibung**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Die Ereignisklasse dient zur Kategorisierung von Ereignissen.|  
|StartTime|3|5|Enthält den Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|SessionType|8|8|Enthält den Typ der Entität, die den Fehler verursachte.|  
|Severity|22|1|Enthält den Schweregrad einer Ausnahme, die dem Fehlerereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Success|23|1|Enthält die Angabe zum Erfolg oder Fehlschlagen des Fehlerereignisses. Die Werte sind:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
|Error|24|1|Enthält die Fehlernummer eines Fehlers, der ggf. dem Fehlerereignis zugeordnet ist.|  
|ConnectionID|25|1|Enthält die eindeutige Verbindungs-ID, die dem Fehlerereignis zugeordnet ist.|  
|DatabaseName|28|8|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , für die das Fehlerereignis aufgetreten ist.|  
|NTUserName|32|8|Enthält den Windows-Benutzernamen, der dem Fehlerereignis zugeordnet ist.|  
|NTDomainName|33|8|Enthält das Windows-Domänenkonto, das dem Anmeldeereignis zugeordnet ist.|  
|ClientHostName|35|8|Enthält den Namen des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird.|  
|ClientProcessID|36|1|Enthält die Prozess-ID der Clientanwendung.|  
|ApplicationName|37|8|Enthält den Namen der Clientanwendung, die die Verbindung mit dem Server hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|SessionID|39|8|Enthält die Serverprozess-ID (SPID), die die dem Fehlerereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|SPID|41|1|Enthält die Serverprozess-ID (SPID), die die dem Fehlerereignis zugeordnete Benutzersitzung eindeutig identifiziert. Die SPID entspricht direkt der Sitzungs-GUID, die von XMLA (XML for Analysis) verwendet wird.|  
|TextData|42|9|Enthält die Textdaten, die dem Fehlerereignis zugeordnet sind.|  
|ServerName|43|8|Enthält den Namen des Servers, auf dem die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ausgeführt wird, auf der das Fehlerereignis aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberwachung-Ereigniskategorie](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
