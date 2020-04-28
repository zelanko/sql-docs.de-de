---
title: xp_cmdshell (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/01/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 27fd489c9076be08a814f3ea0c27ad92f1f07fa7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "80402690"
---
# <a name="xp_cmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erzeugt eine Windows-Befehlsshell und übergibt eine Zeichenfolge für die Ausführung. Die Ausgabe wird ggf. in Textzeilen zurückgegeben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Argumente  
 **"** *command_string* **"**  
 Die Zeichenfolge, die einen an das Betriebssystem zu übergebenden Befehl enthält. *command_string* ist vom Datentyp **varchar (8000)** oder **nvarchar (4000)** und hat keinen Standardwert. *command_string* darf nicht mehr als einen Satz von doppelten Anführungszeichen enthalten. Ein einzelnes Paar von Anführungszeichen ist erforderlich, wenn in den Dateipfaden oder Programmnamen, auf die in *command_string*verwiesen wird, Leerzeichen vorhanden sind. Wenn Probleme mit eingebetteten Leerzeichen auftreten, sollten Sie FAT 8.3-Dateinamen verwenden, um dieses Problem zu umgehen.  
  
 **no_output**  
 Ein optionaler Parameter, der angibt, dass keine Ausgabe an den Client zurückgegeben werden soll.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Mit der folgenden `xp_cmdshell`-Anweisung wird eine Verzeichnisaufstellung des aktuellen Verzeichnisses zurückgegeben.  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 Die Zeilen werden in einer Spalte vom Typ **nvarchar (255)** zurückgegeben. Wenn die **no_output** -Option verwendet wird, wird nur Folgendes zurückgegeben:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der von **xp_cmdshell** erzeugte Windows-Prozess hat die gleichen Sicherheitsrechte wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Dienst Konto.  
  
 **xp_cmdshell** erfolgt synchron. Die Steuerung wird erst dann an den Aufrufer zurückgegeben, wenn der Befehl der Befehlsshell abgeschlossen wurde.  
  
 **xp_cmdshell** können mithilfe der Richtlinien basierten Verwaltung oder durch Ausführen von **sp_configure**aktiviert und deaktiviert werden. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) und [xp_cmdshell Server Configuration Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]
>  Wenn **xp_cmdshell** innerhalb eines Batches ausgeführt wird und einen Fehler zurückgibt, tritt ein Fehler auf. Dies ist eine Änderung des Verhaltens. In früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde der Batch weiterhin ausgeführt.  
  
## <a name="xp_cmdshell-proxy-account"></a>xp_cmdshell-Proxykonto  
 Wenn Sie von einem Benutzer aufgerufen wird, der kein Mitglied der festen Server Rolle **sysadmin** ist, stellt **xp_cmdshell** eine Verbindung mit Windows her, indem er den in den Anmelde Informationen mit dem Namen **# #xp_cmdshell_proxy_account # #** gespeicherten Kontonamen und das Kennwort verwendet. Wenn diese Proxy Anmelde Informationen nicht vorhanden sind, schlägt **xp_cmdshell** fehl.  
  
 Die Anmelde Informationen des Proxy Kontos können durch Ausführen von **sp_xp_cmdshell_proxy_account**erstellt werden. Als Argumente besitzt diese gespeicherte Prozedur einen Windows-Benutzernamen und ein Kennwort. Mit dem folgenden Befehl werden z. B. Proxyanmeldeinformationen für den Windows-Domänenbenutzer `SHIPPING\KobeR` erstellt, der das Windows-Kennwort `sdfh%dkc93vcMt0` besitzt.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Weitere Informationen finden Sie unter [sp_xp_cmdshell_proxy_account &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Da böswillige Benutzer manchmal versuchen, ihre Berechtigungen mithilfe von **xp_cmdshell**zu erhöhen, ist **xp_cmdshell** standardmäßig deaktiviert. Verwenden Sie **sp_configure** oder **Richtlinien basierte Verwaltung** , um Sie zu aktivieren. Weitere Informationen finden Sie unter [xp_cmdshell (Serverkonfigurationsoption)](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 Bei der ersten Aktivierung erfordert **xp_cmdshell** die Control Server-Berechtigung für die Ausführung, und der von **xp_cmdshell** erstellte Windows-Prozess hat denselben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherheitskontext wie das Dienst Konto. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst Konto verfügt häufig über mehr Berechtigungen, als für die Arbeit erforderlich sind, die von dem von **xp_cmdshell**erstellten Prozess ausgeführt wird. Um die Sicherheit zu erhöhen, sollte der Zugriff auf **xp_cmdshell** auf Benutzer mit hohen Privilegien eingeschränkt werden.  
  
 Führen Sie die folgenden Schritte aus, **xp_cmdshell**um nicht Administratoren die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwendung von xp_cmdshell zu gestatten und das Erstellen von untergeordneten Prozessen mit dem Sicherheits Token eines Kontos mit geringen Rechten zu ermöglichen:  
  
1.  Erstellen Sie ein lokales Windows-Benutzerkonto oder ein Domänenkonto mit den geringsten Berechtigungen, die von den Prozessen benötigt werden, und passen Sie es an.  
  
2.  Verwenden Sie das Verfahren **sp_xp_cmdshell_proxy_account** System, um **xp_cmdshell** für die Verwendung dieses Kontos mit den geringsten Berechtigungen zu konfigurieren.  
  
    > [!NOTE]  
    >  Sie können [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dieses Proxy Konto auch mithilfe von konfigurieren, indem Sie in Objekt-Explorer mit der rechten Maustaste auf **Eigenschaften** Ihres Server namens klicken und auf der Registerkarte **Sicherheit** für den Abschnitt **Server Proxy Konto** suchen.  
  
3.  Führen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie in mithilfe der Master-Datenbank die `GRANT exec ON xp_cmdshell TO N'<some_user>';` -Anweisung aus, um bestimmten nicht-**sysadmin** -Benutzern die Ausführung von **xp_cmdshell**zu ermöglichen. Der angegebene Benutzer muss in der Master-Datenbank vorhanden sein.  
  
 Nicht Administratoren können jetzt Betriebssystem Prozesse mit **xp_cmdshell** starten, und diese Prozesse werden mit den Berechtigungen des von Ihnen konfigurierten Proxy Kontos ausgeführt. Benutzer mit Control Server-Berechtigung (Mitglieder der festen Server Rolle **sysadmin** ) empfangen weiterhin die Berechtigungen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst Kontos für untergeordnete Prozesse, die von **xp_cmdshell**gestartet werden.  
  
 Führen Sie die folgende Anweisung aus, um das Windows-Konto zu bestimmen, das von **xp_cmdshell** beim Starten von Betriebssystem Prozessen verwendet wird:  
  
```  
xp_cmdshell 'whoami.exe'  
  
```  
  
 Um den Sicherheitskontext für einen anderen Anmeldenamen zu bestimmen, führen Sie folgende Anweisung aus:  
  
```  
EXECUTE AS LOGIN = '<other_login>' ;  
GO  
xp_cmdshell 'whoami.exe' ;  
REVERT ;  
  
```  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-a-list-of-executable-files"></a>A. Zurückgeben einer Liste der ausführbaren Dateien  
 Im folgenden Beispiel wird mithilfe der erweiterten gespeicherten Prozedur `xp_cmdshell` der Befehl DIR ausgeführt.  
  
```  
EXEC master..xp_cmdshell 'dir *.exe'  
```  
  
### <a name="b-returning-no-output"></a>B. Unterdrücken der Ausgabe  
 Im folgenden Beispiel wird mit `xp_cmdshell` eine Befehlszeichenfolge ausgeführt, ohne dass die Ausgabe an den Client zurückgegeben wird.  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks', NO_OUTPUT;  
GO  
```  
  
### <a name="c-using-return-status"></a>C. Verwenden des Rückgabestatus  
 Im folgenden Beispiel wird von der `xp_cmdshell` erweiterten gespeicherten Prozedur auch der Rückgabestatus vorgeschlagen. Der Rückgabecodewert wird in der Variablen `@result` gespeichert.  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D. Schreiben des Inhalts von Variablen in eine Datei  
 Im folgenden Beispiel wird der Inhalt der `@var`-Variablen in die Datei `var_out.txt` im aktuellen Serververzeichnis geschrieben.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>E. Aufzeichnen des Ergebnisses eines Befehls in einer Datei  
 Im folgenden Beispiel wird der Inhalt des aktuellen Verzeichnisses in die Datei `dir_out.txt` im aktuellen Serververzeichnis geschrieben.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_cmdshell (Server Konfigurations Option)](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
