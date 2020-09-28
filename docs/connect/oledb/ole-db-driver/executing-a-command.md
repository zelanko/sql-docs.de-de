---
title: Ausführen eines Befehls (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Consumer im OLE DB-Treiber für SQL Server einen Befehl ausführt, indem er zunächst eine Sitzung erstellt, ein Rowset abruft und „Execute“ verwendet.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f24216ec62b77c56d5d2b18563f64e37fd4b7691
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861520"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Nachdem die Verbindung zu einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreatSession::CreateSession**-Methode auf, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Der Consumer fordert zum direkten Arbeiten mit einzelnen Tabellen oder Indizes die Schnittstelle **IOpenRowset** an. Die Methode **IOpenRowset::OpenRowset** öffnet und gibt ein Rowset zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Der Consumer fordert zum Ausführen eines Befehls (z.B. SELECT \* FROM Authors) die Schnittstelle **IDBCreateCommand** an. Der Consumer kann die **IDBCreateCommand::CreateCommand**-Methode ausführen, um ein Befehlsobjekt und eine Anforderung für die **ICommandText**-Schnittstelle zu erstellen. Die **ICommandText::SetCommandText**-Methode wird verwendet, um den Befehl anzugeben, der ausgeführt werden soll.  
  
 Der **Execute**-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
