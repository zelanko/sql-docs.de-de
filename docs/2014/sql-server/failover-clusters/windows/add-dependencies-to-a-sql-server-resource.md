---
title: Hinzufügen von Abhängigkeiten zu einer Ressource von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- resource dependencies [SQL Server]
- failover clustering [SQL Server], dependencies
- clusters [SQL Server], dependencies
- dependencies [SQL Server], clustering
ms.assetid: 25dbb751-139b-4c8e-ac62-3ec23110611f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a29577d6027c43fd35a8b27db8b402123c89a4b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63035658"
---
# <a name="add-dependencies-to-a-sql-server-resource"></a>Hinzufügen von Abhängigkeiten zu einer Ressource von SQL Server
  In diesem Thema wird beschrieben, wie einer AlwaysOn-Failoverclusterinstanz-Ressource mithilfe des Failovercluster-Manager-Snap-Ins Abhängigkeiten hinzugefügt werden. Das Failovercluster-Manager-Snap-In ist die Clusterverwaltungsanwendung für den WSFC (Windows Server Failover Clustering)-Dienst.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#Restrictions), [Voraussetzungen](#Prerequisites)  
  
-   **Hinzufügen eine Abhängigkeit zu einer SQL Server-Ressource mit:** [Windows Failover Cluster-Manager](#WinClusManager)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Beachten Sie, dass, wenn Sie der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Gruppe weitere Ressourcen hinzufügen, diese Ressourcen immer über eigene eindeutige SQL-Netzwerknamen und SQL-IP-Adressen verfügen müssen.  
  
 Verwenden Sie die vorhandenen Ressourcen an SQL-Netzwerknamen und SQL-IP-Adressen nur für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressourcen gemeinsam mit anderen Ressourcen verwendet werden, können die folgenden Probleme auftreten:  
  
-   Unerwartete Ausfallzeiten können auftreten.  
  
-   Service Pack-Installationen können fehlschlagen.  
  
-   Das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setupprogramm kann nicht erfolgreich ausgeführt werden. Wenn dieses Problem auftritt, können Sie keine zusätzlichen Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installieren oder Routinewartungsmaßnahmen ausführen.  
  
 Beachten Sie diese zusätzlichen Probleme:  
  
-   FTP mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replikation: Für Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden FTP mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replikation, der FTP-Dienst muss einen der verwenden den gleichen physischen Datenträgern wie bei der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mit der FTP-Dienst eingerichtet ist.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Abhängigkeiten von Ressourcen: Wenn Sie eine Ressource hinzufügen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angehören und Sie besitzen eine Abhängigkeit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Ressource, um sicherzustellen, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar ist, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt, dass Sie eine Abhängigkeit hinzufügen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent-Ressource. Fügen Sie keine Abhängigkeit auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource hinzu. Konfigurieren Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Ressource so, dass bei einem Ausfall der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentressource die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Gruppe nicht beeinträchtigt. Auf diese Weise stellen Sie sicher, dass der Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, hochverfügbar ist.  
  
-   Dateifreigaben und Druckerressourcen: Bei der Installation Dateifreigabe- oder Drucker Clusterressourcen sie sollten nicht gesetzt werden auf derselben physischen Datenträgerressourcen als dem Computer ist mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Bei Verwendung derselben physischen Datenträgerressourcen kann es auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt wird, zu Leistungsabfällen und Dienstausfällen kommen.  
  
-   Überlegungen zu MS DTC: Nachdem Sie das Betriebssystem installieren und der FCI konfigurieren, müssen Sie konfigurieren [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) in einem Cluster zu arbeiten, mit dem Failovercluster-Manager-Snap-in. Wenn MS DTC nicht für die Ausführung in einem Cluster konfiguriert wird, führt dies nicht zu einer Blockierung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setups, aber die Funktionalität der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anwendung kann beeinträchtigt sein, falls MS DTC nicht ordnungsgemäß konfiguriert wurde.  
  
     Wenn Sie MS DTC in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Gruppe installieren und gleichzeitig andere Ressourcen von MS DTC abhängig sind, steht MS DTC nicht zur Verfügung, wenn diese Gruppe offline ist oder ein Failover eintritt. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt, MS DTC möglichst in eine eigene Gruppe mit eigener physischer Datenträgerressource einzufügen.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Wenn Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in einer WSFC-Ressourcengruppe mit mehreren Laufwerken installieren und die Daten auf einem dieser Laufwerke speichern möchten, wird festgelegt, dass die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource ausschließlich von diesem Laufwerk abhängig ist. Um Daten oder Protokolle auf einem anderen Datenträger zu speichern, müssen Sie zuerst der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource eine Abhängigkeit für den zusätzlichen Datenträger hinzufügen.  
  
##  <a name="WinClusManager"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So fügen Sie einer SQL Server-Ressource eine Abhängigkeit hinzu**  
  
-   Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
-   Suchen Sie die Gruppe, die die anwendbare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource enthält, für die Sie eine Abhängigkeit erstellen möchten.  
  
-   Wenn sich die Ressource für den Datenträger bereits in dieser Gruppe befindet, fahren Sie mit Schritt 4 fort. Andernfalls wechseln Sie zu der Gruppe, die den Datenträger enthält. Wenn diese Gruppe und die Gruppe, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthält, nicht zum selben Knoten gehören, verschieben Sie die Gruppe mit der Ressource für den Datenträger zu dem Knoten mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Gruppe.  
  
-   Wählen Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource aus, öffnen Sie das Dialogfeld **Eigenschaften** , und fügen Sie den Datenträger auf der Registerkarte **Abhängigkeiten** den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abhängigkeiten hinzu.  
  
  
