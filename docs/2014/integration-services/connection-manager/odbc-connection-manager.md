---
title: ODBC-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 701ea85cafc22d9ea850e18310c3c2d06748cb08
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438357"
---
# <a name="odbc-connection-manager"></a>ODBC-Verbindungs-Manager
  Mit einem ODBC-Verbindungs-Manager kann ein Paket eine Verbindung mit einer Reihe von Datenbank-Managementsystemen mithilfe der ODBC-Spezifikation (Open Database Connectivity) herstellen.  
  
 Wenn Sie einem Paket eine ODBC-Verbindung hinzufügen und die Eigenschaften des Verbindungs-Managers festlegen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt einen Verbindungs-Manager und fügt der-Auflistung des Pakets den Verbindungs-Manager hinzu `Connections` . Zur Laufzeit wird der Verbindungs-Manager als physische ODBC-Verbindung aufgelöst.  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `ODBC` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den ODBC-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie eine Verbindungszeichenfolge an, die auf einen Benutzer- oder System-Datenquellennamen verweist.  
  
-   Geben Sie den Server für die Verbindungsherstellung an.  
  
-   Geben Sie an, ob die Verbindung zur Laufzeit beibehalten wird.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Konfiguration des ODBC-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [ODBC-Verbindungs-Manager: Referenz zur Benutzeroberfläche](../odbc-connection-manager-ui-reference.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](integration-services-ssis-connections.md)  
  
  
