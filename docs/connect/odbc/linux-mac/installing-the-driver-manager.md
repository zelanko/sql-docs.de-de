---
title: Installieren des Treiber-Managers
description: Dieser Artikel enthält Anweisungen zum Installieren des unixODBC-Treiber-Managers für die Verwendung mit allen Versionen von Microsoft ODBC Driver for SQL Server unter Linux und macOS.
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba758f3c95ef3285424cafe676df46e5d3df7b34
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528244"
---
# <a name="installing-the-driver-manager"></a>Installieren des Treiber-Managers
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Dieser Artikel enthält Anweisungen, um den UnixODBC Treiber-Manager für die Verwendung mit allen Versionen von Microsoft ODBC Driver für SQL Server unter Linux und MacOS zu installieren.  

> [!IMPORTANT]  
> Löschen Sie alle Treiber-Manager-Pakete, die auf Ihrem Computer installiert sind, bevor Sie den unixODBC Treiber-Manager installieren. Die Installation des unixODBC Treiber-Managers kann einen Fehler eines vorhandenen Treiber-Managers verursachen.  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-13-131-and-17"></a>Installieren des Treiber-Managers für Microsoft ODBC Driver 13, 13.1 und 17
Die Abhängigkeit des Treiber-Managers wird durch das Paketverwaltungssystem automatisch aufgelöst, wenn Sie Microsoft ODBC Driver 13, 13.1 oder 17 for SQL Server für Linux oder macOS mithilfe der Anweisungen in den folgenden Artikeln installieren:

- [Installieren von Microsoft ODBC Driver for SQL Server unter Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installieren von Microsoft ODBC Driver for SQL Server unter macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Installieren des Treiber-Managers für Microsoft ODBC Driver 11 (Preview) for SQL Server.  

(SUSE und Red Hat Linux nur.)

**Verwenden des Installationsskripts**  
  
> [!IMPORTANT]  
> Diese Anleitung bezieht sich auf `msodbcsql-11.0.2270.0.tar.gz`, die Installationsdatei für Red Hat Linux. Wenn Sie die Vorschauversion von SUSE Linux installieren, ist der Dateiname `msodbcsql-11.0.2260.0.tar.gz`.  

Installieren des Treiber-Managers:  
  
1.  Stellen Sie sicher, dass Sie die Root-Berechtigung besitzen.  
  
2.  Wechseln Sie zu dem Verzeichnis, in dem der [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-ODBC Driver-Download die Datei `msodbcsql-11.0.2270.0.tar.gz` platziert hat. Stellen Sie sicher, dass Sie die zu Ihrer Linux-Version passende Datei „ \*.tar.g“ besitzen. Führen Sie den folgenden Befehl aus, um die Dateien zu extrahieren: **tar xvzf msodbcsql-11.0.2270.0.tar.gz**.  

3.  Wechseln Sie zum Verzeichnis `msodbcsql-11.0.2270.0`, das eine Datei namens `build_dm.sh` enthalten sollte. Sie können ausführen `build_dm.sh` um den UnixODBC Treiber-Manager zu installieren.

4.  Um eine Liste der verfügbaren Optionen anzuzeigen, geben Sie den folgenden Befehl ein: **./build_dm.sh --help**.  
  
5.  Wenn Sie zur Installation bereit sind und Ihr Computer auf eine externe Website über FTP zugreifen kann, führen Sie den folgenden Befehl aus: **./build_dm.sh**.

Wenn Ihr Computer auf keine externe Website über FTP zugreifen kann, laden Sie `unixODBC-2.3.0.tar.gz` herunter. Sie können `unixODBC-2.3.0.tar.gz` von [http://www.unixodbc.org](http://www.unixodbc.org/) abrufen. Klicken Sie auf den Link **Herunterladen** links auf der Seite, um zur Downloadseite zu wechseln. Klicken Sie dann auf den entsprechenden Link, um unixODBC-2.3.0 (nicht unixODBC-2.3.1) herunterzuladen. unixODBC-2.3.1 wird von dieser Version des [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht unterstützt. Führen Sie den folgenden Befehl aus, um den UnixODBC Treiber-Manager-Installation zu beginnen: **./build_dm.sh --download-url=file://unixODBC-2.3.0.tar.gz**.  

6.  Geben Sie **JA** ein, um mit dem Entpacken der Dateien fortzufahren. Dieser Teil des Prozesses kann bis zu fünf Minuten in Anspruch nehmen.  

7.  Nachdem das Skript beendet ist, befolgen Sie die Anweisungen auf dem Bildschirm, um den unixODBC Treiber-Manager zu installieren.

Sie können nun den Treiber installieren. Weitere Informationen finden Sie in den Installationsanweisungen für den ODBC-Treiber für [Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) oder [macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).

**Manuelle Installation**

Wenn das Skript für die Installation nicht abgeschlossen werden konnte, konfigurieren und erstellen Sie selbst den richtigen Treiber-Manager.

1.  Entfernen Sie alle älteren installierten Versionen von unixODBC (z. B. unixODBC 2.2.11). Führen Sie den folgenden Befehl auf Red Hat Enterprise Linux 5 oder 6 aus: **yum remove unixODBC**. Auf SUSE Linux Enterprise: **Zypper entfernen UnixODBC**.  
  
2.  Wechseln Sie zu [http://www.unixodbc.org](http://www.unixodbc.org/). Klicken Sie auf den Link **Herunterladen** links auf der Seite, um zur Downloadseite zu wechseln. Klicken Sie dann auf den entsprechenden Link, um die Datei „unixodbc-2.3.0.tar.gz“ auf Ihrem Computer zu speichern. UnixODBC-2.3.1 wird von dieser Version des [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht unterstützt.  
  
3.  Führen Sie den Befehl auf Ihrem Linux-Computer: **tar xvzf unixODBC-2.3.0.tar.gz**.  
  
4.  Wechseln Sie zum Verzeichnis „unixODBC-2.3.0“.  
  
5.  Führen Sie den folgenden Befehl in einer Eingabeaufforderung aus: **CPPFLAGS="-DSIZEOF_LONG_INT=8"** .  
  
6.  Führen Sie an einer Eingabeaufforderung den Befehl: **export CPPFLAGS**.  
  
7.  Führen Sie an einer Eingabeaufforderung den Befehl: **"./configure --prefix=/usr --libdir=/usr/lib64 --sysconfdir=/etc --enable-gui=no --enable-drivers=no --enable-iconv --with-iconv-char-enc=UTF8 --with-iconv-ucode-enc=UTF16LE"** .  
  
8.  Nach der Eingabeaufforderung (angemeldet als Root) führen Sie den Befehl **make** aus.  
  
9. Nach der Eingabeaufforderung (angemeldet als Root) führen Sie den Befehl **make install** aus.  

Sie können nun den Treiber installieren. Weitere Informationen finden Sie in den Installationsanweisungen für den ODBC-Treiber für [Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) oder [macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).
  
## <a name="see-also"></a>Weitere Informationen

- [Installieren von Microsoft ODBC Driver for SQL Server unter Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installieren von Microsoft ODBC Driver for SQL Server unter macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
- [Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)
