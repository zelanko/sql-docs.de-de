---
title: Analysis Services-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2018
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 5c1280a60cf7c53454ab77da6fed58fd09902748
ms.sourcegitcommit: 29760037d0a3cec8b9e342727334cc3d01db82a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50411760"
---
# <a name="analysis-services-connection-manager"></a>Analysis Services-Verbindungs-Manager
  Mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager kann ein Paket eine Verbindung mit einem Server herstellen, auf dem eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank ausgeführt wird, oder mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt herstellen, das den Zugriff auf Cube- und Dimensionsdaten ermöglicht. Die Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt ist nur beim Entwickeln von Paketen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]möglich. Zur Laufzeit stellen Pakete eine Verbindung mit dem Server und der Datenbank her, für den bzw. die Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitgestellt haben.  
  
 Für Tasks, wie z. B. den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen und den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verarbeitungstask, und Ziele, wie z. B. das Ziel Data Mining-Modelltraining, wird ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager verwendet.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken finden Sie unter [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Konfiguration des Analysis Services-Verbindungs-Managers  
 Wenn Sie einem Paket einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der Sammlung **Verbindungen** im Paket den Verbindungs-Manager hinzufügt. Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **MSOLAP100**festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager zu konfigurieren:  
  
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des Microsoft OLE DB-Anbieters für Analysis Services-Anbieter erfüllt.  
  
-   Geben Sie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt an, mit der bzw. dem eine Verbindung hergestellt werden soll.  
  
-   Wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]herstellen, geben Sie den Authentifizierungsmodus an.  

> [!NOTE]    
>  Wenn Sie SSIS in Azure Data Factory (ADF) verwenden und eine Verbindung mit der Azure Analysis Services-Instanz (AAS) herstellen möchten, können Sie kein Konto verwenden, für das die mehrstufige Authentifizierung aktiviert ist, sondern müssen auf einen Dienstprinzipal zurückgreifen. Informationen zum Erstellen eines solchen Dienstprinzipals, zum **Verwenden eines bestimmten Benutzernamen und Kennworts** für die Anmeldung bei Ihrem Server über den Verbindungs-Manager und zum Eingeben Ihrer Anwendungs-ID bzw. Ihres Schlüssels als Benutzername bzw. als Kennwort finden Sie [hier](https://docs.microsoft.com/en-us/azure/analysis-services/analysis-services-service-principal). Anschließend müssen Sie die erforderlichen Clientbibliotheken über ein benutzerdefiniertes Setup für Azure-SSIS Integration Runtime installieren. Weitere Informationen finden Sie im Beispiel **AAS** unter [Anpassen des Setups für Azure-SSIS Integration Runtime](https://docs.microsoft.com/en-us/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).
  
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Referenz zur Benutzeroberfläche des Dialogfelds Analysis Services-Verbindungs-Manager hinzufügen](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und unter [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)möglich.  
  
  
