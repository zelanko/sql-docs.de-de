---
title: Installieren von Power Pivot über die Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8b8460927baa185233234baa2f6401fa600f3fff
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952132"
---
# <a name="install-powerpivot-from-the-command-prompt"></a>Installieren von PowerPivot über die Eingabeaufforderung
  Sie können Setup in der Befehlszeile ausführen, um SQL Server PowerPivot für SharePoint zu installieren. Sie müssen den `/ROLE`-Parameter in den Befehl einschließen und den `/FEATURES`-Parameter ausschließen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 SharePoint Server 2010 Enterprise Edition mit Service Pack 1 (SP1) muss installiert sein.  
  
 Sie müssen über Domänenbenutzerkonten verfügen, um Analysis Services bereitzustellen.  
  
 Der Computer muss der gleichen Domäne wie die SharePoint-Farm hinzugefügt werden.  
  
##  <a name="Commands"></a>/Role basierte Installationsoptionen  
 Für PowerPivot für SharePoint-Bereitstellungen wird der `/ROLE`-Parameter anstelle des `/FEATURES`-Parameters verwendet. Gültige Werte sind:  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 Beide Rollen installieren Anwendungs-, Konfigurations- und Bereitstellungsdateien, die die Ausführung von PowerPivot für SharePoint in einer SharePoint-Farm ermöglichen. Die Angabe von beiden Rolle bewirkt, dass Setup Hardware- und Softwareanforderungen für die SharePoint-Integration überprüft.  
  
 Die vorhandene Farmoption geht davon aus, dass eine SharePoint-Farm bereits vorhanden ist. Bei der Option "neue Farm" wird davon ausgegangen, dass Sie eine neue Farm erstellen. Sie unterstützt das Hinzufügen einer Datenbank-Engine Instanz in der Befehlszeilen Syntax, damit Sie die Datenbank-Engine Instanz als Datenbankserver der Farm verwenden können.  
  
 Im Gegensatz zu den vorherigen Versionen werden alle Serverkonfigurationstasks nach der Installation ausgeführt. Wenn Sie Installations- und Konfigurationsschritte automatisieren, können Sie den Server mithilfe von PowerShell konfigurieren. Weitere Informationen finden Sie unter [Power Pivot-Konfiguration mit Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
## <a name="example-commands"></a>Beispielbefehle  
 Die folgenden Beispiele veranschaulichen die Verwendung jeder Option. In Beispiel 1 wird `SPI_AS_ExistingFarm` angezeigt.  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 Beispiel 2 zeigt `SPI_AS_NewFarm`. Beachten Sie, dass es Parameter zum Bereitstellen der Datenbank-Engine einschließt.  
  
```  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="Join"></a>Ändern der Befehlssyntax  
 Ändern Sie die Beispielbefehlssyntax mithilfe der folgenden Schritte.  
  
1.  Kopieren Sie den folgenden Befehl in Editor:  
  
    ```  
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     Der `/q`-Parameter führt Setup im stillen Modus aus, beim dem die Benutzeroberfläche unterdrückt wird.  
  
     `/IAcceptSQLServerLicenseTerms` wird benötigt, wenn der `/q`-Parameter oder der `/qs`-Parameter für nicht beaufsichtigte Installationen angegeben wird.  
  
     Der `/action`-Parameter weist Setup an, eine Installation auszuführen.  
  
     Der `/role`-Parameter weist Setup an, das Analysis Services-Programm und die für PowerPivot für SharePoint erforderlichen Konfigurationsdateien zu installieren. Diese Rolle erkennt auch die vorhandenen Farmkonnektivitätsinformationen und verwendet sie, um auf die SharePoint-Konfigurationsdatenbank zuzugreifen. Dieser Parameter ist erforderlich. Verwenden Sie ihn statt des `/features`-Parameters, um die zu installierenden Komponenten anzugeben.  
  
     Der `/instancename`-Parameter gibt 'PowerPivot' als benannte Instanz an. Dieser Wert ist hartcodiert und kann nicht geändert werden. Er wird im Befehl zu pädagogischen Zwecken angegeben, damit Sie wissen, wie der Dienst installiert wird.  
  
     Mit dem `/indicateprogress`-Parameter können Sie den Status im Eingabeaufforderungsfenster überwachen.  
  
2.  Der `PID`-Parameter wird im Befehl weggelassen, was bewirkt, dass die Evaluation Edition installiert ist. Wenn Sie die Enterprise Edition installieren möchten, fügen Sie dem Setup-Befehl die PID hinzu und geben Sie einen gültigen Product Key ein.  
  
    ```  
  
    /PID=<product key for an Enterprise installation>  
  
    ```  
  
3.  Ersetzen Sie die Platzhalter für \<domain \ username > und \<strongpassword > durch gültige Benutzerkonten und Kenn Wörter.  
  
     Die Parameter "`/assvaccount`" und " **/assvcpassword** " werden verwendet, um die [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz auf dem Anwendungsserver zu konfigurieren. Ersetzen Sie diese Platzhalter durch gültige Kontoinformationen.  
  
     Der **/assysadminaccounts** -Parameter muss auf die Identität des Benutzers festgelegt werden, der SQL Server-Setup ausgeführt wird. Sie müssen wenigstens einen Systemadministrator angeben. Beachten Sie, dass SQL Server-Setup keine automatischen sysadmin-Berechtigungen für Mitglieder der integrierten Gruppe "Administratoren" gewährt.  
  
4.  Entfernen Sie Zeilenumbrüche.  
  
5.  Wählen Sie den gesamten Befehl aus, und klicken Sie dann im Menü Bearbeiten auf **Kopieren** .  
  
6.  Öffnen Sie eine Administrator-Eingabeaufforderung. Klicken Sie hierzu auf **Start**, klicken Sie mit der rechten Maustaste auf die Eingabeaufforderung, und wählen Sie **als Administrator ausführen**aus.  
  
7.  Navigieren Sie zum Laufwerk oder dem freigegebenem Ordner, der die SQL Server-Installationsmedien enthält.  
  
8.  Fügen Sie den überarbeiteten Befehl in die Befehlszeile ein. Klicken Sie hierzu auf das Symbol in der oberen linken Ecke des Eingabe Aufforderungs Fensters, zeigen Sie auf **Bearbeiten**, und klicken Sie dann auf **Einfügen**.  
  
9. Drücken **Sie die Eingabe** Taste, um den Befehl auszuführen. Warten Sie, bis Setup abgeschlossen ist. Sie können den Status von Setup im Eingabeaufforderungsfenster überwachen.  
  
10. Um die Installation zu überprüfen, öffnen Sie die Datei summary.txt unter \Programme\SQL Server\120\Setup Bootstrap\Log. Das Endergebnis sollte "Erfolgreich" lauten, wenn der Server ohne Fehler installiert hat.  
  
11. Konfigurieren Sie den Server. Sie müssen Lösungen bereitstellen, eine Dienstanwendung erstellen und die Funktion für jede Websitesammlung aktivieren. Weitere Informationen finden Sie unter [konfigurieren oder reparieren PowerPivot für SharePoint 2010 &#40;Power Pivot-Konfigurations&#41; Tools](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) oder [Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Power Pivot-Dienst Konten](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
