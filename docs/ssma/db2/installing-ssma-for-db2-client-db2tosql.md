---
title: Installieren von SSMA für DB2-Client (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 09/07/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1623430eed752db7fa387caf33124082eb318490
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70774186"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installieren von SSMA für DB2-Client (DB2ToSQL)

Der SSMA-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:  
  
- Stellen Sie eine Verbindung mit einer DB2-Datenbank her.  
  
- Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
- Konvertieren von DB2-Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bank Objekten in die-Syntax.  
  
- Laden Sie die Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in.  
  
- Migrieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Daten zu.  
  
Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA.  
  
## <a name="prerequisites"></a>Voraussetzungen

SSMA ist für die Verwendung mit DB2 unter z/OS, Version 9,0, 10,0 oder DB2, in LUW, Version 9,8 und 10,1 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] höheren Versionen und 2012 oder höheren Versionen konzipiert.  
  
Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:  
  
- Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder höhere Versionen.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] höher. Die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4,0 ist auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt Medium verfügbar. Sie können Sie auch aus dem [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.  
  
- Microsoft OLE DB-Anbieter für DB2, Version 5 oder höher, und Konnektivität zu den DB2-Datenbanken, die Sie migrieren möchten.  
  
- Zugriff auf und ausreichende Berechtigungen auf dem Computer, auf dem die-Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz oder die Azure SQL-Datenbank gehostet wird, in der Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
- 4 GB RAM empfohlen.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Microsoft OLE DB-Anbieter für DB2  

Um den OLEDB-Anbieter für DB2 Version 6,0 herunterzuladen, wechseln Sie zu [Microsoft® SQL Server® 2017 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmafordb2).  
  
Nachdem Sie die aktuelle Version heruntergeladen haben, extrahieren Sie die Installationsdateien, sodass Sie SSMA installieren können.  
  
So installieren Sie den SSMA-Client:
  
1. Doppelklicken Sie auf SSMA für DB2 *n*. Install. exe, wobei *n* für die Buildnummer steht.  
  
2. Wählen Sie auf der Seite **Willkommen** die Option **Weiter** aus.  
  
   Wenn Sie die erforderlichen Komponenten nicht installiert haben, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.  
  
3. Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **Ich stimme den Bedingungen des Lizenzvertrags**zu, und klicken Sie dann auf **weiter**.  
  
4. Wählen Sie auf der Seite Setuptyp **auswählen** die Option **typisch**aus.  
  
5. Wählen Sie **Installieren** aus.  
  
> [!IMPORTANT]  
> Deinstallieren Sie alle früheren Versionen von SSMA für DB2, bevor Sie die neue Version installieren.
  
Der Standard Speicherort für die Installation ist c:\Programme\Microsoft SQL Server Migration Assistant für DB2.  
  
## <a name="see-also"></a>Weitere Informationen:

[Installieren von SSMA-Komponenten auf SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Migrieren von DB2-Datenbanken zu SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
