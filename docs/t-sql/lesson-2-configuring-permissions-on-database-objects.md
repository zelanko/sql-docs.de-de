---
title: 'T-SQL-Tutorial: Konfigurieren von Berechtigungen für Datenbankobjekte | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 791517685f4204f87f9c0cb96f48fe48d6828c53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122868"
---
# <a name="lesson-2-configure-permissions-on-database-objects"></a>Lektion 2: Konfigurieren von Berechtigungen für Datenbankobjekte
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Wenn Sie einem Benutzer Zugriff auf eine Datenbank gewähren möchten, müssen drei Schritte ausgeführt werden. Zuerst erstellen Sie einen Anmeldenamen. Dieser Anmeldename ermöglicht es dem Benutzer, eine Verbindung mit [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]herzustellen. Anschließend konfigurieren Sie den Anmeldenamen als Benutzer in der angegebenen Datenbank. Im letzten Schritt erteilen Sie diesem Benutzer Berechtigungen für Datenbankobjekte. In dieser Lektion werden diese drei Schritte beschrieben, und es wird gezeigt, wie eine Sicht und eine gespeicherte Prozedur als Objekt erstellt werden.  

  >[!NOTE]
  > Diese Lektion basiert auf Objekten, die in [Lektion 1: Erstellen von Datenbankobjekten](lesson-1-creating-database-objects.md) erstellt wurden. Schließen Sie Lektion 1 ab, bevor Sie mit Lektion 2 fortfahren. 

## <a name="prerequisites"></a>Voraussetzungen
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio und Zugriff auf eine SQL Server-Instanz. 

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Wenn Sie über keinen Zugriff auf eine SQL Server-Instanz verfügen, wählen Sie Ihre Plattform aus den folgenden Links aus. Wenn Sie die SQL-Authentifizierung wählen, verwenden Sie Ihre SQL Server-Anmeldeinformationen.
- **Windows**: [Herunterladen von Microsoft SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- **macOS**: [Herunterladen von SQL Server 2017 für Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens
Benutzer benötigen eine Anmeldung, damit sie auf [!INCLUDE[ssDE](../includes/ssde-md.md)]zugreifen können. Die Anmeldung kann die Identität des Benutzers als Windows-Konto oder als Mitglied einer Windows-Gruppe darstellen, oder es kann sich dabei um eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldung handeln, die nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]vorhanden ist. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
Standardmäßig haben Administratoren auf Ihrem Computer vollständigen Zugriff auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In dieser Lektion benötigen wir einen Benutzer mit geringeren Privilegien. Aus diesem Grund erstellen Sie ein neues lokales Windows-Authentifizierungskonto auf Ihrem Computer. Dazu müssen Sie über Administratorrechte auf dem Computer verfügen. Anschließend erteilen Sie diesem neuen Benutzer Zugriff auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="create-a-new-windows-account"></a>Erstellen eines neuen Windows-Kontos  
  
1.  Klicken Sie auf **Start**und auf **Ausführen**, geben Sie **%SystemRoot%\system32\compmgmt.msc /s** in das Feld **Öffnen**ein, und klicken Sie anschließend auf **OK** , um das Programm Computerverwaltung zu öffnen. 
2.  Erweitern Sie unter **Systemprogramme**den Eintrag **Lokale Benutzer und Gruppen**, klicken Sie mit der rechten Maustaste auf **Benutzer**und anschließend auf **Neuer Benutzer**.    
3.  Geben Sie in das Feld **Benutzername** **Mary**ein.    
4.  Geben Sie in das Feld **Kennwort** und **Kennwort bestätigen** ein sicheres Kennwort ein. Klicken Sie anschließend auf **Erstellen** , um einen neuen lokalen Windows-Benutzer zu erstellen.  
  
### <a name="create-a-sql-login"></a>Erstellen einer SQL-Anmeldung  

Geben Sie in einem Abfrage-Editor-Fenster von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]folgenden Code ein, und führen Sie ihn aus. Ersetzen Sie dabei `computer_name` durch den Namen Ihres Computers. `FROM WINDOWS` gibt an, dass Windows den Benutzer authentifiziert. Mit dem optionalen `DEFAULT_DATABASE` -Argument wird `Mary` mit der `TestData` -Datenbank verbunden, sofern nicht ihre Verbindungszeichenfolge eine andere Datenbank angibt. Diese Anweisung führt das Semikolon als optionale Beendigung für eine [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisung ein.
  
  ```sql  
  CREATE LOGIN [computer_name\Mary]  
      FROM WINDOWS  
      WITH DEFAULT_DATABASE = [TestData];  
  GO  
  ```  
  
  Dadurch wird ein Benutzer mit Namen `Mary`, der von Ihrem Computer authentifiziert wird, zum Zugriff auf diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]berechtigt. Ist auf dem Computer mehr als eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vorhanden, müssen Sie die Anmeldung auf jeder Instanz erstellen, auf die `Mary` Zugriff benötigt.    
  > [!NOTE]  
  > Weil `Mary` kein Domänenkonto ist, kann dieser Benutzername nur auf diesem Computer authentifiziert werden. 


## <a name="grant-access-to-a-database"></a>Gewähren von Zugriff auf eine Datenbank
Mary hat nun Zugriff auf diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], verfügt jedoch nicht über die Berechtigung zum Zugriff auf die Datenbanken. Selbst auf die Standarddatenbank **TestData** kann sie erst zugreifen, wenn Sie sie als Datenbankbenutzerin autorisieren.  
  
Wenn Sie Mary Zugriff gewähren möchten, wechseln Sie zur **TestData** -Datenbank, und ordnen Sie ihren Anmeldenamen mithilfe der CREATE USER-Anweisung einer Benutzerin namens Mary zu.  
  
### <a name="to-create-a-user-in-a-database"></a>So erstellen Sie einen Benutzer in einer Datenbank  
  
Geben Sie die folgenden Anweisungen ein (wobei Sie `computer_name` durch den Namen Ihres Computers ersetzen), und führen Sie sie aus, um `Mary` Zugriff auf die `TestData` -Datenbank zu gewähren.
  
 ```sql  
 USE [TestData];  
 GO  
 
 CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
 GO    
 ```  
  
 Mary hat nun sowohl auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als auch auf die `TestData` -Datenbank Zugriff.  


## <a name="create-views-and-stored-procedures"></a>Erstellen von Ansichten und gespeicherten Prozeduren
Als Administrator können Sie die SELECT-Anweisung in der **Products** -Tabelle und in der **vw_Names** -Sicht ausführen, und Sie können auch die **pr_Names** -Prozedur ausführen. Mary hingegen ist dazu nicht berechtigt. Verwenden Sie die GRANT-Anweisung, um Mary die erforderlichen Berechtigungen zu erteilen.  

### <a name="grant-permission-to-stored-procedure"></a>Erteilen von Berechtigungen für gespeicherte Prozeduren  
Führen Sie die folgende Anweisung aus, um `Mary` die `EXECUTE` -Berechtigung für die gespeicherte Prozedur `pr_Names` zu erteilen.
  
  ```sql  
  GRANT EXECUTE ON pr_Names TO Mary;  
  GO  
  ```  
  
In diesem Szenario kann Mary mithilfe der gespeicherten Prozedur nur auf die **Products** -Tabelle zugreifen. Wenn Sie möchten, dass Mary eine SELECT-Anweisung für die Sicht ausführen kann, müssen Sie auch `GRANT SELECT ON vw_Names TO Mary`ausführen. Verwenden Sie die REVOKE-Anweisung, um den Zugriff auf Datenbankobjekte zu entfernen.  
  
> [!NOTE]  
> Wenn der Besitzer der Tabelle, Sicht und gespeicherten Prozedur nicht das gleiche Schema ist, wird die Erteilung von Berechtigungen komplexer.  
  
### <a name="about-grant"></a>Informationen zu GRANT  
Sie müssen über die EXECUTE-Berechtigung verfügen, um eine gespeicherte Prozedur auszuführen. Sie müssen über die SELECT-, INSERT-, UPDATE- und DELETE-Berechtigungen verfügen, um auf Daten zuzugreifen und sie zu ändern. Die GRANT-Anweisung wird auch für andere Berechtigungen wie die zum Erstellen von Tabellen verwendet.  
  
## <a name="next-steps"></a>Nächste Schritte
Im nächsten Artikel erfahren Sie, wie Sie die Datenbankobjekte entfernen können, die Sie in den anderen Lektionen erstellt haben. 

Zum nächsten Artikel wechseln, um mehr zu erfahren:
> [!div class="nextstepaction"]
>[Nächste Schritte](lesson-3-deleting-database-objects.md)
  
