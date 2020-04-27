---
title: Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a363336af1bee8c3f84ff620f667c7c0d510b73
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080731"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services)
  Die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeicherten Prozeduren oder Assemblys sind externe Routinen, die in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET-Programmiersprache geschrieben sind und die Möglichkeiten von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erweitern. Mit Assemblys können Entwickler die Vorteile der sprachübergreifenden Integration, der Ausnahmebehandlung, der Versionsunterstützung, der Verteilungs- und der Debugunterstützung nutzen.  
  
 Sie müssen ein Serveradministrator sein, um eine Assembly zu registrieren. Weitere Informationen finden Sie unter [Erteilen von Server Administrator Berechtigungen &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Sicherheitskontext für die Ausführung einer gespeicherten Prozedur  
 Alle Benutzer können gespeicherte Prozeduren aufrufen. Je nach Konfiguration der gespeicherten Prozedur kann diese entweder im Kontext des die Prozedur aufrufenden Benutzers oder im Kontext eines anonymen Benutzers ausgeführt werden. Da ein anonymer Benutzer keinen Sicherheitskontext besitzt, müssen Sie für diese Möglichkeit gleichzeitig die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so konfigurieren, dass sie den anonymen Zugriff erlaubt.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in der gespeicherten Prozedur aus, nachdem diese vom Benutzer aufgerufen, jedoch bevor sie von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ausgeführt wird. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in einer gespeicherten Prozedur anhand der Schnittmenge der Berechtigungen für den Benutzer sowie des Berechtigungssatzes zum Ausführen des Verfahrens aus. Wenn die gespeicherte Prozedur eine Aktion enthält, die durch die Datenbankrolle des Benutzers nicht ausgeführt werden kann, wird diese Aktion nicht ausgeführt.  
  
 Beim Ausführen gespeicherter Prozeduren werden die folgenden Berechtigungssätze verwendet:  
  
-   **Sicher** Mit dem Safe-Berechtigungs Satz kann eine gespeicherte Prozedur nicht auf die geschützten Ressourcen [!INCLUDE[msCoName](../includes/msconame-md.md)] im .NET Framework zugreifen. Der Berechtigungssatz lässt nur Berechnungen zu. Dies ist der sicherste Berechtigungssatz. Es gelangen keine Informationen aus [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] heraus, die Berechtigungen können nicht erweitert werden, und das Risiko von Datenmanipulationsangriffen wird minimiert.  
  
-   **Externer Zugriff** Wenn die Berechtigung für den externen Zugriff festgelegt ist, kann eine gespeicherte Prozedur mithilfe von verwaltetem Code auf externe Ressourcen zugreifen. Wenn dieser Berechtigungssatz für eine gespeicherte Prozedur festgelegt wird, werden Programmierfehler ausgeschlossen, die zu einem instabilen Server führen können. Dieser Berechtigungssatz kann jedoch dazu führen, dass Informationen nach außen (außerhalb des Servers) gelangen, und es besteht die Möglichkeit, dass Berechtigungs- und Datenmanipulationsangriffe zunehmen.  
  
-   **Uneingeschränkt** Wenn die uneingeschränkte Berechtigung festgelegt ist, kann eine gespeicherte Prozedur über einen beliebigen Code auf externe Ressourcen zugreifen. Bei diesem Berechtigungssatz gibt es für gespeicherte Prozeduren keine Gewähr für die Sicherheit und Zuverlässigkeit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellassemblys](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
