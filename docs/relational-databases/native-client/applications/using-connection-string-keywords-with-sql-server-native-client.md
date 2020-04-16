---
title: Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86e615d22284c5e22f3c6281caa683becfc35bb0
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388587"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei einigen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client APIs werden Verbindungszeichenfolgen zur Angabe von Verbindungsattributen verwendet. Verbindungszeichenfolgen sind Listen von Schlüsselwörtern und zugehörigen Werten. Jedes Schlüsselwort bezeichnet ein spezielles Verbindungsattribut.  

> [!IMPORTANT]
> Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI) ist weiterhin veraltet, und es wird nicht empfohlen, ihn für neue Entwicklungsarbeiten zu verwenden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.    
> Weitere Informationen finden Sie unter [Verwenden von Verbindungszeichenfolgenschlüsselwörtern mit OLE DB Driver for SQL Server](../../../connect/oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).

> [!NOTE]
> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lässt aus Gründen der Abwärtskompatibilität Mehrdeutigkeit in Verbindungszeichenfolgen zu (einige Schlüsselwörter können beispielsweise mehrmals angegeben werden, und Konflikt verursachende Schlüsselwörter sind unter Umständen zulässig, wenn Konflikte anhand der Position oder Rangfolge aufgelöst werden). Es empfiehlt sich beim Ändern von Anwendungen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden, um eine Abhängigkeit von der Mehrdeutigkeit von Verbindungszeichenfolgen zu umgehen.  
  
 In den folgenden Abschnitten werden die Schlüsselwörter beschrieben, die mit dem OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, dem ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und ADO (ActiveX Data Objects) verwendet werden können, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als Datenanbieter verwendet wird.  
  
## <a name="odbc-driver-connection-string-keywords"></a>ODBC-Treiberverbindungszeichenfolge-Schlüsselwörter  
 ODBC-Anwendungen verwenden Verbindungszeichenfolgen als Parameter für die [SqlDriverConnect-](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) und [SQLBrowseConnect-Funktionen.](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
 Die für ODBC verwendeten Verbindungszeichenfolge haben folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in geschweifte Klammern eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Attributwerte andere Zeichen als alphanumerische Zeichen enthalten. Da die erste rechte geschweifte Klammer als Endzeichen des Werts interpretiert wird, können Werte keine rechten geschweiften Klammern enthalten.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die in einer ODBC-Verbindungszeichenfolge verwendet werden können.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|**Addr**|Synonym für "Address".|  
|**Adresse**|Die Netzwerkadresse des Servers, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird. **Address** ist normalerweise der Netzwerkname des Servers, kann jedoch auch ein anderer Name sein, beispielsweise der einer Pipe, einer IP-Adresse oder eines TCP/IP-Ports und einer Socketadresse.<br /><br /> Wenn Sie eine IP-Adresse angeben, stellen Sie im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager sicher, dass die Protokolle für TCP/IP oder Named Pipes aktiviert sind.<br /><br /> Der Wert von **Address** hat Vorrang vor dem Wert, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der bei Verwendung von Native Client an **Server** in ODBC-Verbindungszeichenfolgen übergeben wird. Beachten Sie `Address=;` außerdem, dass eine Verbindung mit `Address= ;, Address=.;`dem `Address=localhost;`im `Address=(local);` **Schlüsselwort Server** angegebenen Server hergestellt wird, während , und alle eine Verbindung zum lokalen Server herstellen.<br /><br /> Die vollständige Syntax für das **Address**-Schlüsselwort ist folgendermaßen:<br /><br /> [_Protokoll_**:**]*Address*[**,**_port &#124;\pipe\pipename_]<br /><br /> *Protokoll* kann Folgendes sein: **tcp** (TCP/IP), **lpc** (Shared Memory) oder **np** (Named Pipes). Weitere Informationen zu Protokollen finden Sie unter [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Wenn weder *das Protokoll* noch das **Schlüsselwort Network** angegeben ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet Native Client die in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager angegebene Protokollreihenfolge.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.|  
|**AnsiNPW**|Bei Angabe von "yes" verwendet der Treiber die im ANSI-Standard definierten Verhaltensweisen zum Behandeln von NULL-Vergleichen, Auffüllung mit Zeichendaten, Warnungen und NULL-Verkettungen. Bei Angabe von "no", werden die im ANSI-Standard definierten Verhaltensweisen nicht verwendet. Weitere Informationen zu ANSI NPW-Verhalten finden Sie unter [Auswirkungen von ISO-Optionen](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**App**|Name der Anwendung, [die SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) aufruft (optional). Falls angegeben, wird dieser Wert in der Spalte **master.dbo.sysprocesses** **program_name** gespeichert und von [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) und den [APP_NAME-Funktionen](../../../t-sql/functions/app-name-transact-sql.md) zurückgegeben.|  
|**ApplicationIntent**|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**. Der Standardwert lautet **ReadWrite**.  Beispiel:<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> Weitere Informationen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Native Client für finden Sie unter [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|Name der primären Datei einer anfügbaren Datenbank. Geben Sie den vollständigen Pfad an, und versehen Sie sämtliche umgekehrten Schrägstriche (\) mit Escapezeichen, wenn eine C-Zeichenfolgenvariable verwendet wird:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Diese Datenbank wird angefügt und als Standarddatenbank für die Verbindung verwendet. Um **AttachDBFileName** verwenden zu können, müssen Sie auch den Datenbanknamen entweder im [Parameter SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) DATABASE oder im SQL_COPT_CURRENT_CATALOG-Verbindungsattribut angeben. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an. Die angefügte Datenbank wird standardmäßig für die Verbindung verwendet.|  
|**AutoTranslate**|Bei der Angabe von "yes" werden ANSI-Zeichenfolgen übersetzt, die zwischen Client und Server übermittelt werden, indem sie über Unicode konvertiert werden, um so Probleme bei der Zuordnung von Sonderzeichen zwischen den Codeseiten auf Client und Server zu minimieren.<br /><br /> ClientSQL_C_CHAR Daten, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die an eine **char**-, **varchar**- oder **Textvariable,** einen Parameter oder eine Spalte gesendet werden, mithilfe der ANSI-Codepage (ACP) des Clients von Zeichen in Unicode konvertiert und dann von Unicode in ein Zeichen konvertiert werden.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**char**, **varchar**oder **Textdaten,** die an einen Client gesendet werden SQL_C_CHAR Variable wird mit dem Server ACP von Zeichen in Unicode konvertiert und dann mit dem Client ACP von Unicode in ein Zeichen konvertiert.<br /><br /> Diese Konvertierungen werden vom ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client auf dem Client durchgeführt. Dies erfordert, dass auf dem Client die gleiche ACP verfügbar ist, die auf dem Server verwendet wird.<br /><br /> Diese Einstellungen haben keine Auswirkungen auf die Konvertierungen, die für diese Übertragungen stattfinden:<br /><br /> \*Unicode SQL_C_WCHAR Clientdaten, die an **char**, **varchar**oder **Text** auf dem Server gesendet werden.<br /><br /> &#42; **char**-, **varchar**oder **Textserverdaten,** die an eine Unicode-SQL_C_WCHAR-Variable auf dem Client gesendet werden.<br /><br /> \*ANSI SQL_C_CHAR Clientdaten, die an Unicode **nchar**, **nvarchar**oder **ntext** auf dem Server gesendet werden.<br /><br /> \*Unicode **nchar**, **nvarchar**oder **ntext** Serverdaten, die an eine ANSI SQL_C_CHAR-Variable auf dem Client gesendet werden.<br /><br /> Bei Angabe von "no" wird keine Zeichenübersetzung durchgeführt.<br /><br /> Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber übersetzt das ANSI-Zeichen des Clients nicht SQL_C_CHAR Daten, die an **char,** **varchar**oder **Textvariablen,** Parameter oder Spalten auf dem Server gesendet werden. Es wird keine Übersetzung für **char**- **varchar**oder **Textdaten** durchgeführt, die vom Server an SQL_C_CHAR Variablen auf dem Client gesendet werden.<br /><br /> Wenn der Client und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterschiedliche ACPs verwenden, können Sonderzeichen falsch interpretiert werden.|  
|**Datenbank**|Der Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standarddatenbank, die für die Verbindung verwendet wird. Wenn **Datenbank** nicht angegeben ist, wird die für die Anmeldung definierte Standarddatenbank verwendet. Die Standarddatenbank der ODBC-Datenquelle überschreibt die für die Anmeldung definierte Standarddatenbank. Die Datenbank muss eine vorhandene Datenbank sein, es sei **denn, AttachDBFileName** wird ebenfalls angegeben. Wenn **AttachDBFileName** ebenfalls angegeben ist, wird die primäre Datei, auf die sie verweist, angefügt und dem von **Database**angegebenen Datenbanknamen angezeigt.|  
|**Treiber**|Name des Treibers, der von [SQLDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md)zurückgegeben wird. Der Schlüsselwortwert für den ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lautet "{SQL Server Native Client 11.0}". Das **Schlüsselwort Server** ist erforderlich, wenn **Driver** angegeben ist und **DriverCompletion** auf SQL_DRIVER_NOPROMPT festgelegt ist.<br /><br /> Weitere Informationen zu Treibernamen finden Sie unter [Verwenden des SQL Server Native Client Header s.](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)|  
|**Dsn**|Der Name einer vorhandenen ODBC-Benutzer- oder Systemdatenquelle. Dieses Schlüsselwort überschreibt alle Werte, die in den Schlüsselwörtern **Server**, **Network**und **Address** angegeben werden können.|  
|**Verschlüsseln**|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|**Fallback**|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird vom ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ignoriert.|  
|**Failover_Partner**|Name des Failoverpartnerservers, der verwendet werden soll, wenn keine Verbindung mit dem primären Server hergestellt werden kann.|  
|**FailoverPartnerSPN**|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|**FileDSN**|Der Name einer vorhandenen ODBC-Dateidatenquelle.|  
|**Sprache**|Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprache (optional). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]können Nachrichten für mehrere Sprachen in **sysmessages**speichern. Wenn eine Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit einer mit mehreren Sprachen hergestellt wird, gibt **Language** an, welche Nachrichtengruppe für die Verbindung verwendet wird.|  
|**MARS_Connection**|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung. Gültige Werte sind "yes" und "no". Der Standardwert ist "no".|  
|**MultiSubnetFailover**|Geben Sie immer **multiSubnetFailover=Ja** an, wenn Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem Verfügbarkeitsgruppen-Listener einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz herstellen. **multiSubnetFailover=Ja** konfiguriert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client so, dass eine schnellere Erkennung und Verbindung mit dem (derzeit) aktiven Server bereitgestellt wird. Mögliche Werte sind **Ja** und **Nein**. Der Standardwert ist **Nein**. Beispiel:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Weitere Informationen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Native Client für finden Sie unter [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**netto**|Synonym für "Network".|  
|**Netzwerk**|Gültige Werte sind **dbnmpntw** (Named Pipes) und **dbmssocn** (TCP/IP).<br /><br /> Es ist ein Fehler, sowohl **Network** einen Wert für das Network-Schlüsselwort als auch ein Protokollpräfix für das **Server-Schlüsselwort** anzugeben.|  
|**Pwd**|Das Kennwort für das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldekonto, das im UID-Parameter angegeben ist. **PWD** muss nicht angegeben werden, wenn die Anmeldung über`Trusted_Connection = yes`ein NULL-Kennwort verfügt oder wenn die Windows-Authentifizierung ( verwendet wird).|  
|**QueryLog_On**|Bei Angabe von "yes", wird die Protokollierung von langwierigen Abfragen für die Verbindung aktiviert. Bei Angabe von "no" werden keine Daten über langwierige Abfragen protokolliert.|  
|**QueryLogFile**|Vollständiger Pfad- und Dateiname einer Datei, die zur Protokollierung von Daten über Abfragen mit langer Ausführungsdauer verwendet werden soll.|  
|**QueryLogTime**|Ziffernzeichenfolge, die den Schwellenwert (in Millisekunden) zum Protokollieren von langwierigen Abfragen angibt. Jede Abfrage, die nicht innerhalb eines gewissen Zeitraums eine Antwort vom Server erhält, wird in die Protokolldatei für Abfragen langer Ausführungsdauer geschrieben.|  
|**QuotedId**|Bei Angabe von "yes" wird QUOTED_IDENTIFIER für die Verbindung auf ON festgelegt, und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befolgt die ISO-Regeln hinsichtlich der Verwendung von Anführungszeichen in SQL-Anweisungen. Andernfalls wird QUOTED_IDENTIFIERS für die Verbindung auf OFF gesetzt. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befolgt anschließend die [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Legacyregeln im Hinblick auf die Verwendung von Anführungszeichen in SQL-Anweisungen. Weitere Informationen finden Sie unter [Effekte von ISO-Optionen](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**Regional**|Bei Angabe von "yes" verwendet der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Clienteinstellungen, wenn Währungs-, Datums- oder Zeitdaten in Zeichendaten konvertiert werden. Die Konvertierung ist unidirektional. Der Treiber erkennt nur ODBC-Standardformate in zu konvertierenden Datumszeichenfolgen oder Währungswerten, beispielsweise Parameter in einer INSERT- oder UPDATE-Anweisung. Bei Angabe von "no" verwendet der Treiber ODBC-Standardzeichenfolgen zur Darstellung von Währungs-, Datums- und Zeitdaten, die in Zeichendaten konvertiert werden.|  
|**SaveFile**|Der Name einer ODBC-Datenquellendatei, in der die Attribute der aktuellen Verbindung gespeichert werden, wenn die Verbindung erfolgreich hergestellt wurde.|  
|**Server**|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz. Als Wert muss entweder der Name eines Servers im Netzwerk, eine IP-Adresse oder der Aliasname eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Managers angegeben werden.<br /><br /> Das **Address**-Schlüsselwort setzt das **Server**-Schlüsselwort außer Kraft.<br /><br /> Sie können eine Verbindung mit der Standardinstanz auf dem lokalen Server herstellen, indem Sie eine der folgenden Optionen angeben:<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** _Instanzname_ **;**<br /><br /> Weitere Informationen zur LocalDB-Unterstützung finden Sie unter [SQL Server Native Client Support for LocalDB](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md).<br /><br /> Um eine benannte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Instanz **\\**von anzugeben, fügen Sie _InstanceName_an.<br /><br /> Ohne Angabe eines Servers wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Wenn Sie eine IP-Adresse angeben, stellen Sie im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager sicher, dass die Protokolle für TCP/IP oder Named Pipes aktiviert sind.<br /><br /> Die vollständige Syntax für das **Server**-Schlüsselwort ist folgendermaßen:<br /><br /> **Server=**[_Protokoll_**:**]*Server*[**,**_Port_]<br /><br /> *Protokoll* kann Folgendes sein: **tcp** (TCP/IP), **lpc** (Shared Memory) oder **np** (Named Pipes).<br /><br /> Im folgenden Beispiel wird die Angabe einer Named Pipe veranschaulicht:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Diese Zeile gibt das Named Pipe-Protokoll, eine Named Pipe auf dem lokalen Computer (`\\.\pipe`), den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz (`MSSQL$MYINST01`) und den Standardnamen der Named Pipe (`sql/query`) an.<br /><br /> Wenn weder ein *Protokoll* noch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] das **Network-Schlüsselwort** angegeben [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist, verwendet Native Client die in Configuration Manager angegebene Protokollreihenfolge.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.<br /><br /> Leerzeichen werden am Anfang des **Server** Werts ignoriert, der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in ODBC-Verbindungszeichenfolgen an Server übergeben wird, wenn Native Client verwendet wird.|  
|**ServerSPN**|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|**StatsLog_On**|Durch die Angabe von "yes" wird die Aufzeichnung von Leistungsdaten zum ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native aktiviert. Wenn "no" angegeben wird, sind die Leistungsdaten zum ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client nicht für die Verbindung verfügbar.|  
|**StatsLogFile**|Der vollständige Pfad- und Dateiname einer Datei, die zum Aufzeichnen der statistischen Daten zur Leistung des ODBC-Treibers von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet werden soll.|  
|**Trusted_Connection**|Durch die Angabe von "yes" wird der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, den Windows-Authentifizierungsmodus zur Überprüfung der Anmeldung zu verwenden. Andernfalls wird der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und ein Kennwort zur Überprüfung der Anmeldung zu verwenden, und in diesem Fall müssen die Schlüsselwörter UID und PWD angegeben werden.|  
|**Trustservercertificate**|Bei Verwendung mit **Encrypt**aktiviert die Verschlüsselung mithilfe eines selbstsignierten Serverzertifikats.|  
|**UID**|Ein gültiges [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldekonto. Bei Verwendung der Windows-Authentifizierung muss nicht UID angegeben werden.|  
|**UseProcForPrepare**|Dieses Schlüsselwort ist veraltet, und seine Einstellung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird vom Native Client ODBC-Treiber ignoriert.|  
|**WSID**|Die ID der Arbeitsstation. Normalerweise ist dies der Netzwerkname des Computers, auf dem sich die Anwendung befindet (optional). Wenn angegeben, wird dieser Wert im **Hostnamen** der Spalte **master.dbo.sysprocesses** gespeichert und von [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) und der [HOST_NAME-Funktion](../../../t-sql/functions/host-name-transact-sql.md) zurückgegeben.|  
  
> **HINWEIS:** Regionale Konvertierungseinstellungen gelten für Währungs-, Numerische, Datums- und Zeitdatentypen. Die Konvertierungseinstellung gilt nur für Ausgabekonvertierungen und ist nur sichtbar, wenn Währungs-, Zahlen-, Datums- oder Uhrzeitwerte in Zeichenfolgen konvertiert werden.  
  
 Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client verwendet die für den aktuellen Benutzer geltenden Registrierungseinstellungen für das Gebietsschema. Der Treiber berücksichtigt das Gebietsschema des aktuellen Threads nicht, wenn die Anwendung es nach der Verbindung festlegt, indem er z. B. **SetThreadLocale aufruft.**  
  
 Das Verändern des regionalen Verhaltens einer Datenquelle kann Anwendungsfehler verursachen. Eine Anwendung, die Datumszeichenfolgen analysiert und erwartet, dass Datumszeichenfolgen wie von ODBC definiert angezeigt werden, könnte durch die Änderung dieses Werts beeinträchtigt werden.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Verbindungszeichenfolgen-Schlüsselwörter für den OLE DB-Anbieter  
 OLE DB-Anwendungen können Datenquellenobjekte auf zweierlei Weise initialisieren:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Im ersten Fall kann die Anbieterzeichenfolge zum Initialisieren der Verbindungseigenschaften verwendet werden, indem die DBPROP_INIT_PROVIDERSTRING-Eigenschaft im DBPROPSET_DBINIT-Eigenschaftensatz festgelegt wird. Im zweiten Fall kann eine Initialisierungszeichenfolge an die **IDataInitialize::GetDataSource**-Methode übergeben werden, um die Verbindungseigenschaften zu initialisieren. Beide Methoden initialisieren die gleichen OLE DB-Verbindungseigenschaften, es werden jedoch andere Sätze von Schlüsselwörtern verwendet. Die von **IDataInitialize::GetDataSource** verwendeten Schlüsselwörter entsprechen mindestens der Beschreibung der in der Gruppe der Initialisierungseigenschaften enthaltenen Eigenschaften.  
  
 Bei jeder Anbieterzeichenfolgeneinstellung, für die eine zugehörige OLE DB-Eigenschaft vorhanden ist, die auf einen bestimmten Standardwert festgelegt ist oder auf einen spezifischen Wert festgelegt wird, überschreibt der OLE DB-Eigenschaftswert die Einstellung in der Anbieterzeichenfolge.  
  
 Für boolesche Eigenschaften, die in Anbieterzeichenfolgen über DBPROP_INIT_PROVIDERSTRING-Werte festgelegt werden, werden die Werte "yes" und "no" angegeben. Für boolesche Eigenschaften, die in Initialisierungszeichenfolgen über **IDataInitialize::GetDataSource** festgelegt werden, werden die Werte TRUE und FALSE angegeben.  
  
 In Anwendungen, in denen **IDataInitialize::GetDataSource** verwendet wird, können auch die Schlüsselwörter für **IDBInitialize::Initialize** verwendet werden, allerdings nur für Eigenschaften, die nicht über einen Standardwert verfügen. Wenn eine Anwendung sowohl das **IDataInitialize::GetDataSource**-Schlüsselwort als auch das **IDBInitialize::Initialize**-Schlüsselwort in der Initialisierungszeichenfolge angibt, dann wird die **IDataInitialize::GetDataSource**-Schlüsselworteinstellung verwendet. Es wird dringend empfohlen, dass Anwendungen keine **IDBInitialize::Initialize**-Schlüsselwörter in **IDataInitialize:GetDataSource**-Verbindungszeichenfolgen verwenden, da dieses Verhalten in künftigen Versionen möglicherweise nicht beibehalten wird.  
  
> [!NOTE]  
>  Eine von **IDataInitialize::GetDataSource** übergebene Verbindungszeichenfolge wird in Eigenschaften konvertiert und mithilfe von **IDBProperties::SetProperties** angewendet. Wenn Komponentendienste die Eigenschaftenbeschreibung in **IDBProperties::GetPropertyInfo** gefunden haben, wird diese Eigenschaft als eigenständige Eigenschaft angewendet. Andernfalls wird sie mithilfe der DBPROP_PROVIDERSTRING-Eigenschaft angewendet. Wenn Sie z. B. die Verbindungszeichenfolge **Datenquelle=Server1;Server=Server2** angeben, wird **Datenquelle** als Eigenschaft festgelegt, aber **Server** wird in einer Anbieterzeichenfolge verwendet.  
  
 Wenn Sie mehrere Instanzen einer anbieterspezifischen Eigenschaft angeben, wird der erste Wert der ersten Eigenschaft verwendet.  
  
 Für Verbindungszeichenfolgen, die in OLE DB-Anwendungen unter Verwendung von DBPROP_INIT_PROVIDERSTRING mit **IDBInitialize::Initialize** verwendet werden, gilt die folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in geschweifte Klammern eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Attributwerte andere Zeichen als alphanumerische Zeichen enthalten. Da die erste rechte geschweifte Klammer als Endzeichen des Werts interpretiert wird, können Werte keine rechten geschweiften Klammern enthalten.  
  
 Ein Leerzeichen nach dem Gleichheitszeichen (=) eines Verbindungszeichenfolgen-Schlüsselworts wird als Literal interpretiert. Dies gilt auch, wenn der Wert in Anführungszeichen gesetzt ist.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die mit DBPROP_INIT_PROVIDERSTRING verwendet werden können.  
  
|Schlüsselwort|Initialisierungseigenschaft|BESCHREIBUNG|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Synonym für "Address".|  
|**Adresse**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden Sie in der Beschreibung des **Schlüsselworts Address** ODBC weiter unten in diesem Thema.|  
|**App**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert lautet **ReadWrite**. Weitere Informationen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Native Client für finden Sie unter [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Für die Verwendung von **AttachDBFileName** muss auch der Datenbankname mit dem Schlüsselwort „Database“ für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Automatisches Übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Gültige Werte sind "yes" und "no".|  
|**Datenbank**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus der zu verwendenden Datentypbehandlung an. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|**Verschlüsseln**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Sprache**|SSPROP_INIT_CURRENTLANGUAGE|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprache.|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|**netto**|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|**Netzwerk**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Wenn "no" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|**Pwd**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden Sie in der Beschreibung des **Schlüsselworts Server** ODBC in diesem Thema.|  
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Durch die Angabe von "yes" wird der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, den Windows-Authentifizierungsmodus zur Überprüfung der Anmeldung zu verwenden. Andernfalls wird der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und ein Kennwort zur Überprüfung der Anmeldung zu verwenden, und in diesem Fall müssen die Schlüsselwörter UID und PWD angegeben werden.|  
|**Trustservercertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Der Standardwert lautet "no" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**UID**|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird vom OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ignoriert.|  
|**WSID**|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 Verbindungszeichenfolgen, die von OLE DB-Anwendungen verwendet werden, welche **IDataInitialize::GetDataSource** verwenden, haben die folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Die Verwendung von Eigenschaften muss der jeweils dafür zulässigen Syntax entsprechen.  Beispielsweise verwendet **WSID** geschweifte Klammern (**{}**) als Anführungszeichen, und **Application Name** verwendet einfache (**'**) oder doppelte (**"**) Anführungszeichen. Es können nur Zeichenfolgeneigenschaften in Anführungszeichen gesetzt werden. Wenn Sie versuchen, eine ganze Zahl oder eine aufgezählte Eigenschaft in Anführungszeichen zu setzen, wird der Fehler angezeigt, dass die Verbindungszeichenfolge keiner OLE DB-Spezifikation entspricht.  
  
 Attributwerte können optional in einfache oder doppelte Anführungszeichen gesetzt werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Werte andere Zeichen als alphanumerische Zeichen enthalten. Das verwendete Anführungszeichen kann auch innerhalb von Werten stehen, vorausgesetzt, dass es doppelt angegeben wird.  
  
 Ein Leerzeichen nach dem Gleichheitszeichen (=) eines Verbindungszeichenfolgen-Schlüsselworts wird als Literal interpretiert. Dies gilt auch, wenn der Wert in Anführungszeichen gesetzt ist.  
  
 Wenn eine Verbindungszeichenfolge mehrere der in der folgenden Tabelle aufgeführten Eigenschaften aufweist, wird der Wert der letzten Eigenschaft verwendet.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die mit **IDataInitialize::GetDataSource** verwendet werden können:  
  
|Schlüsselwort|Initialisierungseigenschaft|BESCHREIBUNG|  
|-------------|-----------------------------|-----------------|  
|**Anwendungsname**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert lautet **ReadWrite**. Weitere Informationen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Native Client für finden Sie unter [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Automatisches Übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Current Language**|SSPROP_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|**Datenquelle**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden Sie in der Beschreibung des **Schlüsselworts Server** ODBC weiter unten in diesem Thema.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus der zu verwendenden Datentypbehandlung an. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Datentypen.|  
|**Failoverpartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**Failoverpartner-SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Anfangskatalog**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**Anfangsdateiname**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Um **AttachDBFileName**zu verwenden, müssen Sie auch den Datenbanknamen mit dem Schlüsselwort "Providerzeichenfolge DATABASE" angeben. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Integrierte Sicherheit**|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|**MARS-Verbindung**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden Sie in der Beschreibung des **Schlüsselworts Address** ODBC weiter unten in diesem Thema.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Paketgröße**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**Kennwort**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Sicherheitsinformationen permanent speichern**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn FALSE angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen dauerhaft speichern.|  
|**Anbieter**||Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sollte die Angabe "SQLNCLI11" lauten.|  
|**Server-SPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Trust Server-Zertifikat**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|**Benutzer-ID**|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|**Workstation ID**|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 **Hinweis:** In der Verbindungszeichenfolge legt die Eigenschaft „Old Password“ SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Schlüsselwörter für ActiveX Data Objects (ADO)-Verbindungszeichenfolgen  
 ADO-Anwendungen legen die **ConnectionString**-Eigenschaft von **ADODBConnection**-Objekten fest oder stellen eine Verbindungszeichenfolge als Parameter für die **Open**-Methode von **ADODBConnection**-Objekten bereit.  
  
 In ADO-Anwendungen können auch die Schlüsselwörter für die OLE DB-Methode **IDBInitialize::Initialize** verwendet werden, allerdings nur für Eigenschaften, die nicht über Standardwerte verfügen. Wenn eine Anwendung sowohl ADO-Schlüsselwörter als auch die **IDBInitialize::Initialize**-Schlüsselwörter in der Initialisierungszeichenfolge verwendet, dann wird die ADO-Schlüsselworteinstellung verwendet. Es wird dringend empfohlen, dass Anwendungen nur Schlüsselwörter für ADO-Verbindungszeichenfolgen verwenden.  
  
 Die für ADO verwendeten Verbindungszeichenfolge haben folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in doppelte Anführungszeichen eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Werte andere Zeichen als alphanumerische Zeichen enthalten. Attributwerte dürfen keine doppelten Anführungszeichen enthalten.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die in einer ADO-Verbindungszeichenfolge verwendet werden können.  
  
|Schlüsselwort|Initialisierungseigenschaft|BESCHREIBUNG|  
|-------------|-----------------------------|-----------------|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert lautet **ReadWrite**. Weitere Informationen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Native Client für finden Sie unter [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Anwendungsname**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**Automatisches Übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Current Language**|SSPROP_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|**Datenquelle**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden Sie in der Beschreibung des **Schlüsselworts Server** ODBC in diesem Thema.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus der zu verwendenden Datentypbehandlung an. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|**Failoverpartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**Failoverpartner-SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Anfangskatalog**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**Anfangsdateiname**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Um **AttachDBFileName**zu verwenden, müssen Sie auch den Datenbanknamen mit dem Schlüsselwort "Providerzeichenfolge DATABASE" angeben. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Integrierte Sicherheit**|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|**MARS-Verbindung**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur gültigen Adresssyntax finden **Address** Sie in der Beschreibung des Adress-ODBC-Schlüsselworts in diesem Thema.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Paketgröße**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**Kennwort**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Sicherheitsinformationen permanent speichern**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn "false" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|**Anbieter**||Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sollte die Angabe "SQLNCLI11" lauten.|  
|**Server-SPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|**Trust Server-Zertifikat**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|**Benutzer-ID**|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|**Workstation ID**|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 **Hinweis:** In der Verbindungszeichenfolge legt die Eigenschaft „Old Password“ SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
