---
title: Quellen-Editor für OLE DB (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 22b7c9ea4012655043cac7eb7f3d432ef1e2e854
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057045"
---
# <a name="ole-db-source-editor-connection-manager-page"></a>Quellen-Editor für OLE DB (Seite Verbindungs-Manager)
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für OLE DB** wählen Sie den OLE DB-Verbindungs-Manager für die Quelle aus. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
> [!NOTE]  
>  Verwenden Sie zum Laden von Daten aus einer Datenquelle, für die [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007 verwendet wird, eine OLE DB-Quelle. Sie können eine Excel-Quelle nicht zum Laden von Daten aus einer Excel 2007-Datenquelle verwenden. Weitere Informationen finden Sie unter [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md).  
>   
>  Verwenden Sie zum Laden von Daten aus einer Datenquelle, für die [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 oder eine frühere Version verwendet wird, eine Excel-Quelle. Weitere Informationen finden Sie unter [Quellen-Editor für Excel &#40;Seite „Verbindungs-Manager“&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).  
  
> [!NOTE]  
>  Die `CommandTimeout` -Eigenschaft der OLE DB Quelle ist nicht im Quellen- **Editor für OLE DB**verfügbar, kann jedoch mit dem **Erweiterter Editor**festgelegt werden. Weitere Informationen zu dieser Eigenschaft finden Sie im Abschnitt Excel-Quelle von [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).  
  
 Weitere Informationen zur OLE DB-Quelle finden Sie unter [OLE DB Source](data-flow/ole-db-source.md).  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a>Öffnen des Quellen-Editors für OLE DB (Seite "Verbindungs-Manager")  
  
1.  Fügen Sie die OLE DB-Quelle dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Paket in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzu.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Quellkomponente, und klicken Sie dann auf **Bearbeiten**.  
  
3.  Klicken Sie auf **Verbindungs-Manager**.  
  
## <a name="static-options"></a>Statische Optionen  
 **OLE DB Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** einen neuen Verbindungs-Manager.  
  
 **Datenzugriffs Modus**  
 Geben Sie die Methode für die Auswahl von Daten aus der Quelle an.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|Tabelle oder Sicht|Rufen Sie Daten aus einer Tabelle oder Sicht in der OLE DB-Datenquelle ab.|  
|Variable für Tabellenname oder Sichtname|Gibt den Namen der Tabelle oder Sicht in einer Variablen an.<br /><br /> **Verwandte Informationen:** [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)|  
|SQL-Befehl|Rufen Sie mit SQL-Abfrage Daten aus der OLE DB-Datenquelle ab.|  
|SQL-Befehl aus Variable|Gibt den SQL-Abfragetext in einer Variablen an.|  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Datenansicht** eine Vorschau der Ergebnisse an. In der**Vorschau** können bis zu 200 Zeilen angezeigt werden.  
  
> [!NOTE]  
>  In der Datenvorschau enthalten Spalten mit einem CLR-benutzerdefinierten Typ keine Daten. Stattdessen werden die Werte \<Wert zu groß zum Anzeigen> oder „System.Byte[]“ angezeigt. Der erste Wert wird angezeigt, wenn mithilfe des SQL-OLE DB-Anbieters auf die Datenquelle zugegriffen wird. Der zweite Wert wird bei Verwendung des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client-Anbieters angezeigt.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
  
### <a name="data-access-mode--table-or-view"></a>Datenzugriffsmodus = Tabelle oder Sicht  
 **Name der Tabelle oder Sicht**  
 Wählen Sie den Namen der Tabelle oder Sicht aus einer Liste der verfügbaren Namen in der Datenquelle aus.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Datenzugriffsmodus = Variable für Tabellenname oder Sichtname  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Namen der Tabelle oder Sicht enthält.  
  
### <a name="data-access-mode--sql-command"></a>Datenzugriffsmodus = SQL-Befehl  
 **SQL-Befehlstext**  
 Geben Sie den Text einer SQL-Abfrage ein, und erstellen Sie die Abfrage, indem Sie auf **Abfrage erstellen**klicken, oder suchen Sie nach der Datei, die den Abfragetext enthält, indem Sie auf **Durchsuchen**klicken.  
  
 **Parameters**  
 Wenn Sie eine parametrisierte Abfrage eingeben und im Abfragetext ? als Parameterplatzhalter verwenden, können Sie den Paketvariablen mithilfe des Dialogfelds **Abfrageparameter festlegen** Abfrageeingabeparameter zuordnen.  
  
 **Abfrage erstellen**  
 Mithilfe des Dialogfelds **Abfrage-Generator** können Sie die SQL-Abfrage visuell erstellen.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie nach der Datei suchen, die den Text der SQL-Abfrage enthält.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax des Abfragetexts.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Datenzugriffsmodus = SQL-Befehl aus Variable  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Text für die SQL-Abfrage enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [OLE DB &#40;Seite "Spalten" des Quellen-Editors&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md)   
 [OLE DB Quellen-Editor &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md)   
 [Extrahieren von Daten mithilfe der OLE DB Quelle](data-flow/extract-data-by-using-the-ole-db-source.md)   
 [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md)  
  
  
