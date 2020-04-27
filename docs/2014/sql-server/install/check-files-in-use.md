---
title: Dateien in Verwendung überprüfen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34b51b26454766498ee601baae3ccc52cd1c5768
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096528"
---
# <a name="check-files-in-use"></a>Verwendete Dateien überprüfen
  Verwenden Sie zum Vermeiden eines Neustarts von Windows nach dem Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Updates die Seite Verwendete Dateien überprüfen zum Identifizieren von Vorgängen, die vom Setupprogramm für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Update benötigte Dateien blockieren.  
  
 Beenden Sie alle Anwendungen und Dienste, die Verbindungen mit den aktualisierten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen. Dies schließt das Beenden von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ein.  
  
 Wenn vom Setup erkannt wird, dass Dateien während der Installation blockiert sind, müssen Sie den Computer möglicherweise nach dem Fertigstellen der Installation erneut starten. Gegebenenfalls werden Sie aufgefordert, den Computer neu zu starten. Wenn das Setupprogramm einen Dienst während der Installation beenden muss, wird der Dienst nach Abschluss der Installation neu gestartet.  
  
 Damit der Computer nach der Installation nicht neu gestartet werden muss, zeigt das Setup eine Liste der Prozesse an, die Dateien sperren. Beenden Sie die in der Liste aufgeführten Prozesse und Anwendungen. Klicken Sie dann auf **Überprüfung aktualisieren** , um die Überprüfung erneut auszuführen. Klicken Sie zum Beenden einer gerade ausgeführten Überprüfung auf **Überprüfung beenden** . Wenn keine blockierten Dateien gefunden wurden, ist die Tabelle leer. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen, wenn alle blockierten Vorgänge beendet wurden.  
  
 Die Informationen werden vom Setup in den Protokolldateien protokolliert. Weitere Informationen zum Anzeigen der Protokolldateien finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) und [Vorgehensweise: Lesen einer Setupprotokolldatei von SQL Server](https://go.microsoft.com/fwlink/?LinkID=134490).  
  
 Die Protokolldatei enthält die folgenden Informationen:  
  
-   Name des Prozesses  
  
-   Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktion  
  
-   Prozesstyp  
  
-   Konto, unter dem der Prozess ausgeführt wird  
  
-   Prozess-ID  
  
-   Name der gesperrten Datei  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Prozess|Zeigt den vollständigen Namen des Prozesses an, von dem die zu aktualisierenden Dateien verwendet werden.|  
|type|Zeigt den Typ des Prozesses an.|  
|Konto|Zeigt das Konto an, unter dem der Prozess ausgeführt wird.|  
|Prozess-ID|Zeigt die Prozess-ID an.|  
  
  
