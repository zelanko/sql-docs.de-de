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
manager: craigg
ms.openlocfilehash: ed652c47be4bfbe2783f5138bb80f8ed9c37dd32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072306"
---
# <a name="new-database-dialog-box-analysis-services"></a>Neue Datenbank (Dialogfeld) (Analysis Services)
  Mithilfe des Dialogfelds **Neue Datenbank** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie eine neue, leere [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank erstellen. Zum Anzeigen des Dialogfelds **Neue Datenbank** klicken Sie mit der rechten Maustaste auf den Ordner **Datenbanken** einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] im **Objekt-Explorer** , und wählen Sie anschließend **Neue Datenbank**aus.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Datenbankname**|Geben Sie den Namen der neuen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
|**Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitsanmeldeinformationen eines angegebenen Benutzerkontos verwendet. Die angegebenen Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Out-of-Line-Bindungen, lokale Cubes, Miningmodelle, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Für DMX OPENQUERY-Anweisungen werden jedoch die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Benutzername**|Geben Sie die Domäne und den Namen des Benutzerkontos ein, dass von der ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank verwendet werden soll. Verwenden Sie das folgende Format:<br /><br /> Domänen **\\** Name>* \<Benutzerkonto Name>* * \<*<br /><br /> Hinweis: Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.|  
|**Kennwort**|Geben Sie das Kennwort für das Benutzerkonto ein, das unter **Benutzername**angegeben ist.|  
|**Dienst Konto verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank die Sicherheitseinstellungen verwendet, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst zugeordnet sind, der die Datenbank verwaltet. Die Dienstkonto-Anmeldeinformationen werden für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle verwendet. Bei DMX OPENQUERY-Anweisungen, lokalen Cubes und Miningmodellen werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Out-of-Line-Bindungen nicht unterstützt.|  
|**Anmelde Informationen des aktuellen Benutzers verwenden**|Wählen Sie diese Option aus, damit die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank für Out-of-Line-Bindungen, DMX OPENQUERY-Anweisungen, lokale Cubes und Miningmodelle die Sicherheitsanmeldeinformationen des aktuellen Benutzers verwendet. Diese Option wird für Verarbeitungsvorgänge, ROLAP-Abfragen, Remotepartitionen, verknüpfte Objekte und Synchronisierungen vom Ziel zur Quelle nicht unterstützt.|  
|**Vorgegebene**|Wählen Sie diese Option aus, um die Anmeldeinformationen des Standardbenutzerkontos für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu verwenden. Bei dieser Option werden die Standardeinstellungen für die Datenbank zum Verarbeiten von Objekten, Synchronisieren von Servern und Ausführen der Data Mining-Abfragen vom Typ **Open Query** verwendet. Weitere Informationen zum Angeben der Standardeinstellungen auf Datenbankebene finden Sie unter [Festlegen von Eigenschaften für mehrdimensionale Datenbanken &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md).<br /><br /> Standardmäßig ist `DataSourceImpersonationInfo` die-Daten Bank Eigenschaft auf **das Dienst Konto**festgelegt. Unabhängig vom Wert der Eigenschaft `DataSourceImpersonationInfo` werden für Out-of-Line-Bindungen, ROLAP-Abfragen, lokale Cubes und Data Mining-Modelle die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Beschreibung**|Geben Sie die Beschreibung für die neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank ein.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mehrdimensionale Modell Datenbanken &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
