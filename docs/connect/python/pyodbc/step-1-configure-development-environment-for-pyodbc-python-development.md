---
title: 'Schritt 1: Konfigurieren der pyodbc-Python-Umgebung'
description: Schritt 1 dieses Leitfadens für die ersten Schritte umfasst die Installation von Python, des Microsoft ODBC Driver for SQL Server und von pyODBC in der Entwicklungsumgebung.
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ea669649767f55598190093b7c929f5bd8db27f
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528514"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Schritt 1: Konfigurieren von Entwicklungsumgebung für pyodbc-Python

## <a name="windows"></a>Windows  
Herstellen von Verbindungen mit SQL-Datenbanken mithilfe der pyodbc-Python-Entwicklungsumgebung unter Windows
  
1. **Laden Sie das Python-Installationsprogramm herunter.**  
  Installieren Sie Python, wenn das Programm nicht auf Ihrem Computer vorhanden ist. Navigieren Sie zur [Python-Downloadseite](https://www.python.org/downloads/windows/), und laden Sie das entsprechende Installationsprogramm herunter. Wenn Sie beispielsweise auf einem 64-Bit-Computer arbeiten, laden Sie das Installationsprogramm für Python 2.7 oder 3.7 (x64) herunter.  
  
2. **Installieren Sie Python**.  Führen Sie die folgenden Schritte aus, nachdem das Installationsprogramm heruntergeladen wurde: a. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten. b. Wählen Sie die gewünschte Sprache aus, und stimmen Sie den Bedingungen zu. c. Befolgen Sie die Anweisungen auf dem Bildschirm. Python sollte dann auf dem Computer installiert werden. d. Sie können überprüfen, ob Python installiert wurde, indem Sie zu `C:\Python27` oder `C:\Python37` navigieren und `python -V` oder `py -V` (für Version 3.x) ausführen. 
      
3. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Windows.** ](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Öffnen Sie cmd.exe als Administrator.**     

5. **Installieren Sie pyodbc mithilfe des PIP-Python-Paket-Managers.** (Ersetzen Sie `C:\Python27\Scripts` durch den installierten Python-Pfad.)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Herstellen einer Verbindung mit SQL-Datenbank mithilfe von Python (pyodbc):
  
1. **Öffnen Sie ein Terminal.**  

2. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Linux.** ](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installieren Sie pyodbc.**  
```  
> sudo -H pip install pyodbc
```
