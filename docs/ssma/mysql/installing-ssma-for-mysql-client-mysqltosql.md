---
title: Installieren von SSMA für MySQL-Client (mysqldesql) | Microsoft-Dokumentation
description: Informieren Sie sich über die Installations Voraussetzungen für den SQL Server Migration Assistant (SSMA) für MySQL-Client und die Vorgehensweise zum Installieren von.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: d6bda2cad0761dbb53fcc4bb66d29829841f249d
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87824036"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Installieren von SSMA für MySQL-Client (mysqldesql)

Der SSMA für MySQL-Client besteht aus den Programmdateien, die die folgenden Aufgaben ausführen:

- Herstellen einer Verbindung mit einer MySQL-Datenbank  
- Stellen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder her [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .
- Konvertieren der MySQL-Datenbankobjekte in das-oder das- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Objekt.
- Laden Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .
- Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

Dieses Thema enthält die Installations Voraussetzungen und Anweisungen zum Installieren von SSMA für den MySQL-Client.

## <a name="prerequisites"></a>Voraussetzungen

SSMA für MySQL ist für die Verwendung mit MySQL 4,1 oder höheren Versionen und allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder höher und verfügbar [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

Stellen Sie vor der Installation von SSMA sicher, dass der Computer die folgenden Anforderungen erfüllt:

- Windows 7 oder höher oder Windows Server 2008 oder höhere Versionen.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 oder eine höhere Version.
- Die [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Version 4.7.2 oder eine spätere Version. Sie können Sie über das [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)abrufen.
- MySQL ODBC 5,1-Treiber und Konnektivität zu den MySQL-Datenbanken, die Sie migrieren möchten. Sie können MySQL von der MySQL-Website installieren. Weitere Informationen zur Konnektivität finden [Sie unter Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).
- Zugriff auf und ausreichende Berechtigungen auf dem Computer, der die Ziel Instanz von hostet, auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte und-Daten migriert werden sollen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;mysqldesql&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md).
- Bei Projekten der [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Zugriff auf und ausreichende Berechtigungen für die Instanz von, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] in der Datenbankobjekte und-Daten migriert werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).
- 4 GB RAM empfohlen.

## <a name="installing-ssma-for-mysql-client"></a>Installieren von SSMA für MySQL-Client

SSMA ist ein Webdownload. Informationen zum Herunterladen der neuesten Version finden Sie auf der [SQL Server Migration Assistant Downloadseite](https://aka.ms/ssmaformysql).

So installieren Sie den SSMA-Client:

1. Doppelklicken Sie auf **SSMAforMySQL_*n*. msi**, wobei *n* für die Buildnummer steht.
2. Klicken Sie auf der Seite **Willkommen**auf **Weiter**.

   Wenn die erforderlichen Komponenten nicht installiert sind, wird eine Meldung mit dem Hinweis angezeigt, dass Sie zunächst die erforderlichen Komponenten installieren müssen. Stellen Sie sicher, dass Sie alle Voraussetzungen installiert haben, bevor Sie das Installationsprogramm erneut ausführen.

3. Lesen Sie den Endbenutzer-Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **Ich akzeptiere die Vereinbarung**aus, und klicken Sie dann auf **weiter**.
4. Klicken Sie auf der Seite Setuptyp **auswählen** auf **typisch**.
5. Auf der Seite **bereit zur Installation** können Sie bei jedem Start des Tools Telemetrie-und automatische Aktualisierungs Prüfungen aktivieren bzw. deaktivieren. Klicken Sie auf **Installieren**, um die Installation zu starten.

> [!IMPORTANT]
> Deinstallieren Sie alle früheren Versionen von SSMA für MySQL, bevor Sie die neue Version installieren.

Das Standardinstallationsverzeichnis ist `C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL`.

## <a name="see-also"></a>Weitere Informationen

- [Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
