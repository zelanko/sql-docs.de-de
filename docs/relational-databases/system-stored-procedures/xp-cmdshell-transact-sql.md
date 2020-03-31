---
title: xp_cmdshell (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2020
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
ms.openlocfilehash: 2ce32fc31373077418e77d31ce064d60e23f1b24
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
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
 **'** *command_string* **'**  
 Die Zeichenfolge, die einen an das Betriebssystem zu übergebenden Befehl enthält. *command_string* ist **varchar(8000)** oder **nvarchar(4000)**, ohne Standard. *command_string* dürfen nicht mehr als einen Satz doppelter Anführungszeichen enthalten. Ein einzelnes Paar von Anführungszeichen ist erforderlich, wenn in den Dateipfaden oder Programmnamen, auf die in *command_string*verwiesen wird, Leerzeichen vorhanden sind. Wenn Probleme mit eingebetteten Leerzeichen auftreten, sollten Sie FAT 8.3-Dateinamen verwenden, um dieses Problem zu umgehen.  
  
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
  
 Die Zeilen werden in einer **nvarchar(255)-Spalte** zurückgegeben. Wenn die **Option no_output** verwendet wird, wird nur Folgendes zurückgegeben:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der Windows-Prozess, der von **xp_cmdshell** erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde, verfügt über dieselben Sicherheitsrechte wie das Dienstkonto.  
  
 **xp_cmdshell** arbeitet synchron. Die Steuerung wird erst dann an den Aufrufer zurückgegeben, wenn der Befehl der Befehlsshell abgeschlossen wurde.  
  
 **xp_cmdshell** können aktiviert und deaktiviert werden, indem Sie die richtlinienbasierte Verwaltung verwenden oder **sp_configure**ausführen. Weitere Informationen finden Sie unter [Oberflächenbereichskonfiguration](../../relational-databases/security/surface-area-configuration.md) und [xp_cmdshell Serverkonfigurationsoption](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]
>  Wenn **xp_cmdshell** innerhalb eines Batches ausgeführt wird und einen Fehler zurückgibt, schlägt der Stapel fehl.
  
## <a name="xp_cmdshell-proxy-account"></a>xp_cmdshell-Proxykonto  
 Wenn es von einem Benutzer aufgerufen wird, der kein Mitglied der **sysadmin** Fixed Server-Rolle ist, **stellt xp_cmdshell** eine Verbindung mit Windows her, indem er den Kontonamen und das Kennwort verwendet, die in den Anmeldeinformationen mit dem Namen **"#xp_cmdshell_proxy_account"** gespeichert sind. Wenn diese Proxyanmeldeinformationen nicht vorhanden sind, schlägt **xp_cmdshell** fehl.  
  
 Die Anmeldeinformationen für das Proxykonto können durch Ausführen **sp_xp_cmdshell_proxy_account**erstellt werden. Als Argumente besitzt diese gespeicherte Prozedur einen Windows-Benutzernamen und ein Kennwort. Mit dem folgenden Befehl werden z. B. Proxyanmeldeinformationen für den Windows-Domänenbenutzer `SHIPPING\KobeR` erstellt, der das Windows-Kennwort `sdfh%dkc93vcMt0` besitzt.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Weitere Informationen finden Sie unter [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Da böswillige Benutzer manchmal versuchen, ihre Berechtigungen mithilfe von **xp_cmdshell**zu erhöhen, ist **xp_cmdshell** standardmäßig deaktiviert. Verwenden Sie **sp_configure** oder **Richtlinienbasierte Verwaltung,** um sie zu aktivieren. Weitere Informationen finden Sie unter [xp_cmdshell (Serverkonfigurationsoption)](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 Bei der ersten Aktivierung **erfordert xp_cmdshell** die CONTROL SERVER-Berechtigung zum Ausführen, und der von **xp_cmdshell** erstellte Windows-Prozess verfügt über denselben Sicherheitskontext wie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienstkonto. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienstkonto verfügt häufig über mehr Berechtigungen, als für die Arbeit erforderlich sind, die von dem von **xp_cmdshell**erstellten Prozess ausgeführt wird. Um die Sicherheit zu erhöhen, sollte der Zugriff auf **xp_cmdshell** auf Benutzer mit hohen Berechtigungen beschränkt werden.  
  
 Führen Sie die folgenden Schritte aus, damit Nicht-Administratoren **xp_cmdshell**verwenden und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] untergeordnete Prozesse mit dem Sicherheitstoken eines Kontos mit geringerer Berechtigungen erstellen können:  
  
1.  Erstellen Sie ein lokales Windows-Benutzerkonto oder ein Domänenkonto mit den geringsten Berechtigungen, die von den Prozessen benötigt werden, und passen Sie es an.  
  
2.  Verwenden Sie die **sp_xp_cmdshell_proxy_account** Systemprozedur, um **xp_cmdshell** für die Verwendung dieses Kontos mit den geringsten Berechtigungen zu konfigurieren.  
  
    > [!NOTE]  
    >  Sie können dieses Proxykonto [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auch konfigurieren, indem Sie mit der rechten Maustaste auf **Eigenschaften** für Ihren Servernamen im Objekt-Explorer klicken und auf der Registerkarte **Sicherheit** nach dem Abschnitt **Serverproxykonto** suchen.  
  
3.  Führen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie unter der Verwendung `GRANT exec ON xp_cmdshell TO N'<some_user>';` der Masterdatenbank die Anweisung aus, um bestimmten**Nicht-Sysadmin-Benutzern** die Möglichkeit zu geben, **xp_cmdshell**auszuführen. Der angegebene Benutzer muss in der Masterdatenbank vorhanden sein.  
  
 Jetzt können Nicht-Administratoren Betriebssystemprozesse mit **xp_cmdshell** starten, und diese Prozesse werden mit den Berechtigungen des von Ihnen konfigurierten Proxykontos ausgeführt. Benutzer mit CONTROL SERVER-Berechtigung (Mitglieder der **sysadmin** Fixed Server-Rolle) erhalten weiterhin die Berechtigungen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienstkontos für untergeordnete Prozesse, die von **xp_cmdshell**gestartet werden.  
  
 Führen Sie die folgende Anweisung aus, um das Windows-Konto zu ermitteln, das von **xp_cmdshell** beim Starten von Betriebssystemprozessen verwendet wird:  
  
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
 Im folgenden Beispiel `xp_cmdshell` schlägt die erweiterte gespeicherte Prozedur auch den Rückgabestatus vor. Der Rückgabecodewert wird in der Variablen `@result` gespeichert.  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D: Schreiben des Inhalts von Variablen in eine Datei  
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
  
## <a name="see-also"></a>Siehe auch  
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_cmdshell Serverkonfigurationsoption](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Oberflächenflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
