---
title: Dialog Feld ' Assemblyeigenschaften ' (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b21230ddff5a3db043b533a4f921a30b02da739b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062298"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Assemblyeigenschaften' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Assemblyeigenschaften** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Eigenschaften eines Assemblyverweises in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen. Zum Anzeigen des Dialogfelds **Assemblyeigenschaften** klicken Sie in **Objekt-Explorer** mit der rechten Maustaste auf eine Assembly und wählen die Option **Eigenschaften**aus.  
  
## <a name="options"></a>Optionen  
  
|Begriff|Definition|  
|----------|----------------|  
|**Name**|Hier können Sie durch eine Eingabe den Namen des Assemblyverweises ändern.<br /><br /> Hinweis: Durch Ändern dieses Werts wird der Name der Assembly, auf den der Assemblyverweis verweist, nicht geändert. Stattdessen wird der Name geändert, der von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder -Datenbank beim Verweisen auf den Assemblyverweis verwendet wird.|  
|**ID**|Zeigt den Bezeichner der Assembly an, auf den der Assemblyverweis verweist.|  
|**Beschreibung**|Hier können Sie per Eingabe die Beschreibung des Assemblyverweises ändern.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung des Assemblyverweises an.|  
|**Letztes Schemaupdate**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für den Assemblyverweis an.|  
|**Typ**|Zeigt den Typ des Assemblyverweises an. Folgende Werte werden angezeigt:<br /><br /> **.NET-Assembly**: der Assemblyverweis [!INCLUDE[msCoName](../includes/msconame-md.md)] verweist auf eine .NET Framework Assembly.<br /><br /> **Com-dll**: der Assemblyverweis verweist auf eine COM-Bibliothek.|  
|**Quelle**|Zeigt die Quelle des Assemblyverweises an. Diese Eigenschaft enthält in der Regel den vollständigen Pfad und den Dateinamen der Assembly, auf die der Assemblyverweis verweist.|  
|**Berechtigungssatz**|Wählen Sie den Berechtigungssatz aus, mit dem der Zugriff auf den Assemblyverweis bestimmt werden soll. Weitere Informationen zu den verfügbaren Werten für diese Eigenschaft finden Sie unter <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Identitätswechselinformationen**|Wählen Sie die Identitätswechselinformationen aus, die beim Zugreifen auf den Assemblyverweis verwendet werden sollen. Weitere Informationen zu den verfügbaren Werten für diese Eigenschaft finden Sie unter [ImpersonationInfo-Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verwaltung von mehrdimensionalen Modellassemblys](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
