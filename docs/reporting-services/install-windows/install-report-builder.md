---
title: Installieren des Berichts-Generators | Microsoft-Dokumentation
description: Der Berichts-Generator ist eine eigenständige App, die von Ihnen oder einem Administrator auf dem Computer installiert wird.
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ca0071416491700254047b43056d32fc64ed1d9d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97425129"
---
# <a name="install-report-builder"></a>Installieren des Berichts-Generators

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] ist eine eigenständige App, die von Ihnen oder einem Administrator auf dem Computer installiert wird. Sie können sie über das Microsoft Download Center, über einen [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] -Berichtsserver oder über eine in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]integrierte SharePoint-Website installieren.  

> [!NOTE]
> Sie sind auf der Suche nach Informationen zur Installation von Power BI Report Builder? Wechseln Sie zur [Microsoft Power BI Report Builder](https://www.microsoft.com/download/details.aspx?id=58158)-Seite im Download Center. 

 In der Regel installiert und konfiguriert ein Administrator [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], gewährt die Berechtigung zum Herunterladen des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] s vom Webportal und verwaltet Ordner und Berechtigungen für auf dem Berichtsserver gespeicherte Berichte, Berichtsteile und freigegebene Datasets. Weitere Informationen zur Verwaltung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Reporting Services-Berichtsserver (einheitlicher Modus)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md).  
  
## <a name="install-ssrbnoversion-from--a--web-portal-or-sharepoint-library"></a>Installieren des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] s über ein Webportal oder die SharePoint-Bibliothek 

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.
  
 Sie können den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] von einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Webportal oder von einer in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]integrierten SharePoint-Website aus starten. Informationen finden Sie unter [Starten des Berichts-Generators](../../reporting-services/report-builder/start-report-builder.md).  

::: moniker range="=sql-server-2016"
  
### <a name="sharepoint-site-integrated-with-ssrsnoversion"></a>In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]
  
 Wenn auf einer in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]integrierten SharePoint-Website das Menü **Neues Dokument** die Optionen **Berichts-Generator-Bericht**, **Berichts-Generator-Modell** und **Berichtsdatenquelle** nicht enthält, müssen der SharePoint-Bibliothek die entsprechenden Inhaltstypen hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen von Reporting Services-Inhaltstypen zu einer SharePoint-Bibliothek](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  

::: moniker-end
 
## <a name="install-ssrbnoversion-with-microsoft-endpoint-configuration-manager"></a>Installieren des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] mit Microsoft Endpoint Configuration Manager 
  
 Administratoren können auch Software wie Microsoft Endpoint Configuration Manager verwenden, um das Programm auf Ihren Computer zu pushen. In der Dokumentation für die Software wird beschrieben, wie spezifische Software zur Installation des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]s verwendet wird. Weitere Informationen finden Sie in der [Dokumentation zu Microsoft Endpoint Configuration Manager](/configmgr/).  
  
> [!IMPORTANT]  
>  Die Sicherheitsfunktionen von Windows Vista und Windows 7 erfordern erweiterte Berechtigungen zum Ausführen von Befehlszeilenvorgängen. Auch wird die Angabe der Berechtigung zum Ausführen von Vorgängen über die Befehlszeile angefordert. Die Installation erfolgt nicht automatisch. Für eine unbeaufsichtigte Installation müssen Sie die Befehlszeile als Administrator ausführen.  
  
## <a name="system-requirements"></a>Systemanforderungen
  
 Informationen hierzu finden Sie im Abschnitt **Systemanforderungen** auf der [Downloadseite für den Berichts-Generator](https://go.microsoft.com/fwlink/?LinkID=734968) im Microsoft Download Center.
  
##  <a name="to-install-ssrbnoversion-from-the-download-site"></a><a name="download"></a> So installieren Sie den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] über die Downloadwebsite  
  
1.  Klicken Sie auf der [Berichts-Generator-Seite im Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=734968) auf **Herunterladen**.  
  
2.  Nachdem der [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] heruntergeladen wurde, klicken Sie auf **Ausführen**.  
  
     Dadurch wird der SQL Server-Assistent für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] gestartet.  
  
3.  Akzeptieren Sie die Bestimmungen im Lizenzvertrag, und klicken Sie auf **Weiter**.  
  
4.  Geben Sie optional auf der Seite **Standardzielserver** die URL zu dem Zielberichtsserver an, wenn nicht der Standardserver verwendet wird. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] mit einer Verbindung zu einem Berichtsserver verwenden möchten, geben Sie die URL zu dem Server jetzt an. Hierzu können Sie auch das Dialogfeld **Optionen** im [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] verwenden.  
  
5.  Klicken Sie auf **Installieren**, um die Installation des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]s abzuschließen.  
  
## <a name="to-install-ssrbnoversion-from-a-share"></a>So installieren Sie [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] über eine Freigabe  
  
1.  Informationen über den Speicherort der Datei „ReportBuilder.msi“, die zur Installation des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] auf dem lokalen Computer ausgeführt wird, erhalten Sie von Ihrem Administrator.  
  
2.  Suchen Sie „ReportBuilder.msi“, dem Windows Installer-Paket (MSI) für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)], und klicken Sie auf diese Datei.  
  
     Dadurch wird der SQL Server-Assistent für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] gestartet.  
  
3.  Schließen Sie die übrigen Schritte ab, die unter [So installieren Sie Berichts-Generator von der Downloadwebsite aus](#download)aufgeführt sind.  
  
## <a name="to-install-ssrbnoversion-from-the-command-line"></a>So installieren Sie [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] über die Befehlszeile 

 Sie können auch eine Befehlszeileninstallation des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]s ausführen und Argumente angeben, um die Installation anzupassen. Neben den systeminternen MSI-Standardparametern können Sie die benutzerdefinierten Parameter verwenden, die [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] bereitstellt: RBINSTALLDIR und RBSERVERURL. RBINSTALLDIR dient zum Angeben des Stamminstallationsordners für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]. Mit RBSERVERURL wird der Standardberichtsserver angegeben, der vom [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] zum Speichern von Berichten auf dem Server verwendet wird.  
  
 Wenn Sie eine vollständig automatische Installation ohne Eingriff über die Benutzeroberfläche durchführen möchten, geben Sie die Option **/quiet** an. Programmbedingt werden durch das Optionsflag "quiet" Installationsfehler unterdrückt. Deshalb wird bei Verwendung der Option „quiet“ die Angabe der Option **/l** empfohlen, die Protokollierung für diesen Fall angibt.   
  
1.  Klicken Sie auf der [Berichts-Generator-Seite im Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=734968)auf **Herunterladen**.  
  
2.  Nachdem der [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] heruntergeladen wurde, klicken Sie auf **Speichern**.  
  
3.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
4.  Geben Sie **Öffnen** im Feld **Öffnen** ein.  
  
5.  Navigieren Sie im Eingabeaufforderungsfenster zu dem Ordner, in dem Sie die Datei „ReportBuilder.msi“ gespeichert haben.  
  
6.  Geben Sie einen Befehl mit dem folgenden Format ein:  
  
     `msiexec/i ReportBuilder.msi OPTION=OptionValue [OPTION=OptionValue]`  
  
     Die beiden Optionen speziell für die Installation von [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] lauten: RBINSTALLDIR und RBSERVERURL. Diese Argumente müssen nicht unbedingt in der Befehlszeile angegeben werden. Der grundlegende Befehl lautet wie folgt:  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
7.  Drücken Sie die EINGABETASTE, um den Befehl auszuführen.  
  
## <a name="set-ssrbnoversion-defaults"></a>Festlegen von Standardwerten für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]  
  
-   Nach der Installation des [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)]s können Sie einige Standardoptionen festlegen. Klicken Sie auf **Datei** > **Optionen**.  
  
     Das Festlegen des standardmäßigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Webportals oder der SharePoint-Website ist besonders hilfreich. Weitere Informationen finden Sie unter [Set default options for Report Builder](../../reporting-services/report-builder/set-default-options-for-report-builder.md).  
  
-   Klicken Sie auf den **Berichts-Generator** .  
  
     Wenn der Berichtsserver nicht in der Liste vorhandener Server angezeigt wird, schließen Sie das Dialogfeld **Bericht öffnen**, und klicken Sie dann unten im Berichts-Generator **auf** Verbinden [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)], um eine Verbindung mit dem Server herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Berichts-Generators](../../reporting-services/report-builder/start-report-builder.md)   
 [Deinstallieren des Berichts-Generators](../../reporting-services/install-windows/uninstall-report-builder.md)  
  
