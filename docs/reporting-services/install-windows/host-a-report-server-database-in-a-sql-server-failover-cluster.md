---
title: Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster | Microsoft-Dokumentation
ms.date: 03/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8fbd30c139c683eac89761d37686b1f0209e35c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47664798"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Hosten einer Berichtsserver-Datenbank in einem SQL Server-Failovercluster
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Failoverclustering, sodass Sie mehrere Datenträger für eine oder mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen verwenden können. Failovercluster werden nur für die Berichtsserver-Datenbank unterstützt; Sie können den Berichtsserver-Dienst nicht als Teil eines Failoverclusters ausführen.  
  
 Damit eine Berichtsserver-Datenbank in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster gehostet werden kann, muss der Cluster bereits installiert und konfiguriert sein. Daraufhin können Sie den Failovercluster als Servernamen auswählen, wenn Sie die Berichtsserver-Datenbank auf der Seite Setup der Datenbank des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstools erstellen.  
  
 Obwohl der Berichtsserver-Dienst nicht Bestandteil eines Failoverclusters sein kann, können Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf einem Computer installieren, auf dem ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster installiert ist. Der Berichtsserver wird unabhängig vom Failovercluster ausgeführt. Wenn Sie einen Berichtsserver auf einem Computer installieren, der Bestandteil einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverinstanz ist, müssen Sie den Failovercluster nicht für die Berichtsserver-Datenbank verwenden. Sie können eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zum Hosten der Datenbank verwenden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  
