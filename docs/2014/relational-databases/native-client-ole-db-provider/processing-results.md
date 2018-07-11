---
title: Verarbeiten von Ergebnissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 987257e2e3afaa574a26481d9982c41ac3d304f5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427819"
---
# <a name="processing-results"></a>Ergebnisverarbeitung
  Wenn ein Rowsetobjekt durch die Ausführung eines Befehls oder vom Anbieter direkt erzeugt wird, muss der Consumer die Daten im Rowset abrufen und darauf zugreifen können.  
  
 Rowsets sind die zentralen Objekte, die es dem OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ermöglichen, Daten in tabellarischer Form verfügbar zu machen. Grundsätzlich ist ein Rowset ein Satz von Zeilen, in dem jede Zeile Spaltendaten aufweist. Ein Rowsetobjekt macht Schnittstellen verfügbar, z. B. **IRowset** (enthält Methoden zum sequenziellen Abrufen von Zeilen aus dem Rowset), **IAccessor** (ermöglicht die Definition einer Gruppe von spaltenbindungen beschreiben die wie Tabellendaten ist an Programmvariablen des Consumers gebunden), **IColumnsInfo** (bietet Informationen zu den Spalten im Rowset), und **IRowsetInfo** (bietet Informationen zu Rowsets).  
  
 Ein Consumer aufrufen kann die **IRowset:: GetData** Methode, um eine Zeile mit Daten in einen Puffer aus dem Rowset abrufen. Vor dem **GetData** wird aufgerufen, beschreibt der Consumer den Puffer mit einem Satz von DBBINDING-Strukturen. Jede Bindung beschreibt, wie eine Spalte des Rowsets in einem Puffer des Consumer gespeichert werden soll, und enthält folgende Angaben:  
  
-   Ordnungszahl der Spalte (oder des Parameters), auf den sich die Bindung bezieht  
  
-   Informationen darüber, was gebunden wird (z. B. Datenwert, Länge der Daten und Bindungsstatus)  
  
-   Informationen zur Größe des Offsets im Puffer zu jedem dieser Teile  
  
-   Länge und den Typ der Datenwerte, die im Puffer des Consumers vorhanden sind  
  
 Beim Abruf der Daten bestimmt der Anbieter anhand der Informationen in jeder Bindung, wo und wie die Daten aus dem Puffer des Consumers abzurufen sind. Beim Einfügen der Daten in den Puffer des Consumers bestimmt der Anbieter anhand der Informationen in jeder Bindung, wo und wie die Daten in diesen Puffer einzufügen sind.  
  
 Nachdem die DBBINDING-Strukturen angegeben wurden, wird ein Accessor erstellt (**IAccessor:: CreateAccessor**). Ein Accessor ist eine Sammlung von Bindungen. Er dient zum Abrufen oder Einfügen von Daten in den Puffer des Consumers.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Vorgehensweisen für OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
