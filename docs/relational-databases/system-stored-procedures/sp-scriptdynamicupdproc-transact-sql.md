---
title: sp_scriptdynamicupdproc (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptdynamicupdproc_TSQL
- sp_scriptdynamicupdproc
helpviewer_keywords:
- sp_scriptdynamicupdproc
ms.assetid: b4c18863-ed92-4aa2-a04f-7ed832fc9e07
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67ba388871720ff804063f27a378b838d300baf0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68126393"
---
# <a name="sp_scriptdynamicupdproc-transact-sql"></a>sp_scriptdynamicupdproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert die CREATE PROCEDURE-Anweisung, die eine dynamische gespeicherte Updateprozedur erstellt. Die UPDATE-Anweisung in der benutzerdefinierten gespeicherten Prozedur wird dynamisch erstellt. Als Grundlage wird die MCALL-Syntax verwendet, die angibt, welche Spalten geändert werden sollen. Verwenden Sie diese gespeicherte Prozedur, wenn die Anzahl von Indizes für die Abonnementtabelle vergrößert wird und die Anzahl von zu ändernden Spalten klein ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_scriptdynamicupdproc [ @artid =] artid  
```  
  
## <a name="arguments"></a>Argumente  
`[ @artid = ] artid`Ist die Artikel-ID. *artid* ist vom Datentyp **int**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
 Gibt ein Resultset zurück, das aus einer einzelnen **nvarchar (4000)** -Spalte besteht. Das Resultset enthält die vollständige CREATE PROCEDURE-Anweisung, die zum Erstellen der benutzerdefinierten gespeicherten Prozedur verwendet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_scriptdynamicupdproc** wird bei der Transaktions Replikation verwendet. Die standardmäßige MCALL-Skripterstellungslogik schließt alle Spalten in der UPDATE-Anweisung ein und verwendet ein Bitmuster, um die geänderten Spalten zu bestimmen. Wenn eine Spalte nicht geändert wurde, wird sie wieder auf den bestehenden Wert zurückgesetzt. Normalerweise ist dies unproblematisch. Wenn die Spalte indiziert ist, entsteht zusätzlicher Verarbeitungsaufwand. Beim dynamischen Vorgehen enthält das Update nur die Spalten, die geändert wurden, sodass eine optimale UPDATE-Zeichenfolge bereitgestellt wird. Zur Laufzeit entsteht jedoch zusätzlicher Verarbeitungsaufwand für das Erstellen der dynamischen UPDATE-Anweisung. Es wird empfohlen, dass Sie das dynamische und statische Vorgehen testen und dann die bessere Lösung auswählen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_scriptdynamicupdproc**ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird ein Artikel (mit *artid* , der auf **1**festgelegt ist) für die **Autoren** Tabelle in der **Pubs** -Datenbank erstellt und angegeben, dass die Update-Anweisung die auszuführende benutzerdefinierte Prozedur ist:  
  
```  
'MCALL sp_mupd_authors'  
```  
  
 Generieren Sie die benutzerdefinierten gespeicherten Prozeduren, die der Verteilungs-Agent auf dem Abonnenten ausführen soll. Führen Sie hierzu die folgende gespeicherte Prozedur auf dem Verleger aus:  
  
```  
EXEC sp_scriptdynamicupdproc @artid = '1'  
  
The statement returns:  
  
CREATE PROCEDURE [sp_mupd_authors]   
  @c1 varchar(11),@c2 varchar(40),@c3 varchar(20),@c4 char(12),@c5 varchar(40),@c6 varchar(20),  
  @c7 char(2),@c8 char(5),@c9 bit,@pkc1 varchar(11),@bitmap binary(2)  
as  
  
declare @stmt nvarchar(4000), @spacer nvarchar(1)  
SELECT @spacer =N''  
SELECT @stmt = N'UPDATE [authors] SET '  
  
if substring(@bitmap,1,1) & 2 = 2  
begin  
  select @stmt = @stmt + @spacer + N'[au_lname]' + N'=@2'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 4 = 4  
begin  
  select @stmt = @stmt + @spacer + N'[au_fname]' + N'=@3'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 8 = 8  
begin  
  select @stmt = @stmt + @spacer + N'[phone]' + N'=@4'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 16 = 16  
begin  
  select @stmt = @stmt + @spacer + N'[address]' + N'=@5'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 32 = 32  
begin  
  select @stmt = @stmt + @spacer + N'[city]' + N'=@6'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 64 = 64  
begin  
  select @stmt = @stmt + @spacer + N'[state]' + N'=@7'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 128 = 128  
begin  
  select @stmt = @stmt + @spacer + N'[zip]' + N'=@8'  
  select @spacer = N','  
end  
if substring(@bitmap,2,1) & 1 = 1  
begin  
  select @stmt = @stmt + @spacer + N'[contract]' + N'=@9'  
  select @spacer = N','  
end  
select @stmt = @stmt + N' where [au_id] = @1'  
exec sp_executesql @stmt, N' @1 varchar(11),@2 varchar(40),@3 varchar(20),@4 char(12),@5 varchar(40),  
                             @6 varchar(20),@7 char(2),@8 char(5),@9 bit',@pkc1,@c2,@c3,@c4,@c5,@c6,@c7,@c8,@c9  
  
if @@rowcount = 0  
   if @@microsoftversion>0x07320000  
      exec sp_MSreplraiserror 20598  
```  
  
 Nach dem Ausführen dieser gespeicherten Prozedur können Sie den resultierenden Skriptcode zum manuellen Erstellen der gespeicherten Prozedur auf den Abonnenten verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
