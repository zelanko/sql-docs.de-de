---
title: Installieren von SSMA für MySQL-Client (MySQLToSQL)) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1d9317b63b01a4d1e78f5c8d4818c63d9974be4f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187191"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Installieren von SSMA für den MySQL-Client (MySqlToSql)
SSMA für MySQL-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
-   Verbinden Sie mit einer MySQL-Datenbank.  
  
-   Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
-   Konvertieren Sie die MySQL-Datenbank-Objekte, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte.  
  
-   Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
-   Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
Dieses Thema enthält die Voraussetzungen und Anweisungen zum Installieren von SSMA für MySQL-Client.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
SSMA für MySQL dient zum Arbeiten mit MySQL 4.1 oder höher und allen Editionen von SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016, SQL Server 2017 und Azure SQL-Datenbank.  
  
Vor der Installation von SSMA stellen Sie sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 oder höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 auf dem SQL Server-Produktdatenträger verfügbar ist. Sie können auch erhalten sie über die [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   MySQL 5.1 Odbcdriver und Verbindung mit der MySQL-Datenbank, die Sie migrieren möchten. Sie können MySQL auf der MySQL-Website installieren. Weitere Informationen in Bezug auf Konnektivität, finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Zugriff auf und über ausreichende Berechtigungen auf dem Computer, der die Zielinstanz von SQL Server hostet, in denen Datenbankobjekte und Daten migriert werden soll. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   Bei SQL Azure-Projekten Datenbank Zugriff auf und ausreichende Berechtigungen für die Instanz von Azure SQL-Datenbank, in dem Sie der zu migrierenden, Objekte und Daten. Weitere Informationen finden Sie unter [eine Verbindung mit Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-ssma-for-mysql-client"></a>Installieren von SSMA für den MySQL-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie unter den [SQL Server Migration Assistant-Downloadseite](https://aka.ms/ssmaformysql).  
  
Nachdem Sie die neueste Version heruntergeladen haben, müssen Sie die Installationsdateien extrahieren, bevor SSMA installiert werden kann.  
  
**Zum Installieren des SSMA-Clients**  
  
1.  Doppelklicken Sie SSMA für MySQL *n*. Install.exe, wobei *n* ist die Nummer des Builds.  
  
2.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
    Wenn Sie nicht die erforderlichen Komponenten installiert haben, wird eine Meldung angezeigt, der angibt, müssen Sie zunächst die erforderlichen Komponenten installieren. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, bevor Sie das Installationsprogramm erneut ausführen.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **ich stimme den Bedingungen des Lizenzvertrags**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle frühere Versionen von SSMA für MySQL, bevor die neue Version installieren.  
  
Der Standardinstallationspfad lautet c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Migration Assistant für MySQL.  
  
Auf 64-Bit-Windows-Computer ist das Produkt in C:\Microsoft SQL Server Migration Assistant für MySQL installiert.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
