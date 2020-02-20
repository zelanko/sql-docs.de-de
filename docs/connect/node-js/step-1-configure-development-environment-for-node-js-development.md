---
title: 'Schritt 1:  Konfigurieren der Entwicklungsumgebung für die Node.js-Entwicklung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bce89cc12c7493522de55adffb69fcbe3307cbdf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68003760"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Schritt 1:  Konfigurieren der Entwicklungsumgebung für die Node.js-Entwicklung
Sie müssen Ihre Entwicklungsumgebung entsprechend den Voraussetzungen konfigurieren, um mithilfe des Node.js-Treibers für SQL Server eine Anwendung entwickeln zu können.  Die gängigste Methode besteht darin, den Node Package Manager (npm) zu verwenden, um das Tedious-Modul zu installieren. Sie können das Tedious-Modul aber auch direkt von [GitHub](https://github.com/pekim/tedious) herunterladen.  
  
Beachten Sie, dass der Node.js-Treiber das TDS-Protokoll verwendet, das in SQL Server und Azure SQL-Datenbank standardmäßig aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren von Node.js-Runtime und Node Package Manager (npm)**  
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
  
5. **Installieren des Tedious-Moduls in Ihrem Projekt**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber zur Kommunikation mit SQL Server verwendet.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Öffnen eines Terminals**  
  
2. **Installieren der Node.js-Runtime**  
```  
>sudo apt-get install node  
```  
3. **Installieren von npm (Node Package Manager)**  
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
  
6. **Installieren des Tedious-Moduls in Ihrem Projekt**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber zur Kommunikation mit SQL Server verwendet.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren von Node.js-Runtime und Node Package Manager (npm)**  
a. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/).  
b. Klicken Sie auf den entsprechenden Link für das Mac OS-Installationsprogramm.  
c. Wenn der Download abgeschlossen ist, führen Sie die DMG-Datei aus, um Node.js zu installieren.  
  
2. **Öffnen eines Terminals**  
  
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
  
