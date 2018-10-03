---
title: Installieren von SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: MightyPen
ms.author: genemi
manager: craigg
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: de91c5cd6b98d3e7334b76b13eb8dd5947cb5ec4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637008"
---
# <a name="installing-sql-server-native-client"></a>Installieren von SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > Inhalte, die mit früheren Versionen von SQL Server zusammenhängen, finden Sie unter [Installieren von SQL Server Native Client](installing-sql-server-native-client.md).

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 wird bei der Installation installiert [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]. 
 
 Es gibt keine SQL Server 2016 Native Client. Weitere Informationen finden Sie unter [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md). 
 
Sie können sqlncli.msi auch von der SQL Server 2012 Feature Pack-Webseite herunterladen. Zum Herunterladen der neuesten Version von der SQL Server Native Client, wechseln Sie zu [Microsoft® SQL Server® 2012 Feature Pack](http://www.microsoft.com/en-us/download/confirmation.aspx?id=29065). Wenn eine frühere Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als auch SQL Server 2012 auf dem Computer installiert ist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 werden installierte Seite-an-Seite mit der früheren Version.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Dateien (sqlncli11.dll, sqlnclir11.rll und s11ch_sqlncli.chm) werden in folgendem Verzeichnis installiert:  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Während des Installationsvorgangs werden alle erforderlichen Registrierungseinstellungen für den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und den ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vorgenommen.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und -Bibliotheksdateien (sqlncli.h und sqlncli11.lib) werden in folgendem Verzeichnis installiert:  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Neben der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als Teil der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Installation besteht auch die verteilbaren Installationsprogramms SQLNCLI.msi, das sich auf die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Installations-CD an folgendem Speicherort: `%CD%\Setup\`.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client können Sie über sqlncli.msi verteilen. Möglicherweise müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client bei der Bereitstellung einer Anwendung installieren. Eine Möglichkeit, mehrere Pakete in mehreren Installationen, die für den Benutzer wie eine Installation aussehen, zu installieren, besteht in der Verwendung der Chainer- und Bootstrappertechnologie. Weitere Informationen finden Sie unter [Authoring a Custom Bootstrapper Package for Visual Studio 2005 (Erstellen eines benutzerdefinierten Bootstrapper-Pakets für Visual Studio 2005)](http://go.microsoft.com/fwlink/?LinkId=115667) und [Adding Custom Prerequisites (Hinzufügen benutzerdefinierter Voraussetzungen)](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Mit der x64-Version und der Itanium-Version von sqlncli.msi wird auch die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert. Wenn Ihre Anwendung für eine andere Plattform als für diejenige vorgesehen ist, auf der sie entwickelt wurde, können Sie Versionen von sqlncli.msi für x64, Itanium und x86 vom Microsoft Download Center herunterladen.  
  
 Wenn Sie sqlncli.msi aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client entwickelten Anwendung unterstützen. Um auch die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=All` in der Befehlszeile an. Zum Beispiel:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation ohne Eingreifen  
 Wenn Sie die /passiv, /qn, /qb, oder /qr-Option mit msiexec verwenden, müssen Sie auch IACCEPTSQLNCLILICENSETERMS=YES angeben, um explizit anzuzeigen, dass Sie den Bestimmungen der Endbenutzerlizenz zustimmen. Diese Option muss in Großbuchstaben angegeben werden.  
  
## <a name="uninstalling-sql-server-native-client"></a>Deinstallieren von SQL Server Native Client  
 Da Anwendungen, z. B. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Server und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tools hängt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, es ist wichtig, nicht deinstallieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, bis alle abhängigen Anwendungen deinstalliert werden. Damit Benutzern eine Warnung, die Ihre Anwendung abhängt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden die Installationsoption APPGUID im MSI wie folgt:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 Der an APPGUID übergebene Wert ist Ihr spezifischer Produktcode. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Themen zu Vorgehensweisen für die Installation](http://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
