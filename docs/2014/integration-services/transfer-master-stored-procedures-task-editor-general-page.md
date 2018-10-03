---
title: Task Editor (Seite "Allgemein"), Master gespeicherte Prozeduren übertragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 089b12c07b57b24d4c462605af92ed1bf7f0d417
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168770"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a>Editor für den Task 'In 'master' gespeicherte Prozeduren übertragen' (Seite Allgemein)
  Auf der Seite **Allgemein** des Dialogfelds **Editor für den Task "In 'master' gespeicherte Prozeduren übertragen"** können Sie einen Namen und eine Beschreibung für den Task angeben. Weitere Informationen zu diesem Task finden Sie unter [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Dieser Task überträgt lediglich die benutzerdefinierten gespeicherten Prozeduren des **dbo** -Besitzers aus einer **master** -Datenbank auf dem Quellserver in eine **master** -Datenbank auf dem Zielserver. Benutzer müssen die CREATE PROCEDURE-Berechtigung für die **master** -Datenbank des Zielservers besitzen oder Mitglieder der festen Serverrolle **sysadmin** auf dem Zielserver sein, um dort gespeicherte Prozeduren erstellen zu können.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie für den Task 'In 'master' gespeicherte Prozeduren übertragen einen eindeutigen Namen ein. Dieser Name wird im Tasksymbol als Bezeichnung verwendet.  
  
> [!NOTE]  
>  Tasknamen müssen innerhalb eines Pakets eindeutig sein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für den Task 'In 'master' gespeicherte Prozeduren übertragen ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task „In master gespeicherte Prozeduren übertragen“ &#40;Seite „Gespeicherte Prozeduren“&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
