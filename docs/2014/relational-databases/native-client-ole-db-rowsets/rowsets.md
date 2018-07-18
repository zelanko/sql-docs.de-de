---
title: Rowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73f16529f84fd9a7eb0158061ab4f875050a8496
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411709"
---
# <a name="rowsets"></a>Rowsets
  Ein Rowset ist ein Satz von Zeilen, die Spalten mit Daten enthalten. Rowsets sind die zentralen Objekte, die es allen OLE DB-Datenanbietern ermöglichen, Resultsetdaten in tabellarischer Form verfügbar zu machen.  
  
 Nachdem ein Consumer eine Sitzung erstellt, mit der **IDBCreateSession:: CreateSession** -Methode der Consumer können entweder die **IOpenRowset** oder **IDBCreateCommand** die Schnittstelle für die Sitzung, ein Rowset zu erstellen. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt diese beiden Schnittstellen. Diese beiden Methoden werden im Folgenden beschrieben.  
  
-   Erstellen ein Rowsets durch Aufrufen der **IOpenRowset:: OPENROWSET** Methode.  
  
     Dies entspricht dem Erstellen eines Rowsets über eine einzelne Tabelle. Die Methode öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle enthält, und gibt es zurück. Eines der Argumente zu **OpenRowset** ist eine Tabellen-ID, die in der Tabelle aus der das Rowset erstellt sind.  
  
-   Erstellen Sie ein Command-Objekt durch Aufrufen der **IDBCreateCommand:: CreateCommand** Methode.  
  
     Das Befehlsobjekt führt Befehle aus, die der Anbieter unterstützt. Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann der Consumer eine beliebige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung angeben, beispielsweise eine SELECT-Anweisung oder einen Aufruf einer gespeicherten Prozedur. Die Schritte zum Erstellen eines Rowsets mit einem Befehlsobjekt sind folgende:  
  
    1.  Ruft der Consumer die **IDBCreateCommand:: CreateCommand** Methode in der Sitzung, um einen Befehl anfordert erhalten die **ICommandText** Schnittstelle für das Command-Objekt. Dies **ICommandText** -Schnittstelle legt diese fest und ruft Sie den eigentlichen Befehlstext ab. Füllt der Consumer den Textbefehl durch Aufrufen der **ICommandText:: SetCommandText** Methode.  
  
    2.  Der Benutzer ruft die **ICommand:: Execute** -Methode für den Befehl. Das Rowsetobjekt, das erstellt wird, wenn der Befehl ausgeführt wird, enthält das Resultset aus dem Befehl.  
  
 Der Consumer kann verwenden die **ICommandProperties** Schnittstelle zum Abrufen oder Festlegen der Eigenschaften für das von den ausgeführten Befehl zurückgegebene Rowset die **ICommand:: Execute** Schnittstellen. Die am häufigsten angeforderten Eigenschaften sind die Schnittstellen, die das Rowset unterstützen muss. Zusätzlich zu Schnittstellen kann der Consumer Eigenschaften anfordern, die das Verhalten des Rowsets oder der Schnittstelle verändern.  
  
 Consumer geben Rowsets mit der **IRowset** Methode. Mit der Freigabe eines Rowsets werden alle Zeilenhandles freigegeben, die der Consumer für dieses Rowset besitzt. Accessoren werden jedoch bei der Freigabe eines Rowsets nicht freigegeben. Wenn Sie haben eine **IAccessor** -Schnittstelle, diese noch freigegeben werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen eines Rowsets mit 'IopenRowset'](creating-a-rowset-with-iopenrowset.md)  
  
-   [Erstellen von Rowsets mit 'ICommand::Execute'](creating-rowsets-with-icommand-execute.md)  
  
-   [Eigenschaften und Verhaltensweisen von Rowsets](rowset-properties-and-behaviors.md)  
  
-   [Rowsets und SQL Server-Cursor](rowsets-and-sql-server-cursors.md)  
  
-   [Abrufen von Zeilen](fetching-rows.md)  
  
-   [Abrufen einer einzelnen Zeile mit IRow](fetching-a-single-row-with-irow.md)  
  
-   [Lesezeichen](bookmarks.md)  
  
-   [Aktualisieren von Daten in Rowsets](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
