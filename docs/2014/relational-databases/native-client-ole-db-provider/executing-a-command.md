---
title: Ausführen eines Befehls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f94cc014a04c3392fefb61f4fa291a8f5a44ad8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228690"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
  Nachdem die Verbindung mit einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreateSession:: CreateSession** Methode, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Um mit einzelnen Tabellen oder Indizes direkt zu arbeiten, fordert der Consumer die `IOpenRowset`-Schnittstelle an. Die `IOpenRowset::OpenRowset`-Methode öffnet ein Rowset und gibt es zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Zum Ausführen eines Befehls (z. B. SELECT \* FROM Authors), fordert der Consumer die `IDBCreateCommand` Schnittstelle. Der Consumer kann die `IDBCreateCommand::CreateCommand`-Methode ausführen, um ein Befehlsobjekt und eine Anforderung für die `ICommandText`-Schnittstelle zu erstellen. Die `ICommandText::SetCommandText`-Methode wird verwendet, um den Befehl anzugeben, der ausgeführt werden soll.  
  
 Der `Execute`-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
