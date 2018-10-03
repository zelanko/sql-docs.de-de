---
title: Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5f24a5ca8ea44f3e05bc11d0148ab30d6f83e993
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148550"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services)
  Gespeicherte Prozeduren oder Assemblys [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sind externe Routinen, geschrieben einer [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET-Programmiersprache erweitern, die die Funktionen der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Mit Assemblys können Entwickler die Vorteile der sprachübergreifenden Integration, der Ausnahmebehandlung, der Versionsunterstützung, der Verteilungs- und der Debugunterstützung nutzen.  
  
 Sie müssen ein Serveradministrator sein, um eine Assembly zu registrieren. Finden Sie unter [Erteilen von Serveradministratorberechtigungen &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Sicherheitskontext für die Ausführung einer gespeicherten Prozedur  
 Alle Benutzer können gespeicherte Prozeduren aufrufen. Je nach Konfiguration der gespeicherten Prozedur kann diese entweder im Kontext des die Prozedur aufrufenden Benutzers oder im Kontext eines anonymen Benutzers ausgeführt werden. Da ein anonymer Benutzer keinen Sicherheitskontext besitzt, müssen Sie für diese Möglichkeit gleichzeitig die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so konfigurieren, dass sie den anonymen Zugriff erlaubt.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in der gespeicherten Prozedur aus, nachdem diese vom Benutzer aufgerufen, jedoch bevor sie von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ausgeführt wird. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in einer gespeicherten Prozedur anhand der Schnittmenge der Berechtigungen für den Benutzer sowie des Berechtigungssatzes zum Ausführen des Verfahrens aus. Wenn die gespeicherte Prozedur eine Aktion enthält, die durch die Datenbankrolle des Benutzers nicht ausgeführt werden kann, wird diese Aktion nicht ausgeführt.  
  
 Beim Ausführen gespeicherter Prozeduren werden die folgenden Berechtigungssätze verwendet:  
  
-   **Sichere** mit dem Safe-Berechtigungssatz, eine gespeicherte Prozedur kann nicht auf die geschützten Ressourcen in zugreifen der [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework. Der Berechtigungssatz lässt nur Berechnungen zu. Dies ist der sicherste Berechtigungssatz. Es gelangen keine Informationen aus [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] heraus, die Berechtigungen können nicht erweitert werden, und das Risiko von Datenmanipulationsangriffen wird minimiert.  
  
-   **Externer Zugriff** Berechtigungssatz mit dem External Access, eine gespeicherte Prozedur kann Zugriff auf externe Ressourcen mithilfe von verwaltetem Code. Wenn dieser Berechtigungssatz für eine gespeicherte Prozedur festgelegt wird, werden Programmierfehler ausgeschlossen, die zu einem instabilen Server führen können. Dieser Berechtigungssatz kann jedoch dazu führen, dass Informationen nach außen (außerhalb des Servers) gelangen, und es besteht die Möglichkeit, dass Berechtigungs- und Datenmanipulationsangriffe zunehmen.  
  
-   **Unrestricted** mit der uneingeschränkten Berechtigungssatz eine gespeicherte Prozedur kann Zugriff auf externe Ressourcen mithilfe von Code. Bei diesem Berechtigungssatz gibt es für gespeicherte Prozeduren keine Gewähr für die Sicherheit und Zuverlässigkeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
