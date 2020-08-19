---
description: sp_send_dbmail (Transact-SQL)
title: sp_send_dbmail (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 95b9b18b6f36ebbd8d43f38a2bc8fe28d8f3288b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446767"
---
# <a name="sp_send_dbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Sendet eine E-Mail-Nachricht an die angegebenen Empfänger. Die Nachricht kann ein Abfrageresultset, Dateianlagen oder beides enthalten. Wenn e-Mail-Nachrichten erfolgreich in der Datenbank-E-Mail Warteschlange platziert werden, gibt **sp_send_dbmail** den **mailitem_id** der Nachricht zurück. Diese gespeicherte Prozedur wird in der **msdb** -Datenbank gespeichert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_name = ] 'profile_name'` Der Name des Profils, von dem die Nachricht gesendet werden soll. Der *profile_name* ist vom Datentyp **vom Datentyp sysname**und hat den Standardwert NULL. Der *profile_name* muss der Name eines vorhandenen Datenbank-E-Mail Profils sein. Wenn keine *profile_name* angegeben ist, verwendet **sp_send_dbmail** das private Standardprofil für den aktuellen Benutzer. Wenn der Benutzer nicht über ein privates Standardprofil verfügt, verwendet **sp_send_dbmail** das öffentliche Standardprofil für die **msdb** -Datenbank. Wenn der Benutzer nicht über ein privates Standardprofil verfügt und kein öffentliches Standardprofil für die Datenbank vorhanden ist, müssen ** \@ profile_name** angegeben werden.  
  
`[ @recipients = ] 'recipients'` Eine durch Semikolons getrennte Liste von e-Mail-Adressen, an die die Nachricht gesendet werden soll. Die Empfängerliste ist vom Typ **varchar (max)**. Obwohl dieser Parameter optional ist, muss mindestens einer der ** \@ Empfänger**, ** \@ copy_recipients**oder ** \@ blind_copy_recipients** angegeben werden, oder **sp_send_dbmail** gibt einen Fehler zurück.  
  
`[ @copy_recipients = ] 'copy_recipients'` Eine durch Semikolons getrennte Liste von e-Mail-Adressen, in die die Nachricht kopiert werden soll. Die Liste der Kopier Empfänger ist vom Typ **varchar (max)**. Obwohl dieser Parameter optional ist, muss mindestens einer der ** \@ Empfänger**, ** \@ copy_recipients**oder ** \@ blind_copy_recipients** angegeben werden, oder **sp_send_dbmail** gibt einen Fehler zurück.  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'` Ist eine durch Semikolons getrennte Liste von e-Mail-Adressen, an die Blind Kohle kopiert werden soll. Die Liste der Empfänger für blinde Kopien ist vom Typ **varchar (max)**. Obwohl dieser Parameter optional ist, muss mindestens einer der ** \@ Empfänger**, ** \@ copy_recipients**oder ** \@ blind_copy_recipients** angegeben werden, oder **sp_send_dbmail** gibt einen Fehler zurück.  
  
`[ @from_address = ] 'from_address'` Der Wert von "From Address" (from Address) der e-Mail-Nachricht. Dies ist ein optionaler Parameter, mit dem die Einstellungen im Mailprofil überschrieben werden. Dieser Parameter ist vom Typ **varchar (max)**. SMTP-Sicherheitseinstellungen stellen fest, ob diese Überschreibungen akzeptiert werden. Wenn kein Parameter angegeben ist, wird der Standardwert NULL verwendet.  
  
`[ @reply_to = ] 'reply_to'` Der Wert für die Antwort auf die Adresse der e-Mail-Nachricht. Er akzeptiert nur eine E-Mail-Adresse als gültigen Wert. Dies ist ein optionaler Parameter, mit dem die Einstellungen im Mailprofil überschrieben werden. Dieser Parameter ist vom Typ **varchar (max)**. SMTP-Sicherheitseinstellungen stellen fest, ob diese Überschreibungen akzeptiert werden. Wenn kein Parameter angegeben ist, wird der Standardwert NULL verwendet.  
  
`[ @subject = ] 'subject'` Der Betreff der e-Mail-Nachricht. Der Betreff ist vom Typ **nvarchar (255)**. Wenn Sie keinen Betreff angeben, wird standardmäßig 'SQL Server-Nachricht' verwendet.  
  
`[ @body = ] 'body'` Der Text der e-Mail-Nachricht. Der Nachrichtentext ist vom Datentyp **nvarchar (max)** und hat den Standardwert NULL.  
  
`[ @body_format = ] 'body_format'` Das Format des Nachrichten Texts. Der-Parameter ist vom Typ **varchar (20)** und hat den Standardwert NULL. Wenn der Parameter angegeben ist, wird in den Headern der ausgehenden Nachricht angezeigt, dass der Nachrichtentext das angegebene Format besitzt. Der Parameter kann einen der folgenden Werte enthalten:  
  
-   TEXT  
  
-   HTML  
  
 Der Standardwert ist TEXT.  
  
`[ @importance = ] 'importance'` Die Wichtigkeit der Nachricht. Der-Parameter ist vom Typ **varchar (6)**. Der Parameter kann einen der folgenden Werte enthalten:  
  
-   Niedrig  
  
-   Normal  
  
-   High  
  
 Der Standardwert ist Normal.  
  
`[ @sensitivity = ] 'sensitivity'` Die Empfindlichkeit der Nachricht. Der-Parameter ist vom Typ **varchar (12)**. Der Parameter kann einen der folgenden Werte enthalten:  
  
-   Normal  
  
-   Persönlich  
  
-   Private  
  
-   Vertraulich  
  
 Der Standardwert ist Normal.  
  
`[ @file_attachments = ] 'file_attachments'` Eine durch Semikolons getrennte Liste von Dateinamen, die an die e-Mail-Nachricht angefügt werden sollen. Die Dateien in der Liste müssen als absolute Pfade angegeben sein. Die Liste der Anlagen ist vom Typ **nvarchar (max)**. Standardmäßig beschränkt Datenbank-E-Mail Dateianlagen auf 1 MB pro Datei.  
 
 > [!IMPORTANT]
 > Dieser Parameter ist in Azure SQL verwaltete Instanz nicht verfügbar, da er nicht auf das lokale Dateisystem zugreifen kann.
  
`[ @query = ] 'query'` Eine auszuführende Abfrage. Die Ergebnisse der Abfrage können als Datei angefügt oder in den Text der E-Mail-Nachricht eingeschlossen werden. Die Abfrage ist vom Typ **nvarchar (max)** und kann beliebige gültige- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen enthalten. Beachten Sie, dass die Abfrage in einer separaten Sitzung ausgeführt wird, sodass lokale Variablen im Skript, das **sp_send_dbmail** aufrufen, für die Abfrage nicht verfügbar sind.  
  
`[ @execute_query_database = ] 'execute_query_database'` Der Daten Bank Kontext, in dem die gespeicherte Prozedur die Abfrage ausführt. Der-Parameter ist vom Typ **vom Datentyp sysname**und hat den Standardwert der aktuellen Datenbank. Dieser Parameter ist nur anwendbar, wenn die ** \@ Abfrage** angegeben wird.  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file` Gibt an, ob das Resultset der Abfrage als angefügte Datei zurückgegeben wird. *attach_query_result_as_file* ist vom Typ **Bit**und hat den Standardwert 0.  
  
 Wenn der Wert 0 ist, werden die Abfrageergebnisse nach dem Inhalt des ** \@ Body** -Parameters in den Text der e-Mail-Nachricht eingeschlossen. Ist der Wert 1, werden die Ergebnisse als Anlage zurückgegeben. Dieser Parameter ist nur anwendbar, wenn die ** \@ Abfrage** angegeben wird.  
  
`[ @query_attachment_filename = ] query_attachment_filename` Gibt den Dateinamen an, der für das Resultset der Abfrage Anlage verwendet werden soll. *query_attachment_filename* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Dieser Parameter wird ignoriert, wenn *attach_query_result* 0 ist. Wenn *attach_query_result* 1 und dieser Parameter NULL ist, erstellt Datenbank-E-Mail einen beliebigen Dateinamen.  
  
`[ @query_result_header = ] query_result_header` Gibt an, ob die Abfrageergebnisse Spaltenheader einschließen. Der query_result_header Wert ist vom Typ " **Bit**". Bei einem Wert von 1 enthalten die Abfrageergebnisse Spaltenheader. Bei einem Wert von 0 enthalten die Abfrageergebnisse keine Spaltenheader. Dieser Parameter hat den Standardwert **1**. Dieser Parameter ist nur anwendbar, wenn die ** \@ Abfrage** angegeben wird.  
 
   >[!NOTE]
   > Der folgende Fehler kann auftreten, wenn \@ Sie query_result_header auf 0 festlegen und \@ query_no_truncate auf 1 festlegen:
   > <br> Meldung 22050, Ebene 16, Status 1, Zeile 12: Fehler beim Initialisieren der sqlcmd-Bibliothek mit der Fehlernummer-2147024809.
  
`[ @query_result_width = ] query_result_width` Die Linienbreite in Zeichen, die zum Formatieren der Ergebnisse der Abfrage verwendet werden soll. Der *query_result_width* ist vom Typ **int**, der Standardwert ist 256. Der Wert muss zwischen 10 and 32767 liegen. Dieser Parameter ist nur anwendbar, wenn die ** \@ Abfrage** angegeben wird.  
  
`[ @query_result_separator = ] 'query_result_separator'` Das Zeichen, das zum Trennen von Spalten in der Abfrageausgabe verwendet wird. Das Trennzeichen ist vom Typ **char (1)**. Der Standardwert ist ' ' (Leerzeichen).  
  
`[ @exclude_query_output = ] exclude_query_output` Gibt an, ob die Ausgabe der Abfrage Ausführung in der e-Mail-Nachricht zurückgegeben werden soll. **exclude_query_output** ist vom Typ Bit. der Standardwert ist 0. Wenn dieser Parameter 0 ist, druckt die Ausführung der gespeicherten Prozedur **sp_send_dbmail** die Nachricht, die als Ergebnis der Abfrage Ausführung auf der Konsole zurückgegeben wird. Wenn dieser Parameter 1 ist, druckt die Ausführung der gespeicherten Prozedur **sp_send_dbmail** keine Abfrage Ausführungs Nachrichten auf der Konsole.  
  
`[ @append_query_error = ] append_query_error`Gibt an, ob die e-Mail gesendet werden soll, wenn ein Fehler aus der im ** \@ Abfrage** Argument angegebenen Abfrage zurückgegeben wird. **append_query_error** ist vom Typ **Bit**. der Standardwert ist 0. Ist dieser Parameter auf 1 festgelegt, sendet Datenbank-E-Mail die E-Mail-Nachricht und bezieht die Abfragefehlermeldung in den Text der E-Mail-Nachricht ein. Wenn dieser Parameter 0 ist, sendet Datenbank-E-Mail die e-Mail-Nachricht nicht, und **sp_send_dbmail** endet mit dem Rückgabecode 1, was auf einen Fehler hinweist.  
  
`[ @query_no_truncate = ] query_no_truncate` Gibt an, ob die Abfrage mit der Option ausgeführt werden soll, die das Abschneiden von großen Datentypen variabler Länge (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **Text**, **ntext**, **Image**und benutzerdefinierte Datentypen) vermeidet. Wenn fetgelegt, enthalten die Abfrageergebnisse keine Spaltenheader. Der *query_no_truncate* Wert ist vom Typ " **Bit**". Bei einem Wert von 0 oder wenn kein Wert angegeben ist, werden die Spalten in der Abfrage auf 256 Zeichen abgeschnitten. Bei einem Wert von 1 werden die Spalten in der Abfrage nicht abgeschnitten. Dieser Parameter hat den Standardwert 0.  
  
> [!NOTE]  
>  Bei Verwendung mit großen Datenmengen beansprucht die \@ **query_no_truncate** Option zusätzliche Ressourcen und kann die Serverleistung verlangsamen.  
  
`[ @query_result_no_padding ] @query_result_no_padding` Der Typ ist "Bit". Die Standardeinstellung ist 0. Wenn Sie auf 1 festlegen, werden die Abfrageergebnisse nicht aufgefüllt, und möglicherweise wird die Dateigröße reduziert. Wenn Sie \@ query_result_no_padding auf 1 festlegen und den query_result_width- \@ Parameter festlegen, \@ überschreibt der query_result_no_padding-Parameter den \@ query_result_width-Parameter.  
  
 In diesem Fall tritt kein Fehler auf.  
 
  >[!NOTE]
  > Der folgende Fehler kann auftreten, wenn \@ query_result_no_padding auf 1 festgelegt und ein Parameter für query_no_truncate bereitgestellt wird \@ :
  > <br> Meldung 22050, Ebene 16, Status 1, Zeile 0: die Abfrage konnte nicht ausgeführt werden, da \@ sich die Optionen query_result_no_append und \@ query_no_truncate gegenseitig ausschließen. 
  
 Wenn Sie die \@ query_result_no_padding auf 1 festgelegt haben und den \@ query_no_truncate-Parameter festlegen, wird ein Fehler ausgelöst.  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]` Optionaler OUTPUT-Parameter gibt den *mailitem_id* der Nachricht zurück. Der *mailitem_id* ist vom Typ " **int**".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Ein Rückgabecode von 0 steht für Erfolg. Ein beliebiger anderer Wert steht für Fehler. Der Fehlercode für die fehlgeschlagene Anweisung wird in der \@ \@ Fehler Variablen gespeichert.  
  
## <a name="result-sets"></a>Resultsets  
 Bei Erfolg wird die Nachricht "E-Mail in der Warteschlange" zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Vor der Verwendung müssen Datenbank-E-Mail mithilfe des Datenbank-E-Mail Konfigurations-Assistenten oder **sp_configure**aktiviert werden.  
  
 **sysmail_stop_sp** beendet Datenbank-E-Mail, indem die vom externen Programm verwendeten Service Broker Objekte beendet werden. **sp_send_dbmail** akzeptiert weiterhin e-Mails, wenn Datenbank-E-Mail mit **sysmail_stop_sp**beendet wird. Starten Sie Datenbank-E-Mail mithilfe von **sysmail_start_sp**.  
  
 Wenn ** \@ profile** nicht angegeben wird, wird **sp_send_dbmail** ein Standardprofil verwendet. Falls der Benutzer, der die E-Mail-Nachricht sendet, über ein privates Standardprofil verfügt, verwendet Datenbank-E-Mail dieses Profil. Wenn der Benutzer nicht über ein privates Standardprofil verfügt, wird **sp_send_dbmail** das öffentliche Standardprofil verwendet. Wenn kein privates Standardprofil für den Benutzer und kein öffentliches Standardprofil vorhanden ist, gibt **sp_send_dbmail** einen Fehler zurück.  
  
 der **sp_send_dbmail** unterstützt keine e-Mail-Nachrichten ohne Inhalt. Um eine e-Mail-Nachricht zu senden, müssen Sie mindestens einen ** \@ Textkörper**, eine ** \@ Abfrage**, eine ** \@ file_attachments**oder einen ** \@ Betreff**angeben. Andernfalls gibt **sp_send_dbmail** einen Fehler zurück.  
  
 Datenbank-E-Mail verwendet den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Sicherheitskontext des aktuellen Benutzers, um den Dateizugriff zu steuern. Daher können Benutzer, die per Authentifizierung authentifiziert werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dateien nicht mithilfe von ** \@ file_attachments**anfügen. Windows lässt nicht zu, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldeinformationen von einem Remotecomputer für einen anderen Remotecomputer bereitstellt. Aus diesem Grund kann Datenbank-E-Mail möglicherweise Dateien aus einer Netzwerkfreigabe nicht anfügen, wenn der Befehl von einem anderen Computer als dem Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 Wenn sowohl ** \@ Abfrage** als auch ** \@ file_attachments** angegeben sind und die Datei nicht gefunden werden kann, wird die Abfrage weiterhin ausgeführt, aber die e-Mail wird nicht gesendet.  
  
 Wird eine Abfrage angegeben, wird das Resultset als Inlinetext formatiert. Binärdaten im Ergebnis werden im hexadezimalen Format gesendet.  
  
 Die Parameter ** \@ Empfänger**, ** \@ copy_recipients**und ** \@ blind_copy_recipients** sind durch Semikolons getrennte Listen von e-Mail-Adressen. Mindestens einer dieser Parameter muss angegeben werden, oder **sp_send_dbmail** gibt einen Fehler zurück.  
  
 Wenn Sie **sp_send_dbmail** ohne einen Transaktionskontext ausführen, startet Datenbank-E-Mail eine implizite Transaktion und führt einen Commit aus. Wenn **sp_send_dbmail** aus einer vorhandenen Transaktion heraus ausgeführt wird, wird der Benutzer von Datenbank-E-Mail für Änderungen oder Rollbacks der Änderungen angewiesen. Es wird keine innere Transaktion gestartet.  
  
## <a name="permissions"></a>Berechtigungen  
 Ausführungs Berechtigungen für **sp_send_dbmail** standardmäßig allen Mitgliedern der **DatabaseMailUser** -Daten Bank Rolle in der **msdb** -Datenbank hinzu. Wenn der Benutzer, der die Nachricht sendet, jedoch nicht über die Berechtigung verfügt, das Profil für die Anforderung zu verwenden, gibt **sp_send_dbmail** einen Fehler zurück und sendet die Nachricht nicht.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-sending-an-e-mail-message"></a>A. Senden einer E-Mail-Nachricht  
 In diesem Beispiel wird mithilfe der e-Mail-Adresse eine e-Mail an Ihren Freund gesendet `myfriend@Adventure-Works.com` . Die Nachricht hat den Betreff `Automated Success Message`. Der Nachrichtentext enthält den Satz `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. Senden einer E-Mail-Nachricht mit den Ergebnissen einer Abfrage  
 In diesem Beispiel wird mithilfe der e-Mail-Adresse eine e-Mail an Ihren Freund gesendet `yourfriend@Adventure-Works.com` . Die Nachricht hat den Betreff `Work Order Count` und führt eine Abfrage aus, die die Anzahl von Arbeitsaufträgen mit einem `DueDate`-Wert kleiner als zwei Tage nach dem 30. April 2004 anzeigt. Das Ergebnis wird als Textdatei von Datenbank-E-Mail angefügt.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>C. Senden einer E-Mail-Nachricht im HTML-Format  
 In diesem Beispiel wird mithilfe der e-Mail-Adresse eine e-Mail an Ihren Freund gesendet `yourfriend@Adventure-Works.com` . Die Nachricht hat den Betreff `Work Order List` und enthält ein HTML-Dokument, das die Anzahl von Arbeitsaufträgen mit einem `DueDate`-Wert kleiner als zwei Tage nach dem 30. April 2004 anzeigt. Das Ergebnis wird im HTML-Format von Datenbank-E-Mail gesendet.  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
