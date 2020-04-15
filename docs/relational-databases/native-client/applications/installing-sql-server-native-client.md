---
title: Installieren von SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: markingmyname
ms.author: maghan
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
ms.openlocfilehash: 4c6f7dba15a6c86839f7c0285fbb383920e18589
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302482"
---
# <a name="installing-sql-server-native-client"></a>Installieren von SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 wird bei der Installation von [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] installiert. 
 
 Es ist kein SQL Server 2016 Native Client vorhanden. Weitere Informationen finden Sie unter [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md). 
 
Sie können sqlncli.msi auch von der SQL Server 2012 Feature Pack-Webseite herunterladen. Um die neueste Version des SQL Server Native Client herunterzuladen, gehen Sie zu [Microsoft® SQL Server® 2012 Feature Pack](https://www.microsoft.com/download/confirmation.aspx?id=29065). Wenn eine frühere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Version von Native Client vor SQL Server 2012 ebenfalls auf dem Computer installiert ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird Native Client 11.0 neben der früheren Version installiert.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Dateien (sqlncli11.dll, sqlnclir11.rll und s11ch_sqlncli.chm) werden in folgendem Verzeichnis installiert:  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  Während des Installationsvorgangs werden alle erforderlichen Registrierungseinstellungen für den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und den ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vorgenommen.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Header- und -Bibliotheksdateien (sqlncli.h und sqlncli11.lib) werden in folgendem Verzeichnis installiert:  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 Neben der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client im Rahmen der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt es die Möglichkeit der Installation mithilfe des verteilbaren Installationsprogramms sqlncli.msi, das sich auf dem Installationsdatenträger von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in folgendem Verzeichnis befindet: `%CD%\Setup\`.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client können Sie über sqlncli.msi verteilen. Möglicherweise müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client bei der Bereitstellung einer Anwendung installieren. Eine Möglichkeit, mehrere Pakete in mehreren Installationen, die für den Benutzer wie eine Installation aussehen, zu installieren, besteht in der Verwendung der Chainer- und Bootstrappertechnologie. Weitere Informationen finden Sie unter [Authoring a Custom Bootstrapper Package for Visual Studio 2005 (Erstellen eines benutzerdefinierten Bootstrapper-Pakets für Visual Studio 2005)](https://go.microsoft.com/fwlink/?LinkId=115667) und [Adding Custom Prerequisites (Hinzufügen benutzerdefinierter Voraussetzungen)](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
 Mit der x64-Version und der Itanium-Version von sqlncli.msi wird auch die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert. Wenn Ihre Anwendung für eine andere Plattform als für diejenige vorgesehen ist, auf der sie entwickelt wurde, können Sie Versionen von sqlncli.msi für x64, Itanium und x86 vom Microsoft Download Center herunterladen.  
  
 Wenn Sie sqlncli.msi aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Die Clientkomponenten sind Dateien, die das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Ausführen einer Anwendung unterstützen, die mit Native Client entwickelt wurde. Um auch die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=All` in der Befehlszeile an. Beispiel:  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>Installation ohne Eingreifen  
 Wenn Sie die /passiv, /qn, /qb, oder /qr-Option mit msiexec verwenden, müssen Sie auch IACCEPTSQLNCLILICENSETERMS=YES angeben, um explizit anzuzeigen, dass Sie den Bestimmungen der Endbenutzerlizenz zustimmen. Diese Option muss in Großbuchstaben angegeben werden.  
  
## <a name="uninstalling-sql-server-native-client"></a>Deinstallieren von SQL Server Native Client  
 Da Anwendungen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wie Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tools vom nativen Client abhängen, ist es wichtig, native Client erst zu deinstallieren, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wenn alle abhängigen Anwendungen deinstalliert sind. Für Anbieterbenutzer mit einer Warnung, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dass Ihre Anwendung von Native Client abhängt, verwenden Sie die APPGUID-Installationsoption in Ihrer MSI wie folgt:  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 Der an APPGUID übergebene Wert ist Ihr spezifischer Produktcode. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Themen zu Vorgehensweisen für die Installation](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
