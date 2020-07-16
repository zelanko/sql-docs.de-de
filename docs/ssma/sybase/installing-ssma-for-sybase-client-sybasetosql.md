---
title: Installieren von SSMA für den SAP ASE-Client (sybasedesql) | Microsoft-Dokumentation
description: Informieren Sie sich über die Installations Voraussetzungen für SQL Server Migration Assistant (SSMA) für SAP Adaptive Server Enterprise (ASE) und die Vorgehensweise zum Installieren von.
ms.custom: ''
ms.date: 07/14/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 288b6458fc8429077472ba3ba7ad49e6d6fd7565
ms.sourcegitcommit: fd7b268a34562d70d46441f689543ecce7df2e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86411168"
---
# <a name="installing-ssma-for-sap-ase-client-sybasetosql"></a>Installieren von SSMA für den SAP ASE-Client (sybasedesql)

Der SSMA-Client besteht aus den Programmdateien, die zum Herstellen einer Verbindung mit einem SAP Adaptive Server Enterprise-Daten Bank Server (ASE) und einer Instanz von oder verwendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , zum Umwandeln von ASE-Datenbankobjekten in eine- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] -Syntax, zum Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und zum anschließenden Migrieren von Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]

Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA.

## <a name="prerequisites"></a>Voraussetzungen

SSMA ist für die Verwendung mit SAP ASE 11.9.2 oder höheren Versionen und allen Editionen von konzipiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:

- Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.
- Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework Version 4.7.2 oder eine spätere Version. Sie können Sie über das [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.
- Der Sybase-OLE DB/ADO.net/ODBC-Anbieter und die Verbindung mit dem SAP ASE-Datenbankserver, der die zu migrierenden Datenbanken enthält. Sie können Anbieter aus dem SAP ASE-Produkt Medium installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit der Sybase-ASE &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).
- Zugriff auf und ausreichende Berechtigungen auf dem Computer, auf dem die Ziel Instanz von gehostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird, oder auf [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] dem Sie Datenbankobjekte und-Daten migrieren möchten. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Herstellen einer Verbindung mit Azure SQL DB &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).
- 4 GB RAM empfohlen.

## <a name="installing-the-ssma-for-sybase-client"></a>Installieren von SSMA für den Sybase-Client

SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmaforsybase).

So installieren Sie den SSMA-Client:

1. Doppelklicken Sie auf **SSMAforSybase_*n*. msi**, wobei *n* für die Buildnummer steht.
2. Klicken Sie auf der Seite Willkommenauf **Weiter**.

   Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.

3. Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **Ich akzeptiere die Vereinbarung**aus, und klicken Sie dann auf **weiter**.
4. Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.
5. Auf der Seite **bereit zur Installation** können Sie bei jedem Start des Tools Telemetrie-und automatische Aktualisierungs Prüfungen aktivieren bzw. deaktivieren. Klicken Sie auf **Installieren**, um die Installation zu starten.

> [!IMPORTANT]
> Deinstallieren Sie alle früheren Versionen von SSMA für Sybase, bevor Sie die neue Version installieren.

Das Standardinstallationsverzeichnis ist `C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase`.

Zusätzlich zu den SSMA-Programmdateien müssen Sie auch das SSMA für das Sybase-Erweiterungspaket auf installieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Installieren von SSMA-Komponenten auf SQL Server &#40;sybasedesql&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).

## <a name="see-also"></a>Weitere Informationen

- [Installieren von SSMA-Komponenten für SQL Server](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
- [Migrieren von Sybase ASE-Datenbanken zu SQL Server Azure SQL-Datenbank](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
