---
title: Ausführen eines Befehls | Microsoft Docs
description: Ausführen eines Befehls
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 20d2a7314db4a70fbc27221fba34e510441d9236
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665530"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Nachdem die Verbindung mit einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreateSession:: CreateSession** Methode, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Um direkt mit einzelnen Tabellen oder Indizes arbeiten fordert der Consumer die **IOpenRowset** Schnittstelle. Die **IOpenRowset:: OPENROWSET** -Methode öffnet und gibt ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle oder einem Index enthält.  
  
 Zum Ausführen eines Befehls (z. B. SELECT \* FROM Authors), fordert der Consumer die **IDBCreateCommand** Schnittstelle. Der Consumer kann führen Sie die **IDBCreateCommand:: CreateCommand** Methode, um ein Befehlsobjekt zu erstellen und eine Anforderung für die **ICommandText** Schnittstelle. Die **ICommandText:: SetCommandText** Methode wird verwendet, um den Befehl anzugeben, die ausgeführt werden soll.  
  
 Die **Execute** -Befehl wird verwendet, um den Befehl auszuführen. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
