---
title: Überwachen von Ablauf Verfolgungen (XMLA) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62729070"
---
# <a name="monitoring-traces-xmla"></a>Überwachen von Ablaufverfolgungen (XMLA)
  Sie können den Befehl [abonnieren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) in XML for Analysis (XMLA) verwenden, um eine vorhandene Ablauf Verfolgung zu überwachen, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]die in einer Instanz von definiert ist. Der `Subscribe`-Befehl gibt die Ergebnisse einer Ablaufverfolgung als Rowset zurück.  
  
## <a name="specifying-a-trace"></a>Festlegen einer Ablaufverfolgung  
 Die [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Eigenschaft des `Subscribe` -Befehls muss einen Objekt Verweis auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder eine-Ablauf Verfolgung [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf einer-Instanz enthalten. Wenn die `Object`-Eigenschaft nicht festgelegt wird oder wenn in der `Object`-Eigenschaft kein Ablaufverfolgungsbezeichner festgelegt wird, überwacht der `Subscribe`-Befehl die Standardablaufverfolgung der expliziten Sitzung, die im SOAP-Header für den Befehl festgelegt wurde.  
  
## <a name="returning-results"></a>Zurückgeben von Ergebnissen  
 Der `Subscribe`-Befehl gibt ein Rowset zurück, das die Ablaufverfolgungsereignisse enthält, die von der festgelegten Ablaufverfolgung erfasst wurden. Der `Subscribe` Befehl gibt Ablauf Verfolgungs Ergebnisse zurück, bis der Befehl durch den [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) -Befehl abgebrochen wird.  
  
 Das Rowset enthält die in der folgenden Tabelle aufgeführten Spalten.  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|EventClass|Integer|Die von der Ablaufverfolgung empfangene Ereignisklasse des Ereignisses.|  
|EventSubclass|Lange ganze Zahl|Die von der Ablaufverfolgung empfangene Ereignisunterklasse des Ereignisses.|  
|CurrentTime|Datetime|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|StartTime|Datetime|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar. Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".|  
|EndTime|Datetime|Zeitpunkt, zu dem das Ereignis beendet wurde (falls verfügbar). Für das Filtern lauten die erwarteten Formate "JJJJ-MM-TT" und "JJJJ-MM-TT HH:MM:SS".<br /><br /> Diese Spalte wird nicht für Ereignisklassen aufgefüllt, die den Beginn eines Prozesses oder einer Aktion beschreiben.|  
|Duration|Lange ganze Zahl|Die Gesamtzeitspanne (in Millisekunden), die für das Ereignis vergangen ist.|  
|CPUTime|Lange ganze Zahl|Die Prozessorzeit (in Millisekunden), die für das Ereignis vergangen ist.|  
|JobID|Lange ganze Zahl|Der Auftragsbezeichner für den Prozess.|  
|SessionID|String|Der Bezeichner der Sitzung, für die das Ereignis aufgetreten ist.|  
|SessionType|String|Der Typ der Sitzung, für die das Ereignis aufgetreten ist.|  
|ProgressTotal|Lange ganze Zahl|Der Gesamtfortschritt, der von dem Ereignis gemeldet wurde.|  
|IntegerData|Lange ganze Zahl|Die diesem Ereignis zugeordneten ganzzahligen Daten. Der Inhalt dieser Spalte ist von der Ereignisklasse und der Unterklasse des Ereignisses abhängig.|  
|ObjectID|String|Der Bezeichner des Objekts, für das das Ereignis aufgetreten ist.|  
|ObjektType|String|Der Typ des in ObjectName festgelegten Objekts.|  
|ObjectName|String|Der Name des Objekts, für das das Ereignis aufgetreten ist.|  
|ObjectPath|String|Der hierarchische Pfad des Objekts, für das das Ereignis aufgetreten ist. Der Pfad wird als kommagetrennte Zeichenfolge von Objektbezeichnern für die übergeordneten Elemente des in ObjectName festgelegten Objekts dargestellt.|  
|ObjectReference|String|Die XML-Darstellung des Objektverweises für das in ObjectName festgelegte Objekt.|  
|NestLevel|Integer|Die Ebene der Transaktion, für die das Ereignis aufgetreten ist.|  
|NumSegments|Lange ganze Zahl|Die Anzahl der Datensegmente, die von dem Befehl, für den das Ereignis aufgetreten ist, betroffen ist, oder auf die zugegriffen wurde.|  
|severity|Integer|Der Schweregrad einer Ausnahme für das Ereignis. Die Spalte kann einen der folgenden Werte enthalten:<br /><br /> Wert: 0 = Erfolg<br /><br /> Wert: 1 = Informationen<br /><br /> Wert: 2 = Warnung<br /><br /> Wert: 3 = Fehler|  
|Erfolg|Boolean|Gibt an, ob ein Befehl erfolgreich war oder zu einem Fehler geführt hat.|  
|Fehler|Lange ganze Zahl|Die Fehlernummer des Ereignisses (falls zutreffend).|  
|ConnectionID|String|Der Bezeichner der Verbindung, für die das Ereignis aufgetreten ist.|  
|DatabaseName|String|Der Name der Datenbank, für die das Ereignis aufgetreten ist.|  
|NTUserName|String|Der Windows-Benutzername des Benutzers, der dem Ereignis zugeordnet ist.|  
|NTDomainName|String|Die Windows-Domäne des Benutzers, der dem Ereignis zugeordnet ist.|  
|ClientHostName|String|Der Name des Computers, auf dem die Clientanwendung ausgeführt wird. Diese Spalte wird mit den von der Clientanwendung übergebenen Werten aufgefüllt.|  
|ClientProcessID|Lange ganze Zahl|Der Prozessbezeichner der Clientanwendung.|  
|ApplicationName|String|Der Name der Clientanwendung, die die Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Clientanwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|  
|NTCanonicalUserName|String|Der kanonische Windows-Benutzername des Benutzers, der dem Ereignis zugeordnet ist.|  
|SPID|String|Die Serverprozess-ID (SPID) der Sitzung, für die das Ereignis aufgetreten ist. Der Wert dieser Spalte entspricht direkt der Sitzungs-ID, die im SOAP-Header der XMLA-Nachricht festgelegt wurde, für die das Ereignis aufgetreten ist.|  
|TextData|String|Die diesem Ereignis zugeordneten Textdaten. Der Inhalt dieser Spalte ist von der Ereignisklasse und der Unterklasse des Ereignisses abhängig.|  
|Servername|String|Der Name der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz, für die das Ereignis aufgetreten ist.|  
|RequestParameters|String|Die Parameter der parametrisierten Abfrage oder des XMLA-Befehls, für die oder den das Ereignis aufgetreten ist.|  
|RequestProperties|String|Die Eigenschaften der XMLA-Methode, für die das Ereignis aufgetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
