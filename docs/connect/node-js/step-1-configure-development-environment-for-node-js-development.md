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
ms.openlocfilehash: bce89cc12c7493522de55adffb69fcbe3307cbdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003760"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die Node.js-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen konfigurieren, um eine Anwendung mit dem Node. js-Treiber für die SQL Server zu entwickeln.  Die häufigste Methode ist die Verwendung des Node Package Manager (NPM), um das mühsame Modul zu installieren, aber Sie können das mühsame Modul direkt auf [GitHub](https://github.com/pekim/tedious) herunterladen, wenn Sie dies bevorzugen.  
  
Beachten Sie, dass der Node. js-Treiber das TDS-Protokoll verwendet, das standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren der Node. js-Laufzeit und des NPM-Paket-Managers**  
A. Gehe zu [node. js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Windows Installer-MSI-Link.   
c. Führen Sie nach dem herunterladen die MSI aus, um Node. js zu installieren  
  
2. **Öffnen Sie "cmd. exe"**  
  
3. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu dem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Erstellen Sie ein Node-Projekt.**  Zum Beibehalten der Standardwerte während der Projekt Erstellung drücken Sie die EINGABETASTE, bis das Projekt erstellt wird. Am Ende dieses Schritts sollte die Datei "Package. JSON" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> npm init  
```  
  
5. **Installieren Sie das mühsame Modul in Ihrem Projekt.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet, um mit SQL Server zu kommunizieren.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Terminal öffnen**  
  
2. **Installieren der Node. js-Laufzeit**  
```  
>sudo apt-get install node  
```  
3. **Installieren von NPM (Knoten Paket-Manager)**  
```  
> sudo apt-get install npm  
```  
4. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu dem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Erstellen Sie ein Node-Projekt.**  Zum Beibehalten der Standardwerte während der Projekt Erstellung drücken Sie die EINGABETASTE, bis das Projekt erstellt wird. Am Ende dieses Schritts sollte die Datei "Package. JSON" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> sudo npm init  
```  
  
6. **Installieren Sie das mühsame Modul in Ihrem Projekt.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet, um mit SQL Server zu kommunizieren.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren der Node. js-Laufzeit und des NPM-Paket-Managers**  
A. Gehe zu [node. js](https://nodejs.org/en/download/)  
B. Klicken Sie auf den entsprechenden Mac OS installerlink.  
c. Führen Sie nach dem herunterladen das dmg aus, um Node. js zu installieren.  
  
2. **Terminal öffnen**  
  
3. **Erstellen Sie ein Projektverzeichnis** , und navigieren Sie zu dem Verzeichnis.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Erstellen Sie ein Node-Projekt.**  Zum Beibehalten der Standardwerte während der Projekt Erstellung drücken Sie die EINGABETASTE, bis das Projekt erstellt wird. Am Ende dieses Schritts sollte die Datei "Package. JSON" in Ihrem Projektverzeichnis angezeigt werden.  
```  
> npm init  
```  
  
5. **Installieren Sie das mühsame Modul in Ihrem Projekt.**  Dies ist die Implementierung des TDS-Protokolls, das der Treiber verwendet, um mit SQL Server zu kommunizieren.  
```  
> npm install tedious  
```  
  
