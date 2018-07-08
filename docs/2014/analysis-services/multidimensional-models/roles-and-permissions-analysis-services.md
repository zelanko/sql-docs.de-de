---
title: Rollen und Berechtigungen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 506babae85a4b1a04efa7f12b8b40c2527e2e094
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159401"
---
# <a name="roles-and-permissions-analysis-services"></a>Rollen und Berechtigungen (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bietet ein rollenbasiertes Autorisierungsmodell, mit dem der Zugriff auf Vorgänge, Objekte und Daten erteilt wird. Alle Benutzer, die auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder -Datenbank zugreifen, müssen den Vorgang im Kontext einer Rolle ausführen.  
  
 Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Systemadministrator ist dafür verantwortlich, Mitgliedschaften für die **Serveradministratorrolle** zu gewähren, die uneingeschränkten Zugriff auf Servervorgänge bietet. Diese Rolle verfügt über feste Berechtigungen und kann nicht angepasst werden. Standardmäßig sind Mitglieder der lokalen Administratorgruppe automatisch Analysis Services-Systemadministratoren.  
  
 Benutzer, die keine Administratoren sind, und Daten abrufen oder verarbeiten, erhalten Zugriff über **Datenbankrollen**. Als Systemadministrator oder Datenbankadministrator können Sie die Rollen erstellen, mit denen die verschiedenen Zugriffsebenen innerhalb einer bestimmten Datenbank beschrieben werden, und jedem Benutzer, der Zugriff benötigt, eine Mitgliedschaft zuweisen. Jede Rolle besitzt einen benutzerdefinierten Satz von Berechtigungen, mit denen Benutzer in einer bestimmten Datenbank auf Objekte und Vorgänge zugreifen können. Sie können Berechtigungen auf folgenden Ebenen zuweisen: Datenbank, innere Objekte wie Cubes und Dimensionen (aber keine Perspektiven) sowie Zeilen.  
  
 Üblicherweise erfolgt das Erstellen von Rollen und Zuweisen von Mitgliedschaften voneinander getrennt. Der Modellentwickler fügt Rollen häufig in der Entwurfsphase hinzu. Auf diese Weise werden alle Rollendefinitionen in den Projektdateien widergespiegelt, durch die das Modell definiert wird. Rollenmitgliedschaften werden in der Regel später eingerichtet, wenn die Datenbank in die Produktionsumgebung eingebunden wird. Dafür sind normalerweise Datenbankadministratoren zuständig, die Skripts erstellen, die entwickelt, getestet und als unabhängiger Vorgang ausgeführt werden können.  
  
 Die gesamte Autorisierung basiert auf einer gültigen Windows-Benutzeridentität. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wird ausschließlich die Windows-Authentifizierung zum Authentifizieren von Benutzeridentitäten verwendet. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt keine proprietäre Authentifizierungsmethode bereit. Finden Sie unter [von Analysis Services Unterstützte Authentifizierungsmethoden](../instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Berechtigungen sind additiv für jeden Windows-Benutzer/jede Windows-Gruppe, über alle Rollen in der Datenbank hinweg. Wenn eine Rolle dem Benutzer oder der Gruppe das Ausführen bestimmter Tasks oder das Anzeigen bestimmter Daten untersagt, eine andere Rolle dem Benutzer oder der Gruppe diese Berechtigung allerdings erteilt, dann ist der Benutzer oder die Gruppe berechtigt, den Task auszuführen bzw. die Daten anzuzeigen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Erteilen von Datenbankberechtigungen &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)  
  
-   [Erteilen von Cube-oder modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Erteilen von verarbeitungsberechtigungen &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)  
  
-   [Erteilen von Berechtigungen von Definitionen für Objektmetadaten lesen &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Erteilen von Berechtigungen für ein Datenquellenobjekt &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Erteilen von Berechtigungen für Datamining-Strukturen und Modelle &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Erteilen von Berechtigungen für eine Dimension &#40;Analysis Services&#41;](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Erteilen von benutzerdefiniertem Zugriff auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Erteilen von benutzerdefiniertem Zugriff auf Zellendaten &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten von Rollen &#40;SSAS – tabellarisch&#41;](../tabular-models/roles-ssas-tabular.md)  
  
  
