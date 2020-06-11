---
title: Installieren von SSMA für Oracle Client (oracledesql) | Microsoft-Dokumentation
description: Informieren Sie sich über die Installations Voraussetzungen für den SQL Server Migration Assistant (SSMA) für den Oracle-Client und die Vorgehensweise zum Installieren von.
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
manager: shamikg
ms.openlocfilehash: be5f48508c44dc456c2d19e1ff1eba985b982111
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293917"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Installieren von SSMA für den Oracle-Client (OracleToSQL)
Der SSMA-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
-   Stellen Sie eine Verbindung mit einer Oracle-Datenbank her.  
  
-   Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Konvertieren Sie Oracle-Datenbankobjekte in die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax.  
  
-   Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Voraussetzungen  
SSMA ist für die Verwendung mit Oracle 9 oder höheren Versionen und allen Editionen von konzipiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4,0 oder höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4,0 ist auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt Medium verfügbar. Sie können Sie auch aus dem [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.  
  
-   Oracle-Client 9,0 oder eine höhere Version sowie Konnektivität zu den Oracle-Datenbanken, die Sie migrieren möchten. Die Oracle-Client Version muss die gleiche Version wie oder eine neuere Version als die Oracle-Datenbankversion aufweisen.  
  
    Sie können den Oracle-Client auf dem Oracle-Produkt Medium oder auf der Oracle-Website installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit Oracle Database &#40;oracleto SQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Zugriff auf und ausreichende Berechtigungen auf dem Computer, auf dem die-Ziel Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die Azure SQL-Datenbank gehostet wird, in der Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;oracleto SQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 GB RAM empfohlen.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Installieren des SSMA für den Oracle-Client  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmafororacle).  
  
Nachdem Sie die aktuelle Version heruntergeladen haben, müssen Sie die Installationsdateien von extrahieren, bevor Sie SSMA installieren können.  
  
**So installieren Sie den SSMA-Client**  
  
1.  Doppelklicken Sie auf SSMA für Oracle *n*.Install.exe, wobei *n* für die Buildnummer steht.  
  
2.  Klicken Sie auf der Seite Willkommenauf **Weiter**.  
  
    Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, aktivieren Sie **Ich stimme den Bedingungen des Lizenzvertrags**zu, und klicken Sie dann auf **weiter**.  
  
4.  Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.  
  
5.  Klicken Sie auf **Installieren**.  
  
> [!IMPORTANT]  
> 1.  Deinstallieren Sie alle früheren Versionen von SSMA für Oracle, bevor Sie die neue Version installieren.  
  
Der Standard Speicherort für die Installation ist c:\Programme\Microsoft SQL Server Migration Assistant für Oracle.  
  
Zusätzlich zu den SSMA-Programmdateien müssen Sie auch das SSMA für Oracle-Erweiterungspaket auf installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server &#40;oracleto SQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA-Komponenten auf SQL Server &#40;oracledesql-&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
