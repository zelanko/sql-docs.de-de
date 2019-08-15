---
title: Sichern einer Master Data Manager-Webanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 30b1f8addacb1c4502a50ab5d00e507aa4ca63cc
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028806"
---
# <a name="secure-a-master-data-manager-web-application"></a>Schützen einer Master Data Manager-Webanwendung

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Sie können die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung per HTTPS schützen.  
  
> [!NOTE]  
>  Für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung kann entweder HTTP oder HTTPS verwendet werden, jedoch nicht beides.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 So führen Sie die Prozedur aus  
  
-   Sie müssen Administrator auf dem Webserver sein, auf dem [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] installiert ist.  
  
-   Auf dem Webserver muss MDS installiert sein, und es muss eine Webanwendung vorhanden sein. Weitere Informationen finden Sie unter [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md) und [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>So schützen Sie die Master Data Manager-Webanwendung per HTTPS  
  
1.  Nachdem Sie sich vergewissert haben, dass die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung per HTTP ordnungsgemäß konfiguriert wurde, erstellen Sie in IIS ein Zertifikat. Weitere Informationen finden Sie unter [Konfigurieren von Serverzertifikaten in IIS 7.0](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  Klicken Sie im Bereich **Verbindungen** unter **Websites**auf die Website, auf der die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung gehostet wird.  
  
3.  Klicken Sie im **Aktionsbereich** auf **Bindungen**.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
5.  Wählen Sie in der Liste die Option **https**.  
  
6.  Wählen Sie das SSL-Zertifikat aus.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Optional. Um HTTP zu entfernen, damit Benutzer nur per HTTPS auf die Website zugreifen können, klicken Sie in der Liste auf die Zeile mit **http**. Klicken Sie auf **Entfernen** , und klicken Sie im Bestätigungsdialogfeld auf **Ja**.  
  
    > [!IMPORTANT]  
    >  Nachdem HTTP entfernt wurde, müssen die basicHttp- und wsHttpBinding-Konfiguration geändert werden.  
  
9. Klicken Sie zum Schließen des Dialogfelds **Sitebindungen** auf **Schließen**.  
  
10. Öffnen Sie die Datei „web.config“ unter *Laufwerk*:\Programme\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
11. Suchen Sie nach der Zeichenfolge `<security mode="Message">` , und ändern Sie diese in `<security mode="Transport">`.  

12. Ändern Sie `<serviceMetadata httpGetEnable="true" httpsGetEnabled="false">` in `<serviceMetadata httpGetEnable="false" httpsGetEnabled="true">`, um Probleme zu vermeiden, die im Silverlight-Client auftreten können.

13. Speichern und schließen Sie die Datei. Wenn Sie einen Fehler erhalten, kann dies daran liegen, dass Sie die Benutzerkontensteuerung aktiviert haben. Benutzer sollten jetzt per HTTPS auf die Website zugreifen können.  

  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
