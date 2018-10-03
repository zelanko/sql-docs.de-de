---
title: Ausführen eines Befehls | Microsoft-Dokumentation
description: Ausführen eines Befehls
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9f163f1518b5dc89b6fe7e8e670f5b840aded8b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656358"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Nachdem die Verbindung mit einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreateSession:: CreateSession** Methode, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Der Consumer fordert zum direkten Arbeiten mit einzelnen Tabellen oder Indizes die Schnittstelle **IOpenRowset** an. Die Methode **IOpenRowset::OpenRowset** öffnet und gibt ein Rowset zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Der Consumer fordert zum Ausführen eines Befehls (z.B. SELECT \* FROM Authors) die Schnittstelle **IDBCreateCommand** an. Der Consumer kann Ausführen der **IDBCreateCommand:: CreateCommand** Methode, um ein Befehlsobjekt zu erstellen, und fordern Sie für die **ICommandText** Schnittstelle. Die **ICommandText:: SetCommandText** Methode wird verwendet, um den Befehl anzugeben, die ausgeführt werden soll.  
  
 Der **Execute**-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
