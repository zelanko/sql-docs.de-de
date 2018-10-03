---
title: SQL-Ziel-Editor (Seite erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a251b8599ba194a151790c2a781e49c643b00048
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089030"
---
# <a name="sql-destination-editor-advanced-page"></a>Ziel-Editor für SQL (Seite Erweitert)
  Auf der Seite **Erweitert** des Dialogfelds **Ziel-Editor für SQL** können Sie Optionen für die erweiterte Masseneinfügung angeben.  
  
 Weitere Informationen zum SQL Server-Ziel finden Sie unter [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Tastatur  
 **Identität beibehalten**  
 Gibt an, ob der Task Werte in Identitätsspalten einfügen soll. Der Standardwert dieser Eigenschaft ist `False`.  
  
 **NULL-Werte beibehalten**  
 Gibt an, ob der Task NULL-Werte beibehalten soll. Der Standardwert dieser Eigenschaft ist `False`.  
  
 **Tabellensperre**  
 Gibt an, ob die Tabelle beim Laden der Daten gesperrt wird. Der Standardwert dieser Eigenschaft ist `True`.  
  
 **Check-Einschränkungen**  
 Gibt an, ob Einschränkungen vom Task überprüft werden sollen. Der Standardwert dieser Eigenschaft ist `True`.  
  
 **Trigger auslösen**  
 Gibt an, ob die Masseneinfügung Trigger in Tabellen auslösen soll. Der Standardwert dieser Eigenschaft ist `False`.  
  
 **Erste Zeile**  
 Gibt die erste einzufügende Zeile an. Der Standardwert dieser Eigenschaft ist **-1**. Er zeigt an, dass kein Wert zugewiesen wurde.  
  
> [!NOTE]  
>  Löschen Sie den Inhalt des Textfelds im Dialogfeld **Ziel-Editor für SQL** , um anzugeben, dass Sie keinen Wert für diese Eigenschaft zuweisen möchten. Verwenden Sie im Fenster **Eigenschaften** , im Dialogfeld **Erweiterter Editor**und im Objektmodell den Wert -1.  
  
 **Letzte Zeile**  
 Gibt die letzte einzufügende Zeile an. Der Standardwert dieser Eigenschaft ist **-1**. Er zeigt an, dass kein Wert zugewiesen wurde.  
  
> [!NOTE]  
>  Löschen Sie den Inhalt des Textfelds im Dialogfeld **Ziel-Editor für SQL** , um anzugeben, dass Sie keinen Wert für diese Eigenschaft zuweisen möchten. Verwenden Sie im Fenster **Eigenschaften** , im Dialogfeld **Erweiterter Editor**und im Objektmodell den Wert -1.  
  
 **Maximale Anzahl von Fehlern**  
 Gibt die Anzahl der Fehler an, die auftreten können, bevor die Masseneinfügung abgebrochen wird. Der Standardwert dieser Eigenschaft ist **–1**. Er zeigt an, dass kein Wert zugewiesen wurde.  
  
> [!NOTE]  
>  Löschen Sie den Inhalt des Textfelds im Dialogfeld **Ziel-Editor für SQL** , um anzugeben, dass Sie keinen Wert für diese Eigenschaft zuweisen möchten. Verwenden Sie im Fenster **Eigenschaften** , im Dialogfeld **Erweiterter Editor**und im Objektmodell den Wert -1.  
  
 **Timeout**  
 Gibt die Anzahl der Sekunden an, die abgewartet werden, bevor die Masseneinfügung aufgrund eines Timeouts abgebrochen wird.  
  
 **Spalten sortieren**  
 Geben Sie die Namen der zu sortierenden Spalten an. Jede Spalte kann in auf- oder absteigender Reihenfolge sortiert werden. Wenn Sie mehrere Spalten verwenden, nach denen sortiert werden soll, trennen Sie die Namen in der Liste mit Kommas.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für SQL &#40;Seite Verbindungs-Manager&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md)   
 [Ziel-Editor für SQL &#40;Seite "Zuordnungen"&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Massenladen von Daten mithilfe des SQL Server-Ziels](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
