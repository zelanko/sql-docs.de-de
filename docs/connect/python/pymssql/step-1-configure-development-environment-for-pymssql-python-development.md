---
title: 'Schritt 1: Konfigurieren von Pymssql-Python-Entwicklungsumgebung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b60c7aa0f53be6d9c9a249c69ace6780a318e6f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787448"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die pymssql-Python-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen zu konfigurieren, um die Entwicklung einer Anwendung, die mit den Python-Treiber für SQL Server.    
  
Beachten Sie, dass die Python-SQL-Treiber TDS-Protokolls, die standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren von Python-Laufzeit und pip-Paket-manager**  
A. Wechseln Sie zu [python.org](https://www.python.org/downloads/)  
B. Klicken Sie auf den entsprechenden Windows Installer Msi-Link.   
c. Einmal heruntergeladene führen Sie die MSI-Datei zum Installieren von Python-Laufzeit  
  
2. **Herunterladen des Pymssql-Moduls** aus [hier](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Stellen Sie sicher, dass Sie die richtige Whl-Datei auswählen.  Zum Beispiel: Wählen Sie bei Verwendung von Python 2.7 auf einem 64-Bit-Computer: Pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. Nachdem Sie herunterladen, die whl-Datei platzieren Sie es in der der Ordner "C:/Python27".  
      
3. **Öffnen von cmd.exe**  
  
4. **Installieren Sie Pymssql-Modul**     
    Beispielsweise bei Verwendung von Python 2.7 auf einem 64-Bit-Computer:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installieren von Python-Laufzeit und pip-Paket-Manager** Python ist für die meisten Distributionen von Ubuntu vorinstalliert.  Wenn Ihr Computer keinen Python installiert, erhalten Sie Download aus dem Quell-tarballs [python.org](https://www.python.org/downloads/) lokal erstellen und Sie können den Paket-Manager verwenden:  
```  
> sudo apt-get install python   
```  
  
2.  **Open-terminal**  
  
3.  **Installieren Sie Pymssql-Modul und Abhängigkeiten**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren von Python-Laufzeit und pip-Paket-manager**  
A. Wechseln Sie zu [python.org](https://www.python.org/downloads/)  
B. Klicken Sie auf den entsprechenden Mac-Installer-Pkg-Link.   
c. Einmal heruntergeladene führen Sie das Pkg zum Installieren von Python-Laufzeit  
  
2.  **Open-terminal**  
  
3. **Installieren Sie Homebrew-Paket-manager**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installieren von FreeTDS-Modul**  
```  
> brew install FreeTDS  
```  
  
5.  **Installieren Sie Pymssql-Modul**  
```  
> sudo -H pip install pymssql  
```
