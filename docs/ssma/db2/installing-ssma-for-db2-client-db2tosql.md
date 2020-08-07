---
title: Installieren von SSMA für DB2-Client (DB2ToSQL) | Microsoft-Dokumentation
description: Informieren Sie sich über die Installations Voraussetzungen für den SQL Server Migration Assistant (SSMA) für den DB2-Client und die Vorgehensweise zum Installieren von.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5b9679451c1052423cb412b85bf8dde25c4a8351
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823715"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installieren von SSMA für DB2-Client (DB2ToSQL)

Der SSMA-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:

- Stellen Sie eine Verbindung mit einer DB2-Datenbank her.
- Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Konvertieren von DB2-Datenbankobjekten in die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax.
- Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA.

## <a name="prerequisites"></a>Voraussetzungen

SSMA ist für die Verwendung mit DB2 unter z/OS, Version 9,0 und 10,0, DB2 auf LUW Version 9,8 und 10,1 oder höher, DB2 für i Version 7,1 oder höher und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder höhere Versionen konzipiert.

Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:

- Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder höhere Versionen.
- Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.7.2 oder eine spätere Version. Sie können Sie über das [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.
- Microsoft OLE DB-Anbieter für DB2 Version 5 oder höher sowie Konnektivität zu den DB2-Datenbanken, die Sie migrieren möchten.
- Zugriff auf und ausreichende Berechtigungen auf dem Computer, der die Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die Azure SQL-Datenbank hostet, in der Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).
- 4 GB RAM empfohlen.

## <a name="microsoft-ole-db-provider-for-db2"></a>Microsoft OLE DB-Anbieter für DB2

Um den OLE DB Anbieter für DB2 Version 6,0 herunterzuladen, wechseln Sie zu [Microsoft® SQL Server® 2017 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmafordb2).

So installieren Sie den SSMA-Client:

1. Doppelklicken Sie auf **SSMAforDB2_*n*. msi**, wobei *n* für die Buildnummer steht.
2. Wählen Sie auf der Seite **Willkommen** die Option **Weiter** aus.

   Wenn Sie die erforderlichen Komponenten nicht installiert haben, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.

3. Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **Ich akzeptiere die Vereinbarung**aus, und klicken Sie dann auf **weiter**.
4. Wählen Sie auf der Seite Setuptyp **auswählen** die Option **typisch**aus.
5. Auf der Seite **bereit zur Installation** können Sie bei jedem Start des Tools Telemetrie-und automatische Aktualisierungs Prüfungen aktivieren bzw. deaktivieren. Klicken Sie auf **Installieren**, um die Installation zu starten.

> [!IMPORTANT]
> Deinstallieren Sie alle früheren Versionen von SSMA für DB2, bevor Sie die neue Version installieren.

Das Standardinstallationsverzeichnis ist `C:\Program Files\Microsoft SQL Server Migration Assistant for DB2`.

## <a name="see-also"></a>Weitere Informationen

- [Installieren von SSMA-Komponenten für SQL Server](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)
- [Migrating DB2 Databases into SQL Server (Migrieren von DB2-Datenbanken zu SQL Server)](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)
