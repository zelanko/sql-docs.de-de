---
title: Testen der Berechtigungen eines Benutzers (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 38d4b1e7f9bd3e76c00bb4228e53e09416ed8557
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488092"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Testen der Berechtigungen eines Benutzers (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie einen Testbenutzer erstellen und sich bei der Webanwendung anmelden, um Berechtigungen zu testen. Wenn ein Benutzer versucht, auf die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -URL zuzugreifen, werden die Anmeldeinformationen des Benutzers authentifiziert. In Internet Explorer wird über Sicherheitseinstellungen gesteuert, ob dies automatisch stattfindet oder ob der Benutzer einen Benutzernamen und ein Kennwort eingeben muss. Um diese Einstellungen zu ändern, führen Sie die folgenden Schritte aus:  
  
### <a name="to-test-a-users-security"></a>So testen Sie die Sicherheitseinstellungen für einen Benutzer  
  
1.  Klicken Sie in Internet Explorer 7 und höher auf **Extras**, **Internetoptionen**und dann auf die Registerkarte **Sicherheit** .  
  
2.  Klicken Sie auf **Lokales Intranet** und dann auf die Schaltfläche **Stufe anpassen** .  
  
3.  Wählen Sie im Abschnitt **Benutzerauthentifizierung** die Option **Nach Benutzername und Kennwort fragen**aus.  
  
4.  Das nächste Mal, wenn Sie das Browserfenster öffnen, werden Sie zur Eingabe eines Benutzernamens und Kennworts aufgefordert.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
