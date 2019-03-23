---
title: Transformations-Editor (Verbindungsseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f5c2971b1d4da669cadc57f0a557b32bf2b1adde
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389818"
---
# <a name="lookup-transformation-editor-connection-page"></a>Transformations-Editor für Suche (Seite 'Verbindung')
  Auf der Seite **Verbindung** des Dialogfelds **Transformations-Editor für Suche** können Sie einen Verbindungs-Manager auswählen. Wenn Sie einen OLE DB-Verbindungs-Manager auswählen, wählen Sie auch eine Abfrage, Tabelle oder Sicht zum Generieren des Verweisdatasets aus.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Optionen  
 Die folgenden Optionen sind verfügbar, wenn Sie im Dialogfeld **Transformations-Editor für Suche** auf der Seite **Allgemein** die Optionen **Vollcache** und Cacheverbindungs-Manager auswählen.  
  
 **Allgemein**  
 Wählen Sie einen vorhandenen Cacheverbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Editor für den Cacheverbindungs-Manager** eine neue Verbindung.  
  
 Die folgenden Optionen sind verfügbar, wenn Sie im Dialogfeld **Transformations-Editor für Suche**auf der Seite **Allgemein**die Optionen **Vollcache**, **Teilcache**oder **Kein Cache** und OLE DB-Verbindungs-Manager auswählen.  
  
 **Teilcache**  
 Wählen Sie einen vorhandenen OLE DB-Verbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** eine neue Verbindung.  
  
 **Tabelle oder Sicht verwenden**  
 Wählen Sie eine vorhandene Tabelle oder Sicht aus der Liste aus, oder erstellen Sie eine neue Tabelle, indem Sie auf **Neu**klicken.  
  
> [!NOTE]  
>  Wenn Sie auf der Seite **Erweitert** im **Transformations-Editor für Suche** eine SQL-Anweisung angeben, wird durch diese SQL-Anweisung der hier ausgewählte Tabellenname überschrieben und ersetzt. Weitere Informationen finden Sie unter [Transformations-Editor für Suche &#40;Seite „Erweitert“&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle.  
  
 **Ergebnisse einer SQL-Abfrage verwenden**  
 Wählen Sie diese Option aus, um nach einer vorhandenen Abfrage zu suchen, eine neue Abfrage zu erstellen, die Abfragesyntax zu überprüfen und eine Vorschau der Abfrageergebnisse anzuzeigen.  
  
 **Abfrage erstellen**  
 Erstellen Sie eine auszuführende Transact-SQL-Anweisung mit dem **Abfrage-Generator**, einem grafischen Tool, das verwendet wird, um Abfragen mithilfe des Durchsuchens von Daten zu erstellen.  
  
 **Durchsuchen**  
 Verwenden Sie diese Option, um nach einer vorhandenen Abfrage zu suchen, die als Datei gespeichert ist.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax der Abfrage.  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Vorschau der Abfrageergebnisse anzeigen** eine Vorschau der Ergebnisse an. Diese Option zeigt bis zu 200 Zeilen an.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogeintrag [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) (Suchcachemodi) auf blogs.msdn.com  
  
## <a name="see-also"></a>Siehe auch  
 [Transformations-Editor für Suche &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Transformations-Editor für Suche &#40;Seite „Spalten“&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Erweitert“&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Transformation für Fuzzysuche](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
