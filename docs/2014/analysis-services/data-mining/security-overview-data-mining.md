---
title: Sicherheitsübersicht (Datamining) | Microsoft-Dokumentation
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
- security [Analysis Services - data mining], about security
ms.assetid: 387bde00-bcf3-4612-b27b-f9f608dbf71e
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0d7432450357e77875695983f65661f0e645c7a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177017"
---
# <a name="security-overview-data-mining"></a>Sicherheitsübersicht (Data Mining)
  Der Prozess des Sicherns von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] findet auf mehreren Ebenen statt. Sie müssen jede Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und die entsprechenden Datenquellen sichern, um sicherzustellen, dass nur berechtigte Benutzer Lese- und Schreibberechtigungen für ausgewählte Dimensionen, Miningmodelle und Datenquellen haben. Sie müssen auch zugrunde liegende Datenquellen sichern, um zu verhindern, dass unbefugte Benutzer vertrauliche Geschäftsinformationen böswillig gefährden. Die folgenden Themen beschreiben das Sichern einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
##  <a name="bkmk_Architecture"></a> Sicherheitsarchitektur  
 In den folgenden Ressourcen wird die grundlegende Sicherheitsarchitektur einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]erläutert und beschrieben, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung für die Authentifizierung des Benutzerzugriffs verwendet.  
  
-   [Sicherheitsrollen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
-   [Sicherheitseigenschaften](../server-properties/security-properties.md)  
  
-   [Konfigurieren von Dienstkonten &#40;Analysis Services&#41;](../instances/configure-service-accounts-analysis-services.md)  
  
-   [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
##  <a name="bkmk_Logon"></a> Konfigurieren des Anmeldekontos für Analysis Services  
 Sie müssen ein geeignetes Anmeldekonto für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auswählen und die Berechtigungen für dieses Konto angeben. Sie müssen sicherstellen, dass das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Anmeldekonto nur solche Berechtigungen hat, die zum Ausführen der erforderlichen Tasks notwendig sind. Dazu gehören auch die entsprechenden Berechtigungen für die zugrunde liegenden Datenquellen.  
  
 Für Data Mining benötigen Sie eine andere Gruppe von Berechtigungen, um Modelle zu erstellen und zu verarbeiten, als zum Anzeigen oder Abfragen von Modellen erforderlich. Vorhersagen für ein Modell zu treffen ist eine Art von Abfrage und erfordert keine Administratorberechtigungen.  
  
##  <a name="bkmk_Instance"></a> Sichern einer Instanz von Analysis Services  
 Als Nächstes müssen Sie den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Computer, das Windows-Betriebssystem auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Computer, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] selbst und die Datenquellen sichern, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet werden.  
  
##  <a name="bkmk_Access"></a> Konfigurieren des Zugriffs auf Analysis Services  
 Beim Einrichten und Definieren von autorisierten Benutzern für eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]müssen Sie festlegen, welche Benutzer außerdem die Berechtigung zum Verwalten bestimmter Datenbankobjekte, die Berechtigung zum Anzeigen der Definition bestimmter Objekte oder zum Durchsuchen der Modelle und die Berechtigung zum Direktzugriff auf Datenquellen erhalten sollen.  
  
##  <a name="bkmk_DMspecial"></a> Spezielle Überlegungen zu Data Mining  
 Damit ein Analytiker oder Entwickler Data Mining-Modelle erstellen und testen kann, müssen Sie demjenigen Administratorberechtigungen für die Datenbank erteilen, in der die Miningmodelle gespeichert sind. Daraufhin kann der Data Mining-Analytiker oder -Entwickler potenziell andere Objekte erstellen oder löschen, die nicht mit Data Mining verknüpft sind, einschließlich Data Mining-Objekte, die von anderen Analytikern oder Entwicklern erstellt und verwendet werden, oder OLAP-Projekte, die nicht in der Data Mining-Lösung eingeschlossen sind.  
  
 Wenn Sie eine Lösung für Data Mining erstellen, müssen Sie demzufolge die Anforderungen des Analytikers oder Entwicklers zum Entwickeln, Testen und Optimieren von Modellen gegen die Anforderungen anderer Benutzer abwägen und Maßnahmen ergreifen, um vorhandene Datenbankobjekte zu schützen. Ein möglicher Ansatz besteht darin, eine separate Datenbank zu erstellen, die für Data Mining dediziert ist, oder separate Datenbanken für jeden Analytiker zu erstellen.  
  
 Obwohl die Erstellung von Modellen die höchste Berechtigungsebene erfordert, können Sie den Benutzerzugriff auf Data Mining-Modelle für andere Vorgänge, wie die Verarbeitung, das Durchsuchen oder Abfragen, mit der rollenbasierten Sicherheit kontrollieren. Wenn Sie eine Rolle erstellen, legen Sie für Data Mining-Objekte spezifische Berechtigungen fest. Jeder Benutzer, der ein Element einer Rolle ist, verfügt automatisch über alle dieser Rolle zugeordneten Berechtigungen.  
  
 Darüber hinaus verweisen Data Mining-Modelle häufig auf Datenquellen, die vertrauliche Informationen enthalten. Wenn die Miningstruktur und das Miningmodell so konfiguriert wurden, dass Benutzer einen Drillthrough vom Modell in die Daten der Struktur ausführen können, müssen Sie Vorsichtsmaßnahmen ergreifen, um vertrauliche Informationen zu maskieren oder die Zahl der Benutzer einzuschränken, die Zugriff auf zugrunde liegende Daten haben.  
  
 Wenn Sie Integration Services-Pakete zum Bereinigen von Daten, zum Aktualisieren von Miningmodellen oder zum Treffen von Vorhersagen verwenden, müssen Sie sicherstellen, dass der Integration Services-Dienst über die entsprechenden Berechtigungen für die Datenbank verfügt, in der das Modell gespeichert ist, sowie über die entsprechenden Berechtigungen für die Quelldaten.  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen und Berechtigungen &#40;Analysis Services&#41;](../multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
