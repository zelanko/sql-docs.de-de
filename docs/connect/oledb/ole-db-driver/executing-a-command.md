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
ms.openlocfilehash: f13c9177a74212b849572881f114e503a9530286
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994992"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Nachdem die Verbindung mit einer Datenquelle hergestellt wurde, ruft der Consumer die **idbkreatesession:: | atesession** -Methode auf, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Der Consumer fordert zum direkten Arbeiten mit einzelnen Tabellen oder Indizes die Schnittstelle **IOpenRowset** an. Die Methode **IOpenRowset::OpenRowset** öffnet und gibt ein Rowset zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Der Consumer fordert zum Ausführen eines Befehls (z.B. SELECT \* FROM Authors) die Schnittstelle **IDBCreateCommand** an. Der Consumer kann die **idbkreatecommand:: featecommand** -Methode ausführen, um ein Befehls Objekt zu erstellen und die **ICommandText** -Schnittstelle anzufordern. Die **ICommandText:: SetCommandText** -Methode wird verwendet, um den Befehl anzugeben, der ausgeführt werden soll.  
  
 Der **Execute**-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
