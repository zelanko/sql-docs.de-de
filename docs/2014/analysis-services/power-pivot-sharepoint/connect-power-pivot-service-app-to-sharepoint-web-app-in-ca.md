---
title: Verbinden eine PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33d2f83b1b003e6be2fc5c47b8a0e12b440f537c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749425"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a>Verbinden einer PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration
  Eine PowerPivot-Dienstanwendung kann von einer beliebigen Anzahl von SharePoint-Webanwendungen in der Farm verwendet werden. Um eine PowerPivot-Dienstanwendung zur Verfügung zu stellen, fügen Sie sie einer Dienstzuordnungsliste hinzu.  
  
> [!IMPORTANT]  
>  Damit das PowerPivot-Management-Dashboard ordnungsgemäß funktioniert, muss eine PowerPivot-Dienstanwendung in der Standardverbindungsgruppe enthalten sein. Fügen Sie nicht mehr als eine PowerPivot-Dienstanwendung zu der Standardgruppe hinzu. Das Hinzufügen mehrerer Einträge des gleichen Dienstanwendungstyps ist keine unterstützte Konfiguration und könnte Fehler verursachen. Wenn Sie zusätzliche Dienstanwendungen erstellen, fügen Sie sie benutzerdefinierten Listen hinzu.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Hinzufügen von PowerPivot-Dienstanwendung zur Standardgruppe](#default)  
  
 [Hinzufügen einer PowerPivot-Dienstanwendung einer benutzerdefinierten Dienstzuordnungsliste](#custom)  
  
##  <a name="default"></a> Hinzufügen von PowerPivot-Dienstanwendung zur Standardgruppe  
 Eine Dienstanwendungsliste ist eine Liste freigegebener Dienste, die Ressourcen für andere SharePoint-Webanwendungen in der Farm bereitstellen. Es gibt eine Standardgruppe von Dienstzuordnungen für die Farm.  
  
 Eine PowerPivot-Dienstanwendung kann der Liste entweder hinzugefügt werden, wenn Sie die Anwendung erstellen oder im Anschluss daran mithilfe folgender Schritte.  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Dienstanwendungszuordnungen konfigurieren**.  
  
2.  Klicken Sie unter Anwendungsproxygruppe auf **Standard**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben der PowerPivot-Dienstanwendung (durch den Typnamen `PowerPivot Service Application Proxy` gekennzeichnet). Bei mehreren PowerPivot-Dienstanwendung wählen Sie nur eine Anwendung aus.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="custom"></a> Hinzufügen einer PowerPivot-Dienstanwendung einer benutzerdefinierten Dienstzuordnungsliste  
 Die Standardgruppe kann durch eine benutzerdefinierte Liste ersetzt werden. Eine benutzerdefinierte Liste wird speziell für eine einzelne SharePoint-Webanwendung erstellt. Dabei wird die Standardgruppe überschrieben und durch vom Farm- oder Dienstadministrator angegebene Dienstzuordnungen ersetzt. Wenn Sie mehrere PowerPivot-Dienstanwendungen erstellt haben, müssen Sie die zu verwendende Anwendung mithilfe einer benutzerdefinierten Liste angeben. Eine benutzerdefinierte Liste kann nicht von anderen Webanwendungen wiederverwendet werden. Sie gilt nur für die Webanwendung, für die sie erstellt wurde.  
  
1.  Klicken Sie in der Zentraladministration unter **Anwendungsverwaltung**auf **Webanwendungen verwalten**.  
  
2.  Wählen Sie die Anwendung (z. B. SharePoint -80) aus.  
  
3.  Klicken Sie in Webanwendungen unter „Verwalten“ auf **Dienstverbindungen**.  
  
4.  Wählen Sie unter **Folgende Zuordnungsgruppe bearbeiten**die Option **[Benutzerdefiniert]** aus.  
  
5.  Aktivieren Sie das Kontrollkästchen neben jeder Dienstanwendungsverbindung, die Sie verwenden möchten. Falls Sie über mehrere PowerPivot-Dienstanwendungen verfügen (am Typ `PowerPivot Service Application Proxy` erkennbar), achten Sie darauf, nur eine auszuwählen.  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Konfigurieren einer PowerPivot-Dienstanwendung in der Zentraladministration](create-and-configure-power-pivot-service-application-in-ca.md)   
 [Anfängliche Konfiguration &#40;PowerPivot für SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
