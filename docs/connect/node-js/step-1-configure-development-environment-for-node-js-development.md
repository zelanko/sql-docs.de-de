---
title: 'Schritt 1: Konfigurieren der Entwicklungsumgebung für Node.js'
description: Sie müssen Ihre Entwicklungsumgebung entsprechend den Voraussetzungen konfigurieren, um mithilfe des Node.js-Treibers für SQL Server eine Anwendung entwickeln zu können.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 38337772d9ec9db2503637122d0d1b616dc6ef5f
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528134"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Schritt 1:  Konfigurieren der Entwicklungsumgebung für die Node.js-Entwicklung
Sie müssen Ihre Entwicklungsumgebung entsprechend den Voraussetzungen konfigurieren, um mithilfe des Node.js-Treibers für SQL Server eine Anwendung entwickeln zu können.  Die gängigste Methode besteht darin, den Node Package Manager (npm) zu verwenden, um das Tedious-Modul zu installieren. Sie können das Tedious-Modul aber auch direkt von [GitHub](https://github.com/pekim/tedious) herunterladen.  
  
Der Node.js-Treiber verwendet das TDS-Protokoll, das in SQL Server und Azure SQL-Datenbank standardmäßig aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren Sie Node.js-Runtime und Node Package Manager (npm).**  
a. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/).  
b. Klicken Sie auf den Link für das gewünschten Windows-Installationsprogramm (MSI-Datei).   
c. Wenn der Download abgeschlossen ist, führen Sie die MSI-Datei aus, um Node.js zu installieren.  
  
2. **Öffnen von „cmd.exe“**  
  
3. **Erstellen Sie ein Projektverzeichnis**, und wechseln Sie zu diesem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Erstellen eines Node.js-Projekts**  Um bei der Projekterstellung die Standardwerte zu übernehmen, drücken Sie die EINGABETASTE, bis das Projekt erstellt ist. Nach Abschluss dieses Schritts enthält Ihr Projektverzeichnis eine package.json-Datei.  
```  
> npm init  
```  
  
5. **Installieren des Tedious-Moduls in Ihrem Projekt**  Tedious ist die Implementierung des TDS-Protokolls, das zur Kommunikation mit SQL Server verwendet wird.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Öffnen Sie ein Terminal.**  
  
2. **Installieren Sie die Node.js-Runtime.**  
```  
>sudo apt-get install node  
```  
3. **Installieren Sie npm (Node Package Manager).**  
```  
> sudo apt-get install npm  
```  
4. **Erstellen Sie ein Projektverzeichnis**, und wechseln Sie zu diesem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Erstellen eines Node.js-Projekts**  Um bei der Projekterstellung die Standardwerte zu übernehmen, drücken Sie die EINGABETASTE, bis das Projekt erstellt ist. Nach Abschluss dieses Schritts enthält Ihr Projektverzeichnis eine package.json-Datei.  
```  
> sudo npm init  
```  
  
6. **Installieren des Tedious-Moduls in Ihrem Projekt**  Tedious ist die Implementierung des TDS-Protokolls, das zur Kommunikation mit SQL Server verwendet wird.  
```  
> sudo npm install tedious  
```  
  
## <a name="macos"></a>macOS  
  
1. **Installieren Sie die Node.js-Runtime und npm (Node Package Manager).**  
a. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/).  
b. Klicken Sie auf den entsprechenden Link für das macOS-Installationsprogramm.  
c. Wenn der Download abgeschlossen ist, führen Sie die DMG-Datei aus, um Node.js zu installieren.  
  
2. **Öffnen Sie ein Terminal.**  
  
3. **Erstellen Sie ein Projektverzeichnis**, und wechseln Sie zu diesem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Erstellen eines Node.js-Projekts**  Um bei der Projekterstellung die Standardwerte zu übernehmen, drücken Sie die EINGABETASTE, bis das Projekt erstellt ist. Nach Abschluss dieses Schritts enthält Ihr Projektverzeichnis eine package.json-Datei.  
```  
> npm init  
```  
  
5. **Installieren des Tedious-Moduls in Ihrem Projekt**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber zur Kommunikation mit SQL Server verwendet.  
```  
> npm install tedious  
```  
