---
title: Analysis Services-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: acfcf4bc17644c44fc5693527e42f0de40054aa8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769212"
---
# <a name="analysis-services-connection-manager"></a>Analysis Services-Verbindungs-Manager
  Mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager kann ein Paket eine Verbindung mit einem Server herstellen, auf dem eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank ausgeführt wird, oder mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt herstellen, das den Zugriff auf Cube- und Dimensionsdaten ermöglicht. Die Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt ist nur beim Entwickeln von Paketen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]möglich. Zur Laufzeit stellen Pakete eine Verbindung mit dem Server und der Datenbank her, für den bzw. die Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitgestellt haben.  
  
 Für Tasks, wie z. B. den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen und den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verarbeitungstask, und Ziele, wie z. B. das Ziel Data Mining-Modelltraining, wird ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager verwendet.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken finden Sie unter [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Konfiguration des Analysis Services-Verbindungs-Managers  
 Beim Hinzufügen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Verbindungs-Manager einem Paket [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der als aufgelöst wird erstellt eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zur Laufzeit, des Verbindungs-Manager-Eigenschaften festlegt, und fügt den Verbindungs-Manager die `Connections` -Sammlung im Paket. Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `MSOLAP100` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager zu konfigurieren:  
  
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des Microsoft OLE DB-Anbieters für Analysis Services-Anbieter erfüllt.  
  
-   Geben Sie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt an, mit der bzw. dem eine Verbindung hergestellt werden soll.  
  
-   Wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]herstellen, geben Sie den Authentifizierungsmodus an.  
  
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Referenz zur Benutzeroberfläche des Dialogfelds Analysis Services-Verbindungs-Manager hinzufügen](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und unter [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)möglich.  
  
  
