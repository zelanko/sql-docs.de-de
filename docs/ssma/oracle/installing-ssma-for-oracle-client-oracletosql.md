---
title: Installieren von SSMA für Oracle-Client (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 27e5c0ef0c834806351bda73eb69dbe783d78db2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63223581"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Installieren von SSMA für den Oracle-Client (OracleToSQL)
Der SSMA-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
-   Stellen Sie eine Verbindung mit einer Oracle-Datenbank her.  
  
-   Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Konvertieren von Oracle-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax.  
  
-   Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Dieses Thema enthält die Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
SSMA dient zum Arbeiten mit Oracle 9 oder höher und allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Vor der Installation von SSMA stellen Sie sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 oder höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.0 steht auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produktmedien. Sie können auch erhalten sie über die [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Oracle 9.0-Client oder eine höhere Version, und Verbindung mit der Oracle-Datenbank, die Sie migrieren möchten. Die Version der Oracle-Client muss die gleiche Version wie oder eine höhere Version als die Version der Oracle-Datenbank sein.  
  
    Sie können die Oracle-Client aus dem Oracle-Produktdatenträger oder auf der Oracle-Website installieren. Weitere Informationen in Bezug auf Konnektivität, finden Sie unter [Herstellen einer Verbindung mit Oracle-Datenbank &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Zugriff auf und über ausreichende Berechtigungen auf dem Computer, der die Zielinstanz des hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, in dem Sie Datenbankobjekte und Daten migrieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Installieren von SSMA für Oracle-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie unter den [SQL Server Migration Assistant-Downloadseite](https://aka.ms/ssmafororacle).  
  
Nachdem Sie die neueste Version herunterladen, müssen Sie die Installationsdateien extrahieren, bevor SSMA installiert werden kann.  
  
**Zum Installieren des SSMA-Clients**  
  
1.  Doppelklicken Sie auf SSMA für Oracle *n*. Install.exe, wobei *n* ist die Nummer des Builds.  
  
2.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
    Wenn Sie nicht die erforderlichen Komponenten installiert haben, wird eine Meldung angezeigt, der angibt, dass Sie zunächst die erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **ich stimme den Bedingungen des Lizenzvertrags**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle frühere Versionen von SSMA für Oracle an, bevor die neue Version installieren.  
  
Der Standardinstallationspfad lautet c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Migration Assistant für Oracle.  
  
Zusätzlich zu der SSMA-Programmdateien, müssen Sie auch den SSMA for Oracle-Erweiterungspaket installieren, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA-Komponenten auf SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
