---
title: Überwachen von Ablaufverfolgungen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, traces
- XMLA, traces
- monitoring traces [XMLA]
- traces [Analysis Services]
ms.assetid: cdbfb984-18bd-4c4e-8fb7-d64ce298ed35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 678c6d2312261475f4b970b1535ce1faa1f00930
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62729070"
---
# <a name="monitoring-traces-xmla"></a>Überwachen von Ablaufverfolgungen (XMLA)
  Sie können die [abonnieren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) -Befehl in XML for Analysis (XMLA) zum Überwachen einer vorhandenen Ablaufverfolgungs definiert, die auf einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Der `Subscribe`-Befehl gibt die Ergebnisse einer Ablaufverfolgung als Rowset zurück.  
  
## <a name="specifying-a-trace"></a>Festlegen einer Ablaufverfolgung  
 Die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der `Subscribe` -Befehls muss einen Objektverweis auf eine enthalten eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz oder eine Ablaufverfolgung für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz. Wenn die `Object`-Eigenschaft nicht festgelegt wird oder wenn in der `Object`-Eigenschaft kein Ablaufverfolgungsbezeichner festgelegt wird, überwacht der `Subscribe`-Befehl die Standardablaufverfolgung der expliziten Sitzung, die im SOAP-Header für den Befehl festgelegt wurde.  
  
## <a name="returning-results"></a>Zurückgeben von Ergebnissen  
 Der `Subscribe`-Befehl gibt ein Rowset zurück, das die Ablaufverfolgungsereignisse enthält, die von der festgelegten Ablaufverfolgung erfasst wurden. Die `Subscribe` -Befehl gibt Ablaufverfolgungsergebnisse zurück, bis der Befehl, durch abgebrochen wird die [Abbrechen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) Befehl.  
  
 Das Rowset enthält die in der folgenden Tabelle aufgeführten Spalten.  
  
|Spalte|Datentyp|Beschreibung|  
|------------|---------------|-----------------|  
|EventClass|Integer|Die von der Ablaufverfolgung empfangene Ereignisklasse des Ereignisses.|  
|EventSubclass|Lange ganze Zahl|Die von der Ablaufverfolgung empfangene Ereignisunterklasse des Ereignisses.|  
|CurrentTime|DATETIME|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|DATETIME|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|EndTime|DATETIME|Zeitpunkt, zu dem das Ereignis beendet wurde (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".<br /><br /> Diese Spalte wird nicht für Ereignisklassen aufgefüllt, die den Beginn eines Prozesses oder einer Aktion beschreiben.|  
|Duration|Lange ganze Zahl|Die Gesamtzeitspanne (in Millisekunden), die für das Ereignis vergangen ist.|  
|CPUTime|Lange ganze Zahl|Die Prozessorzeit (in Millisekunden), die für das Ereignis vergangen ist.|  
|JobID|Lange ganze Zahl|Der Auftragsbezeichner für den Prozess.|  
|SessionID|Zeichenfolge|Der Bezeichner der Sitzung, für die das Ereignis aufgetreten ist.|  
|SessionType|Zeichenfolge|Der Typ der Sitzung, für die das Ereignis aufgetreten ist.|  
|ProgressTotal|Lange ganze Zahl|Der Gesamtfortschritt, der von dem Ereignis gemeldet wurde.|  
|IntegerData|Lange ganze Zahl|Die diesem Ereignis zugeordneten ganzzahligen Daten. Der Inhalt dieser Spalte ist von der Ereignisklasse und der Unterklasse des Ereignisses abhängig.|  
|ObjectID|Zeichenfolge|Der Bezeichner des Objekts, für das das Ereignis aufgetreten ist.|  
|ObjectType|Zeichenfolge|Der Typ des in ObjectName festgelegten Objekts.|  
|ObjectName|Zeichenfolge|Der Name des Objekts, für das das Ereignis aufgetreten ist.|  
|ObjectPath|Zeichenfolge|Der hierarchische Pfad des Objekts, für das das Ereignis aufgetreten ist. Der Pfad wird als kommagetrennte Zeichenfolge von Objektbezeichnern für die übergeordneten Elemente des in ObjectName festgelegten Objekts dargestellt.|  
|ObjectReference|Zeichenfolge|Die XML-Darstellung des Objektverweises für das in ObjectName festgelegte Objekt.|  
|NestLevel|Integer|Die Ebene der Transaktion, für die das Ereignis aufgetreten ist.|  
|NumSegments|Lange ganze Zahl|Die Anzahl der Datensegmente, die von dem Befehl, für den das Ereignis aufgetreten ist, betroffen ist, oder auf die zugegriffen wurde.|  
|Schweregrad|Integer|Der Schweregrad einer Ausnahme für das Ereignis. Die Spalte kann einen der folgenden Werte enthalten:<br /><br /> Wert: 0 = Erfolg<br /><br /> Wert: 1 = Information<br /><br /> Wert: 2 = Warnung<br /><br /> Wert: 3 = Fehler|  
|Erfolgreich|Boolean|Gibt an, ob ein Befehl erfolgreich war oder zu einem Fehler geführt hat.|  
|Fehler|Lange ganze Zahl|Die Fehlernummer des Ereignisses (falls zutreffend).|  
|ConnectionID|Zeichenfolge|Der Bezeichner der Verbindung, für die das Ereignis aufgetreten ist.|  
|DatabaseName|Zeichenfolge|Der Name der Datenbank, für die das Ereignis aufgetreten ist.|  
|NTUserName|Zeichenfolge|Der Windows-Benutzername des Benutzers, der dem Ereignis zugeordnet ist.|  
|NTDomainName|Zeichenfolge|Die Windows-Domäne des Benutzers, der dem Ereignis zugeordnet ist.|  
|ClientHostName|Zeichenfolge|Der Name des Computers, auf dem die Clientanwendung ausgeführt wird. Diese Spalte wird mit den von der Clientanwendung übergebenen Werten aufgefüllt.|  
|ClientProcessID|Lange ganze Zahl|Der Prozessbezeichner der Clientanwendung.|  
|ApplicationName|Zeichenfolge|Der Name der Clientanwendung, die die Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Clientanwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|NTCanonicalUserName|Zeichenfolge|Der kanonische Windows-Benutzername des Benutzers, der dem Ereignis zugeordnet ist.|  
|SPID|Zeichenfolge|Die Serverprozess-ID (SPID) der Sitzung, für die das Ereignis aufgetreten ist. Der Wert dieser Spalte entspricht direkt der Sitzungs-ID, die im SOAP-Header der XMLA-Nachricht festgelegt wurde, für die das Ereignis aufgetreten ist.|  
|TextData|Zeichenfolge|Die diesem Ereignis zugeordneten Textdaten. Der Inhalt dieser Spalte ist von der Ereignisklasse und der Unterklasse des Ereignisses abhängig.|  
|ServerName|Zeichenfolge|Der Name der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, für die das Ereignis aufgetreten ist.|  
|RequestParameters|Zeichenfolge|Die Parameter der parametrisierten Abfrage oder des XMLA-Befehls, für die oder den das Ereignis aufgetreten ist.|  
|RequestProperties|Zeichenfolge|Die Eigenschaften der XMLA-Methode, für die das Ereignis aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
