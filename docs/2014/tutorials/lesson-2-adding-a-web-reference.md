---
title: 'Lektion 2: Hinzufügen eines Webverweises | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dd4b9edc8c054a7fa2ec84bdc8d892e5b5a903a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63316010"
---
# <a name="lesson-2-adding-a-web-reference"></a>Lektion 2: Hinzufügen eines Webverweises
  Webdienstermittlung ist der Prozess, durch den ein Client einen Webdienst sucht und seine Dienstbeschreibung erhält. Der Prozess der Webdienstermittlung in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] beinhaltet das Abfragen einer Website gemäß einem vorher festgelegten Algorithmus. Ziel des Prozesses ist es, die Dienstbeschreibung zu finden. Diese Beschreibung ist ein XML-Dokument, das WSDL (Web Services Description Language) verwendet.  
  
 Die Dienstbeschreibung gibt an, welche Dienste verfügbar sind und wie mit diesen Diensten interagiert werden kann. Ohne eine Dienstbeschreibung ist es nicht möglich, programmgesteuert mit einem Webdienst zu interagieren.  
  
 Die Anwendung muss ein Kommunizieren mit dem Webdienst sowie eine Suche nach dem Webdienst zur Laufzeit ermöglichen. Das Hinzufügen eines Webverweises zum Projekt für den Webdienst generiert zu diesem Zweck eine Proxyklasse, die eine Schnittstelle mit dem Webdienst sowie eine lokale Darstellung des Webdiensts bietet. Weitere Informationen finden Sie in der Vorgehensweise zum Generieren eines XML-Webdienstproxys in der Dokumentation zu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-add-a-web-reference"></a>So fügen Sie einen Webverweis hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Dienstverweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **erweitert**.  
  
3.  Klicken Sie im Dialogfeld **Dienst Verweis Einstellungen** auf **Webverweis hinzufügen**.  
  
4.  Geben Sie im Dialogfeld **Webverweis hinzufügen** im Feld **URL** die URL ein, um die Dienst Beschreibung des Report Server-Webdiensts zu erhalten http://localhost/reportserver/reportservice2010.asmx, z. b.. Klicken Sie dann auf die Schaltfläche " **go** ", um Informationen zum Webdienst abzurufen.  
  
     \- oder –  
  
     Wenn der Report Server-Webdienst auf dem lokalen Computer vorhanden ist, klicken Sie im Browser **Bereich auf den Link Webdienste auf dem lokalen Computer** . Klicken Sie dann in der angezeigten Liste auf den Link für den ReportService2010-Webdienst.  
  
5.  Benennen Sie im Feld **Webverweis Name** den Webverweis in ReportService2010 um. Dies ist der Namespace, den Sie für diesen Webverweis verwenden werden.  
  
6.  Klicken Sie auf **Verweis hinzufügen** , um einen Webverweis für den Zielweb Dienst hinzuzufügen.  
  
     
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lädt die Dienstbeschreibung herunter und generiert eine Proxyklasse als Schnittstelle zwischen der Anwendung und dem Berichtsserver-Webdienst. Damit der Webverweis funktionsfähig ist, muss auch dem <xref:System.Web.Services>-Namespace ein Verweis hinzugefügt werden.  
  
7.  Klicken Sie im Menü Projekt auf **Verweis hinzufügen**.  
  
8.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.net** die Option **System. Web. Services**aus, und klicken Sie dann auf **OK**.  
  
 Weitere Informationen finden Sie unter [Accessing the SOAP API (Zugriff auf die SOAP-API)](../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver-Webdienst](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Lektion 3: Zugreifen auf den Webdienst](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Zugreifen auf den Report Server-Webdienst mithilfe von Visual Basic oder Visual C&#35; &#40;SSRS-Tutorial&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
