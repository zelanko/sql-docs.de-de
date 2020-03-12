---
title: Datums- und Zeitdaten
description: Beschreibt die Verwendung der neuen in SQL Server 2008 eingeführten Datums- und Uhrzeitdatentypen.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 75d8b98726a758e0533053dbdf8d2e03b3bfdf0d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896991"
---
# <a name="date-and-time-data"></a>Datums- und Zeitdaten

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server 2008 bietet neue Datentypen für Datums- und Uhrzeitinformationen. Die neuen Datentypen umfassen getrennte Typen für Datum und Uhrzeit sowie erweiterte Datentypen mit größerem Umfang, mehr Präzision und besserer Berücksichtigung von Zeitzonen. Der Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient>) bietet volle Unterstützung für alle neuen Features der Datenbank-Engine von SQL Server 2008. Sie müssen .NET Framework 3.5 SP1 (oder höher) oder .NET Core 1.0 (oder höher) installieren, um diese neuen Features mit SqlClient nutzen zu können.  
  
SQL Server-Versionen vor SQL Server 2008 hatten nur zwei Datentypen für das Arbeiten mit Datums- und Uhrzeitwerten: `datetime` und `smalldatetime`. Beide Datentypen enthalten sowohl einen Datumswert als auch einen Uhrzeitwert, wodurch es schwierig ist, nur mit den Datums- oder nur mit den Uhrzeitwerten zu arbeiten. Außerdem unterstützen diese Datentypen nur Datumsangaben nach Einführung des gregorianischen Kalenders in England im Jahr 1753. Eine weitere Einschränkung besteht darin, dass diese älteren Datentypen keine Zeitzonen berücksichtigen, was es schwierig macht, mit Daten zu arbeiten, die aus mehreren Zeitzonen stammen.  
  
Eine vollständige Dokumentation der SQL Server-Datentypen finden Sie in der SQL Server-Onlinedokumentation. Informationen zu Datums- und Uhrzeitdaten für Themen auf Einstiegsebene finden Sie unter [Verwenden von Datums- und Uhrzeitdaten](https://go.microsoft.com/fwlink/?LinkID=98361).
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Einführung von Datum/Uhrzeit-Datentypen in SQL Server 2008  
 In der folgenden Tabelle werden die Datums- und Uhrzeit-Datentypen beschrieben.  
  
|SQL Server-Datentyp|BESCHREIBUNG|  
|--------------------------|-----------------|  
|`date`|Der Bereich der gültigen Werte für den `date`-Datentyp reicht vom 1. Januar 0001 bis zum 31. Dezember 9999 mit einer Genauigkeit von einem Tag. Der Standardwert ist der 1. Januar 1900. Die Speichergröße beträgt 3 Byte.|  
|`time`|Der `time`-Datentyp speichert reine Uhrzeitwerte im 24-Stunden-Format. Der `time`-Datentyp hat einen Bereich von 00:00:00.0000000 bis 23:59:59.9999999 mit einer Genauigkeit von 100 Nanosekunden. Der Standardwert ist 00:00:00.0000000 (Mitternacht). Der `time`-Datentyp unterstützt benutzerdefinierte Sekundenbruchteilgenauigkeit, und die Speichergröße variiert je nach angegebener Genauigkeit zwischen 3 und 6 Bytes.|  
|`datetime2`|Der Datentyp `datetime2` kombiniert den Bereich und die Genauigkeit der Datentypen `date` und `time` zu einem einzelnen Datentyp.<br /><br /> Die Standardwerte und Formate für Zeichenfolgenliterale sind identisch mit denen, die in den Datentypen `date` und `time` definiert sind.|  
|`datetimeoffset`|Der `datetimeoffset`-Datentyp besitzt alle Funktionen von `datetime2`, verfügt darüber hinaus aber auch über eine als Abweichung (Offset) von der koordinierten Weltzeit angegebene Zeitzonenangabe. Der Zeitzonenoffset wird wie folgt dargestellt: [+&#124;-] HH:MM. Bei HH handelt es sich um zwei Ziffern im Bereich von 00 bis 24, die die Anzahl der Stunden im Zeitzonenoffset darstellen. Bei MM handelt es sich um zwei Ziffern im Bereich von 00 bis 59, die die Anzahl der zusätzlichen Minuten im Zeitzonenoffset darstellen. Uhrzeitformate werden mit einer Genauigkeit von bis zu 100 Nanosekunden unterstützt. Das obligatorische Plus- oder Minuszeichen gibt an, ob der Zeitzonenoffset von der UTC (Universal Time Coordinate oder Greenwich Mean Time) addiert oder subtrahiert wird, um die Ortszeit zu erhalten.|  
  
> [!NOTE]
>  Weitere Informationen über die Verwendung des `Type System Version`-Schlüsselworts finden Sie unter <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Datumsformat und -reihenfolge  
Wie SQL Server Datums- und Uhrzeitwerte analysiert, hängt nicht nur von der Typsystem- und Serverversion ab, sondern auch von der Standardsprache und den Formateinstellungen des Servers. Eine Datumszeichenfolge, die für die Datumsformate einer Sprache funktioniert, wird möglicherweise nicht erkannt, wenn die Abfrage über eine Verbindung erfolgt, die eine andere Sprach- und Datumsformateinstellung verwendet.  
  
Die Transact-SQL-Anweisung SET LANGUAGE legt implizit das DATEFORMAT fest, das die Reihenfolge der Datumsteile bestimmt. Sie können die Transact-SQL-Anweisung SET DATEFORMAT für eine Verbindung verwenden, um Datumswerte eindeutig zu bestimmen, indem Sie die Datumsteile in der Reihenfolge MTJ, TMJ, JMT, JTM, MJT oder TJM sortieren.  
  
Wenn Sie kein DATEFORMAT für die Verbindung angeben, verwendet SQL Server die der Verbindung zugeordnete Standardsprache. Beispiel: Die Datumszeichenfolge 01/02/03 würde auf einem Server mit der Spracheinstellung „Englisch (USA)“ als MTJ (Januar 2, 2003) und auf einem Server mit der Spracheinstellung „Englisch (UK)“ als TMJ (1. Februar 2003) interpretiert. Das Jahr wird mithilfe der SQL Server-Regel für das Umstellungsjahr bestimmt, die das Umstellungsdatum für die Zuweisung des Jahrhundertwerts definiert. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation unter [Umstellungsjahr für Angaben mit zwei Ziffern (Option)](https://go.microsoft.com/fwlink/?LinkId=120473).  
  
> [!NOTE]
>  Das Datumsformat JTM wird bei der Konvertierung aus einem Zeichenfolgenformat in `date`, `time`, `datetime2` oder `datetimeoffset` nicht unterstützt.  
  
Weitere Informationen zur Interpretation von Datums- und Zeitdaten in SQL Server finden Sie in der SQL Server 2008-Onlinedokumentation unter [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkID=98361).  
  
## <a name="datetime-data-types-and-parameters"></a>Datums- und Uhrzeitdatentypen und -parameter  
Die folgenden Enumerationen wurden <xref:System.Data.SqlDbType> hinzugefügt, um die neuen Datums- und Uhrzeitdatentypen zu unterstützen.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Sie können den Datentyp eines <xref:Microsoft.Data.SqlClient.SqlParameter> mithilfe einer der voranstehenden <xref:System.Data.SqlDbType>-Enumerationen angeben. 

> [!NOTE]
> Sie können die `DbType`-Eigenschaft von `SqlParameter` nicht auf `SqlDbType.Date` festlegen.

Der Typ eines <xref:Microsoft.Data.SqlClient.SqlParameter> kann auch generisch angegeben werden, indem die <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A>-Eigenschaft eines `SqlParameter`-Objekts auf einen bestimmten <xref:System.Data.DbType>-Enumerationswert festgelegt wird. Zur Unterstützung der Datentypen `datetime2` und `datetimeoffset` wurden <xref:System.Data.DbType> die im Folgenden aufgeführten Enumerationswerte hinzugefügt:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
Diese neuen Enumerationen ergänzen die Enumerationen `Date`, `Time` und `DateTime`.  
  
Der Typ eines Microsoft SqlClient-Datenanbieters eines Parameterobjekts wird vom .NET-Typ des Werts des Parameterobjekts oder vom `DbType` des Parameterobjekts hergeleitet. Es wurden keine neuen <xref:System.Data.SqlTypes>-Datentypen eingeführt, um die neuen Datums- und Uhrzeitdatentypen zu unterstützen. In der folgenden Tabelle werden die Zuordnungen zwischen den Datums- und Uhrzeitdatentypen von SQL Server 2008 und den CLR-Datentypen beschrieben.  
  
|SQL Server-Datentyp|.NET-Typ|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|Date|Date|  
|time|System.TimeSpan|Time|Time|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|Datetime|Datetime|  
|smalldatetime|System.DateTime|Datetime|Datetime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter-Eigenschaften  
 In der folgenden Tabelle werden `SqlParameter`-Eigenschaften beschrieben, die für Datums- und Uhrzeitdatentypen relevant sind.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.IsNullable%2A>|Ruft ab oder legt fest, ob ein Wert NULL sein kann. Wenn Sie den Parameterwert NULL an den Server senden, müssen Sie <xref:System.DBNull> anstelle von `null` (`Nothing` in Visual Basic) angeben. Weitere Informationen zu NULL-Werten in Datenbanken finden Sie unter [Behandeln von NULL-Werten](handle-null-values.md).|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Precision%2A>|Ruft die maximale Anzahl von Stellen ab, die verwendet werden, um den Wert darzustellen, oder legt diese fest. Diese Einstellung wird für Datums -und Uhrzeitdatentypen ignoriert.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Scale%2A>|Ruft die Anzahl der Dezimalstellen für die Auflösung des Uhrzeitteils des Werts für `Time`, `DateTime2` und `DateTimeOffset` ab, oder legt diese fest. Der Standardwert ist 0, was bedeutet, dass die tatsächliche Skala vom Wert hergeleitet und an den Server gesendet wird.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Wird für Datums -und Uhrzeitdatentypen ignoriert.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Ruft den Parameterwert ab oder legt ihn fest.|  
  
> [!NOTE]
>  Uhrzeitwerte, die kleiner als 0 oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
### <a name="creating-parameters"></a>Erstellen von Parametern  
Sie können ein <xref:Microsoft.Data.SqlClient.SqlParameter>-Objekt erstellen, indem Sie seinen Konstruktor verwenden oder es zu einer <xref:Microsoft.Data.SqlClient.SqlCommand>.<xref:Microsoft.Data.SqlClient.SqlCommand.Parameters%2A> -Sammlung hinzufügen, indem Sie die `Add`-Methode von <xref:Microsoft.Data.SqlClient.SqlParameterCollection> aufrufen. Die `Add`-Methode verwendet als Eingabe entweder Konstruktorargumente oder ein vorhandenes Parameterobjekt.  
  
Die nächsten Abschnitte in diesem Thema enthalten Beispiele zum Angeben von Datums- und Uhrzeitparametern.
  
### <a name="date-example"></a>Beispiel für „date“  
Das folgende Codefragment zeigt, wie ein `date`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
### <a name="time-example"></a>Beispiel für „time“  
Das folgende Codefragment zeigt, wie ein `time`-Parameter angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Beispiel für datetime2  
Das folgende Codefragment zeigt, wie ein `datetime2`-Parameter mit Datums- und Uhrzeitteilen angegeben wird.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Beispiel für DateTimeOffSet  
Das folgende Codefragment zeigt, wie ein `DateTimeOffSet`-Parameter mit einem Datum, einer Uhrzeit und dem Zeitzonenoffset 0 angegeben werden kann.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
Sie können Parameter auch mithilfe der `AddWithValue`-Methode von <xref:Microsoft.Data.SqlClient.SqlCommand> angeben, wie im folgenden Codefragment gezeigt. Die `AddWithValue`-Methode ermöglicht jedoch nicht, <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> oder <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> für den Parameter anzugeben.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
Der `@date`-Parameter kann den Datentypen `date`, `datetime` oder `datetime2` auf dem Server zugewiesen werden. Wenn Sie mit den neuen `datetime`-Datentypen arbeiten, müssen Sie die <xref:System.Data.SqlDbType>-Eigenschaft des Parameters explizit auf den Datentyp der Instanz festlegen. Das Verwenden von <xref:System.Data.SqlDbType.Variant> oder implizite Bereitstellen von Parameterwerten kann zu Problemen bei der Abwärtskompatibilität der Datentypen `datetime` und `smalldatetime` führen.  
  
Die folgende Tabelle zeigt, welche `SqlDbTypes` von welchen CLR-Typen abgeleitet werden:  
  
|CLR-Datentyp|Abgeleiteter SqlDbType|  
|--------------|------------------------|  
|Datetime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Abrufen von Datums- und Uhrzeitdaten  
In der folgenden Tabelle werden die Methoden zum Abrufen von Datums- und Uhrzeitwerten in SQL Server 2008 beschrieben.  
  
|SqlClient-Methode|BESCHREIBUNG|  
|----------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTime>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Ruft den angegebenen Spaltenwert als <xref:System.DateTimeOffset>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Gibt den Typ zurück, der der zugrunde liegende anbieterspezifische Typ des Felds ist. Gibt für neue Datums- und Uhrzeittypen die gleichen Typen wie `GetFieldType` zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Ruft den Wert der angegebenen Spalte ab. Gibt für die neuen Datums- und Uhrzeittypen die gleichen Typen wie `GetValue` zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Ruft den Spaltenwert als <xref:System.Data.SqlTypes.SqlString> ab. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als `SqlString` ausgedrückt werden können.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Ruft Spaltendaten als ihren standardmäßigen `SqlDbType` ab. Gibt für die neuen Datums- und Uhrzeittypen die gleichen Typen wie `GetValue` zurück.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Ruft die Werte im angegebenen Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetString%2A>|Ruft den Spaltenwert als Zeichenfolge ab, wenn „Type System Version“ auf SQL Server 2005 festgelegt ist. Eine <xref:System.InvalidCastException> tritt auf, wenn die Daten nicht als Zeichenfolge ausgedrückt werden können.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Ruft den angegebenen Spaltenwert als <xref:System.TimeSpan>-Struktur ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>|Ruft den angegebenen Spaltenwert als zugrunde liegenden CLR-Typ ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>|Ruft Spaltenwerte in einem Array ab.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Gibt eine <xref:System.Data.DataTable> zurück, die die Metadaten des Resultsets beschreibt.|  
  
> [!NOTE]
>  Die neue Datums- und Uhrzeitwerte für `SqlDbTypes` werden nicht für Code unterstützt, der in SQL Server prozessintern ausgeführt wird. Eine Ausnahme wird ausgelöst, wenn einer dieser Typen an den Server übergeben wird.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Angeben von Datums- und Uhrzeitwerten als Literale  
Sie können Datums- und Uhrzeitdatentypen angeben, indem Sie eine Vielzahl verschiedener Formate für Literalzeichenfolgen verwenden, die SQL Server dann zur Laufzeit auswertet und in interne Datums-/Uhrzeitstrukturen konvertiert. SQL Server erkennt Datums- und Uhrzeitdaten, die in einfache Anführungszeichen (') eingeschlossen sind. Die folgenden Beispiele veranschaulichen einige Formate:  
  
- Alphabetische Datumsformate wie `'October 15, 2006'`.  
  
- Numerische Datumsformate wie `'10/15/2006'`.  
  
- Ungetrennte Zeichenfolgenformate wie `'20061015'`, die als 15. Oktober 2006 interpretiert werden, wenn Sie das ISO-Standarddatumsformat verwenden.  
  
> [!NOTE]
>  Sie finden die vollständige Dokumentation aller Formate von Literalzeichenfolgen und anderer Features der Datums- und Uhrzeitdatentypen in der SQL Server-Onlinedokumentation.  
  
Uhrzeitwerte, die kleiner als 0 oder größer oder gleich 24 Stunden sind, lösen eine <xref:System.ArgumentException> aus.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Ressourcen in der SQL Server 2008-Onlinedokumentation  
Weitere Informationen zum Arbeiten mit Datums- und Uhrzeitwerten in SQL Server 2008 finden Sie in den folgenden Ressourcen der SQL Server 2008-Onlinedokumentation.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Bietet eine Übersicht über alle Transact-SQL-Datentypen und -Funktionen zur Angabe des Datums und der Uhrzeit.|  
|[Verwenden von Datums- und Uhrzeitdaten](https://go.microsoft.com/fwlink/?LinkId=98361)|Stellt Informationen zu den Datentypen und Funktionen zur Angabe des Datums und der Uhrzeit sowie Beispiele für deren Verwendung bereit.|  
|[Datentypen (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Beschreibt Systemdatentypen in SQL Server 2008.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
