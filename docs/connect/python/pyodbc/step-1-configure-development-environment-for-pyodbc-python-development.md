---
title: 'Schritt 1: Konfigurieren der pyodbc-python-Entwicklungsumgebung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a1a43540d866faaf79b1c020eb255689862e6d97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992523"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Schritt 1: Konfigurieren von Entwicklungsumgebung für Pyodbc-Python

## <a name="windows"></a>Windows  
Stellen Sie mithilfe von python-pyodbc unter Windows eine Verbindung mit SQL-Datenbank her:
  
1. **Herunterladen des python-Installers**.  
  Wenn Ihr Computer nicht über python verfügt, installieren Sie ihn. Wechseln Sie zur [python-Downloadseite](https://www.python.org/downloads/windows/) , und laden Sie den entsprechenden Installer herunter. Wenn Sie sich z. b. auf einem 64-Bit-Computer befinden, laden Sie das Installationsprogramm für python 2,7 oder 3,7 (x64) herunter.  
  
2. **Installieren Sie Python**.  Nachdem das Installationsprogramm heruntergeladen wurde, führen Sie die folgenden Schritte aus: a. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten. B. Wählen Sie Ihre Sprache aus, und stimmen Sie den Bedingungen zu. c. Befolgen Sie die Anweisungen auf dem Bildschirm, und python sollte auf dem Computer installiert sein. d. Sie können überprüfen, ob python installiert ist, `C:\Python27` indem `C:\Python37` Sie zu `python -V` oder `py -V` ausführen und oder (für 3. x) ausführen. 
      
3. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Windows.** ](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Öffnen Sie "cmd. exe" als Administrator.**     

5. **Installieren von pyodbc mithilfe von PIP-Python-Paket-Manager** (Durch `C:\Python27\Scripts` den installierten Python-Pfad ersetzen)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Stellen Sie mithilfe von python-pyodbc eine Verbindung mit SQL-Datenbank her:
  
1. **Terminal öffnen**  

2. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Linux.** ](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installieren von pyodbc**  
```  
> sudo -H pip install pyodbc
```
