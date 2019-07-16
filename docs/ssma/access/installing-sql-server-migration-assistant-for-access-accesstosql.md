---
title: Installieren von SQL Server Migration Assistant für Access (AccessToSQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4cd58a535836a82dc6cca660ba745aed58e2c84c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986327"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Installieren von SQL Server Migration Assistant für Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für den Zugriff ist mithilfe ein Windows Installer-basierten Assistenten installiert. Dieses Thema enthält Informationen zu Installationsvoraussetzungen, einen Link auf die neueste Version von SSMA und Anweisungen zum Installieren, Lizenzierung, deinstallieren und Aktualisieren von SSMA.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
Vor der Installation von SSMA stellen Sie sicher, dass das System die folgenden Anforderungen erfüllt:  
  
-   Windows 7 oder höher oder Windows Server 2008 oder höher.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 oder höher.  
  
-   Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Version von .NET Framework 4.0 oder höher. .NET Framework, Version 4.0 steht auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produkt-CD, und mithilfe der Informationen in den [Handbuch für Microsoft .NET](https://docs.microsoft.com/dotnet/framework/).
  
-   Zugriff auf und über ausreichende Berechtigungen auf dem Computer, der die Zielinstanz des hostet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure-Datenbank, die auf die Sie Datenbankobjekte und Daten migrieren.  
  
-   Microsoft Data Access Object (DAO) Provider-Version 12.0 oder 14.0. Sie können die DAO-Anbieter von Microsoft Office 2010/2007-Produkt installieren oder Herunterladen von Microsoft-Website.  
  
-   Die SQL Server Native Access Client (SNAC) Version 10.5 und höher für die Migration zu SQL Azure. Sie erhalten die neueste Version von SNAC aus [Microsoft® SQL Server® 2008 R2 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB RAM (empfohlen).  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie unter den [SQL Server Migration Assistant-Downloadseite](https://aka.ms/ssmaforaccess).  
  
Nachdem Sie die neueste Version herunterladen, müssen Sie die Installationsdateien extrahieren, bevor SSMA installiert werden kann.

> [!IMPORTANT]  
> -   Deinstallieren Sie alle vorherige Versionen von SSMA für Access vor der Installation der neuen Version an.  
  
**Installieren von SSMA**  
  
1.  Doppelklicken Sie auf SSMA für Access *n*MSI-Datei, wobei *n* ist die Nummer des Builds.  
  
2.  Klicken Sie auf der Seite Willkommen auf **Weiter**.  
  
    Wenn Sie nicht die erforderlichen Komponenten installiert haben, wird eine Meldung, der angibt, dass Sie zunächst die erforderliche Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle erforderlichen Komponenten installiert haben, und führen Sie das Installationsprogramm erneut aus.  
  
3.  Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **ich stimme der Vereinbarung**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite Installationstyp auswählen auf **Standard**.  
  
5.  Klicken Sie auf **Installieren**.  
  
Der Standardinstallationspfad lautet c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Migration Assistant für Access.  
  
## <a name="uninstalling-ssma-for-access"></a>Deinstallieren von SSMA für Access  
Deinstallieren Sie SSMA mit **Software** in der Systemsteuerung. Denken Sie daran, dass die Deinstallation des Programms nicht SSMA-Projektdateien löschen oder Protokolldateien.  
  
**So deinstallieren Sie SSMA**  
  
1.  Klicken Sie auf **starten**, klicken Sie auf **Systemsteuerung**, und klicken Sie dann auf **Software**.  
  
2.  Wählen Sie **Microsoft SQL Server Migration Assistant für Access**, und klicken Sie dann auf **entfernen**.  
  
## <a name="upgrading-to-a-later-version"></a>Ein Upgrade auf eine höhere version  
Wenn Sie ein Upgrade auf eine höhere Version von SSMA für Access durchführen möchten, müssen Sie zuerst deinstallieren SSMA für Access, und klicken Sie dann die neue Version installieren. Führen Sie die Anweisungen in der Deinstallation von SSMA für Access-Abschnitt, um diesen Vorgang abzuschließen.  
  
Wenn Sie ein Projekt erstellt wurde, in einer früheren Version von SSMA für Access öffnen, werden Sie SSMA gefragt, ob Sie das Projekt auf die neuere Version konvertieren möchten. Klicken Sie auf **Ja** mit dem in der neueren Version von SSMA-Projekt arbeiten.  
  
## <a name="see-also"></a>Siehe auch  
[Access-Datenbanken vorbereitet für die Migration.](preparing-access-databases-for-migration-accesstosql.md)  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Verknüpfen den Zugriff auf Anwendungen mit SQLServer](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
