---
title: ADO NET-Quellen-Editor (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f3d9d2270603c3f38189478ccaaf48510085907f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061691"
---
# <a name="ado-net-source-editor-connection-manager-page"></a>ADO.NET-Quellen-Editor (Seite 'Verbindungs-Manager')
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **ADO.NET-Quellen-Editor** wählen Sie den [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Verbindungs-Manager für die Quelle aus. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
 Weitere Informationen zur ADO NET-Quelle finden Sie unter [ADO NET Source](data-flow/ado-net-source.md).  
  
 **So öffnen Sie die Seite "Verbindungs-Manager"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket, das ADO.NET als Quelle hat.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die ADO.NET-Quelle.  
  
3.  Klicken Sie im **ADO.NET-Quellen-Editor**auf **Verbindungs-Manager**.  
  
## <a name="static-options"></a>Statische Optionen  
 **ADO.NET-Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **ADO.NET-Verbindungs-Manager konfigurieren** einen neuen Verbindungs-Manager.  
  
 **Datenzugriffsmodus**  
 Geben Sie die Methode für die Auswahl von Daten aus der Quelle an.  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|Tabelle oder Sicht|Rufen Sie Daten aus einer Tabelle oder Sicht in der [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Datenquelle ab.|  
|SQL-Befehl|Rufen Sie mit SQL-Abfrage Daten aus der [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Datenquelle ab.|  
  
 **Vorschau**  
 Zeigt mithilfe des Dialogfelds **Datenansicht** eine Vorschau der Ergebnisse an. In der **Vorschau** können bis zu 200 Zeilen angezeigt werden.  
  
> [!NOTE]  
>  In der Datenvorschau enthalten Spalten mit einem CLR-benutzerdefinierten Typ keine Daten. Stattdessen werden die Werte \<Wert zu groß zum Anzeigen> oder „System.Byte[]“ angezeigt. Der erste Wert wird angezeigt, wenn mithilfe des [!INCLUDE[vstecado](../includes/vstecado-md.md)] -Anbieters auf die Datenquelle zugegriffen wird. Der zweite Wert wird bei Verwendung des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client-Anbieters angezeigt.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
  
### <a name="data-access-mode--table-or-view"></a>Datenzugriffsmodus = Tabelle oder Sicht  
 **Name der Tabelle oder Sicht**  
 Wählen Sie den Namen der Tabelle oder Sicht aus einer Liste der verfügbaren Namen in der Datenquelle aus.  
  
### <a name="data-access-mode--sql-command"></a>Datenzugriffsmodus = SQL-Befehl  
 **SQL-Befehls Text**  
 Geben Sie den Text einer SQL-Abfrage ein, und erstellen Sie die Abfrage, indem Sie auf **Abfrage erstellen**klicken, oder suchen Sie nach der Datei, die den Abfragetext enthält, indem Sie auf **Durchsuchen**klicken.  
  
 **Abfrage erstellen**  
 Mithilfe des Dialogfelds **Abfrage-Generator** können Sie die SQL-Abfrage visuell erstellen.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie nach der Datei suchen, die den Text der SQL-Abfrage enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO.net-Quellen-Editor &#40;Seite "Spalten"&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [ADO NET-Quellen-Editor &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md)   
 [ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md)  
  
  
