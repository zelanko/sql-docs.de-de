---
title: Legen Sie die Eigenschaften eines Verbindungs-Managers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], modifying
- modifying connection managers
ms.assetid: 54793114-2198-4d80-8091-e241d5a5d13c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 92ac3366a2473fb92fe33dcf884d3806c65e8609
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62885394"
---
# <a name="set-the-properties-of-a-connection-manager"></a>Festlegen der Eigenschaften eines Verbindungs-Managers
  Alle Verbindungs-Manager können im Fenster **Eigenschaften** konfiguriert werden.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält auch benutzerdefinierte Dialogfelder zum Ändern verschiedener Typen des Verbindungs-Managers in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Das Dialogfeld enthält je nach Typ des Verbindungs-Managers verschiedene Gruppen mit Optionen.  
  
### <a name="to-modify-a-connection-manager-using-the-properties-window"></a>So ändern Sie einen Verbindungs-Manager mithilfe des Eigenschaftenfensters  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im SSIS-Designer auf die Registerkarte **Ablaufsteuerung** , die Registerkarte **Datenfluss** oder die Registerkarte **Ereignishandler** , um den Bereich **Verbindungs-Manager** verfügbar zu machen.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Verbindungs-Manager, und klicken Sie dann auf **Eigenschaften**.  
  
5.  Ändern Sie im Fenster **Eigenschaften** die Eigenschaftswerte. Das Fenster **Eigenschaften** bietet Zugriff auf einige Eigenschaften, die im Standard-Editor für einen Verbindungs-Manager nicht konfigurierbar sind.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-modify-a-connection-manager-using-a-connection-manager-dialog-box"></a>So ändern Sie einen Verbindungs-Manager mithilfe des Dialogfelds Verbindungs-Manager  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Ablaufsteuerung** , **Datenfluss** oder **Ereignishandler** , um den Bereich **Verbindungs-Manager** anzuzeigen.  
  
4.  Doppelklicken Sie im Bereich **Verbindungs-Manager** auf den Verbindungs-Manager, um das Dialogfeld **Verbindungs-Manager** zu öffnen. Informationen über bestimmte Verbindungs-Manager-Typen und die für jeden Typ verfügbaren Optionen finden Sie in der folgenden Tabelle.  
  
    |Ziel-Editor für Dimensionsverarbeitung|Optionen|  
    |------------------------|-------------|  
    |[ADO-Verbindungs-Manager](connection-manager/ado-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md)|[ADO.NET-Verbindungs-Manager konfigurieren](configure-ado-net-connection-manager.md)|  
    |[Analysis Services-Verbindungs-Manager](connection-manager/analysis-services-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Analysis Services-Verbindungs-Manager hinzufügen“](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Excel-Verbindungs-Manager](connection-manager/excel-connection-manager.md)|[Verbindungs-Manager-Editor für Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)|[Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Verbindungs-Manager für mehrere Dateien](connection-manager/multiple-files-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Dateiverbindungs-Manager hinzufügen“](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Verbindungs-Manager für Flatfiles](connection-manager/flat-file-connection-manager.md)|[Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Erweitert&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Verbindungs-Manager für mehrere Flatfiles](connection-manager/multiple-flat-files-connection-manager.md)|[Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Allgemein“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Spalten“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[FTP-Verbindungs-Manager](connection-manager/ftp-connection-manager.md)|[FTP-Verbindungs-Manager-Editor](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[HTTP-Verbindungs-Manager](connection-manager/http-connection-manager.md)|[HTTP-Verbindungs-Manager-Editor &#40;Seite „Server“&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [HTTP-Verbindungs-Manager-Editor &#40;Seite „Proxy“&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[MSMQ-Verbindungs-Manager](connection-manager/msmq-connection-manager.md)|[MSMQ-Verbindungs-Manager-Editor](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[ODBC-Verbindungs-Manager](connection-manager/odbc-connection-manager.md)|[ODBC-Verbindungs-Manager: Referenz zur Benutzeroberfläche](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)|[SMO-Verbindungs-Manager-Editor](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[SMTP-Verbindungs-Manager](connection-manager/smtp-connection-manager.md)|[SMTP-Verbindungs-Manager-Editor](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[SQL Server Compact Edition-Verbindungs-Manager](connection-manager/sql-server-compact-edition-connection-manager.md)|[Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Verbindung“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Alle“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md)|[WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](connection-manager/integration-services-ssis-connections.md)   
 [Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
  
