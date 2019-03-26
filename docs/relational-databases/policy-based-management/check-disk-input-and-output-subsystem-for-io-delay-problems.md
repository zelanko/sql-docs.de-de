---
title: Überprüfen des Datenträger-E/A-Subsystems auf E/A-Verzögerungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 572b7862984fda40d3ef1fff75e25ba1c865feb8
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306028"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a>Überprüfen des Datenträger-E/A-Subsystems auf E/A-Verzögerungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft das Ereignisprotokoll auf die Fehlermeldung 833. Mit dieser Meldung wird angegeben, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Lese- oder Schreibanforderung vom Datenträger ausgegeben wurde und dass die Rückgabe der Anforderung länger als 15 Sekunden gedauert hat. Dieser Fehler wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gemeldet und deutet auf ein Problem mit dem E/A-Subsystem des Datenträgers hin. Verzögerungen dieses Ausmaßes können die Leistung Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebung erheblich beinträchtigen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Sie können diesen Fehler durch Überprüfung des Systemereignisprotokolls auf hardwarebedingte Fehlermeldungen beheben. Sie können zudem hardwarespezifische Protokolle überprüfen, sofern diese verfügbar sind.  
  
 Prüfen Sie mit dem Systemmonitor die folgenden Leistungsindikatoren:  
  
-   Mittlere Sek./Übertragung  
  
-   Durchschnittliche Warteschlangenlänge des Datenträgers  
  
-   Aktuelle Warteschlangenlänge  
  
 Beispielsweise beträgt die Zeit Mittlere Sek./Übertragung für einen Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] normalerweise unter 15 Millisekunden. Wenn sich der Wert Mittlere Sek./Übertragung erhöht, ist dies ein Hinweis darauf, dass das E/A-Subsystem des Datenträgers den E/A-Bedarf nicht optimal erfüllt.  
  
## <a name="for-more-information"></a>Weitere Informationen  
   
  
 [Microsoft Knowledge Base-Artikel 897284](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 [SQL Server I/O Basics, Chapter 2 (in Englisch)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))