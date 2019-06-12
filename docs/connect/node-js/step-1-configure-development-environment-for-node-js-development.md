---
title: 'Schritt 1: Konfigurieren der Entwicklungsumgebung für Node.js-Entwicklung | Microsoft-Dokumentation'
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
manager: jroth
ms.openlocfilehash: 49522e397789c5193ed8f218a5fdf776ba62f001
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799363"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die Node.js-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen zu konfigurieren, um die Entwicklung einer Anwendung mithilfe der Node.js-Treiber für SQL Server.  Die am häufigsten verwendete Methode ist die Verwendung den Node Package Manager (Npm) zum Installieren des Moduls mühsam, aber Sie können das mühsame Modul direkt am [Github](https://github.com/pekim/tedious) Falls gewünscht.  
  
Beachten Sie, dass die Node.js-Treiber TDS-Protokolls, die standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren Sie Node.js-Laufzeit und Npm-Paket-manager**  
A. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Windows Installer Msi-Link.   
c. Nach dem Herunterladen, führen Sie die MSI-Datei, um Node.js zu installieren.  
  
2. **Öffnen von cmd.exe**  
  
3. **Erstellen Sie ein Projektverzeichnis** und navigieren Sie dorthin.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Erstellen Sie ein Node-Projekte.**  Wenn Sie die Standardwerte während der Erstellung von Projekten beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sollte die Datei "package.json" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> npm init  
```  
  
5. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Open-terminal**  
  
2. **Installieren Sie Node.js-Laufzeit**  
```  
>sudo apt-get install node  
```  
3. **Installieren Sie Npm (Knoten-Paket-Manager)**  
```  
> sudo apt-get install npm  
```  
4. **Erstellen Sie ein Projektverzeichnis** und navigieren Sie dorthin.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Erstellen Sie ein Node-Projekte.**  Wenn Sie die Standardwerte während der Erstellung von Projekten beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sollte die Datei "package.json" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> sudo npm init  
```  
  
6. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren Sie Node.js-Laufzeit und Npm-Paket-manager**  
A. Wechseln Sie zu [Node.js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Link für die Mac OS-Installer.  
c. Nach dem Herunterladen, führen Sie die Dmg, um Node.js zu installieren.  
  
2. **Open-terminal**  
  
3. **Erstellen Sie ein Projektverzeichnis** und navigieren Sie dorthin.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Erstellen Sie ein Node-Projekte.**  Wenn Sie die Standardwerte während der Erstellung von Projekten beibehalten möchten, drücken Sie die EINGABETASTE, bis das Projekt erstellt wurde. Am Ende dieses Schritts sollte die Datei "package.json" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> npm init  
```  
  
5. **Installieren Sie mühsam-Modul in Ihrem Projekt ein.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet wird, um die Kommunikation mit SQL Server.  
```  
> npm install tedious  
```  
  
