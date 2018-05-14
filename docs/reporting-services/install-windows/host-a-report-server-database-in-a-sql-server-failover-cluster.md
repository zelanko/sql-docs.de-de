---
title: Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: install-windows
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f89e7e03b56678a97176db31369d6a4aa7ec3afa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Failoverclustering, sodass Sie mehrere Datenträger für eine oder mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen verwenden können. Failovercluster werden nur für die Berichtsserver-Datenbank unterstützt; Sie können den Berichtsserver-Dienst nicht als Teil eines Failoverclusters ausführen.  
  
 Damit eine Berichtsserver-Datenbank in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster gehostet werden kann, muss der Cluster bereits installiert und konfiguriert sein. Daraufhin können Sie den Failovercluster als Servernamen auswählen, wenn Sie die Berichtsserver-Datenbank auf der Seite Setup der Datenbank des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstools erstellen.  
  
 Obwohl der Berichtsserver-Dienst nicht Bestandteil eines Failoverclusters sein kann, können Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem Computer installieren, auf dem ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster installiert ist. Der Berichtsserver wird unabhängig vom Failovercluster ausgeführt. Wenn Sie einen Berichtsserver auf einem Computer installieren, der Bestandteil einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverinstanz ist, müssen Sie den Failovercluster nicht für die Berichtsserver-Datenbank verwenden. Sie können eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zum Hosten der Datenbank verwenden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  
