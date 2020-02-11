---
title: Start Berichts-Generator (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6fc123be862320cd35ccf4aec76d8bc9cf7877af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107600"
---
# <a name="start-report-builder-report-builder"></a>Starten des Berichts-Generators (Berichts-Generator)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]umfasst eigenständige-und [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] -Versionen Berichts-Generator. Die [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version kann im einheitlichen Modus oder im integrierten SharePoint-Modus mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet werden.  
  
> [!NOTE]  
>  Der Berichts-Generator kann nicht auf Itanium 64-basierten Computern installiert werden. Dies betrifft die [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] -Version und die eigenständige Version des Berichts-Generators.  
  
 Wenn die geöffnete [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version von Berichts-Generator eine frühere Version von Berichts-Generator ist, sollten Sie sich an Ihren Administrator wenden, um Berichts-Manager und die SharePoint-Website für die Verwendung der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von Berichts-Generator aktualisieren zu lassen.  
  
 Sie können auch die [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version von Berichts-Generator verwenden, um Berichte zu einer in SharePoint veröffentlichten [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]-Arbeitsmappe zu erstellen. Weitere Informationen zur Verwendung von Berichts-Generator mit [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]finden Sie unter [Erstellen eines Reporting Services Berichts mit Power Pivot-Daten](https://go.microsoft.com/fwlink/?LinkId=185238) auf TechNet.Microsoft.com.  
  
 Um Berichts-Generator eigenständig über das **Startmenü** auf dem lokalen Computer zu starten, müssen Sie oder ein Administrator Berichts-Generator direkt auf Ihrem Computer installieren, bevor das Tool zur Verwendung verfügbar ist. Die eigenständige Version wird nicht installiert, wenn Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installieren; Sie müssen sie separat herunterladen und installieren. Informationen zum Herunterladen Berichts-Generator finden Sie unter [Microsoft® SQL Server® 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=401502).  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>So starten Sie den Berichts-Generator ClickOnce aus dem Berichts-Manager  
  
1.  Geben Sie in der Adressleiste des Webbrowsers die URL für den Berichtsserver ein. Standardmäßig lautet die URL http://\<*Servername*>/Berichte. Der Berichts-Manager wird geöffnet.  
  
2.  Klicken Sie auf **Berichts-Generator**.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>So starten Sie den Berichts-Generator ClickOnce über eine URL  
  
1.  Geben Sie die folgende URL in die Adressleiste des Webbrowsers ein:  
  
     http://\<Servername>/ReportServer/ReportBuilder/ReportBuilder_3_0_0_0. Application  
  
2.  Drücken Sie die EINGABETASTE.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>So starten Sie den ClickOnce-Berichts-Generator im integrierten SharePoint-Modus  
  
1.  Navigieren Sie zu der SharePoint-Website mit der gewünschten Bibliothek.  
  
2.  Öffnen Sie die Bibliothek.  
  
3.  Klicken Sie auf **Dokumente**.  
  
4.  Klicken Sie im Menü **Neues Dokument** auf **Berichts-Generator-Bericht**.  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder auf dem Berichtsserver öffnen.  
  
     **Hinweis** Wenn im Menü **Neues Dokument** die Optionen **Berichts-Generator Bericht**, **Berichts-Generator Modell**und **Berichtsdaten Quelle** nicht aufgeführt sind, müssen die entsprechenden Inhaltstypen der SharePoint-Bibliothek hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen von Berichts Server-Inhaltstypen zu einer Bibliothek &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der [-Online](https://go.microsoft.com/fwlink/?LinkId=154888) Dokumentation auf MSDN.Microsoft.com.  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>So starten Sie den eigenständigen Berichts-Generator über das Menü "Start"  
  
1.  Klicken Sie im Startmenü auf **Alle Programme**, und klicken Sie [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] dann auf **Berichts-Generator**.  
  
2.  Klicken Sie auf den **Berichts-Generator** .  
  
     Der Berichts-Generator wird geöffnet, und Sie können einen Bericht erstellen oder öffnen.  
  
3.  Klicken Sie zum Erstellen eines neuen Berichts in der linken oberen Ecke des Berichts-Generators auf das SQL Server-Symbol, und klicken Sie dann auf "Neu".  
  
4.  Klicken Sie in der linken oberen Ecke des Berichts-Generators auf das SQL Server-Symbol, und klicken Sie dann auf "Öffnen", um einen bereits vorhandenen Bericht zu öffnen, der auf Ihrem lokalen Computer oder einem Berichtsserver gespeichert ist.  
  
     Wenn der Berichts Server in der Liste der vorhandenen Server nicht angezeigt wird, schließen Sie das Dialogfeld **Bericht öffnen** , und klicken Sie dann unten auf der Berichts-Generator auf **verbinden** , um eine Verbindung mit dem Server herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Generator in SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
