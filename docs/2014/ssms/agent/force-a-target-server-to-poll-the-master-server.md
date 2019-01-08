---
title: Erzwingen des Abrufens des Masterservers durch einen Zielserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e9580839c18ed40a6163ab933ce40276bc413ab
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764212"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>Force a Target Server to Poll the Master Server
  Dieses Thema beschreibt, wie Sie erzwingen, dass ein Zielserver den Masterserver abruft. Der Zielserver muss ein registrierter Server auf dem Masterserver sein.  
  
 Ein Auftrag ist eine festgelegte Reihe von Aktionen, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführt. Ein Multiserverauftrag ist ein Auftrag, der von einem Masterserver auf mindestens einem Zielserver ausgeführt wird. Auf jedem Server kann gleichzeitig eine Instanz des gleichen Auftrags ausgeführt werden. Jeder Zielserver ruft in regelmäßigen Abständen den Masterserver ab, lädt eine Kopie aller neuen Aufträge herunter, die dem Zielserver zugewiesen wurden, und trennt dann die Verbindung. Der Zielserver führt den Auftrag lokal aus und stellt dann erneut eine Verbindung mit dem Masterserver her, um den Auftragsergebnisstatus hochzuladen.  
  
> [!NOTE]  
>  Wenn der Zielserver versucht, den Auftragsstatus durch Hochladen zu übertragen, und dabei nicht auf den Masterserver zugreifen kann, bleibt der Auftragsstatus so lange im Spooler (in der Warteschlange), bis der Masterserver wieder zur Verfügung steht.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#Restrictions), [Sicherheit](#Security)  
  
-   **Zu erzwingen, dass einen Zielserver den Masterserver abruft verwenden:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Der Zielserver muss ein registrierter Server auf dem Masterserver sein. Die Anweisungen in diesem Thema müssen auf dem Masterserver ausgeführt werden.  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) und [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
##  <a name="SSMS"></a> Verwendung von SQL Server Management Studio  
 **So erzwingen Sie, dass ein Zielserver den Masterserver abruft**  
  
1.  Erweitern Sie im **Objekt-Explorer**den Masterserver.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserververwaltung**, und klicken Sie dann auf **Zielserver verwalten**.  
  
3.  Klicken Sie auf einen Zielserver und dann auf **Abruf erzwingen**.  
  
  
