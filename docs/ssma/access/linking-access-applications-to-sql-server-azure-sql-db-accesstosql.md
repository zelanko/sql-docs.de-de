---
title: Verknüpfen von Access-Anwendungen mit SQL Server-Azure SQL-Datenbank | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ihre Zugriffs Tabellen mit den migrierten Tabellen verknüpfen, damit Sie Ihre vorhandenen Access-Anwendungen mit SQL Server oder Azure SQL-Datenbank verwenden können.
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, linking to SQL Azure
- Access databases, linking to SQL Server
- auto-increment columns
- data types, unsupported
- hyperlink columns
- linking tables
- migrating databases, post-migration issues
- post-migration issues
- reference, post-migration issues
- refreshing linked tables
- slow performance
- unlinking tables
ms.assetid: 82374ad2-7737-4164-a489-13261ba393d4
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: aadb041b3b9005d0e593e97974090250129ed33d
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823846"
---
# <a name="linking-access-applications-to-sql-server---azure-sql-database-accesstosql"></a>Verknüpfen von Zugriffs Anwendungen mit SQL Server Azure SQL-Datenbank (Access Token)
Wenn Sie die vorhandenen Access-Anwendungen mit verwenden möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie die ursprünglichen Zugriffs Tabellen mit den migrierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen oder den SQL Azure Tabellen verknüpfen. Durch die Verknüpfung wird die Access-Datenbank geändert, sodass Ihre Abfragen, Formulare, Berichte und Datenzugriffsseiten die Daten in der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Datenbank anstelle der Daten in der Access-Datenbank verwenden.  
  
> [!NOTE]  
> Die Zugriffs Tabellen bleiben im Zugriff, werden jedoch nicht mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Updates aktualisiert. Nachdem Sie die Tabellen verknüpft und die Funktionalität überprüft haben, möchten Sie möglicherweise die Zugriffs Tabellen löschen.  
  
## <a name="linking-access-and-sql-server-tables"></a>Verknüpfen von Zugriffs-und SQL Server Tabellen  
Wenn Sie eine Zugriffs Tabelle mit einer- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Tabelle verknüpfen, speichert die Jet-Datenbank-Engine Verbindungsinformationen und Tabellen Metadaten, aber die Daten werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure gespeichert. Diese Verknüpfung ermöglicht, dass ihre Zugriffs Anwendungen mit den Zugriffs Tabellen arbeiten, auch wenn sich die tatsächlichen Tabellen und Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
> [!NOTE]  
> Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Authentifizierung verwenden, wird Ihr Kennwort in Klartext in den verknüpften Zugriffs Tabellen gespeichert. Wir empfehlen die Verwendung der Windows-Authentifizierung.  
  
**So verknüpfen Sie Tabellen**  
  
1.  Wählen Sie unter Access Metadata Explorer die Tabellen aus, die Sie verknüpfen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Tabellen**, und wählen Sie dann **Verknüpfen**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für den Zugriff sichert die ursprüngliche Zugriffs Tabelle und erstellt eine verknüpfte Tabelle.  
  
Nachdem Sie die Tabellen verknüpft haben, werden die Tabellen in SSMA mit einem kleinen Link Symbol angezeigt. In Access werden die Tabellen mit einem "verknüpften" Symbol angezeigt. Hierbei handelt es sich um einen Globus mit einem Pfeil, der darauf zeigt.  
  
Wenn Sie eine Tabelle in Access öffnen, werden die Daten mit einem Keysetcursor abgerufen. Folglich werden bei großen Tabellen nicht alle Daten gleichzeitig abgerufen. Wenn Sie jedoch die Tabelle durchsuchen, ruft der Zugriff nach Bedarf zusätzliche Daten ab.  
  
> [!IMPORTANT]  
> Um Zugriffs Tabellen mit einer Azure-Datenbank zu verknüpfen, benötigen Sie SQL Server Native Client (SNAC) Version 10,5 oder höher.   
> Sie können die neueste Version von SNAC von [Microsoft® SQL Server® 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)abrufen.  
  
## <a name="unlinking-access-tables"></a>Aufheben der Verknüpfung von Zugriffs Tabellen  
Wenn Sie die Verknüpfung einer Zugriffs Tabelle mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder-SQL Azure Tabelle aufheben, stellt SSMA die ursprüngliche Zugriffs Tabelle und die zugehörigen Daten wieder her.  
  
**So deaktivieren Sie die Verknüpfung von Tabellen**  
  
1.  Wählen Sie unter Access Metadata Explorer die Tabellen aus, deren Verknüpfung Sie aufheben möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Tabellen**, und wählen Sie **Verknüpfung**aufheben aus.  
  
## <a name="linking-tables-to-a-different-server"></a>Verknüpfen von Tabellen mit einem anderen Server  
Wenn Sie die Zugriffs Tabellen mit einer SQL Server Instanz verknüpft haben und die Verknüpfungen später zu einer anderen Instanz ändern möchten, müssen Sie die Tabellen neu verknüpfen.  
  
**So verknüpfen Sie Tabellen mit einem anderen Server**  
  
1.  Wählen Sie unter Access Metadata Explorer die Tabellen aus, deren Verknüpfung Sie aufheben möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Tabellen** , und wählen Sie **Verknüpfung**aufheben.  
  
3.  Klicken Sie auf die Schaltfläche **Verbindung mit SQL Server wiederherstellen** .  
  
4.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure her, mit der die Zugriffs Tabellen verknüpft werden sollen.  
  
5.  Wählen Sie unter Access Metadata Explorer die Tabellen aus, die Sie verknüpfen möchten.  
  
6.  Klicken Sie mit der rechten Maustaste auf **Tabellen**, und wählen Sie dann **Verknüpfen**.  
  
## <a name="updating-linked-tables"></a>Aktualisieren von verknüpften Tabellen  
Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Definitionen der Tabellen oder SQL Azure geändert werden, können Sie die Verknüpfung der Tabellen in SSMA mithilfe der zuvor in diesem Thema gezeigten Verfahren aufheben und die Tabellen dann erneut verknüpfen. Sie können die Tabellen auch aktualisieren, indem Sie Access verwenden.  
  
**So aktualisieren Sie verknüpfte Tabellen mithilfe des Zugriffs**  
  
1.  Öffnen Sie die Access-Datenbank.  
  
2.  Klicken Sie in der Liste **Objekte** auf **Tabellen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine verknüpfte Tabelle, und wählen Sie dann Verbindungs- **Manager**  
  
4.  Aktivieren Sie das Kontrollkästchen neben jeder verknüpften Tabelle, die Sie aktualisieren möchten, und klicken Sie dann auf **OK**.  
  
## <a name="possible-post-migration-issues"></a>Mögliche Probleme nach der Migration  
In den folgenden Abschnitten werden Probleme aufgelistet, die möglicherweise in vorhandenen Access-Anwendungen auftreten, nachdem Sie Datenbanken aus dem Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure migriert und dann die Tabellen zusammen mit den Ursachen und Lösungen verknüpft haben.  
  
### <a name="slow-performance-with-linked-tables"></a>Langsame Leistung mit verknüpften Tabellen  
**Ursache:** Einige Abfragen können nach dem Upsizing aus den folgenden Gründen langsam sein:  
  
-   Die Anwendung ist von Funktionen abhängig, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure nicht vorhanden sind. Dies bewirkt, dass Jet Tabellen lokal abruft, um eine SELECT-Abfrage auszuführen.  
  
-   Abfragen, die viele Zeilen aktualisieren oder löschen, werden von Jet als parametrisierte Abfrage für jede Zeile gesendet.  
  
**Lösung:** Konvertieren Sie die Abfragen mit langsamer Ausführung in Pass-Through-Abfragen, gespeicherte Prozeduren oder Sichten. Die Umstellung auf Pass-Through-Abfragen hat folgende Probleme:  
  
-   Pass-Through-Abfragen können nicht geändert werden. Das Ändern des Abfrage Ergebnisses oder das Hinzufügen neuer Datensätze muss auf alternative Weise erfolgen, z. b. durch das explizite **ändern** oder **Hinzufügen** von Schaltflächen auf dem Formular, das an die Abfrage gebunden ist.  
  
-   Einige Abfragen erfordern Benutzereingaben, aber Pass-Through-Abfragen unterstützen keine Benutzereingaben. Benutzereingaben können durch Visual Basic for Applications (VBA)-Code abgerufen werden, der zur Eingabe von Parametern auffordert, oder durch ein Formular, das als Eingabe Steuerelement verwendet wird. In beiden Fällen übermittelt der VBA-Code die Abfrage mit der Benutzereingabe an den Server.  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>AutoIncrement-Spalten werden erst aktualisiert, wenn der Datensatz aktualisiert wurde.  
**Ursache:** Nach dem Aufruf von Recordset. AddNew in Jet ist die Spalte für das automatische Inkrement verfügbar, bevor der Datensatz aktualisiert wird. Dies gilt nicht für die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure. Der neue Wert der Identitäts Spalte "neuer Wert" ist erst nach dem Speichern des neuen Datensatzes verfügbar.  
  
**Lösung:** Führen Sie den folgenden Visual Basic for Applications (VBA)-Code aus, bevor Sie auf das Identitäts Feld zugreifen:  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>Neue Datensätze sind nicht verfügbar.  
**Ursache:** Wenn Sie einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder-SQL Azure Tabelle mithilfe von VBA einen Datensatz hinzufügen, wird der neue Datensatz nicht angezeigt, wenn das eindeutige Index Feld der Tabelle einen Standardwert aufweist und Sie diesem Feld keinen Wert zuweisen. der neue Datensatz wird erst angezeigt, wenn Sie die Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure erneut öffnen. Wenn Sie versuchen, einen Wert aus dem neuen Datensatz zu erhalten, erhalten Sie die folgende Fehlermeldung:  
  
`Run-time error '3167' Record is deleted.`  
  
**Lösung:** Wenn Sie die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Tabelle mithilfe von VBA-Code öffnen, schließen Sie die- `dbSeeChanges` Option wie im folgenden Beispiel ein:  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>Nach der Migration erlauben einige Abfragen dem Benutzer nicht, einen neuen Datensatz hinzuzufügen.  
**Ursache:** Wenn eine Abfrage nicht alle Spalten enthält, die in einem eindeutigen Index enthalten sind, können Sie mit der Abfrage keine neuen Werte hinzufügen.  
  
**Lösung:** Stellen Sie sicher, dass alle Spalten, die in mindestens einem eindeutigen Index enthalten sind, Teil der Abfrage sind.  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Sie können ein verknüpftes Tabellen Schema mit Access nicht ändern.  
**Ursache:** Nach dem Migrieren von Daten und dem Verknüpfen von Tabellen kann der Benutzer das Schema einer Tabelle in Access nicht mehr ändern.  
  
**Lösung:** Ändern Sie das Tabellen Schema mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und aktualisieren Sie dann den Link in Access.  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>Hyperlink-Funktionalität geht nach dem Migrieren von Daten verloren  
**Ursache:** Nach dem Migrieren von Daten verlieren Hyperlinks in Spalten ihre Funktionalität und werden zu einfachen **nvarchar (max)** -Spalten.  
  
**Lösung:** Keine.  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>Einige SQL Server Datentypen werden nicht durch den Zugriff unterstützt.  
**Ursache:** Wenn Sie Ihre-oder-SQL Azure Tabellen später aktualisieren, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sodass Sie Datentypen enthalten, die nicht durch den Zugriff unterstützt werden, können Sie die Tabelle nicht in Access öffnen.  
  
**Lösung:** Sie können eine Zugriffs Abfrage definieren, die nur die Zeilen mit unterstützten Datentypen zurückgibt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
