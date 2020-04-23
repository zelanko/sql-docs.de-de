---
title: Installieren des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Hier finden Sie Informationen zum Installieren und Deinstallieren des OLE DB-Treibers für SQL Server. Zum Installieren des OLE DB-Treibers für SQL Server benötigen Sie das Installationsprogramm „msoledbsql.msi“.
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b971b7e537cecc7e94c87e2692707594fda9aebc
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528395"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installieren des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Zum Installieren des OLE DB-Treibers für SQL Server benötigen Sie das Installationsprogramm „msoledbsql.msi“.
Führen Sie das Installationsprogramm aus, und treffen Sie Ihre bevorzugte Auswahl. Der OLE DB-Treiber für SQL Server kann parallel zu früheren Versionen von Microsoft OLE DB-Anbietern installiert werden.

Die Dateien des OLE DB-Treibers für SQL Server („msoledbsql.dll“, „msoledbsqlr.rll“) werden in `%SYSTEMROOT%\system32\` installiert. Außerdem installiert die x64-msoledbsql.msi-Datei 32-Bit-Binärdateien in `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Alle entsprechenden Registrierungseinstellungen für den OLE DB-Treiber für SQL Server werden im Rahmen des Installationsprozesses festgelegt.  

Die Header- und Bibliotheksdateien des OLE DB-Treibers für SQL Server („msoledbsql.h“ und „msoledbsql.lib“) werden in `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK` installiert. Außerdem installiert die x64-msoledbsql.msi-Datei dieselben Dateien in `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`.  

Sie können den OLE DB-Treiber für SQL Server über „msoledbsql.msi“ verteilen. Möglicherweise müssen Sie den OLE DB-Treiber für SQL Server bei der Bereitstellung einer Anwendung installieren. Eine Möglichkeit, mehrere Pakete in mehreren Installationen, die für den Benutzer wie eine Installation aussehen, zu installieren, besteht in der Verwendung der Chainer- und Bootstrappertechnologie. Weitere Informationen finden Sie unter [Authoring a Custom Bootstrapper Package for Visual Studio 2005 (Erstellen eines benutzerdefinierten Bootstrapper-Pakets für Visual Studio 2005)](https://go.microsoft.com/fwlink/?LinkId=115667) und [Adding Custom Prerequisites (Hinzufügen benutzerdefinierter Voraussetzungen)](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
Die x64-msoledbsql.msi-Datei installiert auch die 32-Bit-Version des OLE DB-Treibers für SQL Server. Wenn Ihre Anwendung für eine andere Plattform als für diejenige vorgesehen ist, auf der sie entwickelt wurde, können Sie Versionen von „msoledbsql.msi“ für x64 und x86 herunterladen.

Wenn Sie „msoledbsql.msi“ aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe des OLE DB-Treibers für SQL Server entwickelten Anwendung unterstützen. Um auch die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=All` in der Befehlszeile an. Beispiel:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installation im Hintergrund  
 Wenn Sie die Optionen „/passive“, „/qn“, „/qb“ oder „/qr“ mit „msiexec“ verwenden, müssen Sie auch IACCEPTSQLNCLILICENSETERMS=YES angeben, um explizit anzuzeigen, dass Sie den Lizenzbedingungen zustimmen. Diese Option muss in Großbuchstaben angegeben werden.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installieren des OLE DB-Treibers für SQL Server als Abhängigkeit  
Es ist wichtig, den OLE DB-Treiber für SQL Server erst zu deinstallieren, wenn alle abhängigen Anwendungen deinstalliert wurden. Damit Benutzern eine Warnung angezeigt wird, dass die Anwendung vom OLE DB-Treiber für SQL Server abhängt, verwenden Sie die Installationsoption APPGUID wie folgt im MSI:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Der an APPGUID übergebene Wert ist Ihr spezifischer Produktcode. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden.
Die Option APPGUID erfordert, dass das Installationsprogramm von einer Eingabeaufforderung mit erhöhten Rechten aus ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
