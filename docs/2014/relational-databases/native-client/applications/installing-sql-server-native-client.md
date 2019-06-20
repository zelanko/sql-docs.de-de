---
title: Installieren von SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71438a61dcaec201d0b3ae21eb7e27d979029204
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046355"
---
# <a name="installing-sql-server-native-client"></a>Installieren von SQL Server Native Client
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 wird bei der Installation von [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] installiert. Es gibt keinen [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client. Weitere Informationen finden Sie unter [Neuigkeiten in SQL Server Native Client](../sql-server-native-client.md). Sie können sqlncli.msi auch von der SQL Server 2012 Feature Pack-Webseite herunterladen. Um die neueste Version von SQL Server Native Client herunterzuladen, wechseln Sie zu [Microsoft?? SqlServer? 2012 SP2 Feature Pack](https://www.microsoft.com/en-us/download/details.aspx?id=43339). Wenn auf dem Computer auch eine frühere Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als SQL Server 2012 installiert ist, wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 parallel zur früheren Version installiert.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Dateien (sqlncli11.dll, sqlnclir11.rll und s11ch_sqlncli.chm) werden in folgendem Verzeichnis installiert:  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Während des Installationsvorgangs werden alle erforderlichen Registrierungseinstellungen für den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und den ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vorgenommen.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und -Bibliotheksdateien (sqlncli.h und sqlncli11.lib) werden in folgendem Verzeichnis installiert:  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Neben der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client im Rahmen der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt es die Möglichkeit der Installation mithilfe des verteilbaren Installationsprogramms sqlncli.msi, das sich auf dem Installationsdatenträger von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in folgendem Verzeichnis befindet: `%CD%\Setup\`.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client können Sie über sqlncli.msi verteilen. Möglicherweise müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client bei der Bereitstellung einer Anwendung installieren. Eine Möglichkeit, mehrere Pakete in mehreren Installationen, die für den Benutzer wie eine Installation aussehen, zu installieren, besteht in der Verwendung der Chainer- und Bootstrappertechnologie. Weitere Informationen finden Sie unter [Authoring a Custom Bootstrapper Package for Visual Studio 2005 (Erstellen eines benutzerdefinierten Bootstrapper-Pakets für Visual Studio 2005)](https://go.microsoft.com/fwlink/?LinkId=115667) und [Adding Custom Prerequisites (Hinzufügen benutzerdefinierter Voraussetzungen)](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Mit der x64-Version und der Itanium-Version von sqlncli.msi wird auch die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert. Wenn Ihre Anwendung für eine andere Plattform als für diejenige vorgesehen ist, auf der sie entwickelt wurde, können Sie Versionen von sqlncli.msi für x64, Itanium und x86 vom Microsoft Download Center herunterladen.  
  
 Wenn Sie sqlncli.msi aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Die Clientkomponenten sind Dateien, die Unterstützung zum Ausführen einer Anwendung, die mit entwickelt wurde [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Um auch die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=All` in der Befehlszeile an. Zum Beispiel:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation ohne Eingreifen  
 Wenn Sie die /passiv, /qn, /qb, oder /qr-Option mit msiexec verwenden, müssen Sie auch IACCEPTSQLNCLILICENSETERMS=YES angeben, um explizit anzuzeigen, dass Sie den Bestimmungen der Endbenutzerlizenz zustimmen. Diese Option muss in Großbuchstaben angegeben werden.  
  
## <a name="uninstalling-sql-server-native-client"></a>Deinstallieren von SQL Server Native Client  
 Da Anwendungen, z. B. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Server und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tools hängt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, es ist wichtig, nicht deinstallieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, bis alle abhängigen Anwendungen deinstalliert werden. Damit Benutzern eine Warnung, die Ihre Anwendung abhängt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden die Installationsoption APPGUID im MSI wie folgt:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 Der an APPGUID übergebene Wert ist Ihr spezifischer Produktcode. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit SQL Server Native Client](installing-sql-server-native-client.md)   
 [Themen zu Vorgehensweisen für die Installation](../../../sql-server/install/installation-how-to-topics.md)  
  
  
