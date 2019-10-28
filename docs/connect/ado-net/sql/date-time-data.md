---
title: Datums- und Zeitdaten
description: Beschreibt, wie die neuen Datums-und Uhrzeit Datentypen verwendet werden, die in SQL Server 2008 eingeführt wurden.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 38626c6c726b9f45bd2d37d5deda480880556856
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452250"
---
# <a name="date-and-time-data"></a>Datums- und Zeitdaten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

In SQL Server 2008 werden neue Datentypen für die Behandlung von Datums-und Uhrzeit Informationen eingeführt. Die neuen Datentypen enthalten separate Typen für Datum und Uhrzeit sowie erweiterte Datentypen mit größerem Bereich, Genauigkeit und Zeit Zonen Bewusstsein. Die Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient>) bieten vollständige Unterstützung für alle neuen Features der SQL Server 2008 Datenbank-Engine. Sie müssen den .NET Framework 3,5 SP1 (oder höher) oder .net Core 1,0 (oder höher) installieren, um diese neuen Features mit SqlClient zu verwenden.  
  
Versionen von SQL Server vor SQL Server 2008 haben nur zwei Datentypen für die Arbeit mit Datums-und Uhrzeitwerten: `datetime` und `smalldatetime`. Beide Datentypen enthalten sowohl einen Datumswert als auch einen Uhrzeitwert, wodurch es schwierig ist, nur mit den Datums- oder nur mit den Uhrzeitwerten zu arbeiten. Außerdem unterstützen diese Datentypen nur Datumsangaben, die nach der Einführung des gregorianischen Kalenders in England in 1753 auftreten. Eine weitere Einschränkung besteht darin, dass diese älteren Datentypen keine Zeit Zonen fähig sind, was die Arbeit mit Daten, die aus mehreren Zeitzonen stammen, erschwert.  
  
Eine umfassende Dokumentation für SQL Server-Datentypen ist in SQL Server-Onlinedokumentation verfügbar. Informationen zu Datums-und Uhrzeit Daten finden [Sie unter Verwenden von Datums-und Uhrzeitdaten](https://go.microsoft.com/fwlink/?LinkID=98361) für Themen auf Einstiegsebene.
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Einführung von Datum/Uhrzeit-Datentypen in SQL Server 2008  
 In der folgenden Tabelle werden die neuen Datums-und Uhrzeit Datentypen beschrieben.  
  
|SQL Server-Datentyp|und Beschreibung|  
|--------------------------|-----------------|  
|`date`|Der Bereich der gültigen Werte für den `date`-Datentyp reicht vom 1. Januar 0001 bis zum 31. Dezember 9999 mit einer Genauigkeit von einem Tag. Der Standardwert ist der 1. Januar 1900. Die Speichergröße beträgt 3 Byte.|  
|`time`|Der `time`-Datentyp speichert reine Uhrzeitwerte im 24-Stunden-Format. Der `time`-Datentyp hat einen Bereich von 00:00:00.0000000 bis 23:59:59.9999999 mit einer Genauigkeit von 100 Nanosekunden. Der Standardwert ist 00:00:00.0000000 (Mitternacht). Der `time`-Datentyp unterstützt benutzerdefinierte Sekundenbruchteilgenauigkeit, und die Speichergröße variiert je nach angegebener Genauigkeit zwischen 3 und 6 Bytes.|  
|`datetime2`|Der `datetime2`-Datentyp kombiniert den Bereich und die Genauigkeit der Datentypen `date` und `time` zu einem einzelnen Datentyp.<br /><br /> Die Standardwerte und Zeichenfolgenliteralformate sind identisch mit denen, die in den Datentypen `date` und `time` definiert sind.|  
|`datetimeoffset`|Der `datetimeoffset`-Datentyp besitzt alle Funktionen von `datetime2`, verfügt darüber hinaus aber auch über eine als Abweichung (Offset) von der koordinierten Weltzeit angegebene Zeitzonenangabe. Der Zeitzonenoffset wird wie folgt dargestellt: [+&#124;-] HH:MM. Bei HH handelt es sich um zwei Ziffern im Bereich von 00 bis 24, die die Anzahl der Stunden im Zeitzonenoffset darstellen. Bei MM handelt es sich um zwei Ziffern im Bereich von 00 bis 59, die die Anzahl der zusätzlichen Minuten im Zeitzonenoffset darstellen. Uhrzeitformate werden mit einer Genauigkeit von bis zu 100 Nanosekunden unterstützt. Das obligatorische +-oder-Vorzeichen gibt an, ob der Zeit Zonen Offset von UTC (Universal Time-Koordinate oder Greenwich Mean Time) hinzugefügt oder davon subtrahiert wird, um die Ortszeit zu erhalten.|  
  
> [!NOTE]
>  Weitere Informationen über die Verwendung des `Type System Version`-Schlüsselworts finden Sie unter <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Datumsformat und Datums Reihenfolge  
Wie SQL Server Datums-und Uhrzeitwerte analysieren, hängt nicht nur von der Typsystem Version und der Server Version ab, sondern auch von der Standardsprache und den Format Einstellungen des Servers. Eine Datums Zeichenfolge, die für die Datumsformate einer Sprache verwendet werden kann, ist möglicherweise nicht erkennbar, wenn die Abfrage von einer Verbindung ausgeführt wird, die eine andere Sprach-und Datumsformat Einstellung verwendet.  
  
Die Transact-SQL-Anweisung Set Language legt implizit das DATEFORMAT fest, das die Reihenfolge der Datums Teile bestimmt. Sie können die Transact-SQL-Anweisung SET DATEFORMAT für eine Verbindung verwenden, um Datumswerte zu unterscheiden, indem Sie die Datums Teile in MDY, DMY, YMD, ydm, MYD oder dym sortieren.  
  
Wenn Sie kein DATEFORMAT für die Verbindung angeben, verwendet SQL Server die Standardsprache, die der Verbindung zugeordnet ist. Eine Datums Zeichenfolge "01/02/03" würde z. b. als MDY (2. Januar 2003) auf einem Server mit der Spracheinstellung USA Englisch und als DMY (1. Februar 2003) auf einem Server mit der Spracheinstellung britisches Englisch interpretiert werden. Das Jahr wird anhand der Regel für das Umstellungs Jahr SQL Server festgelegt, die das Umstellungs Datum zum Zuweisen des Jahrhundert Werts definiert. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation unter [Umstellungsjahr für Angaben mit zwei Ziffern (Option)](https://go.microsoft.com/fwlink/?LinkId=120473).  
  
> [!NOTE]
>  Das ydm-Datumsformat wird nicht unterstützt, wenn aus einem Zeichen folgen Format in `date`, `time`, `datetime2` oder `datetimeoffset`.  
  
Weitere Informationen zur Interpretation von Datums- und Zeitdaten in SQL Server finden Sie in der SQL Server 2008-Onlinedokumentation unter [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkID=98361).  
  
## <a name="datetime-data-types-and-parameters"></a>Datums-/Uhrzeit-Datentypen und-Parameter  
Die folgenden Enumerationen wurden <xref:System.Data.SqlDbType> hinzugefügt, um die neuen Datums-und Uhrzeit Datentypen zu unterstützen.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Sie können den Datentyp eines <xref:Microsoft.Data.SqlClient.SqlParameter> mithilfe einer der voranstehenden <xref:System.Data.SqlDbType>-Enumerationen angeben. 

> [!NOTE]
> Die `DbType`-Eigenschaft einer `SqlParameter` kann nicht auf `SqlDbType.Date` festgelegt werden.

Der Typ eines <xref:Microsoft.Data.SqlClient.SqlParameter> kann auch generisch angegeben werden, indem die <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A>-Eigenschaft eines `SqlParameter`-Objekts auf einen bestimmten <xref:System.Data.DbType>-Enumerationswert festgelegt wird. Zur Unterstützung der Datentypen `datetime2` und `datetimeoffset` wurden <xref:System.Data.DbType> die im Folgenden aufgeführten Enumerationswerte hinzugefügt:  
  
- DbType. datetime2  
  
- DbType. DateTimeOffset  
  
Diese neuen Enumerationen ergänzen die Enumerationen `Date`, `Time` und `DateTime`.  
  
Der Microsoft SqlClient-Datenanbieter Typ eines Parameter Objekts wird vom .NET-Typ des Werts des Parameter Objekts oder vom `DbType` des Parameter Objekts abgeleitet. Es wurden keine neuen <xref:System.Data.SqlTypes> Datentypen eingeführt, um die neuen Datums-und Uhrzeit Datentypen zu unterstützen. In der folgenden Tabelle werden die Zuordnungen zwischen den Datums-und Uhrzeit Datentypen SQL Server 2008 und den CLR-Datentypen beschrieben.  
  
|SQL Server-Datentyp|.NET-Typ|System. Data. SqlDbType|System. Data. DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|date|date|  
|time|System.TimeSpan|Uhrzeit|Uhrzeit|  
|datetime2|System.DateTime|datetime2|datetime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|DATETIME|System.DateTime|datetime|datetime|  
|smalldatetime|System.DateTime|datetime|datetime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter-Eigenschaften  
 In der folgenden Tabelle werden `SqlParameter` Eigenschaften beschrieben, die für Datums-und Uhrzeit Datentypen relevant sind.  
  
|Eigenschaft|und Beschreibung|  
|--------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.IsNullable%2A>|Ruft ab oder legt fest, ob ein Wert NULL-Werte zulässt. Wenn Sie einen NULL-Parameterwert an den Server senden, müssen Sie <xref:System.DBNull> anstatt `null` (`Nothing` in Visual Basic) angeben. Weitere Informationen zu Daten Bank Nullen finden Sie unter [Behandeln von NULL-Werten](handle-null-values.md).|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Precision%2A>|Ruft die maximale Anzahl von Stellen ab, die verwendet werden, um den Wert darzustellen, oder legt diese fest. Diese Einstellung wird für Datums-und Uhrzeit Datentypen ignoriert.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Scale%2A>|Ruft die Anzahl der Dezimalstellen für die Auflösung des Uhrzeitteils des Werts für `Time`, `DateTime2` und `DateTimeOffset` ab, oder legt diese fest. Der Standardwert ist 0. Dies bedeutet, dass die tatsächliche Skala von dem Wert abgeleitet und an den Server gesendet wird.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Wird für Datums-und Uhrzeit Datentypen ignoriert.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
  
> [!NOTE]
>  Zeitwerte, die kleiner als 0 (null) oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
### <a name="creating-parameters"></a>Erstellen von Parametern  
Sie können ein <xref:Microsoft.Data.SqlClient.SqlParameter> Objekt erstellen, indem Sie dessen Konstruktor verwenden oder es einem <xref:Microsoft.Data.SqlClient.SqlCommand> hinzufügen. <xref:Microsoft.Data.SqlClient.SqlCommand.Parameters%2A> Sammlung durch Aufrufen der `Add`-Methode des <xref:Microsoft.Data.SqlClient.SqlParameterCollection>. Die `Add`-Methode übernimmt als Eingabe entweder Konstruktorargumente oder ein vorhandenes Parameter Objekt.  
  
Die nächsten Abschnitte in diesem Thema enthalten Beispiele zum Angeben von Datums-und Uhrzeit Parametern.
  
### <a name="date-example"></a>Beispiel für Datum  
Im folgenden Code Fragment wird veranschaulicht, wie ein `date`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
### <a name="time-example"></a>Zeit Beispiel  
Im folgenden Code Fragment wird veranschaulicht, wie ein `time`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Datetime2-Beispiel  
Im folgenden Code Fragment wird veranschaulicht, wie ein `datetime2`-Parameter mit den Datums-und Uhrzeit Teilen angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>DateTimeOffset-Beispiel  
Das folgende Code Fragment veranschaulicht, wie ein `DateTimeOffSet`-Parameter mit einem Datum, einer Uhrzeit und einem Zeit Zonen Offset von 0 angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
Sie können Parameter auch mit der `AddWithValue`-Methode einer <xref:Microsoft.Data.SqlClient.SqlCommand> angeben, wie im folgenden Code Fragment dargestellt. Die `AddWithValue`-Methode lässt jedoch nicht zu, dass Sie die <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> oder <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> für den Parameter angeben.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
Der `@date`-Parameter kann den Datentypen `date`, `datetime` oder `datetime2` auf dem Server zugewiesen werden. Wenn Sie mit den neuen `datetime`-Datentypen arbeiten, müssen Sie die <xref:System.Data.SqlDbType>-Eigenschaft des Parameters explizit auf den Datentyp der Instanz festlegen. Die Verwendung von <xref:System.Data.SqlDbType.Variant> oder das implizite angeben von Parameterwerten kann zu Problemen mit der Abwärtskompatibilität mit den Datentypen `datetime` und `smalldatetime` führen.  
  
In der folgenden Tabelle wird gezeigt, welche `SqlDbTypes` von welchen CLR-Typen abgeleitet werden:  
  
|CLR-Datentyp|Ableiten von SqlDbType|  
|--------------|------------------------|  
|datetime|SqlDbType. DateTime|  
|TimeSpan|SqlDbType. Time|  
|DateTimeOffset|SqlDbType. DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Abrufen von Datums-und Uhrzeit Daten  
In der folgenden Tabelle werden die Methoden zum Abrufen von Datums- und Uhrzeitwerten in SQL Server 2008 beschrieben.  
  
|SqlClient-Methode|und Beschreibung|  
|----------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTime>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTimeOffset>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Gibt den Typ zurück, bei dem es sich um den zugrunde liegenden anbieterspezifischen Typ für das Feld handelt. Gibt dieselben Typen wie `GetFieldType` für neue Datums-und Uhrzeit Typen zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Ruft den Wert der angegebenen Spalte ab. Gibt dieselben Typen wie `GetValue` für die neuen Datums-und Uhrzeit Typen zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Ruft den Spaltenwert als <xref:System.Data.SqlTypes.SqlString> ab. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als `SqlString` ausgedrückt werden können.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Ruft Spaltendaten als Standard `SqlDbType` ab. Gibt dieselben Typen wie `GetValue` für die neuen Datums-und Uhrzeit Typen zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetString%2A>|Ruft den Spaltenwert als Zeichenfolge ab, wenn „Type System Version“ auf SQL Server 2005 festgelegt ist. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als Zeichenfolge ausgedrückt werden können.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Ruft den angegebenen Spaltenwert als <xref:System.TimeSpan>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>|Ruft den angegebenen Spaltenwert als zugrunde liegenden CLR-Typ ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>|Ruft Spaltenwerte in einem Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Gibt einen <xref:System.Data.DataTable> zurück, der die Metadaten des Resultsets beschreibt.|  
  
> [!NOTE]
>  Die neuen Datums-und Uhrzeit `SqlDbTypes` werden für Code, der in-Process-Vorgänge in SQL Server ausgeführt wird, nicht unterstützt. Eine Ausnahme wird ausgelöst, wenn einer dieser Typen an den Server übermittelt wird.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Angeben von Datums-und Uhrzeitwerten als Literale  
Sie können Datums-und Uhrzeit Datentypen angeben, indem Sie eine Vielzahl unterschiedlicher literalzeichenfolgenformate verwenden, die SQL Server dann zur Laufzeit auswerten und in interne Datums-/uhrzeitstrukturen umwandelt. SQL Server erkennt Datums-und Uhrzeit Daten, die in einfache Anführungszeichen (') eingeschlossen werden. Die folgenden Beispiele veranschaulichen einige Formate:  
  
- Alphabetische Datumsformate, wie z. b. `'October 15, 2006'`.  
  
- Numerische Datumsformate, z. b. `'10/15/2006'`.  
  
- Nicht getrennte Zeichen folgen Formate, wie z. b. `'20061015'`, die als 15. Oktober 2006 interpretiert werden, wenn Sie das ISO-Standard Datumsformat verwenden.  
  
> [!NOTE]
>  Eine vollständige Dokumentation für alle Literalzeichenfolgen-Formate und andere Features der Datums-und Uhrzeit Datentypen finden Sie in SQL Server-Onlinedokumentation.  
  
Zeitwerte, die kleiner als 0 (null) oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Ressourcen in SQL Server 2008-Online Dokumentation  
Weitere Informationen zum Arbeiten mit Datums-und Uhrzeitwerten in SQL Server 2008 finden Sie in den folgenden Ressourcen in SQL Server 2008-Online Dokumentation.  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Bietet eine Übersicht über alle Transact-SQL-Datentypen und -Funktionen zur Angabe des Datums und der Uhrzeit.|  
|[Verwenden von Datums- und Uhrzeitdaten](https://go.microsoft.com/fwlink/?LinkId=98361)|Stellt Informationen zu den Datentypen und Funktionen zur Angabe des Datums und der Uhrzeit sowie Beispiele für deren Verwendung bereit.|  
|[Datentypen (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Beschreibt System Datentypen in SQL Server 2008.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
