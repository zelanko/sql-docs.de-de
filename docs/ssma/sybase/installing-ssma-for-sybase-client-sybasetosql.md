---
title: Installieren von SSMA für den Sybase-Client (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8680685640b234e47f6e68d7fb802fc7e2f5d81c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029021"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Installieren von SSMA für den Sybase-Client (SybaseToSQL)
Der SSMA-Client besteht aus den Programmdateien, die zum Herstellen einer Verbindung mit einem Daten Bank Server von Sybase Adaptive Server Enterprise (ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) und einer Instanz von oder Azure SQL-Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, zum Konvertieren von ASE-Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekten in oder zur Azure SQL-Daten Bank Syntax [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Laden der Objekte in oder Azure SQL-Datenbank und anschließendes Migrieren von Daten zu oder  
  
Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Voraussetzungen  
SSMA ist für die Zusammenarbeit mit ASE 11.9.2 oder höheren Versionen und allen Editionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von konzipiert.  
  
Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.  
  
-   Der [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework Version 4,0 oder eine höhere Version. Die .NET Framework Version 4,0 ist auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt Medium verfügbar. Sie können Sie auch aus dem [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.  
  
-   Der Sybase-OLEDB/ADO.net/ODBC-Anbieter und die Konnektivität mit dem Sybase ASE-Datenbankserver, der die Datenbanken enthält, die Sie migrieren möchten. Sie können Anbieter aus dem Produkt System der Sybase-ASE installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit der Sybase-ASE &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Zugriff auf und ausreichende Berechtigungen auf dem Computer, auf dem die-Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz oder die Azure SQL-Datenbank gehostet wird, in der Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Herstellen einer Verbindung mit Azure SQL DB &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Installieren von SSMA für den Sybase-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmaforsybase).  
  
Nachdem Sie die aktuelle Version heruntergeladen haben, müssen Sie die Installationsdateien von extrahieren, bevor Sie SSMA installieren können.  
  
**So installieren Sie den SSMA-Client**  
  
1.  Doppelklicken Sie auf SSMA für Sybase *n*. Install. exe, wobei *n* für die Buildnummer steht.  
  
2.  Klicken Sie auf der Willkommensseite auf **weiter**.  
  
    Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie **Ich stimme den Bedingungen des Lizenzvertrags**zu, und klicken Sie dann auf **weiter**.  
  
4.  Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle früheren Versionen von SSMA für Sybase, bevor Sie die neue Version installieren.  
  
Der Standard Speicherort für die Installation lautet "c:\Programme\Microsoft SQL Server Migration Assistant for Sybase".  
  
Zusätzlich zu den SSMA-Programmdateien müssen Sie auch das SSMA für das Sybase-Erweiterungspaket auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installieren. Weitere Informationen finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql-&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
