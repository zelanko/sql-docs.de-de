---
title: Datenprofilerstellungs-Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.f1
helpviewer_keywords:
- Data Profiling task [Integration Services], about Data Profiling task
- data profiling
- profiling data
ms.assetid: 248ce233-4342-42c5-bf26-f4387ea152cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0a895fd1dc3fe51296a110902fb1dd4c27d3d5a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62831883"
---
# <a name="data-profiling-task"></a>Datenprofilerstellungs-Task
  Der Datenprofilerstellungs-Task berechnet verschiedene Profile, mit deren Hilfe Sie sich mit einer Datenquelle vertraut machen und Probleme bei den Daten identifizieren können, die behoben werden müssen.  
  
 Den Datenprofilerstellungs-Task können Sie innerhalb eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets verwenden, um ein Profil der in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Daten zu erstellen und potenzielle Probleme mit der Datenqualität zu identifizieren.  
  
> [!NOTE]  
>  In diesem Thema werden nur die Funktionen und Anforderungen des Datenprofilerstellungs-Tasks beschrieben. Eine exemplarische Vorgehensweise zur Verwendung des Datenprofilerstellungs-Tasks finden Sie im Abschnitt [Datenprofilerstellungs-Task und -Viewer](data-profiling-task-and-viewer.md).  
  
## <a name="requirements-and-limitations"></a>Anforderungen und Einschränkungen  
 Der Datenprofilerstellungs-Task funktioniert nur mit Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert werden. Dieser Task funktioniert nicht mit Datenquellen von Drittanbietern oder dateibasierten Datenquellen.  
  
 Um das Paket auszuführen, das den Datenprofilerstellungs-Task enthält, müssen Sie zudem ein Konto verwenden, das über Lese-/Schreibberechtigungen sowie CREATE TABLE-Berechtigungen für die tempdb-Datenbank verfügt.  
  
## <a name="data-profiler-viewer"></a>Datenprofil-Viewer  
 Nachdem Sie Datenprofile mit dem Task berechnet und in einer Datei gespeichert haben, können Sie die Profilausgabe mit dem eigenständigen Datenprofil-Viewer überprüfen. Der Datenprofil-Viewer unterstützt außerdem Drilldownfunktionen, mit deren Hilfe Sie Probleme mit der Datenqualität verstehen können, die in der Profilausgabe identifiziert werden. Weitere Informationen finden Sie unter [Datenprofil-Viewer](data-profile-viewer.md).  
  
> [!IMPORTANT]  
>  Die Ausgabedatei enthält möglicherweise sensible Daten über die Datenbank und die Daten in der Datenbank. Vorschläge zur Verbesserung der Sicherheit dieser Datei finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../access-to-files-used-by-packages.md).  
>   
>  Die Drilldownfunktion, die im Datenprofil-Viewer zur Verfügung steht, sendet Live-Abfragen an die ursprüngliche Datenquelle.  
  
## <a name="available-profiles"></a>Verfügbare Profile  
 Der Datenprofilerstellungs-Task kann acht verschiedene Datenprofile berechnen. Fünf Profile analysieren einzelne Spalten und die restlichen drei analysieren mehrere Spalten oder Beziehungen zwischen Spalten und Tabellen.  
  
 Die folgenden fünf Profile analysieren einzelne Spalten.  
  
|Profile, die einzelne Spalten analysieren|Description|  
|----------------------------------------------|-----------------|  
|Verteilungsprofil für Spaltenlänge|Meldet alle eindeutigen Längen der Zeichenfolgenwerte in der ausgewählten Spalte sowie den Prozentsatz der Zeilen in der Tabelle, die jede Länge repräsentiert.<br /><br /> Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. Werte, die nicht gültig sind. Beispiel: Sie erstellen ein Profil einer Spalte mit den Codes der US-amerikanischen Bundesstaaten, die zwei Zeichen lang sein sollen, und entdecken Werte, die länger als zwei Zeichen sind.|  
|Profil für Spalten-NULL-Verhältnis|Meldet den Prozentsatz der NULL-Werte in der ausgewählten Spalte.<br /><br /> Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. ein unerwartet hohes Verhältnis der NULL-Werte in einer Spalte. Beispiel: Sie erstellen ein Profil der Spalte für die Postleitzahl und entdecken einen unerwartet hohen Prozentsatz an fehlenden Codes.|  
|Spaltenmusterprofil|Meldet einen Satz von regulären Ausdrücken, die den angegebenen Prozentsatz der Werte in einer Zeichenfolgenspalte abdecken.<br /><br /> Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. Zeichenfolgen, die nicht gültig sind. Dieses Profil kann außerdem reguläre Ausdrücke vorschlagen, die künftig zur Überprüfung neuer Werte verwendet werden können. Beispiel: Ein Musterprofil einer Spalte für den US-amerikanischen Zip Code kann folgende reguläre Ausdrücke erstellen: \d{5}-\d{4}, \d{5} und \d{9}. Wenn Sie andere reguläre Ausdrücke erhalten, enthalten Ihre Daten wahrscheinlich ungültige oder falsch formatierte Werte.|  
|Spaltenstatistikprofil|Meldet Statistiken, wie minimale, maximale, durchschnittliche und standardmäßige Abweichung für numerische Spalten und den Mindest- und Höchstwert für `datetime`-Spalten.<br /><br /> Dieses Profil hilft Ihnen, Probleme bei den Daten zu identifizieren, z. B. Datumswerte, die nicht gültig sind. Beispiel: Sie erstellen ein Profil einer Spalte mit historischen Daten und entdecken einen Maximalwert, der in der Zukunft liegt.|  
|Verteilungsprofil für Spaltenwerte|Meldet alle eindeutigen Werte in der ausgewählten Spalte sowie den Prozentsatz der Zeilen in der Tabelle, die jeder Wert repräsentiert. Kann auch Werte melden, die mehr als einen angegebenen Prozentsatz der Zeilen in der Tabelle darstellen.<br /><br /> Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. eine falsche Anzahl eindeutiger Werte in einer Spalte. Beispiel: Sie erstellen ein Profil einer Spalte, die die US-amerikanischen Bundesstaaten enthalten soll, und entdecken mehr als 50 eindeutige Werte.|  
  
 Die folgenden drei Profile analysieren einzelne Spalten oder Beziehungen zwischen Spalten und Tabellen.  
  
|Profile, die mehrere Spalten analysieren|Description|  
|--------------------------------------------|-----------------|  
|Kandidatenschlüsselprofil|Meldet, ob eine Spalte oder eine Gruppe von Spalten ein Schlüssel oder ein ungefährer Schlüssel für die ausgewählte Tabelle ist.<br /><br /> Dieses Profil hilft Ihnen auch, Probleme bei den Daten zu identifizieren, z. B. doppelte Werte in einer potenziellen Schlüsselspalte.|  
|Funktionales Abhängigkeitsprofil|Meldet, in welchem Maß die Werte in einer Spalte (die abhängige Spalte) von den Werten in einer Spalte oder einer Gruppe von Spalten (der determinanten Spalte) abhängig sind.<br /><br /> Dieses Profil hilft Ihnen auch, Probleme bei den Daten zu identifizieren, z. B. Werte, die nicht gültig sind. Beispiel: Sie erstellen ein Profil der Abhängigkeit zwischen einer Spalte, die US-amerikanische Zip Codes enthält, und einer Spalte mit US-amerikanischen Bundesstaaten. Die gleiche Postleitzahl sollte immer denselben Bundesstaat aufweisen, doch das Profil entdeckt Verstöße gegen dieses Abhängigkeitsverhältnis.|  
|Wertinklusionsprofil|Berechnet die Überschneidung in den Werten zwischen zwei Spalten oder Gruppen von Spalten. Dieses Profil kann bestimmen, ob eine Spalte oder eine Gruppe von Spalten geeignet ist, als Fremdschlüssel zwischen den ausgewählten Tabellen zu fungieren.<br /><br /> Dieses Profil hilft Ihnen auch, Probleme bei den Daten zu identifizieren, z. B. Werte, die nicht gültig sind. Beispiel: Sie erstellen ein Profil der Spalte ProductID einer Vertriebstabelle und stellen fest, dass die Spalte Werte enthält, die nicht in der Spalte ProductID der Produkttabelle enthalten sind.|  
  
## <a name="prerequisites-for-a-valid-profile"></a>Erforderliche Komponenten für ein gültiges Profil  
 Ein Profil ist nur gültig, wenn Sie Tabellen oder Spalten auswählen, die nicht leer sind, und die Spalten für das Profil gültige Datentypen enthalten.  
  
### <a name="valid-data-types"></a>Gültige Datentypen  
 Einige der verfügbaren Profile sind nur für bestimmte Datentypen sinnvoll. Ein Spaltenmusterprofil für eine Spalte zu berechnen, die numerische oder `datetime`-Werte enthält, ist beispielsweise nicht sinnvoll. Daher ist ein solches Profil nicht gültig.  
  
|Profil|Gültige Datentypen*|  
|-------------|------------------------|  
|Spaltenstatistikprofil|Die Spalten müssen einen numerischen Typ aufweisen oder vom `datetime`-Typ sein (nicht vom `mean`- Typ und vom `stddev`-Typ für die `datetime`-Spalte).|  
|Profil für Spalten-NULL-Verhältnis|Alle Spalten\*\*|  
|Verteilungsprofil für Spaltenwerte|Die Spalten müssen vom `integer`-Typ, vom `char`-Typ und vom `datetime`-Typ sein.|  
|Verteilungsprofil für Spaltenlänge|Die Spalten müssen vom `char`-Typ sein.|  
|Spaltenmusterprofil|Die Spalten müssen vom `char`-Typ sein.|  
|Kandidatenschlüsselprofil|Die Spalten müssen vom `integer`-Typ, vom `char`-Typ und vom `datetime`-Typ sein.|  
|Funktionales Abhängigkeitsprofil|Die Spalten müssen vom `integer`-Typ, vom `char`-Typ und vom `datetime`-Typ sein.|  
|Inklusionsprofil|Die Spalten müssen vom `integer`-Typ, vom `char`-Typ und vom `datetime`-Typ sein.|  
  
 \* In der vorherigen Tabelle gültiger Datentypen die `integer`, `char`, `datetime`, und `numeric` Typen umfassen die folgenden spezifischen Datentypen:  
  
 Ganzzahltypen umfassen `bit`, `tinyint`, `smallint`, `int`, und `bigint`.  
  
 Typen mit Zeichen umfassen `char`, `nchar`, `varchar`, und `nvarchar,` aber nicht für `varchar(max)` und `nvarchar(max)`.  
  
 Datums- und Zeittypen schließen `datetime`, `smalldatetime`, und `timestamp`.  
  
 Die numerischen Typen umfassen die `integer`-Typen (mit Ausnahme des `bit`-Typs), den `money`-Typ, den `smallmoney`-Typ, den `decimal`-Typ, den `float`-Typ, den `real`-Typ und den `numeric`-Typ.  
  
 \*\* `image`, `text`, `XML`, `udt`, und `variant` Typen werden nicht unterstützt, für andere Profile als das Profil der Spalte Null-Verhältnis.  
  
### <a name="valid-tables-and-columns"></a>Gültige Tabellen und Spalten  
 Wenn die Tabelle oder die Spalte leer ist, führt die Datenprofilerstellung die folgenden Aktionen aus:  
  
-   Wenn die ausgewählte Tabelle oder die Sicht leer ist, berechnet der Datenprofilerstellungs-Task keine Profile.  
  
-   Wenn alle Werte in der ausgewählten Spalte NULL sind, berechnet der Datenprofilerstellungs-Task nur das Profil für Spalten-NULL-Verhältnis. Der Task berechnet das Verteilungsprofil für Spaltenlänge, das Spaltenmusterprofil, das Spaltenstatistikprofil oder das Verteilungsprofil für Spaltenwerte nicht.  
  
## <a name="features-of-the-data-profiling-task"></a>Funktion des Datenprofilerstellungs-Tasks  
 Der Datenprofilerstellungs-Task verfügt über die folgenden zweckmäßigen Konfigurationsoptionen:  
  
-   **Platzhalterspalten** Beim Konfigurieren einer Profilanforderung akzeptiert der Task das Platzhalterzeichen **(\*)** für einen Spaltennamen. Dies vereinfacht die Konfiguration und macht es leichter, die Eigenschaften unbekannter Daten zu ermitteln. Wenn der Task ausgeführt wird, erstellt er für jede Spalte, die über einen entsprechenden Datentyp verfügt, ein Profil.  
  
-   **Schnellprofil** You can select Schnellprofil to configure the task quickly. Ein Schnellprofil erstellt ein Profil einer Tabelle oder einer Sicht mit allen Standardprofilen und Standardeinstellungen.  
  
## <a name="custom-logging-messages-available-on-the-data-profililng-task"></a>Verfügbare benutzerdefinierte Meldungen für den Datenprofilerstellungs-Task  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge für den Datenprofilerstellungs-Task aufgelistet. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) und [Benutzerdefinierte Meldungen für die Protokollierung](../custom-messages-for-logging.md).  
  
|Protokolleintrag|Beschreibung|  
|---------------|-----------------|  
|**DataProfilingTaskTrace**|Stellt beschreibende Informationen zum Taskstatus zur Verfügung. Nachrichten beinhalten folgende Informationen:<br /><br /> Start der Anforderungsverarbeitung<br /><br /> Abfragestart<br /><br /> Abfrageende<br /><br /> Beenden der Anforderungsverarbeitung|  
  
## <a name="output-and-its-schema"></a>Ausgabe und zugehöriges Schema  
 Der Datenprofilerstellungs-Task gibt die ausgewählten Profile im XML-Format aus, das dem Schema DataProfile.xsd entsprechend strukturiert ist. Sie können angeben, ob diese XML-Ausgabe in einer Datei oder einer Paketvariablen gespeichert wird. Sie können dieses Schema online anzeigen unter [https://schemas.microsoft.com/sqlserver/2008/DataDebugger/](https://schemas.microsoft.com/sqlserver/2008/DataDebugger/). Auf der Webseite können Sie eine lokale Kopie des Schemas speichern. Anschließend können Sie die lokale Kopie des Schemas in Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oder einem anderen Schema-Editor, in einem XML-Editor oder einem Texteditor wie Notepad anzeigen.  
  
 Dieses Schema für Datenqualitätsinformationen kann für Folgendes nützlich sein:  
  
-   Austauschen von Datenqualitätsinformationen innerhalb und außerhalb von Organisationen.  
  
-   Erstellen von benutzerdefinierten Tools, die mit Datenqualitätsinformationen arbeiten.  
  
 Der Zielnamespace wird im Schema als [https://schemas.microsoft.com/sqlserver/2008/DataDebugger/](https://schemas.microsoft.com/sqlserver/2008/DataDebugger/) identifiziert.  
  
## <a name="output-in-the-conditional-workflow-of-a-package"></a>Ausgabe im bedingten Workflow eines Pakets  
 Die Komponenten der Datenprofilerstellung umfassen keine integrierten Funktionen zur Implementierung bedingter Logik im Workflow des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets basierend auf der Ausgabe des Datenprofilerstellungs-Tasks. Sie können diese Logik, mit minimalem Programmieraufwand, problemlos in einem Skripttask hinzufügen. Mit diesem Code wird eine Xpath-Abfrage der XML-Ausgabe durchgeführt und das Ergebnis in einer Paketvariablen gespeichert. Die Rangfolgeneinschränkungen, mit denen der Skripttask mit nachfolgenden Tasks verbunden wird, können einen Ausdruck verwenden, um den Workflow zu bestimmen. Der Skripttask stellt beispielsweise fest, dass der Prozentsatz der NULL-Werte in einer Spalte einen bestimmten Schwellenwert überschreitet. Wenn diese Bedingung wahr ist, sollten Sie das Paket unterbrechen und das Problem beheben, bevor Sie fortfahren.  
  
## <a name="configuration-of-the-data-profiling-task"></a>Konfiguration des Datenprofilerstellungs-Tasks  
 Sie konfigurieren den Datenprofilerstellungs-Task mit dem **Editor für den Datenprofilerstellungs-Task**. Der Editor hat zwei Seiten:  
  
 [Seite Allgemein](../general-page-of-integration-services-designers-options.md)  
 Auf der Seite **Allgemein** geben Sie die Ausgabedatei oder die Variable an. Sie können auch **Schnellprofil** auswählen, um den Task schnell zu konfigurieren und Profile mit den Standardeinstellungen zu berechnen. Weitere Informationen finden Sie unter [Schnellprofilformular für eine einzelne Tabelle &#40;Datenprofilerstellungs-Task&#41;](data-profiling-task.md).  
  
 [Seite Profilanforderungen](data-profiling-task-editor-profile-requests-page.md)  
 Auf der Seite **Profilanforderungen** geben Sie die Datenquelle an und wählen und konfigurieren die Datenprofile, die Sie berechnen möchten. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den verschiedenen Profilen zu erhalten, die Sie konfigurieren können:  
  
-   [Optionen für die Anforderung für Kandidatenschlüsselprofil &#40;Datenprofilerstellungs-Task&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Verteilungsprofil für Spaltenlänge &#40;Datenprofilerstellungs-Task&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Profil für NULL-Verhältnis der Spalte &#40;Datenprofilerstellungs-Task&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Spaltenmusterprofil &#40;Datenprofilerstellungs-Task&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Spaltenstatistikprofil &#40;Datenprofilerstellungs-Task&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Verteilungsprofil für Spaltenwert &#40;Datenprofilerstellungs-Task&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für funktionales Abhängigkeitsprofil &#40;Datenprofilerstellungs-Task&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Wertinklusionsprofil &#40;Datenprofilerstellungs-Task&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
  
