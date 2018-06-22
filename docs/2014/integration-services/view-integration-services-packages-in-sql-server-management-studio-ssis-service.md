---
title: Integration Services-Paketen in SQL Server Management Studio (SSIS-Dienst) Ansicht | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8b3f72ed86e681447e373ed682831e2ef86852e9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056502"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a>Anzeigen von Integration Services-Paketen in SQL Server Management Studio (SSIS-Dienst)
    
> [!IMPORTANT]  
>  In diesem Thema wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
 In diesem Verfahren wird beschrieben, wie eine Verbindung mit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] hergestellt und eine Liste der vom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst verwalteten Pakete angezeigt wird.  
  
### <a name="to-connect-to-integration-services"></a>So stellen Sie eine Verbindung mit Integration Services her  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server**, und klicken Sie dann auf **SQL Server Management Studio**.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** in der Liste **Servertyp** die Option **Integration Services** aus, geben Sie im Feld **Servername** einen Servernamen an, und klicken Sie dann auf **Verbinden**.  
  
    > [!IMPORTANT]  
    >  Wenn Sie keine Verbindung mit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]herstellen können, wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst wahrscheinlich nicht ausgeführt. Wenn Sie weitere Informationen zum Status des Diensts erhalten möchten, klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server**, zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**. Klicken Sie im linken Bereich auf **SQL Server-Dienste**. Suchen Sie im rechten Bereich den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst. Starten Sie den Dienst, wenn er nicht bereits ausgeführt wird.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird geöffnet. Standardmäßig ist das Fenster des Objekt-Explorers geöffnet und in der unteren linken Ecke des Studios positioniert. Ist der Objekt-Explorer nicht geöffnet, klicken Sie im Menü **Ansicht** auf **Objekt-Explorer** .  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a>So zeigen Sie die vom Integration Services-Dienst verwalteten Pakete an  
  
1.  Erweitern Sie im Objekt-Explorer den Ordner Gespeicherte Pakete.  
  
2.  Erweitern Sie die Unterordner Gespeicherte Pakete, um die Pakete anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Paketverwaltung &#40;SSIS-Dienst&#41;](service/package-management-ssis-service.md)   
 [Verwenden von SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  