---
title: Erstellen eines mobilen Berichts in Reporting Services | Microsoft-Dokumentation
description: Erstellen Sie mit dem Publisher für mobile Berichte mobile SQL Server Reporting Services-Berichte mit flexiblen Elementen für mobile Berichte für alle Bildschirmgrößen.
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: e84dc855-aede-4fb4-b721-e6d8787961f4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 08076ebf437841f5d60d957df934fc7de6406ded
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79448217"
---
# <a name="create-a-reporting-services-mobile-report"></a>Erstellen eines mobilen Berichts in Reporting Services
Mit dem Publisher für mobile Berichte von SQL Server können Sie schnell mobile Berichte für SQL Server Reporting Services erstellen, die sich problemlos an jede Bildschirmgröße anpassen. Das Tool bietet eine Entwurfsoberfläche mit anpassbaren Rasterzeilen und -spalten sowie flexible Elemente für mobile Berichte.  
  
Wenn Sie zum ersten Mal einen mobilen Bericht erstellen, können Sie den Publisher für mobile Berichte von SQL Server über das Reporting Services-Webportal auf Ihrem lokalen Computer installieren. Die Installation kann auch über das [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=733527)erfolgen. Danach können Sie das Tool entweder aus dem Webportal oder lokal starten.   
    
1. Klicken Sie auf der oberen Leiste des Reporting Services-Webportals auf **Neu** > **Mobiler Bericht**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. Wählen Sie in der Registerkarte **Layout** im Publisher für mobile Berichte einen Navigator, ein Messgerät, ein Diagramm, eine Zuordnung oder ein Datenraster aus, und ziehen Sie es in den Entwurfsbereich.  
  
3. Klicken Sie auf die untere rechte Ecke des Elements und halten Sie sie gedrückt, um die Größe wie gewünscht anzupassen.  
  
   ![SSMRP_ResizeChart](../../reporting-services/mobile-reports/media/ssmrp-resizechart.png)  
  
   Dies ist der **Master** -Entwurfsbereich, in dem Sie die Elemente für Ihren Bericht erstellen können. Später können Sie das [Layout für ein Tablet oder Telefon optimieren](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md).     
     
   Beachten Sie in **Visuelle Eigenschaften** unterhalb des Entwurfsbereichs die verschiedenen Eigenschaften, die Sie festlegen können.  
     
4. Wählen Sie die Registerkarte **Daten** in der linken oberen Ecke aus. Dort werden Sie sehen, dass das Diagramm die ihm zugeordneten Daten bereits simuliert hat.   
  
   ![SSMRP_SimTable](../../reporting-services/mobile-reports/media/ssmrp-simtable.png)  
  
5. Wählen Sie **Daten hinzufügen** in der oberen rechten Ecke aus.  
  
6. Wählen Sie **Lokales Excel** oder **Berichtsserver**aus.  
  
   >**Tipps**: Wenn Sie Daten aus Excel hinzufügen, stellen Sie Folgendes sicher:  
    >* Sie [die Excel-Daten vorbereiten](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md) , damit diese in Ihrem mobilen Bericht funktionieren.  
    >* Sie die Datei zuerst schließen.  
7. Wählen Sie die gewünschten Arbeitsblätter und anschließend **Importieren**aus.   
   Sie können mehr als ein Arbeitsblatt aus einer Arbeitsmappe gleichzeitig hinzufügen.  
    
     ![SSMRP_AddExcelData](../../reporting-services/mobile-reports/media/ssmrp-addexceldata.png)  
  
8. Wählen Sie auf der Registerkarte **Daten** in dem Kästchen **Dateneigenschaften** die Tabelle und das Feld aus, die für das Diagramm verwendet werden sollen.  
  
   ![SSMRP_DataProps](../../reporting-services/mobile-reports/media/ssmrp-dataprops.png)  
  
9. Im Kästchen **Visuelle Eigenschaften** in der Registerkarte **Layout** können Sie Eigenschaften wie **Titel**, **Zeiteinheit**und **Zahlenformat**festlegen.  
  
   ![SSMRP_ChartVizProps](../../reporting-services/mobile-reports/media/ssmrp-chartvizprops.png)  
    
10. Wählen Sie **Vorschau** in der oberen linken Ecke aus, um anzuzeigen, wie sich Ihr Bericht entwickelt.  
  
11. Nun sollten Sie Ihren Bericht speichern. Wählen Sie oben links das Symbol aus, und klicken Sie anschließend auf **Lokal speichern** oder **Auf Server speichern**.  
  
   Sie benötigen Zugriff auf einen SQL Server Reporting Services-Berichtsserver, um den Bericht auf einem Server zu speichern.  
     
   ### <a name="see-also"></a>Weitere Informationen  
     
-   [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-   [Gestalten eines mobilen Reporting Services-Berichts für Telefone oder Tablets](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)  
  
   
