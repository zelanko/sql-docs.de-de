---
title: Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c82a2df266f9e6dce2767ecceb3e2af9bd12fc1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162397"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Erteilen von Berechtigungen für gespeicherte Prozeduren (Analysis Services)
  Gespeicherte Prozeduren oder Assemblys [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sind externe Routinen, geschrieben einer [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET-Programmiersprache erweitern, die die Funktionen der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Mit Assemblys können Entwickler die Vorteile der sprachübergreifenden Integration, der Ausnahmebehandlung, der Versionsunterstützung, der Verteilungs- und der Debugunterstützung nutzen.  
  
 Sie müssen ein Serveradministrator sein, um eine Assembly zu registrieren. Finden Sie unter [Erteilen von Serveradministratorberechtigungen &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Sicherheitskontext für die Ausführung einer gespeicherten Prozedur  
 Alle Benutzer können gespeicherte Prozeduren aufrufen. Je nach Konfiguration der gespeicherten Prozedur kann diese entweder im Kontext des die Prozedur aufrufenden Benutzers oder im Kontext eines anonymen Benutzers ausgeführt werden. Da ein anonymer Benutzer keinen Sicherheitskontext besitzt, müssen Sie für diese Möglichkeit gleichzeitig die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so konfigurieren, dass sie den anonymen Zugriff erlaubt.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in der gespeicherten Prozedur aus, nachdem diese vom Benutzer aufgerufen, jedoch bevor sie von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ausgeführt wird. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet die Aktionen in einer gespeicherten Prozedur anhand der Schnittmenge der Berechtigungen für den Benutzer sowie des Berechtigungssatzes zum Ausführen des Verfahrens aus. Wenn die gespeicherte Prozedur eine Aktion enthält, die durch die Datenbankrolle des Benutzers nicht ausgeführt werden kann, wird diese Aktion nicht ausgeführt.  
  
 Beim Ausführen gespeicherter Prozeduren werden die folgenden Berechtigungssätze verwendet:  
  
-   **Sichere** mit der sicheren Satz von Datenbankberechtigungen, die eine gespeicherte Prozedur kann nicht zugreifen der geschützten Ressourcen in der [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework. Der Berechtigungssatz lässt nur Berechnungen zu. Dies ist der sicherste Berechtigungssatz. Es gelangen keine Informationen aus [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] heraus, die Berechtigungen können nicht erweitert werden, und das Risiko von Datenmanipulationsangriffen wird minimiert.  
  
-   **Externer Zugriff** mit der externen Access-Berechtigungssatz, eine gespeicherte Prozedur kann Zugriff auf externe Ressourcen mithilfe von verwaltetem Code. Wenn dieser Berechtigungssatz für eine gespeicherte Prozedur festgelegt wird, werden Programmierfehler ausgeschlossen, die zu einem instabilen Server führen können. Dieser Berechtigungssatz kann jedoch dazu führen, dass Informationen nach außen (außerhalb des Servers) gelangen, und es besteht die Möglichkeit, dass Berechtigungs- und Datenmanipulationsangriffe zunehmen.  
  
-   **Unrestricted** mit der uneingeschränkten Berechtigungssatz, eine gespeicherte Prozedur kann Zugriff auf externe Ressourcen mithilfe von Code. Bei diesem Berechtigungssatz gibt es für gespeicherte Prozeduren keine Gewähr für die Sicherheit und Zuverlässigkeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionales Modell Assemblys-Verwaltung](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  