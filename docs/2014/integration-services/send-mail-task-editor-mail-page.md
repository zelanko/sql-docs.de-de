---
title: Editor für den Task ' Mail senden ' (Seite e-Mail) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d80ca8e475bf9c2b56c11118a44e5282573f280d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055832"
---
# <a name="send-mail-task-editor-mail-page"></a>Editor für den Task 'Mail senden' (Seite E-Mail)
  Auf der Seite **E-Mail** im Dialogfeld **Editor für den Task „Mail senden“** können Sie die Empfänger, den Nachrichtentyp und die Priorität einer Nachricht angeben. Sie können der Nachricht auch Dateien anfügen. Bei dem Nachrichtentext kann es sich um eine bereitgestellte Zeichenfolge, eine Dateiverbindung mit einer Datei mit Text oder den Namen einer Variablen mit Text handeln.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Tastatur  
 **SMTPConnection**  
 Wählen Sie einen SMTP-Verbindungs-Manager aus der Liste aus, oder klicken Sie ** \<auf neue Verbindung... #b0** , um einen neuen Verbindungs-Manager zu erstellen.  
  
> [!IMPORTANT]  
>  Der SMTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Windows-Authentifizierung. Er unterstützt keine Standardauthentifizierung.  
  
 **Verwandte Themen:** [SMTP-Verbindungs-Manager](connection-manager/smtp-connection-manager.md)  
  
 **Von**  
 Geben Sie die E-Mail-Adresse des Absenders an.  
  
 **An**  
 Stellen Sie die E-Mail-Adresse der Empfänger bereit. Verwenden Sie als Trennzeichen ein Semikolon.  
  
 **125**  
 Geben Sie die E-Mail-Adressen der Personen an, die Kopien der Nachricht erhalten sollen. Verwenden Sie als Trennzeichen ein Semikolon.  
  
 **BCC**  
 Geben Sie die E-Mail-Adressen der Personen an, die Blindkopien der Nachricht erhalten sollen. Verwenden Sie als Trennzeichen ein Semikolon.  
  
 **Betreff**  
 Geben Sie einen Betreff für die E-Mail-Nachricht an.  
  
 **MessageSourceType**  
 Wählen Sie den Quelltyp der Nachricht aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Direkte Eingabe**|Legen Sie für die Quelle den Nachrichtentext fest. Bei Auswahl dieses Wertes wird die dynamische Option **MessageSource**angezeigt.|  
|**Dateiverbindung**|Legen Sie für die Quelle die Datei fest, die den Nachrichtentext enthält. Bei Auswahl dieses Wertes wird die dynamische Option **MessageSource**angezeigt.|  
|**Variable**|Legen Sie für die Quelle eine Variable fest, die den Nachrichtentext enthält. Bei Auswahl dieses Wertes wird die dynamische Option **MessageSource**angezeigt.|  
  
 **Haben**  
 Legen Sie die Priorität der Nachricht fest.  
  
 **Attachments**  
 Geben Sie die Dateinamen der Anlagen für die E-Mail-Nachricht an. Verwenden Sie als Trennzeichen das Pipe-Zeichen (|).  
  
> [!NOTE]  
>  Die Zeilen An, Cc und Bcc sind in Übereinstimmung mit Internetstandards auf 256 Zeichen begrenzt.  
  
## <a name="messagesourcetype-dynamic-options"></a>MessageSourceType (dynamische Optionen)  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Direct Input  
 **MessageSource**  
 Geben Sie den Nachrichtentext ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (…), und geben Sie die Nachricht in das Dialogfeld **Nachrichtenquelle** ein.  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = File connection  
 **MessageSource**  
 Wählen Sie in der Liste einen Dateiverbindungs-Manager aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Variable  
 **MessageSource**  
 Wählen Sie eine Variable aus der Liste aus \<, oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' Mail senden ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
