---
title: Installieren von SSMA für MySQL-Client (mysqldesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9dcdeaff1c4782453a9fd57cc709e17ad3200d28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086825"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Installieren von SSMA für den MySQL-Client (MySqlToSql)
Der SSMA für MySQL-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
-   Herstellen einer Verbindung mit einer MySQL-Datenbank  
  
-   Stellen Sie eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer Instanz von oder SQL Azure her.  
  
-   Konvertieren der MySQL-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die-oder-SQL Azure-Objekte.  
  
-   Laden Sie die Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in oder SQL Azure.  
  
-   Migrieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten zu oder SQL Azure.  
  
Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA für den MySQL-Client.  
  
## <a name="prerequisites"></a>Voraussetzungen  
SSMA für MySQL ist für die Verwendung mit MySQL 4,1 oder höheren Versionen und allen Editionen von SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016, SQL Server 2017 und Azure SQL DB konzipiert.  
  
Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4,0 ist auf dem SQL Server-Produkt Medium verfügbar. Sie können Sie auch aus dem [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.  
  
-   MySQL ODBC 5,1-Treiber und Konnektivität zu den MySQL-Datenbanken, die Sie migrieren möchten. Sie können MySQL von der MySQL-Website installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Zugriff auf und ausreichende Berechtigungen auf dem Computer, auf dem die Ziel Instanz von gehostet wird SQL Server, auf dem Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;mysqldesql&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   Im Fall von SQL Azure Projekten Zugriff auf und ausreichende Berechtigungen für die Instanz von Azure SQL-Datenbank, in der Datenbankobjekte und-Daten migriert werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-ssma-for-mysql-client"></a>Installieren von SSMA für den MySQL-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmaformysql).  
  
Nachdem Sie die aktuelle Version heruntergeladen haben, müssen Sie die Installationsdateien extrahieren, bevor Sie SSMA installieren können.  
  
**So installieren Sie den SSMA-Client**  
  
1.  Doppelklicken Sie auf SSMA für MySQL *n*. Install. exe, wobei *n* für die Buildnummer steht.  
  
2.  Klicken Sie auf der Willkommensseite auf **weiter**.  
  
    Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst die erforderlichen Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle Voraussetzungen installiert haben, bevor Sie das Installationsprogramm erneut ausführen.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie **Ich stimme den Bedingungen des Lizenzvertrags**zu, und klicken Sie dann auf **weiter**.  
  
4.  Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle früheren Versionen von SSMA für MySQL, bevor Sie die neue Version installieren.  
  
Der Standard Speicherort für die Installation lautet c:\Programme\Microsoft SQL Server Migration Assistant for MySQL.  
  
Auf 64-Bit-Windows-Computer wird das Produkt in c:\Microsoft SQL Server Migration Assistant für MySQL installiert.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
