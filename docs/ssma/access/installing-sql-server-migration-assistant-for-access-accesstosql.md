---
title: Installieren von SQL Server Migration Assistant für den Zugriff (Access Token) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 80fc19b17ac1c01f0c57d828a3bc4821050f761d
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257894"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Installieren von SQL Server Migration Assistant für den Zugriff (Access Token)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für den Zugriff wird mithilfe eines Windows Installer basierten Assistenten installiert. Dieses Thema enthält Informationen zu Installations Voraussetzungen, einen Link zur neuesten Version von SSMA sowie Anweisungen zum Installieren, lizenzieren, deinstallieren und Aktualisieren von SSMA.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Stellen Sie vor der Installation von SSMA sicher, dass Ihr System die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder eine höhere Version.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.  
  
-   Der [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework Version 4,0 oder eine höhere Version. Die .NET Framework Version 4,0 ist auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt-CD verfügbar, und Sie erhalten Informationen im [Microsoft .net Handbuch](https://docs.microsoft.com/dotnet/framework/).
  
-   Zugriff auf und ausreichende Berechtigungen auf dem Computer, der die Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hostet/SQL Azure DB, zu der Datenbankobjekte und-Daten migriert werden sollen.  
  
-   Microsoft Data Access Object (DAO)-Anbieter Version 12,0 oder 14,0. Sie können den DAO-Anbieter aus Microsoft Office 2010/2007-Produkt installieren oder von der Microsoft-Website herunterladen.  
  
-   Die SQL Server Native Access Client (SNAC) Version 10,5 und höher für die Migration zu SQL Azure. Sie können die neueste Version von SNAC von [Microsoft® SQL Server® 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=16978) abrufen.  
  
-   4 GB RAM (empfohlen).  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmaforaccess).  
  
Nachdem Sie die aktuelle Version heruntergeladen haben, müssen Sie die Installationsdateien von extrahieren, bevor Sie SSMA installieren können.

> [!IMPORTANT]  
> -   Deinstallieren Sie alle früheren Versionen von SSMA für den Zugriff, bevor Sie die neue Version installieren.  
  
**So installieren Sie SSMA**  
  
1.  Doppelklicken Sie auf SSMA für Access *n*. msi, wobei *n* für die Buildnummer steht.  
  
2.  Klicken Sie auf der Willkommensseite auf **weiter**.  
  
    Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm dann erneut aus.  
  
3.  Lesen Sie den Lizenzvertrag für Endbenutzer. Wenn Sie zustimmen, wählen Sie **Ich akzeptiere die Vereinbarung**aus, und klicken Sie dann auf **weiter**.  
  
4.  Klicken Sie auf der Seite Setuptyp auswählen auf **typisch**.  
  
5.  Klicken Sie auf **Installieren**.  
  
Der Standard Speicherort für die Installation ist c:\Programme\Microsoft SQL Server Migration Assistant für den Zugriff.  
  
## <a name="uninstalling-ssma-for-access"></a>Deinstallieren von SSMA für den Zugriff  
Deinstallieren **Sie SSMA mithilfe der** Option Software in der Systemsteuerung. Beachten Sie, dass beim Deinstallieren des Programms keine SSMA-Projektdateien oder-Protokolldateien gelöscht werden.  
  
**So deinstallieren Sie SSMA**  
  
1.  Klicken Sie auf **Start**, klicken Sie auf **Systemsteuerung**, und klicken Sie dann auf **Programme hinzufügen oder entfernen**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für den Zugriff aus**, und klicken Sie dann auf **Entfernen**.  
  
## <a name="upgrading-to-a-later-version"></a>Aktualisieren auf eine höhere Version  
Wenn Sie für den Zugriff auf eine höhere Version von SSMA aktualisieren möchten, müssen Sie zunächst SSMA für den Zugriff deinstallieren und dann die neuere Version installieren. Befolgen Sie die Anweisungen im Abschnitt Deinstallieren von SSMA for Access, um diesen Vorgang abzuschließen.  
  
Wenn Sie ein Projekt öffnen, das in einer früheren Version von SSMA für den Zugriff erstellt wurde, fragt SSMA, ob das Projekt in die neuere Version konvertiert werden soll. Klicken Sie auf **Ja** , um mit dem Projekt in der neueren Version von SSMA zu arbeiten.  
  
## <a name="see-also"></a>Siehe auch  
[Vorbereiten einer Access-Datenbank für die Migration](preparing-access-databases-for-migration-accesstosql.md)  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Verknüpfen von Zugriffs Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
