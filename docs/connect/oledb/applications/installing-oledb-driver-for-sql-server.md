---
title: Installieren des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Installieren und Deinstallieren von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
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
manager: craigg
ms.openlocfilehash: f47573e6ecc1e7aa4770c8d1ae34768e09720d25
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800658"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installieren des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Zum Installieren der OLE DB-Treiber für SQL Server benötigen Sie msoledbsql.msi-Installer.
Führen Sie das Installationsprogramm aus, und treffen Sie Ihre bevorzugte Auswahl. Der OLE DB-Treiber für SQL Server kann installierte Seite-an-Seite mit früheren Versionen von Microsoft OLE DB-Anbieter sein.

Der OLE DB-Treiber für SQL Server-Datenbankdateien (msoledbsql.dll, msoledbsqlr.rll) werden im installiert `%SYSTEMROOT%\system32\` . Darüber hinaus die msoledbsql.msi installiert die 32-Bit-Binärdateien in X64 `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Alle entsprechenden registrierungseinstellungen für den OLE DB-Treiber für SQL Server werden im Rahmen des Installationsvorgangs vorgenommen.  

Der OLE DB-Treiber für SQL Server-Header- und-Bibliotheksdateien (msoledbsql.h und msoledbsql.lib) werden im installiert `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`. Darüber hinaus die msoledbsql.msi die gleichen Dateien in installiert X64 `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`.  

Sie können den OLE DB-Treiber für SQL Server über msoledbsql.msi verteilen. Sie müssen möglicherweise OLE DB-Treiber für SQL Server installieren, wenn Sie eine Anwendung bereitstellen. Eine Möglichkeit, mehrere Pakete in mehreren Installationen, die für den Benutzer wie eine Installation aussehen, zu installieren, besteht in der Verwendung der Chainer- und Bootstrappertechnologie. Weitere Informationen finden Sie unter [Authoring a Custom Bootstrapper Package for Visual Studio 2005 (Erstellen eines benutzerdefinierten Bootstrapper-Pakets für Visual Studio 2005)](http://go.microsoft.com/fwlink/?LinkId=115667) und [Adding Custom Prerequisites (Hinzufügen benutzerdefinierter Voraussetzungen)](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
Die X64 msoledbsql.msi wird auch die 32-Bit-Version des OLE DB-Treiber für SQL Server installiert. Wenn Ihre Anwendung eine andere Zielplattform als die vorgesehen, die es entwickelt wurde ist, können Sie Versionen von msoledbsql.msi X64 und X86 herunterladen.

Wenn Sie „msoledbsql.msi“ aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe des OLE DB-Treibers für SQL Server entwickelten Anwendung unterstützen. Um auch die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=All` in der Befehlszeile an. Zum Beispiel:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installation ohne Eingreifen  
 Wenn Sie die Optionen „/passive“, „/qn“, „/qb“ oder „/qr“ mit „msiexec“ verwenden, müssen Sie auch IACCEPTSQLNCLILICENSETERMS=YES angeben, um explizit anzuzeigen, dass Sie den Lizenzbedingungen zustimmen. Diese Option muss in Großbuchstaben angegeben werden.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installieren des OLE DB-Treiber für SQLServer als Abhängigkeit  
Es ist wichtig, keine OLE DB-Treiber für SQL Server deinstallieren, bis alle abhängigen Anwendungen deinstalliert werden. Verwenden Sie, um Benutzern mit einer Warnung zu ermöglichen, dass Ihre Anwendung auf OLE DB-Treiber für SQL Server abhängig ist, die Installationsoption APPGUID im MSI wie folgt:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Der an APPGUID übergebene Wert ist Ihr spezifischer Produktcode. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden.
Der APPGUID-Option ist erforderlich, das Installationsprogramm über eine Eingabeaufforderung mit erhöhten Rechten ausführen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
