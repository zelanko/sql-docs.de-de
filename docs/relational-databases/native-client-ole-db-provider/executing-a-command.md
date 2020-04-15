---
title: Ausführen eines Befehls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 88353fa31be9265af5de0e8350aeac5481722351
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290196"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Nachdem die Verbindung zu einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreatSession::CreateSession**-Methode auf, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Der Consumer fordert zum direkten Arbeiten mit einzelnen Tabellen oder Indizes die Schnittstelle **IOpenRowset** an. Die Methode **IOpenRowset::OpenRowset** öffnet und gibt ein Rowset zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Der Consumer fordert zum Ausführen eines Befehls (z.B. SELECT \* FROM Authors) die Schnittstelle **IDBCreateCommand** an. Der Consumer kann die **IDBCreateCommand::CreateCommand**-Methode ausführen, um ein Befehlsobjekt und eine Anforderung für die **ICommandText**-Schnittstelle zu erstellen. Die **ICommandText::SetCommandText**-Methode wird verwendet, um den Befehl anzugeben, der ausgeführt werden soll.  
  
 Der **Execute**-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
