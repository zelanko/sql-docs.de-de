---
title: Verknüpfen von Access-Anwendungen zu SQLServer – Azure SQL-Datenbank | Microsoft-Dokumentation
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
ms.openlocfilehash: 115aa0db8e8d6f2fdc35718ccb60f1d0ed06b5c1
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68259902"
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>Verknüpfen von Access-Anwendungen zu SQL Server – Azure SQL-Datenbank (AccessToSQL)
Wenn Sie möchten, verwenden Sie die vorhandenen Access-Anwendungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können die ursprünglichen Access-Tabellen verknüpfen, um die migrierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen. Verknüpfen die Access-Datenbank ändert, sodass Ihre Abfragen, Formulare, Berichte und Data Access-Seiten verwenden Sie die Daten in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank anstelle der Daten in der Access-Datenbank.  
  
> [!NOTE]  
> Die Access-Tabellen verbleiben in den Zugriff, jedoch werden nicht aktualisiert werden, zusammen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure aktualisiert. Nachdem Sie die Tabellen verknüpfen und überprüfen Sie die Funktionalität, empfiehlt es sich um die Access-Tabellen zu löschen.  
  
## <a name="linking-access-and-sql-server-tables"></a>Verknüpfen von Access und SQL Server-Tabellen  
Wenn Sie eine Access-Tabelle zu verknüpfen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle, die Jet-Datenbank-Engine speichert Verbindungsinformationen und Tabellenmetadaten, aber die Daten werden gespeichert, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Diese Verknüpfung kann die Access-Anwendungen für die Access-Tabellen ausgeführt werden, obwohl die tatsächlichen Tabellen und Daten in sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
> [!NOTE]  
> Bei Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung, Ihr Kennwort in Klartext auf der verknüpften Tabellen für den Zugriff gespeichert. Es wird empfohlen, mithilfe der Windows-Authentifizierung.  
  
**Verknüpfen von Tabellen**  
  
1.  Wählen Sie im Metadaten-Explorer für den Zugriff die Tabellen, die Sie verknüpfen möchten.  
  
2.  Mit der rechten Maustaste **Tabellen**, und wählen Sie dann **Link**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für den Zugriff sichert die ursprünglichen Access-Tabelle und eine verknüpfte Tabelle erstellt.  
  
Nachdem Sie die Tabellen verknüpfen, werden die Tabellen in SSMA mit einem kleinen Linksymbol angezeigt. In Access werden die Tabellen mit ein "verknüpfte" angezeigt wird, handelt es sich eine Welt mit einem Pfeil, der sie darauf zeigen angezeigt.  
  
Wenn Sie eine Tabelle in Access öffnen, werden die Daten über ein Keyset-Cursor abgerufen. Daher bei großen Tabellen alle Daten werden nicht abgerufen auf einmal. Wie Sie in der Tabelle durchsuchen, ruft den Zugriff jedoch zusätzliche Daten bei Bedarf ab.  
  
> [!IMPORTANT]  
> Zum Zugreifen auf Tabellen mit einer Azure-Datenbank zu verknüpfen, die Sie benötigen SQL Server Native Client(SNAC) Version 10.5 oder höher.   
> Sie erhalten die neueste Version von SNAC aus [Microsoft® SQL Server® 2008 R2 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=196940).  
  
## <a name="unlinking-access-tables"></a>Die Verknüpfung Access-Tabellen  
Wenn Sie die Verknüpfung aufheben einer Access-Tabelle aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle SSMA stellt die ursprünglichen Access-Tabelle und die Daten wieder her.  
  
**Aufheben der Verknüpfung für Tabellen**  
  
1.  Wählen Sie im Metadaten-Explorer für den Zugriff die Tabellen, die Sie aufheben möchten.  
  
2.  Mit der rechten Maustaste **Tabellen**, und wählen Sie dann **Unlink**.  
  
## <a name="linking-tables-to-a-different-server"></a>Verknüpfen von Tabellen mit einem anderen server  
Wenn Sie die Access-Tabellen, um eine SQL Server-Instanz verknüpft haben, und Sie später den Links in einer anderen Instanz ändern möchten, müssen Sie die Tabellen neu verknüpfen.  
  
**So verknüpfen Sie Tabellen mit einem anderen server**  
  
1.  Wählen Sie im Metadaten-Explorer für den Zugriff die Tabellen, die Sie aufheben möchten.  
  
2.  Mit der rechten Maustaste **Tabellen** und wählen Sie dann **Unlink**.  
  
3.  Klicken Sie auf die **Wiederherstellen der Verbindung mit SQL Server** Schaltfläche.  
  
4.  Verbinden mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, zum Verknüpfen der Access-Tabellen werden soll.  
  
5.  Wählen Sie im Metadaten-Explorer für den Zugriff die Tabellen, die Sie verknüpfen möchten.  
  
6.  Mit der rechten Maustaste **Tabellen**, und wählen Sie dann **Link**.  
  
## <a name="updating-linked-tables"></a>Aktualisieren verknüpfte Tabellen  
Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellendefinitionen geändert werden, können Sie aufheben und dann erneut verknüpfen die Tabellen in SSMA mithilfe der Verfahren in diesem Thema beschrieben. Sie können auch die Tabellen aktualisieren, mithilfe von Access.  
  
**Verknüpfte Tabellen zu aktualisieren, indem Sie mithilfe des Zugriffs**  
  
1.  Öffnen Sie die Access-Datenbank.  
  
2.  In der **Objekte** auf **Tabellen**.  
  
3.  Mit der rechten Maustaste in einer verknüpften Tabelle aus, und wählen Sie dann **verknüpfte Tabelle Manager**.  
  
4.  Wählen Sie das Kontrollkästchen neben jeder verknüpften Tabelle, die Sie aktualisieren möchten, und klicken Sie dann auf **OK**.  
  
## <a name="possible-post-migration-issues"></a>Mögliche Probleme bei der nach der Paketmigration  
Die folgenden Abschnitte, die in die vorhandenen Access-Anwendungen auftreten können, nach der Migration von Datenbanken aus den Zugriff auf Probleme mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure und verknüpfen Sie dann die Tabellen, zusammen mit den Ursachen und Lösungen.  
  
### <a name="slow-performance-with-linked-tables"></a>Geringe Leistung mit verknüpften Tabellen  
**Ursache:** Einige Abfragen langsam nach Upsizing von den folgenden Gründen möglicherweise:  
  
-   Die Anwendung abhängig von Funktionen, die in nicht vorhanden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wodurch Jet zum Pullen von Tabellen, die lokal auf eine SELECT-Abfrage ausgeführt wird.  
  
-   Abfragen, die aktualisieren oder Löschen von vielen Zeilen, werden für jede Zeile von Jet als parametrisierte Abfrage gesendet.  
  
**Lösung:** Konvertieren Sie Pass-Through-Abfragen, gespeicherten Prozeduren oder Ansichten die langsam ausgeführte Abfragen. Konvertieren in Pass-Through-Abfragen weist die folgenden Probleme:  
  
-   Pass-Through-Abfragen können nicht geändert werden. Ergebnis der Abfrage ändern oder Hinzufügen neuer Datensätze muss auf eine andere Weise, wie z. B. anhand erfolgen müssen expliziten **ändern** oder **hinzufügen** Schaltflächen auf dem Formular, das an die Abfrage gebunden ist.  
  
-   Einige Abfragen eine Benutzereingabe erforderlich ist, aber der Benutzereingabe von Pass-Through-Abfragen nicht unterstützt. Benutzereingaben kann abgerufen werden, indem Sie Visual Basic für Applikationen (VBA) Code, der für Parameter auffordert oder ein Formular, das als ein Eingabesteuerelement verwendet wird. In beiden Fällen sendet der VBA-Code der Abfrage mit der Benutzereingabe an den Server ab.  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>Automatisch inkrementierte Spalten werden nicht aktualisiert werden, bis der Datensatz aktualisiert wird  
**Ursache:** Nach dem Aufruf von RecordSet.AddNew in Jet, ist die automatische-Inkrement-Spalte verfügbar, bevor der Datensatz aktualisiert wird. Dies ist nicht in "true" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Der neue Wert der neue Wert der Identitätsspalte ist erst nach dem Speichern des neuen Datensatzes verfügbar.  
  
**Lösung:** Führen Sie im folgende Visual Basic für Applikationen (VBA) Code vor dem Zugriff auf das Feld "Identity" aus:  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>Neue Datensätze sind nicht verfügbar  
**Ursache:** Wenn Sie einen Eintrag zum Hinzufügen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle mithilfe von VBA, wenn in der Tabelle den eindeutigen Indexfeld den Standardwert hat, und Sie nicht Sie einen Wert an dieses Feld, der neue Datensatz wird nicht angezeigt weisen, bis Sie erneut, in der Tabelle im Öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Wenn Sie versuchen, einen Wert aus der neue Datensatz abrufen, erhalten Sie die folgende Fehlermeldung angezeigt:  
  
`Run-time error '3167' Record is deleted.`  
  
**Lösung:** Beim Öffnen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle mithilfe von VBA-Code, einschließlich der `dbSeeChanges` auswählen, wie im folgenden Beispiel gezeigt:  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>Nach der Migration können einige Abfragen nicht den Benutzer einen neuen Datensatz hinzufügen  
**Ursache:** Wenn eine Abfrage nicht alle Spalten enthält, die in einem eindeutigen Index enthalten sind, können nicht Sie neue Werte hinzufügen, mit der Abfrage.  
  
**Lösung:** Stellen Sie sicher, dass alle im mindestens einen eindeutigen Index enthaltene Spalten Teil der Abfrage sind.  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Eine verknüpfte Tabelle-Schema mit dem Zugriff kann nicht geändert werden.  
**Ursache:** Nach der Migration von Daten und verknüpfen Tabellen kann nicht der Benutzer das Schema einer Tabelle in Access ändern.  
  
**Lösung:** Ändern des Tabellenschemas mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und aktualisieren Sie dann auf den Link in Access.  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>Hyperlinkfunktionalität verloren gegangen ist, nach dem Migrieren von Daten  
**Ursache:** Nach der Migration, Hyperlinks in Spalten ihre Funktionalität verlieren, und werden einfache **nvarchar(max)** Spalten.  
  
**Lösung:** Keine  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>Einige SQL Server-Datentypen werden durch den Zugriff nicht unterstützt.  
**Ursache:** Wenn Sie später aktualisieren Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen, Datentypen, die von Access, nicht unterstützt werden, enthalten Sie können nicht in der Tabelle in Access öffnen.  
  
**Lösung:** Sie können eine Access-Abfrage definieren, die nur die Zeilen mit unterstützten Datentypen zurückgibt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
