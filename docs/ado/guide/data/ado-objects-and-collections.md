---
title: ADO-Objekte und Auflistungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and collections
ms.assetid: 7a745aae-9372-49b6-8dae-b9c93e5f3216
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5743e04b402302cc53b7694d8160edfb11769e0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783878"
---
# <a name="ado-objects-and-collections"></a>ADO-Objekte und -Collections
ADO besteht aus den folgenden neun Objekte und vier Auflistungen.  
  
|Objekt oder einer Auflistung|Description|  
|--------------------------|-----------------|  
|**Verbindung** Objekt|Stellt eine eindeutige Sitzung mit einer Datenquelle dar. Im Fall von einem Client/Server-Datenbanksystem kann es eine tatsächliche Netzwerk-Verbindung mit dem Server entsprechen. Abhängig von den Funktionen, die von der Anbieter, einige Auflistungen, Methoden oder Eigenschaften unterstützt eine **Verbindung** Objekt möglicherweise nicht zur Verfügung.|  
|**Command** -Objekt|Dient zum Definieren der eines bestimmten Befehls z. B. eine SQL-Abfrage für eine Datenquelle ausgeführt werden soll.|  
|**Recordset** Objekt|Stellt die gesamte Gruppe von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Alle **Recordset** Objekte bestehen aus Datensätzen (Zeilen) und Feldern (Spalten).|  
|**Datensatz** Objekt|Stellt eine einzelne Zeile mit Daten, entweder von einem **Recordset** oder vom Anbieter. Dieser Datensatz könnte es sich um einen Datenbankdatensatz oder eine andere Art von Objekt z. B. eine Datei oder ein Verzeichnis, abhängig von Ihrem Anbieter darstellen.|  
|**Stream** Objekt|Stellt einen Datenstrom Binär oder Text dar. Beispielsweise kann ein XML-Dokument in einen Stream für Befehl eingegebene oder zurückgegebene von bestimmten Anbietern wie die Ergebnisse einer Abfrage geladen werden. Ein **Stream** Objekt kann verwendet werden, um die Felder oder Einträge mit diese Datenströme zu bearbeiten.|  
|**Parameter** Objekt|Stellt einen Parameter oder die zugeordnete Argument ein **Befehl** Objekt, auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur.|  
|**Feld** Objekt|Stellt eine Spalte mit einem gemeinsamen Datentyp. Jede **Feld** -Objekt entspricht, auf eine Spalte in der **Recordset**.|  
|**Eigenschaft** Objekt|Repräsentiert eine Eigenschaft eines ADO-Objekts, das vom Anbieter definiert ist. ADO-Objekte verfügen über zwei Typen von Eigenschaften: integrierte und dynamische. Integrierte Eigenschaften sind diese Eigenschaften in ADO und sofort zur Verfügung, um jedes neue Objekt implementiert wird. Die **Eigenschaft** Objekt ist ein Container für die dynamischen Eigenschaften, die vom zugrunde liegenden Anbieter definiert.|  
|**Error** -Objekt|Enthält Details über den Datenzugriff, die auf einem einzigen Vorgang im Zusammenhang mit der Anbieter beziehen.|  
|**Felder** Auflistung|Enthält alle der **Feld** Objekte von einem **Recordset** oder **Datensatz** Objekt.|  
|**Eigenschaften** Auflistung|Enthält alle der **Eigenschaft** Objekte für eine bestimmte Instanz eines Objekts.|  
|**Parameter** Auflistung|Enthält alle der **Parameter** Objekte von einem **Befehl** Objekt.|  
|**Fehler** Auflistung|Enthält alle der **Fehler** Objekte, die in Reaktion auf einen einzelnen Anbieter bezogene Fehler erstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)
