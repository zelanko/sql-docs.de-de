---
title: 'Schritt 1: Konfigurieren der Entwicklungsumgebung für Ruby-Entwicklung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 38af92d3cb0354bc4b75131a349f6a1c26e90490
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992460"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die Ruby-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen konfigurieren, um eine Anwendung mit dem Ruby-Treiber für die SQL Server zu entwickeln.    
  
Beachten Sie, dass der Ruby-Treiber das TDS-Protokoll verwendet, das standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Ruby Installer herunterladen**  
Wenn Ihr Computer nicht über Ruby verfügt, installieren Sie es. Für neue Ruby-Benutzer empfehlen wir die Verwendung von Ruby 2.2. X-Installationsprogrammen. Diese stellen eine stabile Sprache und eine umfangreiche Liste von Paketen (Gems) bereit, die kompatibel und aktualisiert sind. Wechseln Sie zur [Ruby-Downloadseite](https://rubyinstaller.org/downloads/) , und laden Sie den entsprechenden 2.1. x-Installer herunter. Wenn Sie sich beispielsweise auf einem 64-Bit-Computer befinden, laden Sie den Installer für Ruby 2.1.6 (x64) herunter.   
  
2.  **Installieren von Ruby**  
Nachdem das Installationsprogramm heruntergeladen wurde, gehen Sie wie folgt vor:  
A. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten.  
B. Wählen Sie Ihre Sprache aus, und stimmen Sie den Bedingungen zu.  
c.  Aktivieren Sie auf dem Bildschirm "Installationseinstellungen" die Kontrollkästchen neben "Ruby ausführbare Dateien" zu Ihrem Pfad hinzufügen und ". rb"-und ". RBW"-Dateien mit dieser Ruby-Installation verknüpfen.  
  
3.  **Ruby devkit herunterladen**  
Herunterladen von devkit von der Seite rubyinstaller  
  
4.  **Installieren von Ruby devkit**  
Nachdem der Download abgeschlossen ist, führen Sie folgende Schritte aus:  
A. Doppelklicken Sie auf die Datei. Sie werden gefragt, wohin die Dateien extrahiert werden sollen.  
B. Klicken Sie auf "..." , und wählen Sie "c:\devkit" aus. Sie müssen diesen Ordner wahrscheinlich zuerst erstellen, indem Sie auf "neuen Ordner erstellen" klicken.  
c. Klicken Sie auf "OK" und dann auf "extrahieren", um die Dateien zu extrahieren.  
  
5. **Öffnen Sie "cmd. exe"**  
  
6. **Ruby devkit initialisieren**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installieren von tinytds gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Terminal öffnen**  
  
2. **Installieren von Ruby Version Manager (rvm) und Voraussetzungen**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Verwenden von RvM zum Installieren von Ruby**  
Installieren Sie z. b. Version 2.3.0 von Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Stellen Sie sicher, dass die Ausgabe des letzten Befehls anzeigt, dass Sie Version 2.3.0 ausführen.  
  
4.  **Installieren von freetds**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installieren von tinytds**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Beachten Sie, dass Mac OS X bereits Ruby vorinstalliert hat, da das Betriebssystem eine Abhängigkeit aufweist.    
  
1.  **Terminal öffnen**  
  
2. **Installieren des Homebrew-Paket-Managers**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installieren von freetds**  
```  
> brew install FreeTDS  
```  
  
4.  **Installieren von tinytds gem**  
```  
> gem install tiny_tds  
```
