---
title: Überprüfen des Datenträger-E/A-Subsystems auf E/A-Verzögerungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9a3f180426faf307c7397f687eb64ec380a78aac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952335"
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
   
  
 [Microsoft Knowledge Base-Artikel 897284](http://go.microsoft.com/fwlink/?linkid=117743)  
  
 [SQL Server I/O Basics, Chapter 2 (in Englisch)](http://go.microsoft.com/fwlink/?LinkId=69370)  
  
  
