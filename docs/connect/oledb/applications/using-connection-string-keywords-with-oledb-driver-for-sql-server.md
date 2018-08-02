---
title: Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 024f014dda25be2d5b9ab01bd6eeffc57c3efcae
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107216"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Einige OLE DB-Treiber für SQL Server-APIs verwenden Verbindungszeichenfolgen,-Verbindungsattributen angeben. Verbindungszeichenfolgen sind Listen von Schlüsselwörtern und zugehörigen Werten. Jedes Schlüsselwort bezeichnet ein spezielles Verbindungsattribut.  
  
> [!NOTE]
> Der OLE DB-Treiber für SQL Server lässt aus Gründen der Abwärtskompatibilität Mehrdeutigkeit in Verbindungszeichenfolgen zu. Einige Schlüsselwörter können also beispielsweise mehrmals angegeben werden, und Konflikt verursachende Schlüsselwörter sind unter Umständen zulässig, wenn Konflikte anhand der Position oder Rangfolge aufgelöst werden. Zukünftige Versionen des OLE DB-Treiber für SQL Server u. u. nicht Mehrdeutigkeit in Verbindungszeichenfolgen zu. Es empfiehlt sich beim Ändern von Anwendungen, den OLE DB-Treiber für SQL Server zu verwenden, um eine Abhängigkeit von der Mehrdeutigkeit von Verbindungszeichenfolgen zu umgehen.  
  
 In den folgenden Abschnitten werden die Schlüsselwörter, die mit dem OLE DB-Treiber für SQL Server und ActiveX Data Objects (ADO) verwendet werden können bei Verwendung von OLE DB-Treiber für SQL Server als Datenanbieter beschrieben.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Verbindungszeichenfolgen-Schlüsselwörter für den OLE DB-Treiber  
 OLE DB-Anwendungen können Datenquellenobjekte auf zweierlei Weise initialisieren:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Im ersten Fall kann die Anbieterzeichenfolge zum Initialisieren der Verbindungseigenschaften verwendet werden, indem die DBPROP_INIT_PROVIDERSTRING-Eigenschaft im DBPROPSET_DBINIT-Eigenschaftensatz festgelegt wird. Im zweiten Fall kann eine Initialisierungszeichenfolge an die **IDataInitialize::GetDataSource**-Methode übergeben werden, um die Verbindungseigenschaften zu initialisieren. Beide Methoden initialisieren die gleichen OLE DB-Verbindungseigenschaften, es werden jedoch andere Sätze von Schlüsselwörtern verwendet. Die von **IDataInitialize::GetDataSource** verwendeten Schlüsselwörter entsprechen mindestens der Beschreibung der in der Gruppe der Initialisierungseigenschaften enthaltenen Eigenschaften.  
  
 Bei jeder Anbieterzeichenfolgeneinstellung, für die eine zugehörige OLE DB-Eigenschaft vorhanden ist, die auf einen bestimmten Standardwert festgelegt ist oder auf einen spezifischen Wert festgelegt wird, überschreibt der OLE DB-Eigenschaftswert die Einstellung in der Anbieterzeichenfolge.  
  
 Für boolesche Eigenschaften, die in Anbieterzeichenfolgen über DBPROP_INIT_PROVIDERSTRING-Werte festgelegt werden, werden die Werte "yes" und "no" angegeben. Für boolesche Eigenschaften, die in Initialisierungszeichenfolgen über **IDataInitialize::GetDataSource** festgelegt werden, werden die Werte TRUE und FALSE angegeben.  
  
 In Anwendungen, in denen **IDataInitialize::GetDataSource** verwendet wird, können auch die Schlüsselwörter für **IDBInitialize::Initialize** verwendet werden, allerdings nur für Eigenschaften, die nicht über einen Standardwert verfügen. Wenn eine Anwendung sowohl das **IDataInitialize::GetDataSource**-Schlüsselwort als auch das **IDBInitialize::Initialize**-Schlüsselwort in der Initialisierungszeichenfolge angibt, dann wird die **IDataInitialize::GetDataSource**-Schlüsselworteinstellung verwendet. Es wird dringend empfohlen, dass Anwendungen keine **IDBInitialize::Initialize**-Schlüsselwörter in **IDataInitialize:GetDataSource**-Verbindungszeichenfolgen verwenden, da dieses Verhalten in künftigen Versionen möglicherweise nicht beibehalten wird.  
  
> [!NOTE]  
>  Eine von **IDataInitialize::GetDataSource** übergebene Verbindungszeichenfolge wird in Eigenschaften konvertiert und mithilfe von **IDBProperties::SetProperties** angewendet. Wenn Komponentendienste die Eigenschaftenbeschreibung in **IDBProperties::GetPropertyInfo** gefunden haben, wird diese Eigenschaft als eigenständige Eigenschaft angewendet. Andernfalls wird sie mithilfe der DBPROP_PROVIDERSTRING-Eigenschaft angewendet. Wenn Sie angeben, dass die Verbindungszeichenfolge z. B. **Data Source = server1; Server = server2**, **Datenquelle** wird als Eigenschaft festgelegt werden, aber **Server** ein Wechsel in eine Anbieterzeichenfolge übernommen.  
  
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
  
|Schlüsselwort|Initialisierungseigenschaft|und Beschreibung|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Synonym für "Address".|  
|**Adresse**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse des Servers, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird. **Address** ist normalerweise der Netzwerkname des Servers, kann jedoch auch ein anderer Name sein, beispielsweise der einer Pipe, einer IP-Adresse oder eines TCP/IP-Ports und einer Socketadresse.<br /><br /> Wenn Sie eine IP-Adresse angeben, stellen Sie im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager sicher, dass die Protokolle für TCP/IP oder Named Pipes aktiviert sind.<br /><br /> Der Wert des **Adresse** hat Vorrang vor den übergebenen Wert **Server** in Verbindungszeichenfolgen, die bei Verwendung von OLE DB-Treiber für SQL Server. Zudem ist zu beachten, dass mit der Angabe `Address=;` eine Verbindung mit dem im **Server**-Schlüsselwort angegebenen Server hergestellt wird. Die Angaben `Address= ;, Address=.;`, `Address=localhost;` und `Address=(local);` führen dagegen zu einer Verbindungsherstellung mit dem lokalen Server.<br /><br /> Die vollständige Syntax für das **Address**-Schlüsselwort ist folgendermaßen:<br /><br /> [*Protokoll ***:**]* Adresse *[**, *** Port &#124;\pipe\pipename*]<br /><br /> *Protokoll* kann Folgendes sein: **tcp** (TCP/IP), **lpc** (Shared Memory) oder **np** (Named Pipes). Weitere Informationen zu Protokollen finden Sie unter [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Wenn weder *Protokoll* noch die **Netzwerk** -Schlüsselwort angegeben ist, OLE DB-Treiber für SQL Server verwendet die Protokollreihenfolge im angegebenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurations-Manager.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert ist **"ReadWrite"**. Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Für die Verwendung von **AttachDBFileName** muss auch der Datenbankname mit dem Schlüsselwort „Database“ für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Automatisch übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Gültige Werte sind "yes" und "no".|  
|**Datenbank**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus des Datentyps, die die Verarbeitung verwenden. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**Sprache**|SSPROPT_INIT_CURRENTLANGUAGE|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprache.|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Geben Sie immer **MultiSubnetFailover=Yes** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failoverclusterinstanz herstellen. **MultiSubnetFailover=Yes** konfiguriert den OLE DB-Treiber für SQL Server, um eine schnellere Erkennung sowie die Verbindung zu dem (gerade) aktiven Server zu gewährleisten. Mögliche Werte sind **Yes** und **No**. Der Standardwert ist **No**. Zum Beispiel:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Wenn "no" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|**PWD**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz. Als Wert muss entweder der Name eines Servers im Netzwerk, eine IP-Adresse oder der Aliasname eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Managers angegeben werden.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Die **Adresse** Schlüsselwort überschreibt die **Server** Schlüsselwort.<br /><br /> Sie können eine Verbindung mit der Standardinstanz auf dem lokalen Server herstellen, indem Sie eine der folgenden Optionen angeben:<br /><br /> **Server =;**<br /><br /> **Server =.;**<br /><br /> **Server=(Local);;**<br /><br /> **Server=(Local);;**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(LocalDB)\\**  *Instancename* **;**<br /><br /> Weitere Informationen zur Unterstützung von LocalDB finden Sie unter [OLE DB-Treiber für SQL Server-Unterstützung für LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Angeben eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], fügen Sie  **\\ ***InstanceName *.<br /> <br /> Kein Server angegeben ist, wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt. <br /> <br /> Wenn Sie eine IP-Adresse angeben, stellen Sie sicher, dass die TCP/IP oder den named Pipes, in aktiviert sind [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurations-Manager.<br /> <br /> Die vollständige Syntax für die **Server** -Schlüsselwort ist folgendermaßen:<br /> <br /> **Server =**[* Protokoll***:**] *Server*[**, *** Port*]<br /><br /> *Protokoll* kann Folgendes sein: **tcp** (TCP/IP), **lpc** (Shared Memory) oder **np** (Named Pipes).<br /><br /> Im folgenden Beispiel wird die Angabe einer Named Pipe veranschaulicht:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Diese Zeile gibt das Named Pipe-Protokoll, eine Named Pipe auf dem lokalen Computer (`\\.\pipe`), den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz (`MSSQL$MYINST01`) und den Standardnamen der Named Pipe (`sql/query`) an.<br /><br /> Wenn weder ein *Protokoll* noch die **Netzwerk** -Schlüsselwort angegeben ist, OLE DB-Treiber für SQL Server verwendet die Protokollreihenfolge im angegebenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurations-Manager.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.<br /><br /> Leerzeichen werden ignoriert, am Anfang der an übergebene Wert **Server** in Verbindungszeichenfolgen, die bei Verwendung von OLE DB-Treiber für SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Wenn "Ja", weist der OLE DB-Treiber für SQL Server zum Windows-Authentifizierungsmodus zur Überprüfung der Anmeldung zu verwenden. Andernfalls wird der OLE DB-Treiber für SQL Server angewiesen, einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und ein Kennwort zur Überprüfung der Anmeldung zu verwenden. In diesem Fall müssen die Schlüsselwörter UID und PWD angegeben werden.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Der Standardwert lautet "no" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**UID**|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|Steuert, wie die Metadaten abgerufen werden, bei der Verbindung [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und höher. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".<br /><br />Der OLE DB-Treiber für SQL Server verwendet standardmäßig [Sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) und [Sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) gespeicherte Prozeduren zum Abrufen von Metadaten. Diese gespeicherten Prozeduren weisen einige Einschränkungen (z. B. sie fehl, wenn auf temporäre Tabellen). Festlegen von **UseFMTONLY** auf "yes" weist den Treiber mit [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) zum Abrufen von Metadaten stattdessen.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird von der OLE DB-Treiber für SQL Server ignoriert.|  
|**WSID**|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 Verbindungszeichenfolgen, die von OLE DB-Anwendungen verwendet werden, welche **IDataInitialize::GetDataSource** verwenden, haben die folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Die Verwendung von Eigenschaften muss der jeweils dafür zulässigen Syntax entsprechen.  Z. B. **Angaben für WSID** geschweifte Klammern (**{}**) Anführungszeichen und **Anwendungsname** verwendet einzelne (**"**) oder Double (**"**) Anführungszeichen. Es können nur Zeichenfolgeneigenschaften in Anführungszeichen gesetzt werden. Wenn Sie versuchen, eine ganze Zahl oder eine aufgezählte Eigenschaft in Anführungszeichen zu setzen, wird der Fehler angezeigt, dass die Verbindungszeichenfolge keiner OLE DB-Spezifikation entspricht.  
  
 Attributwerte können optional in einfache oder doppelte Anführungszeichen gesetzt werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Werte andere Zeichen als alphanumerische Zeichen enthalten. Das verwendete Anführungszeichen kann auch innerhalb von Werten stehen, vorausgesetzt, dass es doppelt angegeben wird.  
  
 Ein Leerzeichen nach dem Gleichheitszeichen (=) eines Verbindungszeichenfolgen-Schlüsselworts wird als Literal interpretiert. Dies gilt auch, wenn der Wert in Anführungszeichen gesetzt ist.  
  
 Wenn eine Verbindungszeichenfolge mehrere der in der folgenden Tabelle aufgeführten Eigenschaften aufweist, wird der Wert der letzten Eigenschaft verwendet.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die mit **IDataInitialize::GetDataSource** verwendet werden können:  
  
|Schlüsselwort|Initialisierungseigenschaft|und Beschreibung|  
|-------------|-----------------------------|-----------------|  
|**ApplicationName**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert ist **"ReadWrite"**. Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Automatisch übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des **Server**-Schlüsselworts.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus des Datentyps, die die Verarbeitung verwenden. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Datentypen.|  
|**Failoverpartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**Anfangskatalog**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**Anfangsdateiname**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Für die Verwendung von **AttachDBFileName** muss auch der Datenbankname mit dem Schlüsselwort DATABASE für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Integrierte Sicherheit**|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|**MARS-Verbindung**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Geben Sie immer **MultiSubnetFailover=True** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failoverclusterinstanz herstellen. **MultiSubnetFailover=TRUE** konfiguriert den OLE DB-Treiber für SQL Server so, dass der (derzeit) aktive Server schneller erkannt und eine Verbindung zu ihm hergestellt wird. Mögliche Werte sind **True** und **False**. Der Standardwert ist **False**. Zum Beispiel:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des **Address**-Schlüsselworts.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**Kennwort**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn FALSE angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen dauerhaft speichern.|  
|**Anbieter**||Für OLE DB-Treiber für SQL Server muss dies "MSOLEDBSQL" sein.|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Steuert, wie die Metadaten abgerufen werden, bei der Verbindung [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und höher. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.<br /><br />Der OLE DB-Treiber für SQL Server verwendet standardmäßig [Sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) und [Sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) gespeicherte Prozeduren zum Abrufen von Metadaten. Diese gespeicherten Prozeduren weisen einige Einschränkungen (z. B. sie fehl, wenn auf temporäre Tabellen). Festlegen von **FMTONLY verwenden** auf "true" weist den Treiber mit [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) zum Abrufen von Metadaten stattdessen.|  
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
  
|Schlüsselwort|Initialisierungseigenschaft|und Beschreibung|  
|-------------|-----------------------------|-----------------|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.<br /><br /> Der Standardwert ist **"ReadWrite"**. Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**ApplicationName**|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|**Automatisch übersetzen**|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|**Data Source**|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des **Server**-Schlüsselworts.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus der zu verwendenden Datentypbehandlung an. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|**Failoverpartner**|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**Anfangskatalog**|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|**Anfangsdateiname**|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Für die Verwendung von **AttachDBFileName** muss auch der Datenbankname mit dem Schlüsselwort DATABASE für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|**Integrierte Sicherheit**|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|**MARS-Verbindung**|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Geben Sie immer **MultiSubnetFailover=True** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failoverclusterinstanz herstellen. **MultiSubnetFailover=TRUE** konfiguriert den OLE DB-Treiber für SQL Server so, dass der (derzeit) aktive Server schneller erkannt und eine Verbindung zu ihm hergestellt wird. Mögliche Werte sind **True** und **False**. Der Standardwert ist **False**. Zum Beispiel:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Weitere Informationen zu OLE DB-Treiber für SQL Server Unterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [OLE DB-Treiber für SQL Server-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des **Address**-Schlüsselworts.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|**Kennwort**|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn "false" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|**Anbieter**||Für OLE DB-Treiber für SQL Server muss dies "MSOLEDBSQL" sein.|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Eine leere Zeichenfolge bewirkt, dass OLE DB-Treiber für SQL Server Standard, vom Anbieter generierten SPN verwendet.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Steuert, wie die Metadaten abgerufen werden, bei der Verbindung [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] und höher. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.<br /><br />Der OLE DB-Treiber für SQL Server verwendet standardmäßig [Sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) und [Sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) gespeicherte Prozeduren zum Abrufen von Metadaten. Diese gespeicherten Prozeduren weisen einige Einschränkungen (z. B. sie fehl, wenn auf temporäre Tabellen). Festlegen von **FMTONLY verwenden** auf "true" weist den Treiber mit [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) zum Abrufen von Metadaten stattdessen.|  
|**Benutzer-ID**|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|**Workstation ID**|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 **Hinweis:** In der Verbindungszeichenfolge legt die Eigenschaft „Old Password“ SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
