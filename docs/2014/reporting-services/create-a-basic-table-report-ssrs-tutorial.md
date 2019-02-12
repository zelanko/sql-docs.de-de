---
title: Erstellen eines einfachen Tabellenberichts (SSRS-Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1f8dcab2a07aca7971ea8c799660b075fe0bcfd2
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022973"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>Erstellen eines einfachen Tabellenberichts (SSRS-Lernprogramm)
  In diesem Tutorial wurde entwickelt, unterstützt Sie beim Erstellen eines einfachen Tabellenberichts basierend auf den [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank mithilfe von Berichts-Designer. Sie können die Berichte auch mithilfe des Berichts-Generators oder des Berichts-Assistenten erstellen. In diesem Lernprogramm erstellen Sie ein Berichtsprojekt, richten Verbindungsinformationen ein, definieren eine Abfrage, fügen einen Tabellendatenbereich hinzu und zeigen den Bericht in der Vorschau an.  
  
> [!NOTE]  
>  Zum Durcharbeiten dieses Lernprogramms müssen Sie [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus ausführen. Wenn Sie [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus verwenden, können die Schritte nicht ausgeführt werden, in denen Berichtsserver-URLs enthalten sind. Weitere Informationen zu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Modi finden Sie unter [Reporting Services-Berichtsserver](reporting-services-report-server.md).  
  
## <a name="requirements"></a>Anforderungen  
 Auf Ihrem System müssen zum Verwenden dieses Lernprogramms folgende Anwendungen installiert sein:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Datenbankmodul.  
  
-   Die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank.  Weitere Informationen finden Sie unter [Adventure Works für SQL Server 2012 (Adventure Works für SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471).. Weitere Informationen zur Unterstützung für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Beispieldatenbanken und Beispielcode für [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], finden Sie unter [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) auf der CodePlex-Website.  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]. installiert haben.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 Sie müssen auch über Leseberechtigung verfügen, um Daten aus der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank abrufen zu können.  
  
## <a name="tasks"></a>Richtlinienübersicht  
 [Lektion 1: Erstellen eines Berichtsserverprojekts &#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [Lektion 2: Angeben von Verbindungsinformationen &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [Lektion 3: Definieren eines Datasets für den Tabellenbericht &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [Lektion 4: Hinzufügen einer Tabelle zum Bericht &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [Lektion 5: Formatieren eines Berichts &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)  
  
 [Lektion 6: Hinzufügen von Gruppierungen und Gesamtwerten &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  Anzeige der Lernprogramme empfehlen wir, hinzuzufügen, **Weiter** und **zurück** in der Symbolleiste der Dokumentanzeige die Schaltflächen. Weitere Informationen finden Sie weiter oben unter  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Tutorials &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  
