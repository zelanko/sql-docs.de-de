---
title: Ausführen eines Befehls | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d9c0f935bf4d3cd903346281080a8b08384c1e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148592"
---
# <a name="executing-a-command"></a>Ausführen eines Befehls
  Nachdem die Verbindung mit einer Datenquelle hergestellt wurde, ruft der Consumer die **IDBCreateSession:: CreateSession** Methode, um eine Sitzung zu erstellen. Die Sitzung fungiert als Befehl, Rowset oder Transaktionsfactory.  
  
 Um mit einzelnen Tabellen oder Indizes direkt zu arbeiten, fordert der Consumer die `IOpenRowset`-Schnittstelle an. Die `IOpenRowset::OpenRowset`-Methode öffnet ein Rowset und gibt es zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.  
  
 Zum Ausführen eines Befehls (z. B. SELECT \* FROM Authors), fordert der Consumer die `IDBCreateCommand` Schnittstelle. Der Consumer kann die `IDBCreateCommand::CreateCommand`-Methode ausführen, um ein Befehlsobjekt und eine Anforderung für die `ICommandText`-Schnittstelle zu erstellen. Die `ICommandText::SetCommandText`-Methode wird verwendet, um den Befehl anzugeben, der ausgeführt werden soll.  
  
 Der `Execute`-Befehl wird zum Ausführen des Befehls verwendet. Bei dem Befehl kann es sich um jede SQL-Anweisung oder jeden Prozedurnamen handeln. Nicht alle Befehle erzeugen ein Resultsetobjekt (Rowset). Befehle, wie z. B. SELECT * FROM Authors, erzeugen ein Resultset.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  