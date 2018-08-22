---
title: Installieren von SSMA für Sybase Client (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: eef420b0581d5b1a2907c0bb0bc1ace05193c39e
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40396494"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Installieren von SSMA für den Sybase-Client (SybaseToSQL)
Der SSMA-Client besteht aus den Programmdateien, die verwendet werden, zur Verbindung mit einem Datenbankserver von Sybase Adaptive Server Enterprise (ASE) und einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, konvertieren Sie die ASE-Datenbankobjekten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Syntax, laden die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, und klicken Sie dann migrieren Sie Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure-SQLDB.  
  
Dieses Thema enthält die Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
SSMA dient zum Arbeiten mit ASE 11.9.2 oder höheren Versionen und allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Vor der Installation von SSMA stellen Sie sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Version von .NET Framework 4.0 oder höher. .NET Framework, Version 4.0 steht auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produktmedien. Sie können auch erhalten sie über die [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Der Anbieter für Sybase OLEDB/ADO.Net/ODBC und die Verbindung mit der Sybase ASE-Datenbankserver mit den Datenbanken, die Sie migrieren möchten. Sie können den Anbieter vom Sybase ASE-Produktdatenträger installieren. Weitere Informationen in Bezug auf Konnektivität, finden Sie unter [Herstellen einer Verbindung mit Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Zugriff auf und über ausreichende Berechtigungen auf dem Computer, der die Zielinstanz des hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, in dem Sie Datenbankobjekte und Daten migrieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)/[eine Verbindung mit Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Installieren von SSMA für Sybase-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie unter den [SQL Server Migration Assistant-Downloadseite](http://aka.ms/ssmaforsybase).  
  
Nachdem Sie die neueste Version herunterladen, müssen Sie die Installationsdateien extrahieren, bevor SSMA installiert werden kann.  
  
**Zum Installieren des SSMA-Clients**  
  
1.  Doppelklicken Sie auf SSMA für Sybase *n*. Install.exe, wobei *n* ist die Nummer des Builds.  
  
2.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
    Wenn Sie nicht die erforderlichen Komponenten installiert haben, wird eine Meldung angezeigt, der angibt, dass Sie zunächst die erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **ich stimme den Bedingungen des Lizenzvertrags**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle frühere Versionen von SSMA für Sybase, bevor die neue Version installieren.  
  
Der Standardinstallationspfad lautet c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Migration Assistant für Sybase.  
  
Zusätzlich zu der SSMA-Programmdateien, müssen Sie auch die SSMA für Sybase-Erweiterungspaket installieren, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA-Komponenten auf SQLServer &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
