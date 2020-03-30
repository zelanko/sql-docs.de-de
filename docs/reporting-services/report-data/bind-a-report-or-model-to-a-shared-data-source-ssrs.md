---
title: Binden eines Berichts an eine freigegebene Datenquelle | Microsoft-Dokumentation
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c5aa5e504c8434d3634b903c08b6a03c0e62345c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081419"
---
# <a name="bind-a-report-to-a-shared-data-source-ssrs"></a>Binden eines Berichts an eine freigegebene Datenquelle (SSRS)
  In einigen Situationen, z.B., wenn Sie einen Bericht von einem Testserver auf einen Produktionsserver verschieben, sollten Sie die Datei auf dem lokalen Computer speichern und anschließend auf einen anderen Berichtsserver hochladen. Wenn Sie den Bericht auf den neuen Server hochladen, müssen Sie ihn erneut an eine freigegebene, auf dem neuen Berichtsserver gespeicherte Datenquelle binden. Wenn Sie den Bericht nicht erneut binden, kann er nicht ordnungsgemäß verwendet werden, wenn über den neuen Berichtsserver auf ihn zugegriffen wird.  
  
> [!IMPORTANT]  
>  Vor dem erneuten Binden eines Berichts an eine freigegebene Datenquelle müssen die Daten bereits auf dem Berichtsserver oder in der SharePoint-Bibliothek vorhanden sein. Weitere Informationen zu Datenquellen finden Sie unter [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>So binden Sie einen Bericht an eine freigegebene Datenquelle auf einem Berichtsserver im einheitlichen Modus  
  
1.  Klicken Sie im Webportal auf die Auslassungspunkte (...) in der oberen rechten Ecke der Berichtskachel und anschließend auf **Verwalten**.  

2.  Klicken Sie auf **Datenquellen**.  
  
3.  Klicken Sie auf **Eine freigegebene Datenquelle**, und navigieren Sie dann zu der Datenquelle, an die Sie den Bericht binden möchten.  
  
4.  Wählen Sie die Datenquelle aus, und klicken Sie dann auf **Speichern**.  
  
5.  Klicken Sie auf **Anwenden**.  
  
     Der Bericht ist nun an die ausgewählte Datenquelle gebunden.  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>So binden Sie einen Bericht an eine freigegebene Datenquelle auf einem Berichtsserver im integrierten SharePoint-Modus  
  
1.  Klicken Sie auf der Schnellstartleiste auf den Namen der Bibliothek, wenn sie nicht bereits geöffnet ist. Wenn der Name der Bibliothek nicht angezeigt wird, klicken Sie auf **Alle Websiteinhalte einblenden**und anschließend auf den Namen der Bibliothek.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Pfeil nach unten.  
  
3.  Klicken Sie auf **Datenquellen verwalten**.  
  
4.  Klicken Sie auf **dataSource1**.  
  
5.  Überprüfen Sie im Bereich **Verbindungstyp** , ob **Freigegebene Datenquelle** ausgewählt ist.  
  
6.  Klicken Sie im Bereich **Datenquellenlink** auf die Schaltfläche mit den Auslassungspunkten (...).  
  
7.  Suchen Sie die Datenquelle, die Sie verwenden möchten.  
  
8.  Wählen Sie die Datenquelle aus, und klicken Sie auf **OK**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hochladen von Dokumenten in eine SharePoint-Bibliothek (Reporting Services im SharePoint-Modus)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Erstellen und Verwalten von freigegebenen Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](https://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [Erstellen von Datenverbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
