---
title: Statische Datenmaskierung | Microsoft-Dokumentation
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: a62f4ff9-2953-42ca-b7d8-1f8f527c4d66
author: egranet
ms.author: esgranet
manager: ajayj
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 18dd28aeb4c1678b4b6ae454c065d3d96770cb5a
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539108"
---
# <a name="static-data-masking"></a>Statische Datenmaskierung
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Bei der statischen Datenmaskierung handelt es sich um eine Komponente von [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) 18.0 Preview 5 und höher. Sie können die neueste Vorschauversion von SQL Server Management Studio [hier](../../ssms/download-sql-server-management-studio-ssms.md) herunterladen. 

![Statische Datenmaskierung](../../relational-databases/security/media/sql-static-data-masking/static_data_masking_intro_image.PNG)


## <a name="what-is-static-data-masking"></a>Was ist die statische Datenmaskierung? 
Bei der statischen Datenmaskierung handelt es sich um ein Feature von SQL Server Management Studio, mit dem Benutzer eine maskierte Kopie einer Datenbank erstellen können. Das Feature wurde für Organisationen entwickelt, in denen (teilweise vertrauliche) Daten teamübergreifend oder für andere Organisationen freigegeben werden müssen. 

Die statische Datenmaskierung vereinfacht folgende Szenarios, indem Sie vertrauliche Daten (Daten vor der Maskierung) durch neue Daten (Daten nach der Maskierung) ersetzt: 
- Entwickeln und Testen 
- Analysen und Unternehmensberichterstellung 
- Problembehandlung 
- Freigeben einer Datenbank für einen Berater, ein Forschungsteam oder einen Drittanbieter 

Im folgenden Beispiel wird veranschaulicht, wie die statische Datenmaskierung in der Praxis funktioniert. Vor der Maskierung enthält die Spalte US-Sozialversicherungsnummern. Nach der Maskierung wurden die ersten fünf Ziffern jeder US-Sozialversicherungsnummer durch zufällig generierte Zahlen ersetzt.

| US-Sozialversicherungsnummer (vor der Maskierung)   | US-Sozialversicherungsnummer (nach der Maskierung)  |
| ------------- | ------------- |
| 140-38-9110 | 302-92-9110 |
| 463-34-5535 | 189-70-5535 |
| 116-30-8733 | 201-01-8733 |
| 209-36-1971 | 683-10-1971 |
| 372-38-6948 | 372-38-6948 |
| 267-64-2334 | 100-03-2334 |
| 523-93-4176 | 582-20-4176 |
| 573-91-5137 | 730-20-5137 |
| 612-72-1026 | 369-40-1026 |

Die Benutzer können aus verschiedenen Funktionen für die statische Datenmaskierung auswählen. Abhängig von der Maskierungsfunktion können die Daten vor und nach der Maskierungsfunktion sich stark bis gar nicht ähneln. Bei einer Maskierungsfunktion, die einen Shuffle durchführt, ähneln sich die Daten vor und nach der Maskierung. 

| US-Sozialversicherungsnummer (vor der Maskierung) | US-Sozialversicherungsnummer (nach der Maskierung) |
| ------------- | ------------- |
| 140-38-9110 | 612-72-1026 |  
| 463-34-5535 | 372-38-6948 | 
| 116-30-8733 | 523-93-4176 |
| 209-36-1971 | 209-36-1971 | 
| 372-38-6948 | 140-38-9110 |
| 267-64-2334 | 463-34-5535 | 
| 523-93-4176 | 573-91-5137 | 
| 573-91-5137 | 267-64-2334 | 
| 612-72-1026 | 116-30-8733 |

Bei einer Maskierungsfunktion, die eine Ersetzung durch den Wert NULL durchführt, ähneln sich die Daten vor und nach der Maskierung nicht. 
 
| US-Sozialversicherungsnummer (vor der Maskierung) | US-Sozialversicherungsnummer (nach der Maskierung) |
| ------------- | ------------- |
| 140-38-9110 | NULL |  
| 463-34-5535 | NULL | 
| 116-30-8733 | NULL |
| 209-36-1971 | NULL | 
| 372-38-6948 | NULL |
| 267-64-2334 | NULL | 
| 523-93-4176 | NULL | 
| 573-91-5137 | NULL | 
| 612-72-1026 | NULL |

## <a name="how-does-static-data-masking-work"></a>Wie funktioniert die statische Datenmaskierung?
Die statische Datenmaskierung erfolgt auf Spaltenebene. Die Benutzer wählen aus, welche Spalten maskiert wählen sollen und welche Maskierungsfunktion auf die ausgewählten Spalten angewendet werden sollen. Es stehen mehrere Maskierungsfunktionen zur Auswahl. Diese werden unter [Maskierungsfunktionen](#masking-functions) ausführlich erläutert. 

Die statische Datenmaskierung erstellt anschließend eine Kopie der Datenbank. In Azure SQL-Datenbank wird die Kopie über die [Kopierfunktion](https://azure.microsoft.com/blog/static-data-masking-preview/) erstellt. In SQL Server wird diese über einen Sicherungsvorgang und einen anschließenden Wiederherstellungsvorgang erstellt. Nun beginnt die statische Datenmaskierung damit, in jeder Zeile die unmaskierten Daten der ausgewählten Maskierungsfunktion entsprechend durch maskierte Daten zu ersetzen. 

Die Ersetzung erfolgt auf Speicherebene. Deshalb ist es nicht möglich, die unmaskierten Daten aus der maskierten Kopie der Datenbank abzurufen, nachdem die statische Datenmaskierung durchgeführt wurde.

## <a name="how-to-guide"></a>Vorgehensweise

Hier finden Sie eine ausführliche Anleitung für die Ausführung der statischen Datenmaskierung. 
 
1. Starten Sie SQL Server Management Studio. Stellen Sie eine Verbindung mit Ihrer Datenbank her. Erweitern Sie im Bereich **Objekt-Explorer** auf der linken Seite den Ordner „Databases“ (Datenbanken). Klicken Sie mit der rechten Maustaste auf die Datenbank, die Sie maskieren möchten. Klicken Sie auf **Tasks**. Klicken Sie auf **Datenbank maskieren... (Vorschau)**.
 
 ![Menü „Tasks“](../../relational-databases/security/media/sql-static-data-masking/task_data_masking.PNG)
 
2. Ein Fenster für die Konfiguration der Maskierung wird geöffnet. In diesem werden alle Tabellen in der Datenbank angezeigt. Die Tabellen werden nach Schema angezeigt und innerhalb eines Schemas in alphabetischer Reihenfolge sortiert. 
 
 ![Benutzeroberfläche](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown.PNG)
 
3. Klicken Sie auf das Dropdownsymbol neben dem Tabellennamen, um eine Liste aller Spalten in der Tabelle anzuzeigen. Für jede Spalte in der Tabelle werden der Datentyp und ob NULL-Werte zulässig sind angegeben. Wenn für eine Spalte „nullable“ angegeben ist, kann für diese Spalte der Wert NULL als Eintrag festgelegt werden. 
 
 ![Dropdownliste der Tabellen](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown_column.png)
 
4. Wählen Sie alle Spalten aus, die maskiert werden sollen, und die Maskierungsfunktion, die angewendet werden soll. Folgende Maskierungsfunktionen sind verfügbar: **Shuffle**, **Group Shuffle** (Gruppenshuffle), **Single value** (Einzelwert), **NULL** und **String Composite** (Zusammengesetzte Zeichenfolge). 
 
 ![Dropdownliste der Maskierungsfunktionen](../../relational-databases/security/media/sql-static-data-masking/masking_functions.PNG)
 
 Hinweis: Für die meisten dieser Maskierungsfunktionen gibt es zusätzliche Konfigurationsparameter. Für die Shufflemaskierung ist ein Standardparameter in der statischen Datenmaskierung verfügbar. Für die Funktionen „Group Shuffle“ (Gruppenshuffle), „Single value“ (Einzelwert) und „String Composite“ (Zusammengesetzte Zeichenfolge) muss der Benutzer Konfigurationsparameter angeben. Klicken Sie zum Ändern oder Bereitstellen von Konfigurationsparametern auf die Option **Konfigurieren...**, und geben Sie in dem Dialogfeld, das angezeigt wird, einen (alternativen) Wert für den Parameter an. Die Maskierungsfunktionen werden unter [Maskierungsfunktionen](#masking-functions) ausführlich beschrieben.
 
 ![Schaltfläche „Konfigurieren...“ für Maskierungsfunktionen](../../relational-databases/security/media/sql-static-data-masking/masking_functions_configure.png)
 
 Die Optionen für die Konfiguration der Maskierung werden sofort auf Fehler und Warnungen überprüft, die in Zusammenhang mit der Konfiguration und dem Schema stehen.  Ermittelte Probleme werden auf der linken Seite als Symbol angezeigt, auf das Sie mit der Maus zeigen können, um weitere Details anzuzeigen. 
 
 Im folgenden Beispiel hat der Benutzer die Maskierung „NULL“ für eine Spalte ausgewählt, für die keine NULL-Werte zulässig sind (NOT NULL-Beschränkung).
 
 ![Fehler bei der Überprüfung](../../relational-databases/security/media/sql-static-data-masking/validation_mechanism_error_message.PNG)
 
 Im folgenden Beispiel hat der Benutzer die Maskierung „Group Shuffle“ (Gruppenshuffle) für nur eine Spalte ausgewählt. Da hierfür mindestens zwei Spalten ausgewählt werden müssen, wurde eine Warnung ausgelöst. 
 
 ![Warnung bei der Überprüfung](../../relational-databases/security/media/sql-static-data-masking/validation_warning.PNG)
 
5. Die vollständige Konfiguration für die Maskierung kann für spätere Verwendung in einer XML-Datei gespeichert werden.  Die Konfiguration für Maskierungsfunktionen ist zwar für Azure SQL-Datenbank und lokale Datenbanken gleich, es gibt jedoch geringfügige Unterschiede beim Speichern anderer Eigenschaften (z.B. der Pfad für Sicherungsdateien). Klicken Sie auf **Save Config** (Konfig. speichern), geben Sie einen Dateinamen an, und klicken Sie auf „Speichern“, um die Konfiguration zu speichern.  Die Benutzer können eine vorhandene Konfigurationsdatei dann über die Option **Load Config** (Konfig. laden) laden. Es wird empfohlen, Konfigurationsdateien für Tabellen zu verwenden, die viele Spalten enthalten. 
 
 ![Konfigurationsdatei](../../relational-databases/security/media/sql-static-data-masking/load_save_config.PNG)
 
6. Bei der statischen Datenmaskierung wird im Ordner **Dokumente** des Benutzers ein Ordner namens „Static Data Masking“ (Statische Datenmaskierung) erstellt, in dem Protokolldateien gespeichert werden. Die Protokolldateien können beim Debuggen nützlich sein. Der Name der Protokolldatei wird am unteren Rand des Konfigurationsfensters angezeigt. 
  
 
7. Nur SQL Server: Wenn Sie die statische Datenmaskierung auf einer lokalen Datenbank ausführen, führt diese eine Sicherung und eine Wiederherstellung durch. Geben Sie unter **Step 2: Clone .BAK file Location** (Schritt 2: Speicherort der BAK-Datei klonen) den Speicherort auf dem Server an, an dem die Sicherungsdatei gespeichert wird. 

## <a name="masking-functions"></a>Maskierungsfunktionen

### <a name="null-masking"></a>Maskierung mit NULL-Werten

Bei der NULL-Maskierung werden alle Werte in der Spalte durch NULL ersetzt. Wenn die Spalte keine NULL-Werte zulässt, gibt das Tool für die statische Datenmaskierung einen Fehler zurück. 

### <a name="single-value-masking"></a>Maskierung mit Einzelwerten

Bei der Maskierung mit Einzelwerten werden alle Werte in der Spalte durch einen einzelnen, vom Benutzer festgelegten Wert ersetzt. Das Format der Eingabe muss in den Typ der ausgewählten Spalte konvertierbar sein. Klicken Sie auf **Konfigurieren...**, geben Sie einen Wert an, und klicken Sie anschließend auf **OK**, um einen Wert festzulegen. 

![Parameter für die Maskierung mit Einzelwerten](../../relational-databases/security/media/sql-static-data-masking/single_value_parameter.PNG)


### <a name="shuffle-masking"></a>Shufflemaskierung

Alle Werte in der Spalte werden per Shuffle neuen Zeilen zugeordnet. Es werden keine neuen Daten generiert. Bei der Shufflemaskierung besteht die Möglichkeit, die NULL-Einträge in der jeweiligen Spalte beizubehalten. Klicken Sie hierfür auf **Konfigurieren...**, und aktivieren Sie das Kontrollkästchen „Maintain NULL positions“ (NULL-Positionen beibehalten).

![Parameter für die Shufflemaskierung](../../relational-databases/security/media/sql-static-data-masking/shuffle_parameter.PNG)

Im Folgenden finden Sie ein Beispiel für die Shufflemaskierung, bei der die NULL-Werte einmal beibehalten wurden und einmal nicht.


| US-Sozialversicherungsnummer (vor der Maskierung) | US-Sozialversicherungsnummer (nach der Maskierung mit verschobenen NULL-Einträgen) | US-Sozialversicherungsnummer (nach der Maskierung mit nicht verschobenen NULL-Einträgen) |
| ------------- | ------------- | ------------- |
| 116-30-8733 | 612-72-1026 | 463-34-5535 |
| 140-38-9110 | NULL | 573-91-5137  |
| 209-36-1971 | 523-93-4176 | 140-38-9110 |
| NULL | 209-36-1971 | NULL |
| 463-34-5535 | 140-38-9110 | 116-30-8733  |
| 523-93-4176 | 463-34-5535 | 612-72-1026  |
| NULL | 573-91-5137 | NULL |
| 573-91-5137 | NULL | 523-93-4176 |
| 612-72-1026  | 116-30-8733  | 209-36-1971 |  

### <a name="group-shuffle-masking"></a>Maskierung mit Gruppenshuffle
Bei einem Gruppenshuffle werden mehrere Spalten zu einer „Shufflegruppe“ zusammengefasst. Die Spalten in einer Shufflegruppe werden zusammen verschoben. Der Benutzer muss den Namen der Shufflegruppe mithilfe der Option **Konfigurieren...** festlegen.

![Parameter für die Maskierung mit Gruppenshuffle](../../relational-databases/security/media/sql-static-data-masking/group_shuffle_parameter.PNG)

Ein Gruppenshuffle wird immer in einer Tabelle durchgeführt. Wenn ein Shufflegruppenname in mehreren Tabellen verwendet wird, werden diese Shufflegruppen in unabhängigen Vorgängen verarbeitet. Der Gruppenname muss für alle Spalten, die in der Gruppe enthalten sein sollen, gleich sein. Beim Namen wird die Groß- und Kleinschreibung berücksichtigt. Mehrere Shufflegruppen (mit unterschiedlichen Namen) können in einer Tabelle vorhanden sein. 

### <a name="string-composite-masking"></a>Maskierung mit zusammengesetzten Zeichenfolgen

Bei der Maskierung mit zusammengesetzten Zeichenfolgen werden zufällige Zeichenfolgen nach einem bestimmten Muster generiert. Diese wurde für Zeichenfolgen entworfen, die einem vordefinierten Muster entsprechen müssen, um gültig zu sein. US-Sozialversicherungsnummern weisen Beispielsweise das Format „123-45-6789“ auf. Die Syntax für die Maskierung mit zusammengesetzten Zeichenfolgen wird in dem Dialogfeld festgelegt, in dem der Benutzer das Muster eingeben muss.

![Parameter für Maskierung mit zusammengesetzten Zeichenfolgen](../../relational-databases/security/media/sql-static-data-masking/string_composite.PNG)

Bei der Maskierung mit zusammengesetzten Zeichenfolgen stehen drei Beispielmuster zur Verfügung, die Sie testen können, indem Sie auf diese klicken. Wenn Sie auf „Phone Number“ (Telefonnummer) klicken, wird das Feld für das Muster automatisch mit der Formel aufgefüllt, die für das Generieren zufälliger US-amerikanischer Telefonnummern erforderlich ist.

![Beispiel für Parameter bei der Maskierung mit zusammengesetzten Zeichenfolgen](../../relational-databases/security/media/sql-static-data-masking/string_composite_phone_example.PNG)

Es gibt außerdem einen erweiterten Modus für die Maskierung mit zusammengesetzten Zeichenfolgen, bei dem Unterabschnitte von vorhandenen Daten durch aus Mustern generierte Zeichenfolgen ersetzt werden können. Der ersetzte Teil der Zeichenfolge wird von der Erfassungsgruppe in einem regulären Ausdruck bestimmt. Der Benutzername einer E-Mail kann beispielsweise ersetzt werden, während die Domäne beibehalten wird, oder eine Telefonnummer kann ersetzt werden, während die Vorwahl beibehalten wird. Weitere Informationen zu regulären Ausdrücken finden Sie [hier](https://docs.microsoft.com/dotnet/standard/base-types/regular-expression-language-quick-reference).

![Beispiel für Parameter bei der Maskierung mit zusammengesetzten Zeichenfolgen im erweiterten Modus](../../relational-databases/security/media/sql-static-data-masking/string_composite_advanced.PNG)

Die Maskierung mit zusammengesetzten Zeichenfolgen und deren erweiterter Modus können nur für Spalten mit den [Datentypen](../../t-sql/data-types/data-types-transact-sql.md) char, varchar, text, nchar, nvarchar und ntext verwendet werden.

## <a name="limitations"></a>Einschränkungen 

Für die statische Datenmaskierung gelten die folgenden Einschränkungen:

- Für die statische Datenmaskierung werden keine Datenbanken mit [temporären Tabellen](../../relational-databases/tables/temporal-tables.md) unterstützt.

- Mit der statischen Datenmaskierung können keine [speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md) maskiert werden.

- Mit der statischen Datenmaskierung können keine [berechneten Spalten](../../relational-databases/tables/specify-computed-columns-in-a-table.md) und [Identitätsspalten](../../t-sql/statements/create-table-transact-sql-identity-property.md) maskiert werden.

- Die statische Datenmaskierung unterstützt keine Hyperscaledatenbanken von Azure SQL-Datenbank.

- Bei der statischen Datenmaskierung werden die Datentypen „geometry“ und „geography“ nicht unterstützt. 

Außerdem gibt es drei Beschränkungen bei der statischen Datenmaskierung:

- Die statische Datenmaskierung aktualisiert keine [Histogrammstatistiken](../../relational-databases/statistics/statistics.md). Daher kann die maskierte Kopie der Datenbank weiterhin vertrauliche Daten in den Histogrammstatistiken enthalten, nachdem die statische Datenmaskierung durchgeführt wurde. Sie können [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) ausführen, um das Problem zu beheben. 

- Wenn die statische Datenmaskierung einen Fehler zurückgibt, werden alle Maskierungsvorgänge angehalten. Die Kopie der Datenbank wird nicht gelöscht und kann vertrauliche Informationen enthalten. Der Benutzer muss die Kopie der Datenbank selbst löschen, wenn die statische Datenmaskierung einen Fehler zurückgibt. 

- Nur SQL Server: Die [Datendatei(en)](../../relational-databases/databases/database-files-and-filegroups.md) und die [Protokolldatei](../../relational-databases/logs/the-transaction-log-sql-server.md) können weiterhin Teile von vertraulichen Daten im nicht zugeordneten Arbeitsspeicher enthalten, nachdem die statische Datenmaskierung durchgeführt wurde. Diese vertraulichen Daten können mit einem Hexadezimal-Editor abgerufen werden, wenn Zugriff auf die Datendatei(en) und die Protokolldatei besteht.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Dynamische Datenmaskierung](../../relational-databases/security/dynamic-data-masking.md)   
 [Erste Schritte mit der statischen Datenmaskierung in SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-static-data-masking-get-started/)  
