---
title: Installieren der eigenständigen Version des Berichts-Generators (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 119fa4121e6f18d9592b60b6fcb8504a1228d848
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353920"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a>Installieren der eigenständigen Version des Berichts-Generators (Berichts-Generator)
  Sie können den Berichts-Generator über installieren die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature Packs der [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=168472) oder an einem Speicherort wie für Öffentliche Ordner, der die Datei "reportbuilder3_x86.msi", das Windows Installer-Paket für den Berichts-Generator verfügt über, heruntergeladen wurde.  
  
 Sie können auch eine Befehlszeileninstallation des Berichts-Generators ausführen und Argumente angeben, um die Installation anzupassen. Neben den systeminternen MSI-Standardparametern können Sie die benutzerdefinierten Parameter aus, denen Berichts-Generator bereitstellt: RBINSTALLDIR und REPORTSERVERURL. "RBINSTALLDIR" dient zum Angeben des Stamminstallationsordners für den Berichts-Generator. Mit "REPORTSERVERURL" wird der Standardberichtsserver angegeben, der vom Berichts-Generator zum Speichern von Berichten auf dem Server verwendet wird.  
  
 Wenn Sie eine vollständig automatische Installation ohne Eingriff über die Benutzeroberfläche durchführen möchten, geben Sie die Option **/quiet** an. Programmbedingt werden durch das Optionsflag "quiet" Installationsfehler unterdrückt. Deshalb wird bei Verwendung der Option „quiet“ die Angabe der Option **/l** empfohlen, die Protokollierung für diesen Fall angibt.  
  
> [!IMPORTANT]  
>  Die Sicherheitsfunktionen von Windows Vista und Windows 7 erfordern erweiterte Berechtigungen zum Ausführen von Befehlszeilenvorgängen. Auch wird die Angabe der Berechtigung zum Ausführen von Vorgängen über die Befehlszeile angefordert. Die Installation erfolgt nicht automatisch. Für eine unbeaufsichtigte Installation müssen Sie die Befehlszeile als Administrator ausführen.  
  
### <a name="to-install-report-builder-from-the-download-site"></a>So installieren Sie Berichts-Generator von der Downloadwebsite aus  
  
1.  Wechseln Sie zu [Microsoft SQL Server 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkID=219138) und suchen Sie den Berichts-Generator-Abschnitt der Webseite.  
  
2.  Klicken Sie auf **X86 Paket**.  
  
3.  In der **Dateidownload** Dialogfeld klicken Sie auf **ausführen**.  
  
    > [!IMPORTANT]  
    >  Laden Sie nur Dateien aus vertrauenswürdigen Quellen herunter.  
  
4.  Klicken Sie in der Internet Explorer-Dialogfeld auf **ausführen**.  
  
    > [!IMPORTANT]  
    >  Führen Sie nur Dateien aus vertrauenswürdigen Quellen aus.  
  
5.  Der Assistent für Microsoft SQL Server Berichts-Generator wird gestartet.  
  
6.  Auf der **Willkommen beim Installations-Assistenten** auf **Weiter**.  
  
7.  Auf der **-Software-Lizenzbedingungen** Seite, lesen Sie den Lizenzvertrag, und wählen Sie dann die **ich stimme den Bedingungen des Lizenzvertrags** Option. Klicken Sie auf **Weiter**.  
  
8.  Geben Sie Ihren Namen und den Firmennamen an. Klicken Sie auf **Weiter**.  
  
9. Auf der **Funktionsauswahl** Seite, klicken Sie optional auf **Durchsuchen** oder **Speicherplatz**. Klicken Sie auf **Weiter**.  
  
    -   Klicken Sie auf **Durchsuchen** auf den Standardspeicherort von Berichts-Generator und zu aktualisieren.  
  
        > [!NOTE]  
        >  Der Standardinstallationsordner für Berichts-Generator ist \<Laufwerk > Programme\Microsoft SQL Server.  
  
    -   Klicken Sie auf **Speicherplatz** , erfahren, wie viel Speicherplatz Berichts-Generator nutzt.  
  
        > [!NOTE]  
        >  Wenn ein Volume nicht genügend freien Speicherplatz hat, wird das Volume hervorgehoben.  
  
10. Geben Sie optional auf der Seite **Standardzielserver** die URL zu dem Zielberichtsserver an, wenn nicht der Standardserver verwendet wird. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie den Berichts-Generator mit einer Verbindung zu einem Berichtsserver verwenden möchten, geben Sie die URL zu dem Server jetzt an. Aber Sie können hierzu auch die **Optionen** im Dialogfeld, wenn Sie im Berichts-Generator arbeiten.  
  
11. Klicken Sie auf **installieren** zum Abschließen der Installation von Berichts-Generator.  
  
### <a name="to-install-report-builder-from-a-share"></a>So installieren Sie Berichts-Generator von einer Freigabe aus  
  
1.  Informationen zum Speicherort der Datei "ReportBuilder3_x86.msi", die Sie zum Installieren des Berichts-Generators auf dem lokalen Computer ausführen müssen, erhalten Sie von Ihrem Administrator.  
  
2.  Suchen Sie nach dem Windows Installer-Paket (MSI) für den Berichts-Generator ("ReportBuilder3_x86.msi"), und klicken Sie darauf.  
  
     Der Assistent für Microsoft SQL Server Berichts-Generator wird gestartet.  
  
3.  Auf der **Willkommen beim Installations-Assistenten** auf **Weiter**.  
  
4.  Auf der **-Software-Lizenzbedingungen** Seite, lesen Sie den Lizenzvertrag, und wählen Sie dann die **ich stimme den Bedingungen des Lizenzvertrags** Option. Klicken Sie auf **Weiter**.  
  
5.  Geben Sie Ihren Namen und den Firmennamen an. Klicken Sie auf **Weiter**.  
  
6.  Auf der **Funktionsauswahl** Seite, klicken Sie optional auf **Durchsuchen** oder **Speicherplatz**. Klicken Sie auf **Weiter**.  
  
    -   Klicken Sie auf **Durchsuchen** auf den Standardspeicherort von Berichts-Generator und zu aktualisieren.  
  
        > [!NOTE]  
        >  Der Standardinstallationsordner für Berichts-Generator ist \<Laufwerk > Programme\Microsoft SQL Server.  
  
    -   Klicken Sie auf **Speicherplatz** , erfahren, wie viel Speicherplatz Berichts-Generator nutzt.  
  
        > [!NOTE]  
        >  Wenn ein Volume nicht genügend freien Speicherplatz hat, wird das Volume hervorgehoben.  
  
7.  Geben Sie optional auf der Seite **Standardzielserver** die URL zu dem Zielberichtsserver an, wenn nicht der Standardserver verwendet wird. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Wenn Sie den Berichts-Generator mit einer Verbindung zu einem Berichtsserver verwenden möchten, geben Sie die URL zu dem Server jetzt an. Aber Sie können hierzu auch die **Optionen** im Dialogfeld, wenn Sie im Berichts-Generator arbeiten.  
  
8.  Klicken Sie auf **installieren** zum Abschließen der Installation von Berichts-Generator.  
  
### <a name="to-install-report-builder-from-the-command-line"></a>So installieren Sie Berichts-Generator mithilfe der Befehlszeile  
  
1.  Wechseln Sie zu [Microsoft SQL Server 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkID=219138) und suchen Sie den Berichts-Generator-Abschnitt.  
  
2.  Klicken Sie auf **X86 Paket**.  
  
3.  Klicken Sie auf Speichern.  
  
4.  Optional: Navigieren Sie zum gewünschten Speicherort speichern, stellen Sie sicher die **speichern als** Option **Windows Installer-Paket**, und klicken Sie dann auf **speichern**.  
  
5.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
6.  Geben Sie in das Textfeld Öffnen `cmd.`  
  
7.  Navigieren Sie im Eingabeaufforderungsfenster zu dem Ordner, in dem "ReportBuilder3_x86.msi" gespeichert wurde.  
  
8.  Geben Sie einen Befehl mit dem folgenden Format ein:  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     Die zwei bestimmte Optionen für die Installation von Berichts-Generator sind: RBINSTALLDIR und REPORTSERVERURL. Diese Argumente müssen nicht unbedingt in der Befehlszeile angegeben werden. Der grundlegende Befehl lautet wie folgt:  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. Um den Befehl auszuführen, drücken Sie die EINGABETASTE.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren und Deinstallieren von Berichts-Generator-Unterstützung](../install-uninstall-and-report-builder-support.md)   
 [Deinstallieren der eigenständigen Version des Berichts-Generators &#40;Berichts-Generator&#41;](install-report-builder.md)  
  
  
