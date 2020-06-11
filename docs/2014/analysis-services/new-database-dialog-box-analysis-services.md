---
title: Dialog Feld ' neue Datenbank ' (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.newdatabase.f1
ms.assetid: ddc7804b-acb0-4ae4-a88f-e8cdf704c341
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07eeee6136965671b000923dc3f240de06ce0bd0
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541192"
---
# <a name="new-database-dialog-box-analysis-services"></a>Neue Datenbank (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Neue Datenbank** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie eine neue, leere [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank erstellen. Zum Anzeigen des Dialogfelds **Neue Datenbank** klicken Sie mit der rechten Maustaste auf den Ordner **Datenbanken** einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] im **Objekt-Explorer** , und wählen Sie anschließend **Neue Datenbank**aus.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenbankname**|Geben Sie den Namen der neuen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
|**Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitsanmeldeinformationen eines angegebenen Benutzerkontos verwendet. Die angegebenen Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Out-of-Line-Bindungen, lokale Cubes, Miningmodelle, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Für DMX OPENQUERY-Anweisungen werden jedoch die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Benutzername**|Geben Sie die Domäne und den Namen des Benutzerkontos ein, dass von der ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank verwendet werden soll. Verwenden Sie das folgende Format:<br /><br /> *\<Domain name>* **\\** *\<User account name>*<br /><br /> Hinweis: Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.|  
|**Kennwort**|Geben Sie das Kennwort für das Benutzerkonto ein, das unter **Benutzername**angegeben ist.|  
|**Dienstkonto verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitseinstellungen verwendet, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst zugeordnet sind, der die Datenbank verwaltet. Die Dienstkonto-Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Bei DMX OPENQUERY-Anweisungen, lokalen Cubes und Miningmodellen werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Out-of-Line-Bindungen nicht unterstützt.|  
|**Anmeldeinformationen des aktuellen Benutzers verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank für Out-of-Line-Bindungen, DMX OPENQUERY-Anweisungen, lokale Cubes und Miningmodelle die Sicherheitsanmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle nicht unterstützt.|  
|**Standard**|Wählen Sie diese Option aus, um die Anmeldeinformationen des Standardbenutzerkontos für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu verwenden. Bei dieser Option werden die Standardeinstellungen für die Datenbank zum Verarbeiten von Objekten, Synchronisieren von Servern und Ausführen der Data Mining-Abfragen vom Typ **Open Query** verwendet. Weitere Informationen zum Angeben der Standardeinstellungen auf Datenbankebene finden Sie unter [Festlegen von Eigenschaften für mehrdimensionale Datenbanken &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md).<br /><br /> Standardmäßig ist die- `DataSourceImpersonationInfo` Daten Bank Eigenschaft auf **das Dienst Konto**festgelegt. Unabhängig vom Wert der Eigenschaft `DataSourceImpersonationInfo` werden für Out-of-Line-Bindungen, ROLAP-Abfragen, lokale Cubes und Data Mining-Modelle die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Beschreibung**|Geben Sie die Beschreibung für die neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
