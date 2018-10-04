---
title: Informationen zum Identitätswechsel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05236d05e1b543ea7acb36f0856083e1c1db77a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209720"
---
# <a name="impersonation-information"></a>Identitätswechselinformationen
  Verwenden Sie die Seite **Identitätswechselinformationen** , um die Anmeldeinformationen anzugeben, mit denen Analysis Services eine Verbindung mit der Datenquelle herstellt.  
  
## <a name="options"></a>Tastatur  
 **Bestimmten Windows-Benutzernamen und bestimmtes Kennwort**  
 Wählen Sie diese Option aus, damit das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Objekt die Sicherheitsanmeldeinformationen eines angegebenen Windows-Benutzerkontos verwendet. Die angegebenen Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Out-of-Line-Bindungen, lokale Cubes, Miningmodelle, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Bei OPENQUERY-Anweisungen von Data Mining-Erweiterungen (DMX) wird diese Option jedoch ignoriert, und es werden die Anmeldeinformationen des aktuellen Benutzers verwendet.  
  
 **Benutzername**  
 Geben Sie die Domäne und den Namen des Benutzerkontos ein, die von dem ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verwendet werden sollen. Verwenden Sie folgendes Format:  
  
 *\<Domänenname >* **\\**  *\<Benutzerkontonamen >*  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Benutzerkontos ein, das von dem ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Objekt verwendet werden soll.  
  
 Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.  
  
 **Dienstkonto verwenden**  
 Wählen Sie diese Option aus, damit das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt die Anmeldeinformationen mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst verwendet, der das Objekt verwaltet. Die Dienstkonto-Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Bei OPENQUERY-Anweisungen von Data Mining-Erweiterungen (DMX), lokalen Cubes und Miningmodellen werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Out-of-Line-Bindungen nicht unterstützt.  
  
 **Anmeldeinformationen des aktuellen Benutzers verwenden**  
 Wählen Sie diese Option aus, damit vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt für Out-of-Line-Bindungen, DMX OPENQUERY-Anweisungen, lokale Cubes und Miningmodelle die Sicherheitsanmeldeinformationen des aktuellen Benutzers verwendet werden. Diese Option wird für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle nicht unterstützt.  
  
 **Erben**  
 Aktivieren Sie diese Option, um das auf Datenbankebene definierte Identitätswechselverhalten zu verwenden. Dies wurde mithilfe der Datenbankeigenschaft `DataSourceImpersonation` vom Serveradministrator festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen in mehrdimensionalen Modellen](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
