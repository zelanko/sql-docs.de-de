---
title: Ändern der Größe des Auftragsverlaufsprotokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1a8c9ab517d1f6a122144604d6b147e6f5eeaf6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62650887"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
  In diesem Thema wird beschrieben, wie Sie Größen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Beschränkungen für-Agent- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Auftragsverlaufs Protokolle in mithilfe [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]von festlegen.  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So legen Sie Größenbeschränkungen für Auftragsverlaufs Protokolle fest mit:**  
  
     [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>So ändern Sie die Größe des Auftragsverlaufsprotokolls basierend auf der Basisgröße  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Verlauf** aus und bestätigen Sie dann, dass **Größe des Auftragsverlaufsprotokolls beschränken**aktiviert ist.  
  
4.  Geben Sie im Feld **Maximale Länge des Auftragsverlaufsprotokolls** die Anzahl von Zeilen ein, die maximal für das Auftragsverlaufsprotokoll zulässig sind.  
  
5.  Geben Sie im Feld **Maximale Zeilenanzahl pro Auftrag in Auftragsverlauf** die Anzahl von Zeilen ein, die maximal für das Auftragsverlaufsprotokoll eines Auftrags zulässig sind.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>So ändern Sie die Größe des Auftragsverlaufsprotokolls basierend auf der Zeit  
  
1.  Stellen Sie in **Objekt-Explorer**eine Verbindung mit einer Instanz [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]von her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Verlauf** aus, und klicken Sie dann auf **Agentverlauf automatisch entfernen**.  
  
4.  Wählen Sie die entsprechende Anzahl für **Tag(e)**, **Woche(n)** oder **Monat(e)** aus.  
  
  
