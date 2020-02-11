---
title: Einrichten des Auftragsverlaufsprotokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 613c0ccae7be912bd3bec63905b838b7f07b59b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63033577"
---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Auftragsverlaufs Protokoll des-Agents einrichten.  
  
-   Vorbereitungen **:**[Sicherheit](#Security)    
  
-   **Einrichten des Auftragsverlaufs Protokolls mit:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
 **So richten Sie das Auftragsverlaufs Protokoll ein**  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Eigenschaften des SQL Server-Agents** die Seite **Verlauf** aus.  
  
4.  Sie können zwischen folgenden Optionen wählen:  
  
    1.  Aktivieren Sie die Option **Größe des Auftragsverlaufsprotokolls beschränken**, und geben Sie dann die maximale Anzahl von Zeilen für das Auftragsverlaufsprotokoll sowie die maximale Anzahl von Zeilen je Auftrag ein.  
  
    2.  Aktivieren Sie die Option **Agentverlauf automatisch entfernen**, und geben Sie den Zeitraum an, nach dem ältere Verlaufsdaten aus dem Protokoll gelöscht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Aufträgen](implement-jobs.md)   
 [Überwachen der Auftrags Aktivität](monitor-job-activity.md)   
 [Erstellen von Aufträgen](create-jobs.md)  
  
  
