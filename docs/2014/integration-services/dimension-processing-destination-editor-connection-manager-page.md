---
title: Ziel-Editor für Dimensions Verarbeitung (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c34da1807f405c25ec071bb94232c3647b7efecd
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429467"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>Ziel-Editor für Dimensionsverarbeitung (Seite Verbindungs-Manager)
  Verwenden Sie die Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für Dimensionsverarbeitung**, um eine Verbindung mit einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekt oder einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz anzugeben.  
  
 Weitere Informationen zum Ziel für Dimensionsverarbeitung finden Sie unter [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Optionen  
 **Verbindungs-Manager**  
 Wählen Sie einen vorhandenen Verbindungs-Manager aus der Liste aus, oder klicken Sie auf **Neu** , um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Analysis Services-Verbindungs-Manager hinzufügen** eine neue Verbindung.  
  
 **Liste der verfügbaren Dimensionen**  
 Wählen Sie die zu verarbeitende Dimension aus.  
  
 **Verarbeitungsmethode**  
 Wählen Sie die Verarbeitungsmethode aus, die auf die in der Liste ausgewählte Dimension angewendet werden soll. Der Standardwert für diese Option ist **Vollständig**.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Hinzufügen (inkrementell)**|Führt eine inkrementelle Verarbeitung der Dimension aus.|  
|**Vollständig**|Führt eine vollständige Verarbeitung der Dimension aus.|  
|**Update**|Führt eine Verarbeitung der Updates für die Dimension aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Dimensions Verarbeitung &#40;Seite Zuordnungen&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [Ziel-Editor für Dimensionsverarbeitung &#40;Seite „Erweitert“&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
