---
title: Ziel-Editor für OLE DB (Seite "Verbindungs-Manager") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 21ec7d4d38996ecf4cb5522fcfdf29fb6e80db89
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424167"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a>Ziel-Editor für OLE DB (Seite Verbindungs-Manager)
  Mithilfe der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für OLE DB** können Sie die OLE DB-Verbindung für das Ziel auswählen. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
> [!NOTE]  
>  Die- `CommandTimeout` Eigenschaft des OLE DB Ziels ist nicht im Ziel- **Editor für OLE DB**verfügbar, kann jedoch mit dem **Erweiterter Editor**festgelegt werden. Außerdem sind bestimmte Optionen für schnelles Laden nur in der **Erweiterter Editor**verfügbar. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt OLE DB-Ziel von [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).  
  
 Weitere Informationen zum OLE DB-Ziel finden Sie unter [OLE DB Destination](data-flow/ole-db-destination.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **OLE DB Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** einen neuen Verbindungs-Manager.  
  
 **Datenzugriffs Modus**  
 Gibt das Verfahren für das Laden von Daten in das Ziel an. Für das Laden von Doppelbyte-Zeichensatzdaten (Double-Byte Character Set oder DBCS) ist die Verwendung einer der Optionen für schnelles Laden erforderlich. Weitere Informationen zu Datenzugriffsmodi für schnelles Laden, die für Masseneinfügungen optimiert sind, finden Sie unter [OLE DB Destination](data-flow/ole-db-destination.md).  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|Tabelle oder Sicht|Lädt Daten in eine Tabelle oder Sicht im OLE DB-Ziel.|  
|Tabelle oder Sicht - schnelles Laden|Lädt Daten in eine Tabelle oder Sicht im OLE DB-Ziel und verwendet die Option für das schnelle Laden. Weitere Informationen zu Datenzugriffsmodi für schnelles Laden, die für Masseneinfügungen optimiert sind, finden Sie unter [OLE DB Destination](data-flow/ole-db-destination.md).|  
|Variable für Tabellenname oder Sichtname|Gibt den Namen der Tabelle oder Sicht in einer Variablen an.<br /><br /> **Verwandte Informationen:**[Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)|  
|Variable für Tabellenname oder Sichtname - schnelles Laden|Gibt den Namen der Tabelle oder Sicht in einer Variablen an und verwendet zum Laden der Daten die Option für das schnelle Laden. Weitere Informationen zu Datenzugriffsmodi für schnelles Laden, die für Masseneinfügungen optimiert sind, finden Sie unter [OLE DB Destination](data-flow/ole-db-destination.md).|  
|SQL-Befehl|Lädt Daten mithilfe einer SQL-Abfrage in das OLE DB-Ziel.|  
  
 **Vorschau**  
 Zeigen Sie mithilfe des Dialogfelds **Vorschau der Abfrageergebnisse anzeigen** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
 Für jede der Einstellungen für **Datenzugriffsmodus** werden spezifische dynamische Optionen angezeigt. In den folgenden Abschnitten werden alle dynamischen Optionen, die für die einzelnen Einstellungen für **Datenzugriffsmodus** verfügbar sind, beschrieben.  
  
### <a name="data-access-mode--table-or-view"></a>Datenzugriffsmodus = Tabelle oder Sicht  
 **Name der Tabelle oder Sicht**  
 Wählen Sie den Namen der Tabelle oder Sicht aus einer Liste der verfügbaren Namen in der Datenquelle aus.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle.  
  
> [!NOTE]  
>  Wenn Sie auf **neu**klicken, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generiert eine standardmäßige CREATE TABLE-Anweisung, die auf der verbundenen Datenquelle basiert. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
### <a name="data-access-mode--table-or-view---fast-load"></a>Datenzugriffsmodus = Tabelle oder Ansicht – schnelles Laden  
 **Name der Tabelle oder Sicht**  
 Wählen Sie mithilfe dieser Liste eine Tabelle oder Sicht in der Datenbank aus, oder erstellen Sie eine neue Tabelle, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle.  
  
> [!NOTE]  
>  Wenn Sie auf **neu**klicken, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generiert eine standardmäßige CREATE TABLE-Anweisung, die auf der verbundenen Datenquelle basiert. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Identität beibehalten**  
 Gibt an, ob beim Laden von Daten Identitätswerte kopiert werden sollen. Diese Eigenschaft ist nur für die Option für das schnelle Laden verfügbar. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **NULL-Werte beibehalten**  
 Gibt an, ob beim Laden von Daten NULL-Werte kopiert werden sollen. Diese Eigenschaft ist nur für die Option für das schnelle Laden verfügbar. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **Tabellensperre**  
 Gibt an, ob die Tabelle während des Ladens gesperrt ist. Der Standardwert dieser Eigenschaft ist `true`.  
  
 **Check-Einschränkungen**  
 Gibt an, ob das Ziel beim Laden von Daten Einschränkungen überprüft. Der Standardwert dieser Eigenschaft ist `true`.  
  
 **Zeilen pro Batch**  
 Geben Sie die Anzahl der Zeilen in einem Batch an. Der Standardwert dieser Eigenschaft ist **-1**und gibt an, dass kein Wert zugewiesen wurde.  
  
> [!NOTE]  
>   Löschen Sie im Dialogfeld **Ziel-Editor für OLE DB** den Inhalt des Textfelds, um anzugeben, dass für diese Eigenschaft kein benutzerdefinierter Wert zugewiesen werden soll.  
  
 **Maximale Einfügungscommitgröße**  
 Gibt die Batchgröße an, für die das OLE DB-Ziel bei schnellen Ladevorgängen die Durchführung eines Commits versucht. Der Wert **0** gibt an, dass nach dem Verarbeiten aller Zeilen für alle Daten in einem einzelnen Batch ein Commit ausgeführt wird.  
  
> [!NOTE]  
>  Der Wert **0** bewirkt möglicherweise, dass das Paket bei der Ausführung nicht mehr reagiert, wenn das OLE DB-Ziel und andere Datenflusskomponenten dieselbe Quelltabelle aktualisieren. Um zu verhindern, dass die Paketausführung beendet wird, legen Sie die Option **Maximale Einfügungscommitgröße** auf **2147483647**fest.  
  
 Wenn Sie für diese Eigenschaft einen Wert bereitstellen, führt das Ziel für Zeilen in Batches, die kleiner sind als (a) die **Maximale Einfügungscommitgröße**oder (b) die verbleibenden Zeilen im Puffer, der gerade verarbeitet wird, einen Commit durch.  
  
> [!NOTE]  
>   Einschränkungsfehler am Ziel bewirken, dass der gesamte Batch mit Zeilen, die durch **Maximale Einfügungscommitgröße** definiert sind, fehlschlägt.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Datenzugriffsmodus = Variable für Tabellenname oder Sichtname  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Namen der Tabelle oder Sicht enthält.  
  
### <a name="data-access-mode--table-name-or-view-name-variable---fast-load"></a>Datenzugriffsmodus = Variable für Tabellenname oder Ansichtsname – schnelles Laden  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Namen der Tabelle oder Sicht enthält.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Tabelle erstellen** eine neue Tabelle.  
  
> [!NOTE]  
>  Wenn Sie auf **neu**klicken, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generiert eine standardmäßige CREATE TABLE-Anweisung, die auf der verbundenen Datenquelle basiert. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Identität beibehalten**  
 Gibt an, ob beim Laden von Daten Identitätswerte kopiert werden sollen. Diese Eigenschaft ist nur für die Option für das schnelle Laden verfügbar. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **NULL-Werte beibehalten**  
 Gibt an, ob beim Laden von Daten NULL-Werte kopiert werden sollen. Diese Eigenschaft ist nur für die Option für das schnelle Laden verfügbar. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **Tabellensperre**  
 Gibt an, ob die Tabelle während des Ladens gesperrt ist. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **Check-Einschränkungen**  
 Gibt an, ob Einschränkungen vom Task überprüft werden sollen. Der Standardwert dieser Eigenschaft ist `false`.  
  
 **Zeilen pro Batch**  
 Geben Sie die Anzahl der Zeilen in einem Batch an. Der Standardwert dieser Eigenschaft ist **-1**und gibt an, dass kein Wert zugewiesen wurde.  
  
> [!NOTE]  
>   Löschen Sie im Dialogfeld **Ziel-Editor für OLE DB** den Inhalt des Textfelds, um anzugeben, dass für diese Eigenschaft kein benutzerdefinierter Wert zugewiesen werden soll.  
  
 **Maximale Einfügungscommitgröße**  
 Gibt die Batchgröße an, für die das OLE DB-Ziel bei schnellen Ladevorgängen die Durchführung eines Commits versucht. Der Standardwert **2147483647** zeigt an, dass nach dem Verarbeiten aller Zeilen für alle Daten in einem einzelnen Batch ein Commit durchgeführt wird.  
  
> [!NOTE]  
>  Der Wert **0** bewirkt möglicherweise, dass das Paket bei der Ausführung nicht mehr reagiert, wenn das OLE DB-Ziel und andere Datenflusskomponenten dieselbe Quelltabelle aktualisieren. Um zu verhindern, dass die Paketausführung beendet wird, legen Sie die Option **Maximale Einfügungscommitgröße** auf **2147483647**fest.  
  
### <a name="data-access-mode--sql-command"></a>Datenzugriffsmodus = SQL-Befehl  
 **SQL-Befehlstext**  
 Geben Sie den Text einer SQL-Abfrage ein, und erstellen Sie die Abfrage, indem Sie auf **Abfrage erstellen**klicken, oder suchen Sie nach der Datei, die den Abfragetext enthält, indem Sie auf **Durchsuchen**klicken.  
  
> [!NOTE]  
>  Vom OLE DB-Ziel werden keine Parameter unterstützt. Wenn Sie eine parametrisierte INSERT-Anweisung ausführen müssen, ziehen Sie die Transformation für den OLE DB-Befehl in Betracht. Weitere Informationen finden Sie unter [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).  
  
 **Abfrage erstellen**  
 Mithilfe des Dialogfelds **Abfrage-Generator** können Sie die SQL-Abfrage visuell erstellen.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie nach der Datei suchen, die den Text der SQL-Abfrage enthält.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax des Abfragetexts.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [OLE DB Ziel-Editor &#40;Seite Zuordnungen&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md)   
 [OLE DB Ziel-Editor &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md)   
 [Laden von Daten mithilfe des OLE DB-Ziels](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
