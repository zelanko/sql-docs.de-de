---
title: Wählen Sie die Datenquelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
caps.latest.revision: 31
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8cb8cb384b83c4d5ca8ba16e017cbf79d53f3742
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161269"
---
# <a name="select-the-data-source"></a>Auswählen der Datenquelle
  Auf dieser Seite des Berichts-Assistenten können Sie eine Datenquelle für den Bericht definieren.  
  
## <a name="options"></a>Tastatur  
 **Freigegebene Datenquelle**  
 Wählen Sie **Freigegebene Datenquelle** aus, um eine vordefinierte Datenquelle zu verwenden, die bereits über die zu verwendenden Datenquellen-Verbindungsinformationen verfügt. Die Liste enthält alle freigegebenen Datenquellen, die in dem Projekt enthalten sind.  
  
 **Neue Datenquelle**  
 Wählen Sie **Neue Datenquelle** aus, um eine neue Datenquelle zu definieren. Die Datenquelleninformationen werden nur mit dem aktuellen Bericht verwendet.  
  
 **Name**  
 Geben Sie einen Namen für die Verbindung mit der Datenquelle ein. Der Datenquellenname muss innerhalb des Berichts eindeutig sein.  
  
 **Typ**  
 Wählen Sie den Typ der verwendeten Datenquelle aus (bei einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank z.B. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge für die Datenquelle ein. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Klicken Sie auf **Bearbeiten** , um den Datenquellenserver im Dialogfeld **Verbindungseigenschaften** anzugeben. Sie können eine lokale oder Remotedatenquelle angeben.  
  
 Klicken Sie auf **Anmeldeinformationen** , um Datenbankanmeldeinformationen anzugeben. Die Anmeldeinformationen müssen für Sie ausreichend sein, um zu Berichtsentwurfszwecken eine Verbindung mit der Datenquelle herzustellen. Wenn der Bericht auf einem Berichtsserver bereitgestellt wird, müssen die Datenbankanmeldeinformationen alle Benutzer des Berichts enthalten. Wenn Sie z.B. möchten, dass alle Berichtsbenutzer mithilfe ihrer Anmeldeinformationen eine Verbindung mit der Datenquelle herstellen, wählen Sie **Windows-Authentifizierung verwenden (integrierte Sicherheit)** aus. Die von Ihnen angegebenen Anmeldeinformationen müssen für die Datenquelle gültig sein. Wenn Sie also die Windows-Authentifizierung wählen, müssen Sie sicherstellen, dass die Datenquelle die Verbindungen von allen Benutzerkonten annimmt, die den Bericht ausführen. Die Datenbankanmeldeinformationen können getrennt vom Bericht verwaltet werden. Weitere Informationen finden Sie unter [Verwalten von Berichtsdatenquellen](report-data/manage-report-data-sources.md).  
  
 **Eine freigegebene Datenquelle**  
 Wählen Sie diese Option aus, um die Datenquelle im Projekt als freigegebene Datenquelle, statt im Bericht zu speichern. Auf diese Weise können Sie sie als Datenquelle für andere Berichte im Projekt nutzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services-Berichtsserver](../../2014/reporting-services/reporting-services-report-server.md)   
 [RSReportDesigner-Konfigurationsdatei](report-server/rsreportdesigner-configuration-file.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Hilfe des Berichts-Assistenten](../../2014/reporting-services/report-wizard-help.md)  
  
  