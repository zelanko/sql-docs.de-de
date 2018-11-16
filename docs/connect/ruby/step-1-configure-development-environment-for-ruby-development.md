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
manager: craigg
ms.openlocfilehash: a298a7c7f65a198e5bfb0922f2b061fd44079739
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604700"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die Ruby-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen zu konfigurieren, um die Entwicklung einer Anwendung, die mit der Ruby-Treiber für SQL Server.    
  
Beachten Sie, dass der Ruby-Treiber TDS-Protokolls, die standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Ruby-Installationsprogramm herunterladen**  
Wenn Ihr Computer nicht installieren sie Ruby verfügt. Für neue Benutzer für Ruby empfehlen wir, dass Sie Ruby 2.2.X Installationsprogramme verwenden. Diese bieten eine stabile Sprache und eine umfassende Liste von Paketen (Gems), die kompatibel sind und aktualisiert werden. Wechseln Sie die [Ruby Downloadseite](https://rubyinstaller.org/downloads/) und Laden Sie den entsprechenden 2.1.x-Installer. Für das Beispiel, wenn Sie auf einem 64-Bit-Computer sind, laden Sie den Ruby 2.1.6 die Produktversion von (x 64)-Installer.   
  
2.  **Installieren von Ruby**  
Sobald das Installationsprogramm heruntergeladen wurde, führen Sie folgende Schritte aus:  
A. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten.  
B. Wählen Sie Ihre Sprache aus, und stimmen Sie den Bedingungen.  
c.  Wählen Sie die Kontrollkästchen neben den beiden hinzufügen Ruby ausführbaren Dateien an den Pfad und zuordnen ".RB", und .rbw-Dateien mit der Ruby-Installation auf dem Bildschirm Einstellungen installieren.  
  
3.  **Herunterladen von Ruby DevKit**  
Laden Sie auf der Seite RubyInstaller DevKit  
  
4.  **Installieren Sie Ruby DevKit**  
Nachdem der Download abgeschlossen ist, führen Sie folgende Schritte aus:  
A. Doppelklicken Sie auf die Datei. Sie werden aufgefordert, wo Sie die Dateien extrahiert werden.  
B. Klicken Sie auf die Schaltfläche "...", und wählen Sie "C:\DevKit". Sie müssen wahrscheinlich dieser Ordner zuerst zu erstellen, indem Sie auf "Neuer Ordner stellen".  
c. Klicken Sie auf "OK", und klicken Sie dann "extrahieren", um die Dateien zu extrahieren.  
  
5. **Öffnen von cmd.exe**  
  
6. **Initialisieren Sie Ruby DevKit**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installieren von TinyTDS gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Open-terminal**  
  
2. **Installieren Sie Ruby-Versions-Manager (Rvm) und Voraussetzungen**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Verwenden Sie Rvm zum Installieren von Ruby**  
Installieren Sie Ruby-Version 2.3.0 beispielsweise:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Stellen Sie sicher, dass die Ausgabe mit dem letzten Befehl gibt an, dass Sie Version 2.3.0 ausgeführt werden.  
  
4.  **Installieren von FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installieren von TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Beachten Sie, dass Mac OS X bereits vorab installiert ist, Ruby wie das Betriebssystem abhängig ist.    
  
1.  **Open-terminal**  
  
2. **Installieren Sie Homebrew-Paket-manager**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installieren von FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Installieren von TinyTDS gem**  
```  
> gem install tiny_tds  
```
