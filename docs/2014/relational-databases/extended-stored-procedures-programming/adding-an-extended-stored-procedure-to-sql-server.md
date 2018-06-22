---
title: Hinzufügen einer erweiterten gespeicherten Prozedur zu SQLServer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b69f6ba2dd0fc6c5b3b2ce4f93e70239d8868007
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060715"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a>Hinzufügen einer erweiterten gespeicherten Prozedur zu SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Eine DLL, die erweiterte gespeicherte Prozedurfunktionen enthält, stellt eine Erweiterung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dar. Um die DLL zu installieren, kopieren Sie die Datei in ein Verzeichnis, z. B. das Projekt, das den Standard enthält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL-Dateien (C:\Program Files\Microsoft SQL Server\MSSQL12.0. *X*standardmäßig \MSSQL\Binn).  
  
 Nachdem die DLL mit der erweiterten gespeicherten Prozedur auf den Server kopiert wurde, muss ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemadministrator jede Funktion der in der DLL enthaltenen erweiterten gespeicherten Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registrieren. Hierzu wird die gespeicherte Systemprozedur sp_addextendedproc verwendet.  
  
> [!IMPORTANT]  
>  Der Systemadministrator muss die erweiterte gespeicherte Prozedur sorgfältig überprüfen, um sicherzustellen, dass sie keinen schädlichen oder bösartigen Code enthält, bevor er sie dem Server hinzufügt und anderen Benutzern Berechtigungen zum Ausführen der Prozedur gewährt.  Überprüfen Sie alle Benutzereingaben. Verketten Sie Benutzereingaben nicht vor der Überprüfung. Führen Sie niemals Befehle aus, die sich aus nicht überprüften Benutzereingaben zusammensetzen.  
  
 Der erste Parameter namens sp_addextendedproc gibt den Namen der Funktion an, und der zweite Parameter gibt den Namen der DLL an, in der sich die Funktion befindet. Es ist empfehlenswert, den vollständigen Pfad der DLL anzugeben.  
  
> [!IMPORTANT]  
>  Vorhandene DLLs, die nicht mit einem vollständigen Pfad registriert wurden, sind nach dem Upgrade auf SQL Server 2005 oder höher nicht mehr funktionsfähig. Verwenden Sie zum Beheben des Problems sp_dropextendedproc, um die Registrierung der DLL aufzuheben. Registrieren Sie sie dann mit sp_addextendedproc unter Angabe des vollständigen Pfades erneut.  
  
 Der Name der im `sp_addextendedproc`-Parameter angegebenen Funktion muss genau (einschließlich Groß-/Kleinschreibung) dem Funktionsnamen in der DLL entsprechen. Zum Beispiel wird mit dem folgenden Befehl die Funktion `xp_hello,`, die sich in der DLL mit dem Namen `xp_hello.dll` befindet, als erweiterte gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur registriert:  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 Entspricht der in `sp_addextendedproc` angegebene Funktionsname nicht genau dem Funktionsnamen in der DLL, dann wird der neue Name in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert, kann jedoch nicht verwendet werden. Beispielsweise zwar `xp_Hello` als registriert eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erweiterte gespeicherte Prozedur befindet sich im `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird nicht in der Lage, die Funktion in der DLL finden, wenn Sie `xp_Hello` später die Funktion aufgerufen.  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 Wenn der in `sp_addextendedproc` angegebene Funktionsname genau dem Funktionsnamen in der DLL entspricht, und die in der Sortierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht zwischen Groß- und Kleinschreibung unterschieden wird, dann kann der Benutzer die erweiterte gespeicherte Prozedur unter Angabe des Namens aufrufen, wobei dieser beliebige Kombinationen von Klein- und Großbuchstaben enthalten kann.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 Wenn die Sortierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zwischen Groß- und Kleinschreibung unterscheidet, dann kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die erweiterte gespeicherte Prozedur nicht aufrufen, wenn sich die Groß-/Kleinschreibung des Namens im Aufruf vom registrierten Namen unterscheidet. Dies gilt auch dann, wenn die Prozedur mit dem gleichen Namen und der gleichen Sortierung wie die Funktion in der DLL registriert wurde.  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 Es ist nicht notwendig, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu beenden und neu zu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
