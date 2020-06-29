---
title: Einrichten von Datenprofilerstellungs-Tasks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], configuring
ms.assetid: fe050ca4-fe45-43d7-afa9-99478041f9a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0780e96d2779fadba7110b8eae02c5fe095d4b5
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433017"
---
# <a name="setup-of-the-data-profiling-task"></a>Einrichten von Datenprofilerstellungs-Tasks
  Bevor Sie ein Profil der Quelldaten überprüfen können, müssen Sie zunächst den Datenprofilerstellungs-Task einrichten und ausführen. Sie erstellen diesen Task in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket. Zum Konfigurieren des Datenprofilerstellungs-Tasks verwenden Sie den Editor für den Datenprofilerstellungs-Task. Mit diesem Editor können Sie auswählen, wo die Profile ausgegeben und welche Profile berechnet werden sollen. Nachdem Sie den Task eingerichtet haben, führen Sie das Paket aus, um die Datenprofile zu berechnen.  
  
## <a name="requirements-and-limitations"></a>Anforderungen und Einschränkungen  
 Der Datenprofilerstellungs-Task funktioniert nur mit Daten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert werden. Dieser Task funktioniert nicht mit Datenquellen von Drittanbietern oder dateibasierten Datenquellen.  
  
 Um das Paket auszuführen, das den Datenprofilerstellungs-Task enthält, müssen Sie zudem ein Konto verwenden, das über Lese-/Schreibberechtigungen sowie CREATE TABLE-Berechtigungen für die tempdb-Datenbank verfügt.  
  
## <a name="data-profiling-task-in-a-package"></a>Datenprofilerstellungs-Task in einem Paket  
 Der Datenprofilerstellungs-Task konfiguriert nur die Profile und erstellt die Ausgabedatei, die die berechneten Profile enthält. Zum Überprüfen dieser Ausgabedatei verwenden Sie den Datenprofil-Viewer, ein eigenständiges Viewer-Programm. Da Sie die Ausgabedatei separat anzeigen müssen, können Sie den Datenprofilerstellungs-Task in einem Paket verwenden, das keine anderen Tasks enthält.  
  
 Der Datenprofilerstellungs-Task muss jedoch nicht als einziger Task in einem Paket verwendet werden. Wenn Sie die Datenprofilerstellung im Workflow oder im Datenfluss eines komplexeren Pakets ausführen möchten, stehen folgende Optionen zur Verfügung:  
  
-   Zur Implementierung bedingter Logik, die auf der Ausgabedatei des Tasks basiert, nehmen Sie in der Ablaufsteuerung des Pakets nach dem Datenprofilerstellungs-Tasks einen Skripttask auf. Mit diesem Skripttask können Sie anschließend die Ausgabedatei abfragen.  
  
-   Um ein Profil der Daten im Datenfluss zu erstellen, nachdem die Daten geladen und transformiert wurden, müssen Sie die geänderten Daten vorübergehend in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle speichern. Anschließend können Sie ein Profil der gespeicherten Daten erstellen.  
  
 Weitere Informationen finden Sie unter [Einschließen einer Datenprofilerstellungs-Task in den Paketworkflow](incorporate-a-data-profiling-task-in-package-workflow.md).  
  
## <a name="setup-of-the-task-output"></a>Einrichten der Taskausgabe  
 Nachdem der Datenprofilerstellungs-Task in einem Paket aufgenommen wurde, müssen Sie die Ausgabe für die Profile einrichten, die vom Task berechnet werden. Zum Einrichten der Ausgabe für die Profile verwenden Sie die Seite **Allgemein** des Editors für den Datenprofilerstellungs-Task. Zusätzlich zur Angabe des Ziels für die Ausgabe bietet die Seite **Allgemein** auch die Möglichkeit zur Ausführung eines Schnellprofils der Daten an. Bei Auswahl von **Schnellprofil**erstellt der Datenprofilerstellungs-Task eine Tabelle oder eine Sicht mit einigen oder allen Standardprofilen und deren Standardeinstellungen.  
  
 Weitere Informationen finden Sie unter [Editor für den Datenprofilerstellungs-Task &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md) und [Schnellprofilformular für eine einzelne Tabelle &#40;Datenprofilerstellungs-Task&#41;](data-profiling-task.md).  
  
> [!IMPORTANT]  
>  Die Ausgabedatei enthält möglicherweise vertrauliche Daten über Ihre Datenbank und die darin enthaltenen Daten. Vorschläge zur Verbesserung der Sicherheit dieser Datei finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../access-to-files-used-by-packages.md).  
  
## <a name="selection-and-configuration-of-the-profiles-to-be-computed"></a>Auswählen und Konfigurieren der zu berechnenden Profile  
 Nachdem Sie die Ausgabedatei eingerichtet haben, müssen Sie auswählen, welche Datenprofile berechnet werden sollen. Der Datenprofilerstellungs-Task kann acht verschiedene Datenprofile berechnen. Fünf Profile analysieren einzelne Spalten und die restlichen drei analysieren mehrere Spalten oder Beziehungen zwischen Spalten und Tabellen. In einem Datenprofilerstellungs-Task können Sie mehrere Profile für mehrere Spalten oder Kombinationen von Spalten in mehreren Tabellen oder Sichten berechnen.  
  
 Die folgende Tabelle beschreibt die Berichte, die von jedem dieser Profile berechnet werden, und die Datentypen, für die das Profil gültig ist.  
  
|Zum Berechnen|Welche bei der Identifizierung helfen|Verwenden Sie dieses Profil|  
|----------------|-------------------------|----------------------|  
|Alle eindeutigen Längen der Zeichenfolgenwerte in der ausgewählten Spalte sowie der Prozentsatz der Zeilen in der Tabelle, den jede Länge darstellt.|**Ungültige Zeichenfolgenwerte**: Sie erstellen beispielsweise ein Profil einer Spalte, die zwei Zeichen für die Codes der US-amerikanischen Bundesstaaten verwenden soll, stellen jedoch fest, dass diese Werte enthält, die länger sind als zwei Zeichen.|**Spalten Längenverteilung-** Gültig für eine Spalte mit einem der folgenden Datentypen:<br /><br /> Zeichendatentypen: `char`, `nchar`, `varchar` und `nvarchar`|  
|Ein Satz von regulären Ausdrücken, die den angegebenen Prozentsatz der Werte in einer Zeichenfolgenspalte abdecken.<br /><br /> Auch zum Finden regulärer Ausdrücke, die künftig zur Überprüfung neuer Werte verwendet werden können|**Zeichen folgen Werte, die nicht gültig sind oder nicht im richtigen Format vorliegen:** Beispielsweise kann ein Muster Profil einer Spalte mit Postleitzahl die regulären Ausdrücke erstellen: \d {5} -\d {4} , \d {5} und \d {9} . Wenn die Ausgabe andere reguläre Ausdrücke enthält, enthalten die Daten ungültige oder falsch formatierte Werte.|**Spaltenmusterprofil:** Gültig für eine Spalte mit einem der folgenden Datentypen:<br /><br /> Zeichendatentypen: `char`, `nchar`, `varchar` und `nvarchar`|  
|Der Prozentsatz der NULL-Werte in der ausgewählten Spalte.|**Ein unerwartet hohes Verhältnis von NULL-Werten in einer Spalte** . Beispielsweise können Sie ein Profil für eine Spalte erstellen, die USA ZIP-Codes enthalten soll, aber einen unerwartet hohen Prozentsatz an fehlenden Postleitzahlen ermitteln.|**NULL-Verhältnis der Spalte-** Gültig für eine Spalte mit den folgenden Datentypen:<br /><br /> Jeder Datentyp. Dazu zählen `image`, `text`, `xml`, benutzerdefinierte Typen und Variant-Typen.|  
|Statistiken, wie minimale, maximale, durchschnittliche und standardmäßige Abweichung für numerische Spalten sowie Mindest- und Höchstwert für `datetime`-Spalten.|**Numerische Werte und Datumsangaben, die nicht gültig sind**, z. b. Erstellen eines Profils für eine Spalte mit historischen Daten, Ermitteln eines maximalen Datums, das in der Zukunft liegt.|**Spalten Statistik Profil-** Gültig für eine Spalte mit einem der folgenden Datentypen:<br /><br /> Numerische Datentypen: Integer-Typen (außer `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` und `numeric`<br /><br /> Datums- und Uhrzeit-Datentypen: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` und `datetimeoffset`<br />Hinweis: Für eine Spalte, die über ein Datum- und einen Zeitdatentyp verfügt, berechnet das Profil nur Minimum und Maximum.|  
|Alle eindeutigen Werte in der ausgewählten Spalte sowie der Prozentsatz der Zeilen in der Tabelle, den jeder Wert darstellt. Oder die Werte, die mehr als einen angegebenen Prozentwert in der Tabelle darstellen.|**Eine falsche Anzahl eindeutiger Werte in einer Spalte**. Sie können z. b. ein Profil für eine Spalte erstellen, die Zustände im USA enthält, aber mehr als 50 unterschiedliche Werte ermitteln.|**Verteilung von Spaltenwerten:** Gültig für eine Spalte mit einem der folgenden Datentypen:<br /><br /> Numerische Datentypen: Integer-Typen (außer `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` und `numeric`<br /><br /> Zeichendatentypen: `char`, `nchar`, `varchar` und `nvarchar`<br /><br /> Datums- und Uhrzeit-Datentypen: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` und `datetimeoffset`|  
|Ob eine Spalte oder eine Gruppe von Spalten ein Schlüssel oder ein ungefährer Schlüssel für die ausgewählte Tabelle ist.|**Doppelte Werte in einer potenziellen Schlüssel Spalte:** Beispielsweise erstellen Sie ein Profil der Spalten "Name" und "Address" in einer Customers-Tabelle und ermitteln doppelte Werte, bei denen die Kombinationen aus Name und Adresse eindeutig sein sollten.|**Kandidaten Schlüssel-** Ein Profil mit mehreren Spalten, das meldet, ob eine Spalte oder eine Gruppe von Spalten geeignet ist, um als Schlüssel für die ausgewählte Tabelle zu fungieren. Gültig für Spalten mit einem dieser Datentypen:<br /><br /> Integer-Datentypen: `bit`, `tinyint`, `smallint`, `int` und `bigint`<br /><br /> Zeichendatentypen: `char`, `nchar`, `varchar` und `nvarchar`<br /><br /> Datums- und Uhrzeit-Datentypen: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` und `datetimeoffset`|  
|Das Ausmaß, bis zu dem die Werte in einer Spalte (die abhängige Spalte) von den Werten in einer anderen Spalte oder einer Gruppe von Spalten (die determinante Spalte) abhängig sind.|**Werte, die in abhängigen Spalten nicht gültig sind:** Beispielsweise erstellen Sie ein Profil der Abhängigkeit zwischen einer Spalte, die USA ZIP-Codes enthält, und einer Spalte, die Zustände im USA enthält. Einer Postleitzahl sollte immer derselbe Bundesstaat zugeordnet sein. Das Profil stellt jedoch Abhängigkeitsverletzungen fest.|**Funktionale Abhängigkeit:** Gültig für Spalten mit einem dieser Datentypen:<br /><br /> Integer-Datentypen: `bit`, `tinyint`, `smallint`, `int` und `bigint`<br /><br /> Zeichendatentypen: `char`, `nchar`, `varchar` und `nvarchar`<br /><br /> Datums- und Uhrzeit-Datentypen: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` und `datetimeoffset`|  
|Ob eine Spalte oder eine Gruppe von Spalten geeignet ist, um als Fremdschlüssel zwischen den ausgewählten Tabellen zu fungieren.<br /><br /> Das bedeutet, dass dieses Profil die Überschneidung in den Werten zwischen zwei Spalten oder Gruppen von Spalten meldet.|Ungültige **Werte:** Beispielsweise erstellen Sie ein Profil der ProductID-Spalte einer Sales-Tabelle. Das Profil erkennt, dass die Spalte Werte enthält, die nicht in der Spalte ProductID der Products-Tabelle enthalten sind.|**Wert Einbindung-** Gültig für Spalten mit einem dieser Datentypen:<br /><br /> Integer-Datentypen: `bit`, `tinyint`, `smallint`, `int` und `bigint`<br /><br /> Zeichen Datentyp: `char` , `nchar` , `varchar` und`nvarchar`<br /><br /> Datums- und Uhrzeit-Datentypen: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` und `datetimeoffset`|  
  
 Zur Auswahl der zu berechnenden Profile verwenden Sie die Seite **Profilanforderungen** im Editor für den Datenprofilerstellungs-Task. Weitere Informationen finden Sie unter [Editor für den Datenprofilerstellungs-Task &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Auf der Seite **Profilanforderungen** geben Sie auch die Datenquelle an und konfigurieren die Datenprofile. Beachten Sie beim Konfigurieren des Tasks die folgenden Informationen:  
  
-   Um die Konfiguration zu vereinfachen und das Ermitteln von Merkmalen unbekannter Daten zu vereinfachen, können Sie anstelle eines einzelnen Spaltennamens den Platzhalter **( \* )** verwenden. Wenn Sie diesen Platzhalter verwenden, erstellt der Task ein Profil von jeder Spalte, die über einen entsprechenden Datentyp verfügt. Dies kann die Verarbeitungsgeschwindigkeit beeinträchtigen.  
  
-   Wenn die ausgewählte Tabelle oder die Sicht leer ist, berechnet der Datenprofilerstellungs-Task keine Profile.  
  
-   Wenn alle Werte in der ausgewählten Spalte NULL sind, berechnet der Datenprofilerstellungs-Task nur das Profil für Spalten-NULL-Verhältnis. Der Task berechnet nicht das Verteilungsprofil für Spaltenlänge, das Spaltenmusterprofil, das Spaltenstatistikprofil oder das Verteilungsprofil für Spaltenwerte für die leere Spalte.  
  
 Jedes verfügbare Datenprofil hat eigene Konfigurationsoptionen. Weitere Informationen zu diesen Optionen finden Sie in den folgenden Themen:  
  
-   [Optionen für die Anforderung für Kandidatenschlüsselprofil &#40;Datenprofilerstellungs-Task&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Verteilungsprofil für Spaltenlänge &#40;Datenprofilerstellungs-Task&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Profil für NULL-Verhältnis der Spalte &#40;Datenprofilerstellungs-Task&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Spaltenmusterprofil &#40;Datenprofilerstellungs-Task&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für Spaltenstatistikprofil &#40;Datenprofilerstellungs-Task&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Verteilungsprofil für Spaltenwert &#40;Datenprofilerstellungs-Task&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für die Anforderung für funktionales Abhängigkeitsprofil &#40;Datenprofilerstellungs-Task&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Optionen für Anforderung für Wertinklusionsprofil &#40;Datenprofilerstellungs-Task&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
## <a name="execution-of-the-package-that-contains-the-data-profiling-task"></a>Ausführen des Pakets, das den Datenprofilerstellungs-Task enthält  
 Nachdem Sie den Datenprofilerstellungs-Task eingerichtet haben, können Sie den Task ausführen. Der Task berechnet dann die Datenprofile und gibt diese Informationen im XML-Format in einer Datei oder einer Paketvariablen aus. Die Struktur dieses XML-Formats folgt dem DataProfile.xsd-Schema. Sie können das Schema in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oder einem anderen Schema-Editor, in einem XML-Editor oder in einem Text-Editor wie Notepad öffnen. Dieses Schema für Datenqualitätsinformationen kann für folgende Zwecke nützlich sein:  
  
-   Zum Austauschen von Datenqualitätsinformationen innerhalb und außerhalb von Organisationen.  
  
-   Zum Erstellen von benutzerdefinierten Tools, die mit Datenqualitätsinformationen arbeiten.  
  
 Der Ziel Namespace wird im Schema als identifiziert [https://schemas.microsoft.com/sqlserver/2008/DataDebugger/](https://schemas.microsoft.com/sqlserver/2008/DataDebugger/) .  
  
## <a name="next-step"></a>Nächster Schritt  
 [Datenprofil-Viewer](data-profile-viewer.md).  
  
  
