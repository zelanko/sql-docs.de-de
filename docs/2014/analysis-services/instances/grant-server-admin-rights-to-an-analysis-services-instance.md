---
title: Erteilen von Serveradministratorberechtigungen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b3100fc8ccf9f21a6c0cf760d799dcf1b15cbb5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202210"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a>Erteilen von Serveradministratorberechtigungen (Analysis Services)
  Mitglieder der Serveradministratorrolle in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz haben uneingeschränkten Zugriff auf alle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte und -Daten in dieser Instanz. Ein Benutzer muss Mitglied der Serveradministratorrolle sein, um serverweite Tasks wie z. B. Erstellen oder Verarbeiten einer Datenbank, das Ändern von Servereigenschaften oder das Starten einer Ablaufverfolgung (außer für Verarbeitungsereignisse) ausführen zu können.  
  
 Rollenmitgliedschaften werden bei der Installation von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eingerichtet. Der Benutzer das Setupprogramm ausführen kann oder gruppenerstellung der Rolle hinzufügen oder einen anderen Benutzer hinzufügen, bei der. Sie können die Rollenmitgliedschaft nach der Installation mithilfe der folgenden Schritte ändern.  
  
## <a name="modify-server-role-membership"></a>Ändern der Serverrollenmitgliedschaft  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Instanznamen, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie im Bereich **Seite auswählen** auf **Sicherheit** , und klicken Sie anschließend unten auf der Seite auf **Hinzufügen** , um der Serverrolle einen oder mehrere Windows-Benutzer bzw. Windows-Benutzergruppen hinzuzufügen.  
  
     ![Benutzer Dialogfelds "hinzufügen" in Management Studio](../media/ssas-serveradminadd.png "Benutzer Dialogfelds \"hinzufügen\" in Management Studio")  
  
 Zur Installationszeit erfordert SQL Server-Setup, dass mindestens ein Benutzerkonto als Analysis Services-Systemadministrator angegeben wird.  
  
 Standardmäßig werden den Mitgliedern der lokalen Administratorgruppe ebenfalls Administratorrechte im Analysis-Server gewährt. Obwohl die lokale Gruppe keine explizit gewährte Mitgliedschaft in der Serveradministratorrolle von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist, können lokale Administratoren Datenbanken erstellen, Benutzer und Berechtigungen hinzufügen und jede andere Aufgabe ausführen, zu deren Ausführung Systemadministratoren berechtigt sind. Dieses Verhalten ist konfigurierbar. Es richtet sich nach der `BuiltinAdminsAreServerAdmins` Servereigenschaft, die auf **"true"** standardmäßig. Sie können diese Eigenschaft in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ändern. Weitere Informationen finden Sie unter [Sicherheitseigenschaften](../server-properties/security-properties.md).  
  
 Sie können Serverrollen auch mithilfe von Analysis Management Objects (AMOs) verwalten. Weitere Informationen finden Sie unter [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Sicherheitsrollen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
