---
title: Herstellen einer Verbindung mit Sybase ASE (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to Sybase ASE
ms.assetid: a45a2330-9175-4c9e-af38-ef920e350614
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: e1debb31cd70c73e3fecd569a58534377742a9a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948525"
---
# <a name="connecting-to-sybase-ase-sybasetosql"></a>Herstellen einer Verbindung mit der Sybase-ASE (SybaseToSQL)
Zum Migrieren von Sybase-Datenbanken vom Typ Adaptive [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Server Enterprise (ASE) zu oder SQL Azure müssen Sie eine Verbindung mit dem adaptiven Server herstellen, der die zu migrierenden Datenbanken enthält. Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken auf dem adaptiven Server und zeigt Daten Bank Metadaten im Sybase-metadatenexplorer-Bereich an. SSMA speichert Informationen über den Datenbankserver, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit der ASE bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie die Verbindung mit der ASE wiederherstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten.  
  
Metadaten zum adaptiven Server werden nicht automatisch aktualisiert. Wenn Sie die Metadaten im Sybase-metadatenexplorer aktualisieren möchten, müssen Sie stattdessen die Metadaten manuell aktualisieren, wie im Abschnitt "Aktualisieren von Sybase ASE-Metadaten" weiter unten in diesem Thema beschrieben.  
  
## <a name="required-ase-permissions"></a>Erforderliche ASE-Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit der ASE verwendet wird, muss mindestens über einen **öffentlichen** Zugriff auf die Master-Datenbank und alle Quell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken verfügen, die zu migriert oder SQL Azure werden. Außerdem muss der Benutzer über die SELECT-Berechtigung für die folgenden Systemtabellen verfügen, um Berechtigungen für Tabellen auszuwählen, die migriert werden:  
  
-   [source_db]. dbo. sysobjects  
  
-   [source_db]. dbo. syscolumschlag  
  
-   [source_db]. dbo. sysusers  
  
-   [source_db]. dbo. systypes  
  
-   [source_db]. dbo. syseinschränkungen  
  
-   [source_db]. dbo. syscomments  
  
-   [source_db]. dbo. sysindexes  
  
-   [source_db]. dbo. sysreferences  
  
-   Master. dbo. sysdatenbanken  
  
## <a name="establishing-a-connection-to-ase"></a>Herstellen einer Verbindung mit der ASE  
Wenn Sie eine Verbindung mit einem adaptiven Server herstellen, liest SSMA die Metadaten der Datenbank auf dem Datenbankserver und fügt diese Metadaten dann der Projektdatei hinzu. Diese Metadaten werden von SSMA verwendet, wenn die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-oder-SQL Azure-Syntax konvertiert werden, und beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migrieren von Daten zu oder SQL Azure. Sie können diese Metadaten im Bereich "Sybase-metadatenexplorer" Durchsuchen und die Eigenschaften einzelner Datenbankobjekte überprüfen.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit dem Datenbankserver herzustellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren kann.  
  
**So stellen Sie eine Verbindung mit Sybase ASE her**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit Sybase verbinden**aus.  
  
    Wenn Sie zuvor eine Verbindung mit Sybase hergestellt haben, stellt der Befehls Name **erneut eine Verbindung mit Sybase**her.  
  
2.  Wählen Sie im Feld **Anbieter** einen der auf dem Computer installierten Anbieter aus, um eine Verbindung mit dem Sybase-Server herzustellen.  
  
3.  Wählen Sie im Feld **Modus** entweder **Standard Modus** oder erweiterter **Modus**aus.  
  
    Verwenden Sie den Standardmodus, um den Servernamen, den Port, den Benutzernamen und das Kennwort anzugeben. Verwenden Sie den erweiterten Modus, um eine Verbindungs Zeichenfolge anzugeben. Dieser Modus wird in der Regel nur für die Problembehandlung oder die Arbeit mit dem technischen Support verwendet.  
  
4.  Wenn Sie den **Standard Modus**auswählen, geben Sie die folgenden Werte an:  
  
    1.  Geben Sie im Feld **Server Name** den Namen oder die IP-Adresse des Datenbankservers ein, oder wählen Sie ihn aus.  
  
    2.  Wenn der Datenbankserver nicht für die Annahme von Verbindungen über den Standardport (5000) konfiguriert ist, geben Sie im Feld **Serverport** die Portnummer ein, die für Sybase-Verbindungen verwendet wird.  
  
    3.  Geben Sie im Feld **Benutzername** ein Sybase-Konto ein, das über die erforderlichen Berechtigungen verfügt.  
  
    4.  Geben Sie im Feld **Kennwort** das Kennwort für den angegebenen Benutzernamen ein.  
  
5.  Wenn Sie den **erweiterten Modus**auswählen, geben Sie im Feld **Verbindungs Zeichenfolge** eine Verbindungs Zeichenfolge an.  
  
    Beispiele für verschiedene Verbindungs Zeichenfolgen:  
  
    1.  **Verbindungs Zeichenfolgen für den Sybase-OLE DB Anbieter:**  
  
        Für Sybase ASE OLE DB 12,5 lautet die folgende Beispiel Verbindungs Zeichenfolge:  
  
        `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
        Für Sybase-ASE OLE DB 15 lautet eine Beispiel Verbindungs Zeichenfolge wie folgt:  
  
        `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider= ASEOLEDB;Port=5000;`  
  
    2.  **Verbindungs Zeichenfolge für den Sybase-ODBC-Anbieter:**  
  
        `Driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
    3.  **Verbindungs Zeichenfolge für den Sybase ADO.NET-Anbieter:**  
  
        `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
    Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Sybase &#40;sybasedesql&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md).  
  
## <a name="reconnecting-to-sybase-ase"></a>Erneutes Herstellen einer Verbindung mit Sybase ASE  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung herstellen, wenn Sie eine aktive Verbindung mit dem adaptiven Server herstellen möchten. Sie können offline arbeiten, bis Sie Metadaten aktualisieren, Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure laden und Daten migrieren möchten.  
  
## <a name="refreshing-sybase-ase-metadata"></a>Aktualisieren von Sybase ASE-Metadaten  
Metadaten zu den ASE-Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten im Sybase-metadatenexplorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit dem adaptiven Server hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben Sie können Metadaten für eine einzelne Datenbank, ein einzelnes Datenbankschema oder alle Datenbanken manuell aktualisieren.  
  
**So aktualisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit dem adaptiven Server verbunden sind.  
  
2.  Aktivieren Sie im Sybase-metadatenexplorer das Kontrollkästchen neben der Datenbank oder dem Datenbankschema, das Sie aktualisieren möchten.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder eine einzelne Datenbank oder ein Datenbankschema, und wählen Sie dann **aus Datenbank aktualisieren aus**  
  
4.  Wenn Sie aufgefordert werden, das aktuelle Objekt zu überprüfen, klicken Sie auf **Ja**.  
  
## <a name="next-step"></a>Nächster Schritt  
  
-   Der nächste Schritt des Migrations Vorgangs besteht darin, [eine Verbindung mit einer Instanz von herzustellen SQL Server](connecting-to-sql-server-sybasetosql.md) / eine[Verbindung mit einer Instanz von herzustellen SQL Azure](connecting-to-azure-sql-db-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
