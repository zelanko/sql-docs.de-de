---
title: Konfigurieren von Geschäftsregeln für das Senden von Benachrichtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b0ea6e215b5192d1b9e84ed252708b188d5c5a59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483953"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>Konfigurieren von Geschäftsregeln für das Senden von Benachrichtigungen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]konfigurieren Sie Geschäftsregeln für das Senden von Benachrichtigungen, wenn Sie Benutzer über Änderungen von Attributwerten in Kenntnis setzen möchten.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf die Funktionsbereiche **Systemverwaltung** und **Benutzer- und Gruppenberechtigungen** verfügen. Wenn Sie nicht über die Berechtigung für den Funktionsbereich **Benutzer- und Gruppenberechtigungen** verfügen, können Sie die Liste der Benutzer und Gruppen nicht anzeigen, an die Benachrichtigungen gesendet werden sollen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Es muss bereits eine Geschäftsregel vorhanden sein, die eine Überprüfungsaktion verwendet. Weitere Informationen finden Sie unter [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   Der Benutzer oder die Gruppe, der bzw. die die Benachrichtigung empfängt, muss mindestens die **Leseberechtigung** für das Attribut haben, dessen Überprüfung einen Fehler ergibt. Benutzer oder Gruppen, denen die Berechtigung für das Attribut explizit oder implizit verweigert wird, empfangen die E-Mail, können jedoch in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]nicht auf das Attribut zugreifen.  
  
-   Wenn eine E-Mail an eine Gruppe gesendet wird, wird die E-Mail nur Mitgliedern der Gruppe zugestellt, die auf den [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zugegriffen haben.  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>So konfigurieren Sie Geschäftsregeln für das Senden von Benachrichtigungen  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie in der Liste **Elementtyp** einen Typ des Members aus.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Doppelklicken Sie im Raster in der Zeile für die Geschäftsregel auf das **Benachrichtigungs** Feld.  
  
8.  Klicken Sie im Untermenü auf einen Benutzer oder eine Gruppe, an den die e-Mail-Benachrichtigung gesendet werden soll.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Führen Sie zum Anwenden von Geschäftsregeln auf Daten eine der folgenden Prozeduren aus:  
  
    -   [Überprüfen bestimmter Mitglieder anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Konfigurieren Sie das E-Mail-Protokoll wie folgt:  
  
    -   [Konfigurieren von e-Mail-Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)   
 [Konfigurieren von e-Mail-Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
