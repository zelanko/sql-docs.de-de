---
description: Analysis Services-Verbindungs-Manager
title: Analysis Services-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/25/2019
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 633dd8288a9168422d0e5187caa1265615911a8a
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130612"
---
# <a name="analysis-services-connection-manager"></a>Analysis Services-Verbindungs-Manager

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Verbindungs-Manager kann ein Paket eine Verbindung mit einem Server herstellen, auf dem eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank ausgeführt wird. Außerdem kann damit eine Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekt hergestellt werden, das den Zugriff auf Cube- und Dimensionsdaten ermöglicht. Die Verbindung mit einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt ist nur beim Entwickeln von Paketen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]möglich. Zur Laufzeit stellen Pakete eine Verbindung mit dem Server und der Datenbank her, für den bzw. die Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitgestellt haben.  
  
 Für Tasks, wie z. B. den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Task DDL ausführen und den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verarbeitungstask, und Ziele, wie z. B. das Ziel Data Mining-Modelltraining, wird ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager verwendet.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken finden Sie unter [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](/analysis-services/multidimensional-models/multidimensional-model-databases-ssas).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Konfiguration des Analysis Services-Verbindungs-Managers  
 Wenn Sie einem Paket einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit als [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der Sammlung **Verbindungen** im Paket den Verbindungs-Manager hinzufügt. Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **MSOLAP100** festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Verbindungs-Manager zu konfigurieren:  
  
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des Microsoft OLE DB-Anbieters für Analysis Services-Anbieter erfüllt.  
  
-   Geben Sie die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt an, mit der bzw. dem eine Verbindung hergestellt werden soll.  
  
-   Wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]herstellen, geben Sie den Authentifizierungsmodus an.  

> [!NOTE]    
>  Wenn Sie SSIS in Azure Data Factory (ADF) verwenden und eine Verbindung mit der Azure Analysis Services-Instanz (AAS) herstellen möchten, können Sie kein Konto verwenden, für das die mehrstufige Authentifizierung aktiviert ist, sondern müssen auf ein Konto zurückgreifen, das keine Interaktivität/MFA bzw. keinen Dienstprinzipal erfordert. Wenn Sie Letzteres verwenden möchten, finden Sie [hier](/azure/analysis-services/analysis-services-service-principal) Informationen zum Erstellen und zum Zuweisen der Serveradministratorrolle. Wählen Sie anschließend **SQL Server-Authentifizierung verwenden** aus, um sich im Verbindungs-Manager beim Server anzumelden, und geben Sie abschließend `User name: app:YourApplicationID` und `Password: YourAuthorizationKey` ein.
  
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Referenz zur Benutzeroberfläche des Dialogfelds „Analysis Services-Verbindungs-Manager hinzufügen“](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
