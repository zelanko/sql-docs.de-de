---
title: 'Schritt 1: Konfigurieren der Entwicklungsumgebung für Ruby'
description: Erfahren Sie, wie Sie Ihre Entwicklungsumgebung für Ruby konfigurieren.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700b0c1979b0eccc1544afb59296fba867e24c53
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634592"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die Ruby-Entwicklung
Sie müssen Ihre Entwicklungsumgebung entsprechend den Voraussetzungen konfigurieren, um mithilfe des Ruby-Treibers für SQL Server eine Anwendung entwickeln zu können.    
  
Der Ruby-Treiber verwendet das TDS-Protokoll, das in SQL Server und Azure SQL-Datenbank standardmäßig aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Herunterladen des Ruby-Installationsprogramms**  
Wenn Ruby auf Ihrem Computer nicht vorhanden ist, installieren Sie die Sprache. Neue Ruby-Benutzer sollten die Ruby 2.2.X-Installationsprogramme verwenden, die eine stabile Sprache und eine umfangreiche Liste von Paketen (Gems) bereitstellen, die kompatibel und aktualisiert sind. Wechseln Sie zur [Downloadseite von Ruby](https://rubyinstaller.org/downloads/), und laden Sie das entsprechende 2.1.X-Installationsprogramm herunter. Wenn Sie beispielsweise auf einem 64-Bit-Computer arbeiten, laden Sie das Installationsprogramm für Ruby 2.1.6 (x64) herunter.   
  
2.  **Installieren von Ruby**  
Nachdem das Installationsprogramm heruntergeladen wurde:  
a. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten.  
b. Wählen Sie die gewünschte Sprache aus, und stimmen Sie den Bedingungen zu.  
c.  Aktivieren Sie auf dem Bildschirm mit den Installationseinstellungen die Kontrollkästchen für „Ausführbare Ruby-Dateien zu PATH hinzufügen“, und verknüpfen Sie `.rb`- und `.rbw`-Dateien mit dieser Ruby-Installation.  
  
3.  **Herunterladen des DevKit für Ruby**  
Laden Sie das DevKit von der Seite des Ruby-Installationsprogramms herunter.  
  
4.  **Installieren des DevKit für Ruby**  
Wenn der Download abgeschlossen ist:  
a. Doppelklicken Sie auf die Datei. Sie werden gefragt, wohin die Dateien extrahiert werden sollen.  
b. Klicken Sie auf die Schaltfläche „...“, und wählen Sie „C:\DevKit“ aus. Möglicherweise müssen Sie diesen Ordner zuerst erstellen, indem Sie auf „Neuen Ordner erstellen“ klicken.  
c. Klicken Sie auf „OK“ und dann auf „Extrahieren“, um die Dateien zu extrahieren.  
  
5. **Öffnen von „cmd.exe“**  
  
6. **Installieren des DevKit für Ruby**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Installieren von TinyTDS (Gem)**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Öffnen Sie ein Terminal.**  
  
2. **Installieren von Ruby Version Manager (`rvm`) und Voraussetzungen**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Verwenden von `rvm` zum Installieren von Ruby**  
Installieren Sie beispielsweise Version 2.3.0 von Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Stellen Sie sicher, dass aus der Ausgabe des letzten Befehls hervorgeht, dass Version 2.3.0 ausgeführt wird.  
  
4.  **Installieren von FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Installieren von TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="macos"></a>macOS  
  
Hinweis: Ruby ist unter macOS bereits vorinstalliert, da das Betriebssystem eine Abhängigkeit aufweist.
  
1.  **Öffnen Sie ein Terminal.**  
  
2. **Installieren des Homebrew-Paket-Managers**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Installieren von FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Installieren von TinyTDS (Gem)**  
```  
> gem install tiny_tds  
```
