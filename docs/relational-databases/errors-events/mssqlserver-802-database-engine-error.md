---
title: Datenbank-Engine-Fehler MSSQLSERVER_802 | Microsoft Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f880cd41cdde662913099e06ef93eacc17d94265
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68007034"
---
# <a name="mssqlserver802---database-engine-error"></a>Datenbank-Engine-Fehler MSSQLSERVER_802
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|802|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NO_BUFS|  
|Meldungstext|Nicht genügend Arbeitsspeicher im Pufferpool.|  
  
## <a name="explanation"></a>Erklärung  
Diese Meldung wird verursacht, wenn der Pufferpool voll ist und nicht weiter vergrößert werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
In der folgenden Liste werden allgemeine Schritte erläutert, die bei der Problembehandlung von Arbeitsspeicherfehlern helfen:  
  
1.  Überprüfen Sie, ob andere Anwendungen oder Dienste Arbeitsspeicher auf dem Server beanspruchen. Rekonfigurieren Sie weniger kritische Anwendungen oder Dienste, damit sie weniger Speicher beanspruchen.  
  
2.  Beginnen Sie die Sammlung der Leistungsindikatoren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Puffer-Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Speicher-Manager**.  
  
3.  Überprüfen Sie die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherkonfigurationsparameter:  
  
    -   **Max. Serverarbeitsspeicher**  
  
    -   **Min. Serverarbeitsspeicher**  
  
    -   **Min. Arbeitsspeicher pro Abfrage**  
  
    Beachten Sie alle ungewöhnlichen Einstellungen, und korrigieren Sie sie bei Bedarf. Konto für erhöhte Arbeitsspeicheranforderungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Standardeinstellungen werden unter "Festlegen von Serverkonfigurationsoptionen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation aufgeführt.  
  
4.  Verfolgen Sie die Ausgabe von DBCC MEMORYSTATUS und deren Veränderungen beim Anzeigen der Fehlermeldungen.  
  
5.  Überprüfen Sie die Arbeitsauslastung (Anzahl der gleichzeitigen Sitzungen, aktuell ausgeführte Abfragen).  
  
Durch die folgenden Aktionen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mehr Arbeitsspeicher zur Verfügung gestellt werden:  
  
-   Wenn Anwendungen neben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sehr ressourcenaufwändig sind, versuchen Sie, diese Anwendungen zu beenden oder auf einem getrennten Server auszuführen.  
  
-   Wenn Sie **Max. Serverarbeitsspeicher** konfiguriert haben, erhöhen Sie die Einstellung.  
  
Führen Sie die folgenden DBCC-Befehle aus, um mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speichercaches freizugeben.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Wenn das Problem weiterhin besteht, müssen Sie weitere Untersuchungen ausführen und möglicherweise die Arbeitsauslastung reduzieren.  
  
