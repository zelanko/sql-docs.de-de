---
title: Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c454dece75264c08d4f4bdc9f9549a1ef0f9b932
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418881"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Aktivieren und Deaktivieren des clientseitige Drucks für Reporting Services
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX-Steuerelement, **RSClientPrint**, bietet eine clientseitige Druckfunktion für Berichte in einem Browser angezeigt. Vom Steuerelement wird ein benutzerdefiniertes Dialogfeld zum Drucken angezeigt, das die Funktionen enthält, die in Druckdialogfeldern üblicherweise vorkommen. Dazu zählen Druckvorschau, Seitenauswahl zum Angeben bestimmter Seiten und Bereiche, Seitenränder und Ausrichtung. Clientseitiges Drucken ist standardmäßig aktiviert, Sie können diese Funktion jedoch auf Wunsch deaktivieren.  
  
> [!NOTE]  
>  Zum Herunterladen von ActiveX-Steuerelementen sind Administratorberechtigungen erforderlich.  
  
## <a name="downloading-the-activex-control"></a>Herunterladen des ActiveX-Steuerelements  
 Benutzer, die die Druckfunktion verwenden möchten, müssen das ActiveX-Steuerelement, von dem die Clientdruckfunktionalität bereitgestellt wird, herunterladen und installieren. Zum ersten Mal ein Benutzer klickt der **Drucker** Symbol auf der Berichtssymbolleiste, die Microsoft ActiveX Control wird auf den Computer heruntergeladen. Nachdem das Steuerelement heruntergeladen wurde, die **Drucken** im Dialogfeld angezeigt, wenn der Benutzer klickt auf die **Drucker** Symbol.  
  
 Abhängig von den Browsereinstellungen bestehen folgende Möglichkeiten: Der Benutzer wird zur Installation des Steuerelements aufgefordert, die Installation des Steuerelements wird verhindert, oder das Steuerelement wird unbeaufsichtigt im Hintergrund installiert.  
  
 Für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, Einstellungen, die ActiveX-Steuerelement herunterladen installieren und werden angegeben, über die **-ActiveX-Steuerelemente und Plug-Ins** Knoten in der **Sicherheitseinstellungen** Seite die Webinhaltszone. Von folgenden Einstellungen wird bestimmt, ob Benutzer das Druckensteuerelement herunterladen und ausführen können. Das Verhalten basiert auf Einstellungen der Webzonensicherheit:  
  
-   Download von signierten ActiveX-Steuerelementen.  
  
-   ActiveX-Steuerelemente ausführen, die für die Skripterstellung sicher sind.  
  
-   ActiveX-Steuerelemente und Plug-Ins ausführen.  
  
 Benutzer, die zu verwendende **RSClientPrint** des clientseitigen Druckens ausführen müssen, aktivieren die folgenden:  
  
-   **Download von signierten ActiveX-Steuerelementen** und **Skript ActiveX-Steuerelement sicher für Skripting markiert** zu Installationszwecken.  
  
-   **Ausführen von ActiveX-Steuerelemente und Plug-Ins** für fortlaufende Druckvorgänge.  
  
 Die **RSClientPrint** ActiveX-Steuerelement ist signiert, d. h., er enthält ein gültiges digitales Zertifikat vom [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="enabling-and-disabling-client-side-printing"></a>Aktivieren und Deaktivieren des clientseitigen Druckens  
 Berichtsserveradministratoren können die Druckfunktion deaktivieren, indem Sie die Berichtsserver-Systemeigenschaft festlegen **EnableClientPrinting** zu `false`. Dadurch wird das clientseitige Drucken für alle von diesem Server verwalteten Berichte deaktiviert. In der Standardeinstellung **EnableClientPrinting** nastaven NA hodnotu `true`. Sie können das clientseitige Drucken folgendermaßen deaktivieren:  
  
-   Für einen **Berichtsserver im einheitlichen Modus**:  
  
    1.  Starten Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorrechten.  
  
    2.  Stellen Sie eine Verbindung mit einer Berichtsserverinstanz in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]her.  
  
    3.  Klicken Sie mit der rechten Maustaste auf den Berichtsserverknoten, und klicken Sie anschließend auf **Eigenschaften**. Wenn die Option **Eigenschaften** deaktiviert ist, überprüfen Sie, ob [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorrechten gestartet wurde.  
  
    4.  Wählen Sie **aktivieren-Download für das ActiveX-Client-Drucksteuerelement**.  
  
    5.  Klicken Sie auf **OK**.  
  
-   Für einen **Berichtsserver im SharePoint-Modus**:  
  
    1.  Klicken Sie in der SharePoint-Zentraladministration auf **Anwendungsverwaltung**.  
  
    2.  Klicken Sie auf **Dienstanwendungen verwalten**.  
  
    3.  Klicken Sie auf den Namen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung und anschließend im SharePoint-Menüband auf **Verwalten** .  
  
    4.  Klicken Sie auf **Systemeinstellungen**.  
  
    5.  Wählen Sie **Clientdruck aktivieren**aus. Die Option **Clientdruck aktivieren** befindet sich weiter unten auf der Seite.  
  
    6.  Klicken Sie auf **OK**.  
  
-   Schreiben eines Skripts oder Codeabschnitts zum Festlegen der Berichtsserver-Systemeigenschaft **EnableClientPrinting** auf `false.`  
  
 Im folgenden Beispielskript wird eine Methode zum Deaktivieren des clientseitigen Druckens erläutert. Kompilieren Sie den folgenden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Code, und führen Sie ihn anschließend aus, um die **EnableClientPrinting** -Eigenschaft auf **FALSE**festzulegen. Führen Sie nach der Ausführung des Codes einen Neustart von IIS aus.  
  
### <a name="sample-script"></a>Beispielskript  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
