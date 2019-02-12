---
title: Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2f5d07383c2a312747cff94508ab2397f402793c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56043151"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Failoverclustering, sodass Sie mehrere Datenträger für eine oder mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen verwenden können. Failovercluster werden nur für die Berichtsserver-Datenbank unterstützt; Sie können den Berichtsserver-Dienst nicht als Teil eines Failoverclusters ausführen.  
  
 Damit eine Berichtsserver-Datenbank in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster gehostet werden kann, muss der Cluster bereits installiert und konfiguriert sein. Daraufhin können Sie den Failovercluster als Servernamen auswählen, wenn Sie die Berichtsserver-Datenbank auf der Seite Setup der Datenbank des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstools erstellen.  
  
 Obwohl der Berichtsserver-Dienst nicht Bestandteil eines Failoverclusters sein kann, können Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem Computer installieren, auf dem ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster installiert ist. Der Berichtsserver wird unabhängig vom Failovercluster ausgeführt. Wenn Sie einen Berichtsserver auf einem Computer installieren, der Bestandteil einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverinstanz ist, müssen Sie den Failovercluster nicht für die Berichtsserver-Datenbank verwenden. Sie können eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zum Hosten der Datenbank verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../report-server/report-server-database-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
