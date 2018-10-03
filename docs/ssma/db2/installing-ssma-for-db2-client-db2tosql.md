---
title: Installieren von SSMA für DB2-Client (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4e77b08484a08871d2b9dcd70de0ddf339bb8f07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805968"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installieren von SSMA für DB2-Client (DB2ToSQL)
Der SSMA-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
-   Verbinden Sie mit einer DB2-Datenbank.  
  
-   Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Konvertieren von DB2-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax.  
  
-   Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Dieses Thema enthält die Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
SSMA für die Arbeit mit DB2 für Z/OS, Version 9.0 und 10.0 oder DB2 für LUW, Version 9,8 und 10.1 oder höher Versionen dient und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
Vor der Installation von SSMA stellen Sie sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 oder höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 steht auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produktmedien. Sie können auch erhalten sie über die [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Microsoft OLE DB-Anbieter für DB2, Version 5 oder eine höhere Version und eine Verbindung mit der DB2-Datenbank, die Sie migrieren möchten.  
  
-   Zugriff auf und über ausreichende Berechtigungen auf dem Computer, der die Zielinstanz des hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, in dem Sie Datenbankobjekte und Daten migrieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Microsoft OLE DB-Anbieter für DB2  
Wechseln Sie zum Herunterladen der OLE DB-Anbieter für DB2, Version 5.0 zu [Microsoft® SQL Server® 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie unter den [SQL Server Migration Assistant-Downloadseite](http://aka.ms/ssmafordb2).  
  
Nachdem Sie die neueste Version herunterladen, müssen Sie die Installationsdateien extrahieren, bevor SSMA installiert werden kann.  
  
**Zum Installieren des SSMA-Clients**  
  
1.  Doppelklicken Sie auf SSMA für DB2 *n*. Install.exe, wobei *n* ist die Nummer des Builds.  
  
2.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
    Wenn Sie nicht die erforderlichen Komponenten installiert haben, wird eine Meldung angezeigt, der angibt, dass Sie zunächst die erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **ich stimme den Bedingungen des Lizenzvertrags**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle frühere Versionen von SSMA für DB2, bevor die neue Version installieren.  
  
Der Standardinstallationspfad lautet c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Migration Assistant für DB2.  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA-Komponenten auf SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
