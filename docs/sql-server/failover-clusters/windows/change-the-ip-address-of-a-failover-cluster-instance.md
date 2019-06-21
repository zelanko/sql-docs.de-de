---
title: Ändern der IP-Adresse einer Failoverclusterinstanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cfe93e513d9f60933b9e774979495dc29e2779e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63037346"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Ändern der IP-Adresse einer Failoverclusterinstanz
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie die IP-Adressressource in einer Always On-Failoverclusterinstanz (FCI) mithilfe des Failovercluster-Manager-Snap-Ins geändert wird. Das Failovercluster-Manager-Snap-In ist die Clusterverwaltungsanwendung für den WSFC (Windows Server Failover Clustering)-Dienst.  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Lesen Sie vor der Installation das folgende Thema in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation: [Before Installing Failover Clustering](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Warten oder Aktualisieren einer FCI müssen Sie ein lokaler Administrator sein und über die Berechtigung verfügen, sich bei allen Knoten der FCI als Dienst anzumelden.  
  
##  <a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So ändern Sie die IP-Adressressource für eine FCI**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie den Knoten **Dienste und Anwendungen** im linken Bereich, und klicken Sie auf die FCI.  
  
3.  Klicken Sie im rechten Bereich unter der Kategorie **Servername** mit der rechten Maustaste auf die SQL Server-Instanz, und wählen Sie die Option **Eigenschaften** , um das Dialogfeld **Eigenschaften** zu öffnen.  
  
4.  Ändern Sie auf der Registerkarte **Allgemein** die IP-Adressressource.  
  
5.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
6.  Klicken Sie im rechten Fensterbereich mit der rechten Maustaste auf „SQL IP Address1(Name der Failoverclusterinstanz)“, und wählen Sie **Offline schalten**aus. SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name) und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Statusänderung von Online in Ausstehende Offlineschaltung und anschließend Offline werden angezeigt.  
  
7.  Klicken Sie im rechten Fensterbereich mit der rechten Maustaste auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], und klicken Sie dann auf **Online schalten**. SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name) und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Statusänderung von Offline in Ausstehende Onlineschaltung und anschließend Online werden angezeigt.  
  
8.  Schließen Sie das Failovercluster-Manager-Snap-In.  
  
  
