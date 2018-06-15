---
title: Rowsets | Microsoft Docs
description: Rowsets in OLE DB-Treiber für SQLServer
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5e03aa5a887f25e9909ff2c755cfbfa598166475
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306699"
---
# <a name="rowsets"></a>Rowsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein Rowset ist ein Satz von Zeilen, die Spalten mit Daten enthalten. Rowsets sind die zentralen Objekte, die es allen OLE DB-Datenanbietern ermöglichen, Resultsetdaten in tabellarischer Form verfügbar zu machen.  
  
 Nachdem ein Consumer eine Sitzung erstellt, mit der **IDBCreateSession:: CreateSession** -Methode der Consumer können entweder die **IOpenRowset** oder **IDBCreateCommand** die Schnittstelle für die Sitzung, die ein Rowset zu erstellen. Der OLE DB-Treiber für SQL Server unterstützt beide Schnittstellen. Diese beiden Methoden werden im Folgenden beschrieben.  
  
-   Erstellen ein Rowsets durch Aufrufen der **IOpenRowset:: OPENROWSET** Methode.  
  
     Dies entspricht dem Erstellen eines Rowsets über eine einzelne Tabelle. Die Methode öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle enthält, und gibt es zurück. Eines der Argumente zu **OpenRowset** eine Tabellen-ID, die die Tabelle, aus der das Rowset erstellt identifiziert wird.  
  
-   Erstellt ein Command-Objekt durch Aufrufen der **IDBCreateCommand:: CreateCommand** Methode.  
  
     Das Befehlsobjekt führt Befehle aus, die der Anbieter unterstützt. Mit dem OLE DB-Treiber für SQL Server kann der Consumer geben alle [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung wie SELECT-Anweisung oder einen Aufruf einer gespeicherten Prozedur. Die Schritte zum Erstellen eines Rowsets mit einem Befehlsobjekt sind folgende:  
  
    1.  Der Consumer Ruft die **IDBCreateCommand:: CreateCommand** Methode für die Sitzung auf einen Befehl anfordert Abrufen der **ICommandText** Schnittstelle für das Command-Objekt. Dies **ICommandText** -Schnittstelle legt diese fest und ruft den eigentlichen Befehlstext ab. Füllt der Consumer den Textbefehl ein durch Aufrufen der **ICommandText:: SetCommandText** Methode.  
  
    2.  Der Benutzer ruft den **ICommand:: Execute** -Methode für den Befehl. Das Rowsetobjekt, das erstellt wird, wenn der Befehl ausgeführt wird, enthält das Resultset aus dem Befehl.  
  
 Der Consumer können die **ICommandProperties** Schnittstelle zum Abrufen oder Festlegen der Eigenschaften für das durch den vom ausgeführten Befehl zurückgegebene Rowset die **ICommand:: Execute** Schnittstellen. Die am häufigsten angeforderten Eigenschaften sind die Schnittstellen, die das Rowset unterstützen muss. Zusätzlich zu Schnittstellen kann der Consumer Eigenschaften anfordern, die das Verhalten des Rowsets oder der Schnittstelle verändern.  
  
 Consumer geben Rowsets mit der **IRowset** Methode. Mit der Freigabe eines Rowsets werden alle Zeilenhandles freigegeben, die der Consumer für dieses Rowset besitzt. Accessoren werden jedoch bei der Freigabe eines Rowsets nicht freigegeben. Wenn Sie haben eine **IAccessor** -Schnittstelle, diese noch freigegeben werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen eines Rowsets mit 'IopenRowset'](../../oledb/ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Erstellen von Rowsets mit 'ICommand::Execute'](../../oledb/ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Eigenschaften und Verhaltensweisen von Rowsets](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Rowsets und SQL Server-Cursor](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Abrufen von Zeilen](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
-   [Abrufen einer einzelnen Zeile mit IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Lesezeichen](../../oledb/ole-db-rowsets/bookmarks.md)  
  
-   [Aktualisieren von Daten in Rowsets](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
