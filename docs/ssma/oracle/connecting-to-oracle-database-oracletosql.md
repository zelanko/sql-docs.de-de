---
title: Herstellen einer Verbindung mit Oracle-Datenbank (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: c127ef44f10723a74b2f03fed46ea42b9bbdfff5
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394461"
---
# <a name="connecting-to-oracle-database-oracletosql"></a>Herstellen einer Verbindung mit Oracle Database (OracleToSQL)
Migrieren von Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie müssen eine Verbindung, mit der Oracle-Datenbank, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, SSMA Ruft Metadaten zu allen Oracle-Schemas ab, und anschließend in der Oracle-Metadaten-Explorer-Bereich angezeigt. SSMA speichert Informationen zu den Datenbankserver, aber die Kennwörter werden nicht gespeichert.  
  
Die Verbindung mit der Datenbank bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank.  
  
Metadaten für die Oracle-Datenbank wird nicht automatisch aktualisiert. Stattdessen sollten Sie die Metadaten in Oracle-Metadaten-Explorer zu aktualisieren, müssen Sie manuell es aktualisieren. Weitere Informationen finden Sie im Abschnitt "Aktualisieren von Oracle-Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-oracle-permissions"></a>Erforderliche Oracle-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung zur Oracle-Datenbank muss zumindest **CONNECT** Berechtigungen. Dies ermöglicht der SSMA zum Abrufen von Metadaten aus Schemas im Besitz des Benutzers eine Verbindung herstellt. Um Metadaten für Objekte in anderen Schemas zu erhalten, und klicken Sie dann die Objekte in diesen Schemas konvertieren, muss das Konto folgenden Berechtigungen verfügen:  
  
-   ERSTELLEN SIE EINE PROZEDUR  
  
-   FÜHREN SIE EINE PROZEDUR  
  
-   WÄHLEN SIE EINE TABELLE  
  
-   WÄHLEN SIE EINE BELIEBIGE SEQUENZ  
  
-   ERSTELLEN SIE EINEN BELIEBIGEN TYP  
  
-   ERSTELLEN SIE EINEN BELIEBIGEN TRIGGER  
  
-   WÄHLEN SIE ALLE WÖRTERBUCH  
  
## <a name="establishing-a-connection-to-oracle"></a>Herstellen einer Verbindung mit Oracle  
Wenn Sie eine Verbindung mit einer Datenbank herstellen, SSMA liest die Datenbankmetadaten und fügt dann diese Metadaten zu der Projektdatei. Diese Metadaten werden vom SSMA verwendet, wenn Objekte konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und wenn es Daten migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können diese Metadaten im Oracle-Metadaten-Explorer durchsuchen und überprüfen Sie die Eigenschaften einzelner Datenbankobjekte.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung herstellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit Oracle**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Oracle**.  
  
    Wenn Sie zuvor mit Oracle verbunden, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung mit Oracle**.  
  
2.  In der **Anbieter** Kontrollkästchen **Oracle-Client-Anbieter** oder **OLE DB-Anbieter**, je nachdem, welcher Anbieter installiert ist. Der Standardwert ist Oracle-Client.  
  
3.  In der **Modus** wählen **Modus "Standard"**, **TNSNAME Modus**, oder **verbindungszeichenfolgenmodus**.  
  
    Verwenden Sie Modus "standard", um den Servernamen und Port anzugeben. Verwenden Sie Namen Dienstmodus, um die Oracle-Dienstname manuell anzugeben. Verwenden Sie verbindungszeichenfolgenmodus, um eine vollständige Verbindungszeichenfolge bereitstellen.  
  
4.  Bei Auswahl von **Modus "Standard"**, geben Sie die folgenden Werte:  
  
    1.  In der **Servernamen** Feld eingeben oder auswählen, den Namen oder IP-Adresse des Datenbankservers.  
  
    2.  Wenn der Datenbankserver nicht konfiguriert ist, um auf Clientverbindungen standardmäßig port (1521) verwenden, geben Sie die Portnummer, die verwendet wird, für Oracle-Verbindungen in der **Serverport** Feld.  
  
    3.  In der **Oracle SID** Geben Sie die ID des Systems.  
  
    4.  In der **Benutzernamen** Geben Sie eine Oracle-Konto, das die erforderlichen Berechtigungen verfügt.  
  
    5.  In der **Kennwort** Geben Sie das Kennwort für den angegebenen Benutzernamen ein.  
  
5.  Bei Auswahl von **TNSNAME Modus**, geben Sie die folgenden Werte:  
  
    1.  In der **Connect Bezeichner** Geben Sie eine Verbindung herstellen (TNS Alias) der Bezeichner der Datenbank.  
  
    2.  In der **Benutzernamen** Geben Sie eine Oracle-Konto, das die erforderlichen Berechtigungen verfügt.  
  
    3.  In der **Kennwort** Geben Sie das Kennwort für den angegebenen Benutzernamen ein.  
  
6.  Bei Auswahl von **verbindungszeichenfolgenmodus**, geben Sie eine Verbindungszeichenfolge in der **Verbindungszeichenfolge** Feld.  
  
    Das folgende Beispiel zeigt eine OLE DB-Verbindungszeichenfolge:  
  
    `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`  
  
    Das folgende Beispiel zeigt eine Oracle-Client-Verbindungszeichenfolge, die die integrierte Sicherheit verwendet wird:  
  
    `Data Source=MyOracleDB;Integrated Security=yes;`  
  
    Weitere Informationen finden Sie unter [auf Oracle Verbinden &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).  
  
## <a name="reconnecting-to-oracle"></a>Wiederherstellen der Verbindung mit Oracle  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank. Sie können offline arbeiten, bis Sie die Metadaten aktualisieren, laden Sie die Datenbankobjekte in möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und Daten migrieren.  
  
## <a name="refreshing-oracle-metadata"></a>Aktualisieren von Metadaten für Oracle  
Metadaten für die Oracle-Datenbank wird nicht automatisch aktualisiert. Die Metadaten in Oracle-Metadaten-Explorer ist eine Momentaufnahme der Metadaten, wenn Sie zuerst eine Verbindung hergestellt oder der letzten, dass Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Schemas, ein einzelnes Schema oder einzelne Datenbankobjekte manuell aktualisieren.  
  
**Aktualisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit der Datenbank verbunden sind.  
  
2.  Wählen Sie in Oracle-Metadaten-Explorer das Kontrollkästchen neben jedem Schema oder die Datenbank-Objekt, das Sie aktualisieren möchten.  
  
3.  Mit der rechten Maustaste **Schemas**, oder die einzelnes Schema oder die Datenbank-Objekt, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
    SSMA wird angezeigt, wenn Sie nicht über eine aktive Verbindung verfügen, die **Herstellen einer Verbindung mit Oracle** Dialogfeld, sodass Sie eine Verbindung herstellen können.  
  
4.  Geben Sie in der Aktualisierung von Datenbank (Dialogfeld) welche Objekte aktualisiert.  
  
    -   Um ein Objekt zu aktualisieren, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein Pfeil angezeigt wird.  
  
    -   Um zu verhindern, dass ein Objekt aktualisiert wird, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein **X** angezeigt wird.  
  
    -   Klicken Sie zum Aktualisieren, oder lehnen Sie eine Kategorie von Objekten ab, auf die **Active** Feld neben dem Ordner "Kategorie".  
  
    Um die Definitionen der farbcodierung anzuzeigen, klicken Sie auf die **Legende** Schaltfläche.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-step"></a>Nächster Schritt  
  
-   Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit einer Instanz von SQL Server](connecting-to-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
