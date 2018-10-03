---
title: Quelle auswählen (SSIS-PaketUpgrade-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7d553bd07dd72ec136c5ec449f67b84dea2d6c57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228534"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a>Quellspeicherort auswählen (SSIS Paketupgrade-Assistent)
  Mithilfe der Seite **Quellspeicherort auswählen** geben Sie die Quelle an, aus der Pakete aktualisiert werden sollen.  
  
> [!NOTE]  
>  Diese Seite ist nur verfügbar, wenn Sie den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Paketupgrade-Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder an der Eingabeaufforderung ausführen.  
  
 **So führen Sie den SSIS Paketupgrade-Assistenten aus**  
  
-   [Aktualisieren von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Statische Optionen  
 **Paketquelle**  
 Wählen Sie den Speicherort aus, der die zu aktualisierenden Pakete enthält. Für diese Option sind die in der folgenden Tabelle aufgeführten Werte verfügbar.  
  
|value|Description|  
|-----------|-----------------|  
|**Dateisystem**|Gibt an, dass sich die zu aktualisierenden Pakete in einem Ordner auf dem lokalen Computer befinden.<br /><br /> Die ursprünglichen Pakete müssen im Dateisystem gespeichert sein, damit der Assistent die ursprünglichen Pakete vor deren Upgrade sichern kann. Weitere Informationen finden Sie in den Vorgehensweisen zu diesem Thema.|  
|**SSIS-Paketspeicher**|Gibt an, dass sich die zu aktualisierenden Pakete im Paketspeicher befinden. Der Paketspeicher besteht aus dem Satz von Dateisystemordnern, die vom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst verwaltet werden. Weitere Informationen finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](service/package-management-ssis-service.md).<br /><br /> Bei Auswahl dieses Werts werden die entsprechenden dynamischen Optionen **Paketquelle** angezeigt.|  
|**Microsoft SQL Server**|Gibt an, dass die zu aktualisierenden Pakete aus einer vorhandenen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]stammen.<br /><br /> Bei Auswahl dieses Werts werden die entsprechenden dynamischen Optionen **Paketquelle** angezeigt.|  
  
 **Ordner**  
 Geben Sie den Namen eines Ordners ein, in dem die zu aktualisierenden Pakete enthalten sind, oder klicken Sie auf **Durchsuchen** , und suchen Sie den Ordner.  
  
 **Durchsuchen**  
 Suchen Sie nach dem Ordner, der die zu aktualisierenden Pakete enthält.  
  
## <a name="package-source-dynamic-options"></a>Dynamische Paketquellenoptionen  
  
### <a name="package-source--ssis-package-store"></a>Paketquelle = SSIS-Paketspeicher  
 **Server**  
 Geben Sie den Namen des Servers ein, auf dem die zu aktualisierenden Pakete gespeichert sind, oder wählen Sie diesen Server aus der Liste aus.  
  
### <a name="package-source--microsoft-sql-server"></a>Paketquelle = Microsoft SQL Server  
 **Server**  
 Geben Sie den Namen des Servers ein, auf dem die zu aktualisierenden Pakete gespeichert sind, oder wählen Sie diesen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Wählen Sie diese Option aus, um für die Herstellung einer Verbindung mit dem Server die Windows-Authentifizierung zu verwenden.  
  
 **SQL Server-Authentifizierung verwenden**  
 Wählen Sie diese Option aus, um für die Herstellung einer Verbindung mit dem Server die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung zu verwenden. Wenn Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, den die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwendet, um eine Verbindung mit dem Server herzustellen.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, das die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwendet, um eine Verbindung mit dem Server herzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Integration Services-Paketen](install-windows/upgrade-integration-services-packages.md)  
  
  
