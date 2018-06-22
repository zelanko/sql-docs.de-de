---
title: 'Lektion 2: Hinzufügen eines Webverweises | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
caps.latest.revision: 29
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ff574cf6ab00b4b368a7d372957b2348757ad0f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147798"
---
# <a name="lesson-2-adding-a-web-reference"></a>Lektion 2: Hinzufügen eines Webverweises
  Webdienstermittlung ist der Prozess, durch den ein Client einen Webdienst sucht und seine Dienstbeschreibung erhält. Der Prozess der Webdienstermittlung in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] beinhaltet das Abfragen einer Website gemäß einem vorher festgelegten Algorithmus. Ziel des Prozesses ist es, die Dienstbeschreibung zu finden. Diese Beschreibung ist ein XML-Dokument, das WSDL (Web Services Description Language) verwendet.  
  
 Die Dienstbeschreibung gibt an, welche Dienste verfügbar sind und wie mit diesen Diensten interagiert werden kann. Ohne eine Dienstbeschreibung ist es nicht möglich, programmgesteuert mit einem Webdienst zu interagieren.  
  
 Die Anwendung muss ein Kommunizieren mit dem Webdienst sowie eine Suche nach dem Webdienst zur Laufzeit ermöglichen. Das Hinzufügen eines Webverweises zum Projekt für den Webdienst generiert zu diesem Zweck eine Proxyklasse, die eine Schnittstelle mit dem Webdienst sowie eine lokale Darstellung des Webdiensts bietet. Weitere Informationen finden Sie in der Vorgehensweise zum Generieren eines XML-Webdienstproxys in der Dokumentation zu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-add-a-web-reference"></a>So fügen Sie einen Webverweis hinzu  
  
1.  Auf der **Projekt** Menü klicken Sie auf **Hinzufügen eines Dienstverweises**.  
  
2.  In der **Hinzufügen eines Dienstverweises** (Dialogfeld), klicken Sie auf **erweitert**.  
  
3.  In der **Dienstverweiseinstellungen** (Dialogfeld), klicken Sie auf **Webverweis hinzufügen**.  
  
4.  In der **URL** im Feld der **Webverweis hinzufügen** Dialogfeld Geben Sie die URL, um die dienstbeschreibung des Report Server-Webdienst zu erhalten, wie z. B. http://localhost/reportserver/reportservice2010.asmx. Klicken Sie dann auf die **Go** Schaltfläche, um Informationen über den Webdienst abzurufen.  
  
     \- oder –  
  
     Wenn der Berichtsserver-Webdienst auf dem lokalen Computer vorhanden ist, klicken Sie auf die **-Webdienste auf dem lokalen Computer** Link im Browserbereich. Klicken Sie dann in der angezeigten Liste auf den Link für den ReportService2010-Webdienst.  
  
5.  In der **Webverweisname** Feld, benennen Sie den Webverweis ReportService2010, dies ist der Namespace, die Sie für diesen Webverweis verwenden.  
  
6.  Klicken Sie auf **Verweis hinzufügen** um einen Webverweis für den Zielwebdienst hinzuzufügen.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lädt die Dienstbeschreibung herunter und generiert eine Proxyklasse als Schnittstelle zwischen der Anwendung und dem Berichtsserver-Webdienst. Sie müssen auch einen Verweis hinzufügen der <xref:System.Web.Services> Namespace-URI für den Webverweis arbeiten.  
  
7.  Klicken Sie auf das Menü Projekt auf **Verweis hinzufügen**.  
  
8.  In der **Verweis hinzufügen** Dialogfeld die **.NET** Registerkarte **System.Web.Services**, klicken Sie dann auf **OK**.  
  
 Weitere Informationen finden Sie unter [Accessing the SOAP API (Zugriff auf die SOAP-API)](../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver-Webdienst](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Lektion 3: Zugreifen auf den Webdienst](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Zugriff auf die Berichtsserver-Webdienst mit Visual Basic oder Visual C#&#35; &#40;SSRS-Lernprogramm&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  