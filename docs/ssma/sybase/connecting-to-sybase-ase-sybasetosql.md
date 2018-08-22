---
title: Herstellen einer Verbindung mit Sybase ASE (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connecting to Sybase ASE
ms.assetid: a45a2330-9175-4c9e-af38-ef920e350614
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a8411cdb507b27e69f86f0d853e1c98b4d24d29a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394499"
---
# <a name="connecting-to-sybase-ase-sybasetosql"></a>Herstellen einer Verbindung mit der Sybase-ASE (SybaseToSQL)
Zum Migrieren von Sybase Adaptive Server Enterprise (ASE) Datenbanken auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Sie müssen eine Verbindung mit dem Adaptive Server mit den Datenbanken, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, wird SSMA Ruft Metadaten zu allen Datenbanken auf dem adaptiven Server ab und zeigt Datenbankmetadaten in der Sybase-Metadaten-Explorer-Bereich. SSMA speichert Informationen zu den Datenbankserver, aber die Kennwörter werden nicht gespeichert.  
  
Die Verbindung mit der ASE bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie die ASE erneut, wenn Sie möchten, dass eine aktive Verbindung mit dem Server verbinden.  
  
Metadaten für die Adaptive Server wird nicht automatisch aktualisiert. Stattdessen sollten Sie die Metadaten in der Sybase-Metadaten-Explorer zu aktualisieren, müssen Sie manuell den Metadaten aktualisieren, wie im Abschnitt "Aktualisieren von Sybase ASE-Metadaten" weiter unten in diesem Thema beschrieben.  
  
## <a name="required-ase-permissions"></a>Erforderliche ASE-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung, die ASE muss zumindest **öffentliche** Zugriff auf die master-Datenbank und alle Quelldatenbanken für die Migration zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Darüber hinaus muss der Benutzer zum Auswählen von Berechtigungen für Tabellen, die migriert werden, SELECT-Berechtigungen für die folgenden Systemtabellen verfügen:  
  
-   [Source_db].dbo.sysobjects  
  
-   [Source_db].dbo.syscolumns  
  
-   [Source_db].dbo.sysusers  
  
-   [Source_db].dbo.systypes  
  
-   [Source_db].dbo.sysconstraints  
  
-   [Source_db].dbo.syscomments  
  
-   [Source_db].dbo.sysindexes  
  
-   [Source_db].dbo.sysreferences  
  
-   master.dbo.sysdatabases  
  
## <a name="establishing-a-connection-to-ase"></a>Herstellen einer Verbindung mit der ASE  
Wenn Sie mit der eine Adaptive Server verbinden, SSMA liest die Metadaten der Datenbank auf dem Datenbankserver und fügt dann diese Metadaten zu der Projektdatei. Diese Metadaten werden von SSMA verwendet, wenn die Objekte konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax, und wenn es Daten migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können diese Metadaten im Bereich Sybase-Metadaten-Explorer durchsuchen und überprüfen Sie die Eigenschaften einzelner Datenbankobjekte.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit dem Datenbankserver herstellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit Sybase ASE**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Sybase**.  
  
    Wenn Sie zuvor mit Sybase verbunden, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung in Sybase**.  
  
2.  In der **Anbieter** wählen einen der installierten Anbieter auf dem Computer zur Verbindung mit Sybase-Servers.  
  
3.  In der **Modus** wählen **Modus "Standard"** oder **im erweiterten Modus**.  
  
    Verwenden Sie Modus "standard", um den Servernamen, Port, Benutzername und Kennwort anzugeben. Verwenden Sie im erweiterten Modus, um eine Verbindungszeichenfolge bereitstellen. Dieser Modus ist in der Regel nur für die Problembehandlung von oder Arbeiten mit dem technischen Support verwendet.  
  
4.  Bei Auswahl von **Modus "Standard"**, geben Sie die folgenden Werte:  
  
    1.  In der **Servernamen** Feld eingeben oder auswählen, den Namen oder IP-Adresse des Datenbankservers.  
  
    2.  Wenn der Datenbankserver nicht konfiguriert ist, um auf Clientverbindungen standardmäßig port (5000), geben Sie die Portnummer, die verwendet wird, für die Sybase-Verbindungen in der **Serverport** Feld.  
  
    3.  In der **Benutzernamen** Geben Sie ein Sybase-Konto, das die erforderlichen Berechtigungen verfügt.  
  
    4.  In der **Kennwort** Geben Sie das Kennwort für den angegebenen Benutzernamen ein.  
  
5.  Bei Auswahl von **im erweiterten Modus**, geben Sie eine Verbindungszeichenfolge in der **Verbindungszeichenfolge** Feld.  
  
    Beispiele für verschiedene Verbindungszeichenfolgen lauten wie folgt aus:  
  
    1.  **Verbindungszeichenfolgen für Sybase OLE DB-Anbieter:**  
  
        Für Sybase ASE OLE DB 12,5 ist eine Beispiel-Verbindungszeichenfolge wie folgt:  
  
        `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
        Für Sybase ASE OLE DB 15 ist eine Beispiel-Verbindungszeichenfolge wie folgt:  
  
        `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider= ASEOLEDB;Port=5000;`  
  
    2.  **Die Verbindungszeichenfolge für den Sybase ODBC-Anbieter:**  
  
        `Driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
    3.  **Die Verbindungszeichenfolge für die ADO NET-Anbieter für Sybase:**  
  
        `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
    Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md).  
  
## <a name="reconnecting-to-sybase-ase"></a>Wiederherstellen der Verbindung mit Sybase ASE  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie eine aktive Verbindung mit dem Adaptive Server möchten. Sie können offline arbeiten, bis Sie die Metadaten aktualisieren, laden Sie die Datenbankobjekte in möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, und Daten migrieren.  
  
## <a name="refreshing-sybase-ase-metadata"></a>Aktualisieren von Sybase ASE-Metadaten  
Metadaten zu den ASE-Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in der Sybase-Metadaten-Explorer ist eine Momentaufnahme der Metadaten, wenn Sie zuerst, auf die Adaptive oder dem letzten verbunden, dass Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für eine einzelne Datenbank, ein einzelnes Datenbankschema oder alle Datenbanken manuell aktualisieren.  
  
**Aktualisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit der Adaptive Server verbunden sind.  
  
2.  Wählen Sie in der Sybase-Metadaten-Explorer das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
3.  Mit der rechten Maustaste, Datenbanken oder die einzelnen Datenbank oder das Datenbankschema, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
4.  Wenn Sie aufgefordert werden, um das aktuelle Objekt zu überprüfen, klicken Sie auf **Ja**.  
  
## <a name="next-step"></a>Nächster Schritt  
  
-   Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit einer Instanz von SQL Server](connecting-to-sql-server-sybasetosql.md) / [Herstellen einer Verbindung mit einer Instanz von SQL Azure](connecting-to-azure-sql-db-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
