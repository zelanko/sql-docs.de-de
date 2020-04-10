---
title: 'Schritt 1: Konfigurieren der pymssql-Python-Entwicklungsumgebung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3310f268bf04b015c5f80cd08b2ae3909fd3a5c2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926803"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Schritt 1: Konfigurieren der Entwicklungsumgebung für die pymssql-Python-Entwicklung
Sie müssen Ihre Entwicklungsumgebung entsprechend den Voraussetzungen konfigurieren, um mithilfe des Python-Treibers für SQL Server eine Anwendung entwickeln zu können.    
  
Beachten Sie, dass der Python-SQL-Treiber das TDS-Protokoll verwendet, das in SQL Server und Azure SQL-Datenbank standardmäßig aktiviert ist.  Es ist keine zusätzliche Konfiguration erforderlich.  
  
## <a name="windows"></a>Windows  
  
1. **Installieren der Python-Runtime und des pip-Paket-Managers**  
a. Gehen Sie zu [python.org](https://www.python.org/downloads/).  
b. Klicken Sie auf den Link für das gewünschten Windows-Installationsprogramm (MSI-Datei).   
c. Wenn der Download abgeschlossen ist, führen Sie die MSI-Datei aus, um die Python-Runtime zu installieren.  
  
2. **Das pymssql-Modul** können Sie [hier](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql) herunterladen.  
  
    Stellen Sie sicher, dass Sie die richtige WHL-Datei auswählen.  Beispiel: Wählen Sie bei Verwendung von Python 2.7 auf einem 64-Bit-Computer die Datei „pymssql‑2.1.1‑cp27‑none‑win_amd64.whl“ aus. Speichern Sie die WHL-Datei nach dem Herunterladen im Ordner „C:/Python27“.  
      
3. **Öffnen Sie „cmd.exe“.**  
  
4. **Installieren Sie das pymssql-Modul.**      
    Wenn Sie beispielsweise Python 2.7 auf einem 64-Bit-Computer verwenden, funktioniert das folgendermaßen:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installieren Sie die Python-Runtime und den pip-Paket-Manager.** Python ist auf den meisten Ubuntu-Distributionen bereits vorinstalliert.  Wenn auf Ihrem Computer kein Python installiert ist, können Sie entweder den Quelltarball von [python.org](https://www.python.org/downloads/) herunterladen und lokale Builds erstellen oder den Paket-Manager verwenden:  
```  
> sudo apt-get install python   
```  
  
2.  **Öffnen Sie ein Terminal.**  
  
3.  **Installieren Sie das pymssql-Modul und alle Abhängigkeiten.**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installieren der Python-Runtime und des pip-Paket-Managers**  
a. Gehen Sie zu [python.org](https://www.python.org/downloads/).  
b. Klicken Sie auf den entsprechenden Link für das Mac-Installationsprogramm (pkg).   
c. Wenn der Download abgeschlossen ist, führen Sie die PKG-Datei aus, um die Python-Runtime zu installieren.  
  
2.  **Öffnen Sie ein Terminal.**  
  
3. **Installieren Sie den Homebrew-Paket-Manager.**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installieren Sie das FreeTDS-Modul.**  
```  
> brew install FreeTDS  
```  
  
5.  **Installieren Sie das pymssql-Modul.**  
```  
> sudo -H pip install pymssql  
```
