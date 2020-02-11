---
title: Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07da79ea46ca0e9e23abb7197730821d8c31bfa8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66100011"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a>Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält mehrere Befehlszeilen-Hilfsprogramme, die Sie zum Verwalten eines Berichts Servers verwenden können. Diese Hilfsprogramme werden beim Installieren eines Berichtsservers automatisch installiert.  
  
|Name|Befehlsdatei|Unterstützter Bereitstellungsmodus|BESCHREIBUNG|  
|----------|------------------|-------------------------------|-----------------|  
|RSS-Hilfsprogramm|rs.exe|Einheitlicher Modus und SharePoint-Modus. In der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Version wurde die SharePoint-Modusunterstützung eingeführt.|Das [rs-Hilfsprogramm](rs-exe-utility-ssrs.md) ist ein Skripthost, den Sie zum Ausführen von Skriptvorgängen verwenden können. Führen Sie mit diesem Tool [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Skripts aus, die Daten zwischen Berichtsserver-Datenbanken kopieren, Berichte veröffentlichen, Elemente in einer Berichtsserver-Datenbank erstellen usw. Weitere Informationen zur Verwendung von Scripts in der Severadministration finden Sie unter [Skripts für Bereitstellungs- und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md).|  
|PowerShell-Cmdlets||Nur SharePoint|Eine Liste der PowerShell-Cmdlets finden Sie unter [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|  
|rsconfig (Hilfsprogramm)|rsconfig.exe|Nur systemeigen|Mit dem [rsconfig-Hilfsprogramm](rsconfig-utility-ssrs.md) können Sie eine Berichtsserververbindung zur Berichtsserver-Datenbank konfigurieren und verwalten. Darüber hinaus können Sie damit ein Benutzerkonto für die unbeaufsichtigte Berichtsverarbeitung angeben. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../report-server/reporting-services-report-server-native-mode.md). Weitere Informationen zur Verbindungskonfiguration finden Sie unter [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank (SSRS-Konfigurations-Manager)](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Hilfsprogramm rskeymgmt|rskeymgmt.exe|Nur systemeigen|Das [rskeymgmt-Hilfsprogramm](rskeymgmt-utility-ssrs.md) ist ein Verwaltungstool für Verschlüsselungsschlüssel. Mit diesem Programm können Sie symmetrische Schlüssel sichern, anwenden, neu erstellen und löschen. Außerdem können Sie mit diesem Tool eine Berichtsserverinstanz an eine freigegebene Berichtsserver-Datenbank anfügen. Rskeymgmt kann bei Wiederherstellungsvorgängen für Datenbanken verwendet werden. Sie können eine vorhandene Datenbank in einer neuen Installation erneut verwenden, indem Sie eine Sicherungskopie des symmetrischen Schlüssels anwenden. Wenn die Schlüssel nicht wiederhergestellt werden können, bietet das Tool eine Möglichkeit zum Löschen nicht mehr benötigter verschlüsselter Inhalte. Weitere Informationen über das Verwalten von Schlüsseln und das Speichern sensibler Daten finden Sie unter [Speichern verschlüsselter Berichtsserverdaten (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) und [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
  
> [!NOTE]  
>  Wenn Sie ein Tool mit einer grafischen Benutzeroberfläche bevorzugen, können Sie anstelle von `rsconfig` und `rskeymgmt` den Reporting Services-Konfigurations-Manager verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services-Tools](reporting-services-tools.md)   
 [Reporting Services-Berichtsserver (einheitlicher Modus)](../report-server/reporting-services-report-server-native-mode.md)  
  
  
