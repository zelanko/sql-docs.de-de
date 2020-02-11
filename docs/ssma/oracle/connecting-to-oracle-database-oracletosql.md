---
title: Herstellen einer Verbindung mit Oracle Database (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: fc25c36a0d0133975414f4c7270da2974b552f40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266189"
---
# <a name="connecting-to-oracle-database-oracletosql"></a>Herstellen einer Verbindung mit Oracle Database (OracleToSQL)
Zum Migrieren von Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken zu müssen Sie eine Verbindung mit der Oracle-Datenbank herstellen, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, werden von SSMA Metadaten zu allen Oracle-Schemas abgerufen und anschließend im Bereich Oracle-metadatenexplorer angezeigt. SSMA speichert Informationen über den Datenbankserver, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit der Datenbank bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung herstellen, wenn Sie eine aktive Verbindung mit der Datenbank herstellen möchten.  
  
Metadaten über die Oracle-Datenbank werden nicht automatisch aktualisiert. Wenn Sie die Metadaten im Oracle-metadatenexplorer aktualisieren möchten, müssen Sie Sie stattdessen manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Aktualisieren von Oracle-Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-oracle-permissions"></a>Erforderliche Oracle-Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit der Oracle-Datenbank verwendet wird, muss mindestens über **Connect** -Berechtigungen verfügen. Dies ermöglicht SSMA das Abrufen von Metadaten aus Schemas im Besitz des Benutzers, der eine Verbindung herstellt. Zum Abrufen von Metadaten für Objekte in anderen Schemas und zum anschließenden Konvertieren von Objekten in diesen Schemas muss das Konto über die folgenden Berechtigungen verfügen:  
  
-   beliebige Prozedur erstellen  
  
-   beliebige Prozedur ausführen  
  
-   beliebige Tabelle auswählen  
  
-   beliebige Sequenz auswählen  
  
-   beliebigen Typ erstellen  
  
-   beliebigen-Auslösers  
  
-   beliebiges Wörterbuch auswählen  
  
## <a name="establishing-a-connection-to-oracle"></a>Herstellen einer Verbindung mit Oracle  
Wenn Sie eine Verbindung mit einer Datenbank herstellen, liest SSMA die Metadaten der Datenbank und fügt diese Metadaten dann der Projektdatei hinzu. Diese Metadaten werden von SSMA verwendet, wenn Objekte in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Syntax konvertiert werden und Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migriert werden. Sie können diese Metadaten im Bereich Oracle-metadatenexplorer durchsuchen und die Eigenschaften einzelner Datenbankobjekte überprüfen.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung herzustellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren kann.  
  
**Zum Herstellen einer Verbindung mit Oracle**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit Oracle verbinden**aus.  
  
    Wenn Sie zuvor eine Verbindung mit Oracle hergestellt haben, wird der Befehls Name **erneut mit Oracle**verbunden.  
  
2.  Wählen Sie im Feld **Anbieter** die Option **Oracle-Client Anbieter** oder **OLE DB Anbieter**aus, je nachdem, welcher Anbieter installiert ist. Der Standardwert ist Oracle Client.  
  
3.  Wählen Sie im Feld **Modus** entweder den **Standard Modus**, den **TNSNAME-Modus**oder den **Verbindungs Zeichen folgen Modus**aus.  
  
    Verwenden Sie den Standardmodus, um den Servernamen und den Port anzugeben. Verwenden Sie den Dienstnamen Modus, um den Oracle-Dienstnamen manuell anzugeben. Verwenden Sie den Verbindungs Zeichen folgen Modus, um eine vollständige Verbindungs Zeichenfolge  
  
4.  Wenn Sie den **Standard Modus**auswählen, geben Sie die folgenden Werte an:  
  
    1.  Geben Sie im Feld **Server Name** den Namen oder die IP-Adresse des Datenbankservers ein, oder wählen Sie ihn aus.  
  
    2.  Wenn der Datenbankserver nicht für die Annahme von Verbindungen über den Standardport (1521) konfiguriert ist, geben Sie im Feld **Serverport** die Portnummer ein, die für Oracle-Verbindungen verwendet wird.  
  
    3.  Geben Sie im Feld **Oracle sid** den System Bezeichner ein.  
  
    4.  Geben Sie im Feld **Benutzername** ein Oracle-Konto ein, das über die erforderlichen Berechtigungen verfügt.  
  
    5.  Geben Sie im Feld **Kennwort** das Kennwort für den angegebenen Benutzernamen ein.  
  
5.  Wenn Sie den **TNSNAME-Modus**auswählen, geben Sie die folgenden Werte an:  
  
    1.  Geben Sie im Feld **Verbindungs Bezeichner** den Verbindungs Bezeichner (TNS-Alias) der Datenbank ein.  
  
    2.  Geben Sie im Feld **Benutzername** ein Oracle-Konto ein, das über die erforderlichen Berechtigungen verfügt.  
  
    3.  Geben Sie im Feld **Kennwort** das Kennwort für den angegebenen Benutzernamen ein.  
  
6.  Wenn Sie den **Verbindungs Zeichen folgen Modus**auswählen, geben Sie im Feld **Verbindungs Zeichenfolge** eine Verbindungs Zeichenfolge an.  
  
    Das folgende Beispiel zeigt eine OLE DB Verbindungs Zeichenfolge:  
  
    `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`  
  
    Das folgende Beispiel zeigt eine Oracle-Client Verbindungs Zeichenfolge, die die integrierte Sicherheit verwendet:  
  
    `Data Source=MyOracleDB;Integrated Security=yes;`  
  
    Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle &#40;oracleto SQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).  
  
## <a name="reconnecting-to-oracle"></a>Erneutes Herstellen einer Verbindung mit Oracle  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung herstellen, wenn Sie eine aktive Verbindung mit der Datenbank herstellen möchten. Sie können offline arbeiten, bis Sie Metadaten aktualisieren, Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]laden und Daten migrieren möchten.  
  
## <a name="refreshing-oracle-metadata"></a>Aktualisieren von Oracle-Metadaten  
Metadaten über die Oracle-Datenbank werden nicht automatisch aktualisiert. Bei den Metadaten im Oracle-metadatenexplorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung hergestellt haben, oder wenn Sie das letzte Mal manuell Sie können Metadaten für alle Schemas, ein einzelnes Schema oder einzelne Datenbankobjekte manuell aktualisieren.  
  
**So aktualisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit der Datenbank verbunden sind.  
  
2.  Aktivieren Sie im Oracle-metadatenexplorer das Kontrollkästchen neben jedem Schema oder Datenbankobjekt, das Sie aktualisieren möchten.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Schemas**oder das einzelne Schema oder Datenbankobjekt, und wählen Sie dann **aus Datenbank aktualisieren aus**.  
  
    Wenn Sie nicht über eine aktive Verbindung verfügen, zeigt SSMA das Dialogfeld **Verbindung mit Oracle herstellen an** , sodass Sie eine Verbindung herstellen können.  
  
4.  Geben Sie im Dialogfeld aus Datenbank aktualisieren an, welche Objekte aktualisiert werden sollen.  
  
    -   Um ein Objekt zu aktualisieren, klicken Sie auf das **aktive** Feld neben dem Objekt, bis ein Pfeil angezeigt wird.  
  
    -   Um zu verhindern, dass ein Objekt aktualisiert wird, klicken Sie auf das **aktive** Feld neben dem Objekt, bis ein **X** angezeigt wird.  
  
    -   Um eine Kategorie von Objekten zu aktualisieren oder abzulehnen, klicken Sie auf das **aktive** Feld neben dem Kategorieordner.  
  
    Um die Definitionen der Farbcodierung anzuzeigen, klicken Sie auf die Schaltfläche **Legende** .  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-step"></a>Nächster Schritt  
  
-   Der nächste Schritt des Migrations Vorgangs besteht darin, [eine Verbindung mit einer Instanz von SQL Server herzustellen](connecting-to-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
