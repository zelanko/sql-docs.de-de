---
title: ADO-Objekte und-Sammlungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 89093367532177ec87fb3a5fd86e38e98345962c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926043"
---
# <a name="ado-objects-and-collections"></a>ADO-Objekte und -Collections
ADO besteht aus den folgenden neun Objekten und vier Auflistungen.  
  
|Objekt oder Sammlung|BESCHREIBUNG|  
|--------------------------|-----------------|  
|**Verbindungs** Objekt|Stellt eine eindeutige Sitzung mit einer Datenquelle dar. Im Fall eines Client/Server-Datenbanksystems ist es möglicherweise Äquivalent zu einer tatsächlichen Netzwerkverbindung mit dem Server. Abhängig von der vom Anbieter unterstützten Funktionalität sind einige Sammlungen, Methoden oder Eigenschaften eines **Verbindungs** Objekts möglicherweise nicht verfügbar.|  
|**Command** -Objekt|Wird verwendet, um einen bestimmten Befehl (z. b. eine SQL-Abfrage) zu definieren, der für eine Datenquelle ausgeführt werden soll.|  
|**Recordset** -Objekt|Stellt den gesamten Satz von Datensätzen aus einer Basistabelle oder die Ergebnisse eines ausgeführten Befehls dar. Alle **Recordset** -Objekte bestehen aus Datensätzen (Zeilen) und Feldern (Spalten).|  
|**Datensatz** -Objekt|Stellt eine einzelne Daten Zeile dar, entweder aus einem **Recordset** oder aus dem Anbieter. Dieser Datensatz kann je nach Anbieter einen Datenbankdaten Satz oder einen anderen Objekttyp, z. b. eine Datei oder ein Verzeichnis, darstellen.|  
|**Stream** -Objekt|Stellt einen Stream von Binär-oder Textdaten dar. Beispielsweise kann ein XML-Dokument für Befehlseingaben in einen Stream geladen oder von bestimmten Anbietern als Ergebnisse einer Abfrage zurückgegeben werden. Ein **Stream** -Objekt kann verwendet werden, um Felder oder Datensätze zu bearbeiten, die diese Datenströme enthalten.|  
|**Parameter** -Objekt|Stellt einen Parameter oder ein Argument dar, der einem **Befehls** Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur zugeordnet ist.|  
|**Field** -Objekt|Stellt eine Datenspalte mit einem gemeinsamen Datentyp dar. Jedes **Feld** Objekt entspricht einer Spalte im **Recordset**.|  
|**Property** -Objekt|Stellt ein Merkmal eines ADO-Objekts dar, das vom Anbieter definiert wird. ADO-Objekte verfügen über zwei Arten von Eigenschaften: integrierte und dynamische Eigenschaften. Integrierte Eigenschaften sind die Eigenschaften, die in ADO implementiert werden und für jedes neue Objekt sofort verfügbar sind. Das **Property** -Objekt ist ein Container für dynamische Eigenschaften, die vom zugrunde liegenden Anbieter definiert werden.|  
|**Error** -Objekt|Enthält Details zu Datenzugriffs Fehlern, die sich auf einen einzelnen Vorgang beziehen, der den Anbieter einbezieht.|  
|**Fields** -Auflistung|Enthält alle **Feld** Objekte eines **Recordsets** oder eines **Datensatz** -Objekts.|  
|**Properties** -Sammlung|Enthält alle **Eigenschafts** Objekte für eine bestimmte Instanz eines-Objekts.|  
|**Parameter** Sammlung|Enthält alle **Parameter** Objekte eines **Befehls** Objekts.|  
|**Fehler** Sammlung|Enthält alle Fehler Objekte, die als Reaktion auf einen einzelnen Anbieter **Fehler** erstellt wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)
