---
title: 'Schritt 1: Konfigurieren der pymssql-python-Entwicklungsumgebung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 5bf2942b79cf7e72efbb36a53019de8208cd3b8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935826"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die pymssql-Python-Entwicklung
Sie müssen Ihre Entwicklungsumgebung mit den Voraussetzungen konfigurieren, um eine Anwendung mit dem python-Treiber für die SQL Server zu entwickeln.    
  
Beachten Sie, dass die python-SQL-Treiber das TDS-Protokoll verwenden, das standardmäßig in SQL Server und Azure SQL-Datenbank aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren der python-Laufzeit und des PIP-Paket-Managers**  
A. Gehe zu [python.org](https://www.python.org/downloads/)  
B. Klicken Sie auf den entsprechenden Windows Installer-MSI-Link.   
c. Nach dem herunterladen die MSI-Datei zum Installieren der python-Laufzeit  
  
2. **Pymssql-Modul** [hier herunterladen](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Stellen Sie sicher, dass Sie die richtige WHL-Datei auswählen.  Wenn Sie z. b. python 2,7 auf einem 64-Bit-Computer verwenden, wählen Sie: pymssql-2.1.1-cp27-None-win_amd64. WHL aus. Nachdem Sie die WHL-Datei heruntergeladen haben, platzieren Sie Sie im Ordner "C:/Python27".  
      
3. **Öffnen Sie "cmd. exe"**  
  
4. **Installieren des pymssql-Moduls**     
    Wenn Sie z. b. python 2,7 auf einem 64-Bit-Computer verwenden:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installieren der python-Laufzeit und des PIP-Paket-Managers**  Python ist bei den meisten Distributionen von Ubuntu vorinstalliert.  Wenn auf Ihrem Computer python nicht installiert ist, können Sie entweder den Quell-Tarball aus [python.org](https://www.python.org/downloads/) herunterladen und lokal erstellen, oder Sie können den Paket-Manager verwenden:  
```  
> sudo apt-get install python   
```  
  
2.  **Terminal öffnen**  
  
3.  **Installieren des pymssql-Moduls und der Abhängigkeiten**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren der python-Laufzeit und des PIP-Paket-Managers**  
A. Gehe zu [python.org](https://www.python.org/downloads/)  
B. Klicken Sie auf den entsprechenden Mac-Installer pkg-Link.   
c. Nach dem herunterladen das pkg zum Installieren der python-Laufzeit ausführen  
  
2.  **Terminal öffnen**  
  
3. **Installieren des Homebrew-Paket-Managers**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installieren des freetds-Moduls**  
```  
> brew install FreeTDS  
```  
  
5.  **Installieren des pymssql-Moduls**  
```  
> sudo -H pip install pymssql  
```
