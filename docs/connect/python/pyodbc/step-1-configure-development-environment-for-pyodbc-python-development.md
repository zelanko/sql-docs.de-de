---
title: 'Schritt 1: Konfigurieren von Pyodbc-Python-Entwicklungsumgebung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f588174ea80677066628cb3e756d7c38bd42fba
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2018
ms.locfileid: "42786714"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Schritt 1: Konfigurieren von Entwicklungsumgebung für Pyodbc-Python

## <a name="windows"></a>Windows  
Herstellen einer Verbindung mit SQL-Datenbank mithilfe von Python - Pyodbc unter Windows:
  
1. **Python-Installationsprogramm herunterladen**.  
  Wenn Ihr Computer keinen Python, installieren Sie ihn aus. Wechseln Sie zu der [Python-Downloadseite](https://www.python.org/downloads/windows/) und Laden Sie das entsprechende Installationsprogramm herunter. Wenn Sie auf einem 64-Bit-Computer sind, laden Sie z. B. den Python 2.7- oder den 3.7 (x 64)-Installer.  
  
2. **Installieren Sie Python**.  Sobald das Installationsprogramm heruntergeladen wurde, gehen Sie folgendermaßen vor: ein. Doppelklicken Sie auf die Datei, um das Installationsprogramm zu starten. B. Wählen Sie Ihre Sprache aus, und stimmen Sie den Bedingungen. c. Befolgen Sie die Anweisungen auf dem Bildschirm und Python auf Ihrem Computer installiert werden soll. d. Sie können überprüfen, ob Python installiert ist, indem Sie zu `C:\Python27` oder `C:\Python37` , und führen Sie `python -V` oder `py -V` (für 3.x) 
      
3. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Windows.**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Öffnen Sie als Administrator cmd.exe**     

5. **Mithilfe von Pip - Python-Paket-Manager "Pyodbc" installieren** (ersetzen Sie dies `C:\Python27\Scripts` mit den installierten Python-Pfad)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Herstellen einer Verbindung mit SQL-Datenbank mithilfe von Python - Pyodbc:
  
1. **Open-terminal**  

2. [**Installieren Sie Microsoft ODBC Driver for SQL Server unter Linux.**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **"Pyodbc" installieren**  
```  
> sudo -H pip install pyodbc
```
