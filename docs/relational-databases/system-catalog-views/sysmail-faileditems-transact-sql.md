---
title: Sysmail_faileditems (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_faileditems
- sysmail_faileditems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_faileditems database mail view
ms.assetid: a31562c5-358e-4cfc-a72d-b3faccc53851
author: stevestein
ms.author: sstein
ms.openlocfilehash: 586727c86dca057abeb221c828720ea38e24d7b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060215"
---
# <a name="sysmailfaileditems-transact-sql"></a>sysmail_faileditems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Datenbank-Mail-Nachricht mit der **Fehler** Status. Verwenden Sie diese Sicht, um zu ermitteln, welche Nachrichten nicht erfolgreich gesendet werden konnten.  
  
 Um alle von der Datenbank-e-Mails verarbeiteten Nachrichten anzuzeigen, verwenden [Sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Um nur ungesendete Nachrichten anzuzeigen, verwenden Sie [Sysmail_unsentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Um nur die Nachrichten anzuzeigen, die gesendet wurden, verwenden [Sysmail_sentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md). Verwenden Sie zum Anzeigen der e-Mail-Anlagen [Sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Der Bezeichner des E-Mail-Elements in der E-Mail-Warteschlange.|  
|**profile_id**|**int**|Der Bezeichner des Profils, das zum Übermitteln der Nachricht verwendet wurde.|  
|**Empfänger**|**varchar(max)**|Die E-Mail-Adressen der Nachrichtenempfänger.|  
|**copy_recipients**|**varchar(max)**|Die E-Mail-Adressen derer, die Kopien der Nachricht erhalten.|  
|**blind_copy_recipients**|**varchar(max)**|Die E-Mail-Adressen derer, die Kopien der Nachricht erhalten, deren Namen jedoch nicht im Nachrichtenkopf angezeigt werden.|  
|**subject**|**nvarchar(510)**|Die Betreffzeile der Nachricht.|  
|**body**|**varchar(max)**|Der Textkörper der Nachricht.|  
|**body_format**|**varchar(20)**|Das Textkörperformat der Nachricht. Mögliche Werte sind TEXT und HTML.|  
|**Wichtigkeit**|**varchar(6)**|Die **Wichtigkeit** -Parameter der Nachricht.|  
|**Empfindlichkeit**|**varchar(12)**|Die **Vertraulichkeit** -Parameter der Nachricht.|  
|**file_attachments**|**varchar(max)**|Eine durch Semikolons getrennte Liste der Dateinamen, die an die E-Mail-Nachricht angehängt wurden.|  
|**Attachment_encoding**|**varchar(20)**|Der Typ der E-Mail-Anlage.|  
|**Query**|**varchar(max)**|Die Abfrage, die vom E-Mail-Programm ausgeführt wurde.|  
|**execute_query_database**|**sysname**|Der Datenbankkontext, in dem das E-Mail-Programm die Abfrage ausgeführt hat.|  
|**attach_query_result_as_file**|**bit**|Bei einem Wert von 0 wurden die Abfrageergebnisse hinter dem Inhalt des Textkörpers in den Textkörper der E-Mail-Nachricht eingeschlossen. Bei einem Wert von 1 wurden die Ergebnisse als Anlage zurückgegeben.|  
|**query_result_header**|**bit**|Bei einem Wert von 1 enthielten die Abfrageergebnisse Spaltenheader. Bei einem Wert von 0 enthielten die Abfrageergebnisse keine Spaltenheader.|  
|**query_result_width**|**int**|Die **Query_result_width** -Parameter der Nachricht.|  
|**query_result_separator**|**char(1)**|Das Zeichen, das zum Trennen der Spalten in der Abfrageausgabe verwendet wird.|  
|**exclude_query_output**|**bit**|Die **Exclude_query_output** -Parameter der Nachricht. Weitere Informationen finden Sie unter [Sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Die **Append_query_error** -Parameter der Nachricht. 0 zeigt an, dass die Datenbank-E-Mail die Nachricht nicht senden soll, wenn die Abfrage einen Fehler enthält.|  
|**send_request_date**|**datetime**|Das Datum und die Uhrzeit, an dem bzw. zu der die Nachricht in der E-Mail-Warteschlange platziert wurde.|  
|**send_request_user**|**sysname**|Der Benutzer, der die Nachricht übermittelt hat. Hierbei handelt es sich um den Benutzerkontext der Datenbank-E-Mail-Prozedur, nicht um das Von-Feld der Nachricht.|  
|**sent_account_id**|**int**|Der Bezeichner des Datenbank-E-Mail-Kontos, das zum Senden der Nachricht verwendet wird. Für diese Sicht immer NULL.|  
|**sent_status**|**varchar(8)**|Der Status der E-Mail. Immer **Fehler** für diese Sicht.|  
|**sent_date**|**datetime**|Das Datum und die Uhrzeit, an dem bzw. zu der die Nachricht aus der E-Mail-Warteschlange entfernt wurde.|  
|**last_mod_date**|**datetime**|Das Datum und die Uhrzeit der letzten Änderung der Zeile.|  
|**last_mod_user**|**sysname**|Der Benutzer, der die Zeile zuletzt geändert hat.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Sysmail_faileditems** um anzuzeigen, welche Nachrichten nicht durch Datenbank-e-Mails gesendet wurden. Wenn Sie Probleme mit der Datenbank-E-Mail behandeln, kann diese Sicht Ihnen helfen, die Ursache des Problems zu identifizieren, da sie Ihnen die Attribute der Nachrichten anzeigt, die nicht gesendet wurden. Die Ursache des Fehlers finden Sie unter dem Eintrag für die fehlerhafte Nachricht in die [Sysmail_event_log &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) anzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Gewährt **Sysadmin** Serverrolle und **Databasemailuserrole** -Datenbankrolle. Beim Ausführen von einem Mitglied der **Sysadmin** festen Serverrolle in dieser Ansicht werden alle fehlgeschlagene Nachrichten. Für alle anderen Benutzer werden nur die von ihnen übermittelten fehlgeschlagenen Nachrichten angezeigt.  
  
  
