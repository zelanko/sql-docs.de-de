---
title: Installieren Sie die eigenständige Version von Berichts-Generator (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60a96db6a7568c2af22242f10f96e7a2abf13937
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73637835"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a>Installieren der eigenständigen Version des Berichts-Generators (Berichts-Generator)
  Sie können Berichts-Generator über das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613) oder einen Speicherort installieren, z. b. den öffentlichen Ordner, in den die ReportBuilder3_x86. msi, das Windows Installer Paket für Berichts-Generator heruntergeladen wurde.  
  
 Sie können auch eine Befehlszeileninstallation des Berichts-Generators ausführen und Argumente angeben, um die Installation anzupassen. Neben den systeminternen MSI-Standardparametern können Sie die vom Berichts-Generator bereitgestellten benutzerdefinierten Parameter "RBINSTALLDIR" und "REPORTSERVERURL" verwenden. "RBINSTALLDIR" dient zum Angeben des Stamminstallationsordners für den Berichts-Generator. Mit "REPORTSERVERURL" wird der Standardberichtsserver angegeben, der vom Berichts-Generator zum Speichern von Berichten auf dem Server verwendet wird.  
  
 Wenn Sie eine vollständig automatische Installation ohne Eingriff über die Benutzeroberfläche durchführen möchten, geben Sie die Option **/quiet** an. Programmbedingt werden durch das Optionsflag "quiet" Installationsfehler unterdrückt. Deshalb wird bei Verwendung der Option „quiet“ die Angabe der Option **/l** empfohlen, die Protokollierung für diesen Fall angibt.  
  
> [!IMPORTANT]  
>  Die Sicherheitsfunktionen von Windows Vista und Windows 7 erfordern erweiterte Berechtigungen zum Ausführen von Befehlszeilenvorgängen. Auch wird die Angabe der Berechtigung zum Ausführen von Vorgängen über die Befehlszeile angefordert. Die Installation erfolgt nicht automatisch. Für eine unbeaufsichtigte Installation müssen Sie die Befehlszeile als Administrator ausführen.  
  
### <a name="to-install-report-builder-from-the-download-site"></a>So installieren Sie Berichts-Generator von der Downloadwebsite aus  
  
1.  Wechseln Sie zu [Microsoft SQL Server 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkID=219138) , und suchen Sie den Abschnitt Berichts-Generator der Webseite.  
  
2.  Klicken Sie auf **x86-Paket**.  
  
3.  Klicken Sie im Dialogfeld **Datei Download** auf **Ausführen**.  
  
    > [!IMPORTANT]  
    >  Laden Sie nur Dateien aus vertrauenswürdigen Quellen herunter.  
  
4.  Klicken Sie im Dialogfeld Internet Explorer auf **Ausführen**.  
  
    > [!IMPORTANT]  
    >  Führen Sie nur Dateien aus vertrauenswürdigen Quellen aus.  
  
5.  Der Assistent für Microsoft SQL Server Berichts-Generator wird gestartet.  
  
6.  Klicken Sie auf der Seite **Willkommen** auf **weiter**.  
  
7.  Lesen Sie auf der Seite **Lizenzvertrag** die Vereinbarung, und wählen Sie dann die Option **Ich stimme den Bedingungen des Lizenzvertrags** zu. Klicken Sie auf **Weiter**.  
  
8.  Geben Sie Ihren Namen und den Firmennamen an. Klicken Sie auf **Weiter**.  
  
9. Klicken Sie optional auf der Seite **Funktionsauswahl** auf **Durchsuchen** oder auf Datenträger **Kosten**. Klicken Sie auf **Weiter**.  
  
    -   Klicken Sie auf **Durchsuchen** , um den Standard Speicherort Berichts-Generator anzuzeigen und zu aktualisieren.  
  
        > [!NOTE]  
        >  Der Standard Installationsordner für Berichts-Generator ist \<Laufwerk>Programme\Microsoft SQL Server.  
  
    -   Klicken Sie auf Datenträger **Kosten** , um zu erfahren, wie viel Speicherplatz Berichts-Generator beansprucht.  
  
        > [!NOTE]  
        >  Wenn ein Volume nicht genügend freien Speicherplatz hat, wird das Volume hervorgehoben.  
  
10. Geben Sie optional auf der Seite **Standardzielserver** die URL zu dem Zielberichtsserver an, wenn nicht der Standardserver verwendet wird. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie den Berichts-Generator mit einer Verbindung zu einem Berichtsserver verwenden möchten, geben Sie die URL zu dem Server jetzt an. Allerdings können Sie dies auch über das Dialogfeld **Optionen** tun, wenn Sie in Berichts-Generator arbeiten.  
  
11. Klicken Sie auf **Installieren** , um die Installation von Berichts-Generator abzuschließen.  
  
### <a name="to-install-report-builder-from-a-share"></a>So installieren Sie Berichts-Generator von einer Freigabe aus  
  
1.  Informationen zum Speicherort der Datei "ReportBuilder3_x86.msi", die Sie zum Installieren des Berichts-Generators auf dem lokalen Computer ausführen müssen, erhalten Sie von Ihrem Administrator.  
  
2.  Suchen Sie nach dem Windows Installer-Paket (MSI) für den Berichts-Generator ("ReportBuilder3_x86.msi"), und klicken Sie darauf.  
  
     Der Assistent für Microsoft SQL Server Berichts-Generator wird gestartet.  
  
3.  Klicken Sie auf der Seite **Willkommen** auf **weiter**.  
  
4.  Lesen Sie auf der Seite **Lizenzvertrag** die Vereinbarung, und wählen Sie dann die Option **Ich stimme den Bedingungen des Lizenzvertrags** zu. Klicken Sie auf **Weiter**.  
  
5.  Geben Sie Ihren Namen und den Firmennamen an. Klicken Sie auf **Weiter**.  
  
6.  Klicken Sie optional auf der Seite **Funktionsauswahl** auf **Durchsuchen** oder auf Datenträger **Kosten**. Klicken Sie auf **Weiter**.  
  
    -   Klicken Sie auf **Durchsuchen** , um den Standard Speicherort Berichts-Generator anzuzeigen und zu aktualisieren.  
  
        > [!NOTE]  
        >  Der Standard Installationsordner für Berichts-Generator ist \<Laufwerk>Programme\Microsoft SQL Server.  
  
    -   Klicken Sie auf Datenträger **Kosten** , um zu erfahren, wie viel Speicherplatz Berichts-Generator beansprucht.  
  
        > [!NOTE]  
        >  Wenn ein Volume nicht genügend freien Speicherplatz hat, wird das Volume hervorgehoben.  
  
7.  Geben Sie optional auf der Seite **Standardzielserver** die URL zu dem Zielberichtsserver an, wenn nicht der Standardserver verwendet wird. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie den Berichts-Generator mit einer Verbindung zu einem Berichtsserver verwenden möchten, geben Sie die URL zu dem Server jetzt an. Allerdings können Sie dies auch über das Dialogfeld **Optionen** tun, wenn Sie in Berichts-Generator arbeiten.  
  
8.  Klicken Sie auf **Installieren** , um die Installation von Berichts-Generator abzuschließen.  
  
### <a name="to-install-report-builder-from-the-command-line"></a>So installieren Sie Berichts-Generator mithilfe der Befehlszeile  
  
1.  Wechseln Sie zu [Microsoft SQL Server 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkID=219138) , und suchen Sie den Abschnitt Berichts-Generator.  
  
2.  Klicken Sie auf **x86-Paket**.  
  
3.  Klicken Sie auf Speichern.  
  
4.  Navigieren Sie optional zum Speicherort, in dem gespeichert werden soll, überprüfen Sie, ob die Option **Speichern** unter **Windows Installer Paket**ist, und klicken Sie dann auf **Speichern**.  
  
5.  Klicken Sie im **Startmenü** auf **Ausführen**.  
  
6.  Geben Sie im Textfeld Öffnen den Befehl  ein.`cmd.`  
  
7.  Navigieren Sie im Eingabeaufforderungsfenster zu dem Ordner, in dem "ReportBuilder3_x86.msi" gespeichert wurde.  
  
8.  Geben Sie einen Befehl mit dem folgenden Format ein:  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     Bei den beiden folgenden Optionen handelt es sich um spezifische Optionen für die Installation des Berichts-Generators: "RBINSTALLDIR" und "REPORTSERVERURL". Diese Argumente müssen nicht unbedingt in der Befehlszeile angegeben werden. Der grundlegende Befehl lautet wie folgt:  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. Drücken Sie die EINGABETASTE, um den Befehl auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützung für Installation, Deinstallation und Berichts-Generator](../install-uninstall-and-report-builder-support.md)   
 [Deinstallieren Sie die eigenständige Version von Berichts-Generator &#40;Berichts-Generator&#41;](install-report-builder.md)  
  
  
