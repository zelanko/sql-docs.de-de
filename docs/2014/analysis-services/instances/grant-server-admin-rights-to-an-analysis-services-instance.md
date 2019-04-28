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
ms.openlocfilehash: 8df7e950f300028b2246450bf29ed0e8776f2cd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62703683"
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
  
 Sie können Serverrollen auch mithilfe von Analysis Management Objects (AMOs) verwalten. Weitere Informationen finden Sie unter [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).  
  
## <a name="see-also"></a>Siehe auch  
 [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Sicherheitsrollen &#40;Analysis Services – Mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
