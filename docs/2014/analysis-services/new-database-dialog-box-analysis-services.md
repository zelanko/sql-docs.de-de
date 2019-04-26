---
title: Neue Datenbank (Dialogfeld) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.newdatabase.f1
ms.assetid: ddc7804b-acb0-4ae4-a88f-e8cdf704c341
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bef5adba44a5202e3cc0fc7f2eb48fae08a0e3c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743717"
---
# <a name="new-database-dialog-box-analysis-services"></a>Neue Datenbank (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Neue Datenbank** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie eine neue, leere [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank erstellen. Zum Anzeigen des Dialogfelds **Neue Datenbank** klicken Sie mit der rechten Maustaste auf den Ordner **Datenbanken** einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] im **Objekt-Explorer**, und wählen Sie anschließend **Neue Datenbank** aus.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenbankname**|Geben Sie den Namen der neuen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
|**Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitsanmeldeinformationen eines angegebenen Benutzerkontos verwendet. Die angegebenen Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Out-of-Line-Bindungen, lokale Cubes, Miningmodelle, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Für DMX OPENQUERY-Anweisungen werden jedoch die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Benutzername**|Geben Sie die Domäne und den Namen des Benutzerkontos ein, dass von der ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank verwendet werden soll. Verwenden Sie folgendes Format:<br /><br /> *\<Domänenname >* **\\**  *\<Benutzerkontonamen >*<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn **bestimmten Benutzernamen und bestimmtes Kennwort** ausgewählt ist.|  
|**Kennwort**|Geben Sie das Kennwort für das Benutzerkonto ein, das unter **Benutzername**angegeben ist.|  
|**Dienstkonto verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitseinstellungen verwendet, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst zugeordnet sind, der die Datenbank verwaltet. Die Dienstkonto-Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Bei DMX OPENQUERY-Anweisungen, lokalen Cubes und Miningmodellen werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Out-of-Line-Bindungen nicht unterstützt.|  
|**Anmeldeinformationen des aktuellen Benutzers verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank für Out-of-Line-Bindungen, DMX OPENQUERY-Anweisungen, lokale Cubes und Miningmodelle die Sicherheitsanmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle nicht unterstützt.|  
|**Default**|Wählen Sie diese Option aus, um die Anmeldeinformationen des Standardbenutzerkontos für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu verwenden. Bei dieser Option werden die Standardeinstellungen für die Datenbank zum Verarbeiten von Objekten, Synchronisieren von Servern und Ausführen der Data Mining-Abfragen vom Typ **Open Query** verwendet. Weitere Informationen zum Angeben der Standardeinstellungen auf Datenbankebene finden Sie unter [Festlegen von Eigenschaften für mehrdimensionale Datenbanken &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md).<br /><br /> Standardmäßig die `DataSourceImpersonationInfo` Datenbank-Eigenschaftensatz auf **Dienstkonto**. Unabhängig vom Wert der Eigenschaft `DataSourceImpersonationInfo` werden für Out-of-Line-Bindungen, ROLAP-Abfragen, lokale Cubes und Data Mining-Modelle die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Beschreibung**|Geben Sie die Beschreibung für die neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
