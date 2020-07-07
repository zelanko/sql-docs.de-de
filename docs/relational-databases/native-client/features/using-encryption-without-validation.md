---
title: Verwenden von Verschlüsselung ohne Überprüfung | Microsoft-Dokumentation
description: Erfahren Sie, wie der SQL Server Native Client OLE DB Anbieter und der ODBC-Treiber die Verschlüsselung ohne Validierung und Empfehlungen für den Verwendungs Zeitpunkt unterstützen.
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bf5497fbddb255a9964d97094838dd3a7ece583e
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009854"
---
# <a name="using-encryption-without-validation"></a>Verwenden von Verschlüsselung ohne Überprüfung
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verschlüsselt stets Netzwerkpakete, die mit der Anmeldung verbunden sind. Wenn auf dem Server beim Start kein Zertifikat bereitgestellt wird, erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein selbstsigniertes Zertifikat, mit dem Anmeldungspakete verschlüsselt werden.  

Bei selbstsignierten Zertifikaten kann die Sicherheit nicht garantiert werden. Der verschlüsselte Handshake basiert auf dem Windows NT-LAN-Manager (NTLM). Sie sollten für eine sichere Konnektivität unbedingt ein verifizierbares Zertifikat für SQL Server bereitstellen. Transport Layer Security (TLS) kann nur mit einer Zertifikatüberprüfung gesichert werden.

Anwendungen erfordern möglicherweise auch die Verschlüsselung des gesamten Netzwerkdatenverkehrs mit Verbindungszeichenfolgenschlüsselwörtern oder Verbindungseigenschaften. Die Schlüsselwörter sind "verschlüsseln" für ODBC und OLE DB, wenn eine Anbieter Zeichenfolge mit **IDBInitialize:: Initialize**verwendet wird, oder "Use Encryption for Data" für ADO und OLE DB, wenn eine Initialisierungs Zeichenfolge mit " **IDataInitialize**" verwendet wird. Dies kann auch vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager mithilfe der Option **Protokollverschlüsselung erzwingen** konfiguriert werden, und indem der Client so konfiguriert wird, dass er verschlüsselte Verbindungen anfordert. Standardmäßig ist für die Verschlüsselung des Netzwerkverkehrs für eine Verbindung die Bereitstellung eines Zertifikats auf dem Server erforderlich. Wenn Sie festlegen, dass Ihr Client dem Zertifikat auf dem Server vertraut, werden Sie möglicherweise anfällig für Man-in-the-Middle-Angriffe. Wenn Sie ein verifizierbares Zertifikat auf dem Server bereitstellen, sollten Sie die Vertrauenseinstellungen des Clients für das Zertifikat in FALSE ändern.

Weitere Informationen zu Schlüsselwörtern für Verbindungs Zeichenfolgen finden [Sie unter Verwenden von Schlüssel SQL Server Native Client Wörtern für Verbindungs Zeichenfolgen](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Um die Verschlüsselung zu aktivieren, die verwendet werden soll, wenn kein Zertifikat auf dem Server bereitgestellt wurde, kann der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager zum Festlegen der Optionen **Protokollverschlüsselung erzwingen** und **Serverzertifikat vertrauen** verwendet werden. In diesem Fall wird bei der Verschlüsselung ein selbstsigniertes Serverzertifikat ohne Überprüfung verwendet, wenn kein überprüfbares Zertifikat auf dem Server bereitgestellt wurde.  
  
 Anwendungen können auch das Schlüsselwort "TrustServerCertificate" oder das zugeordnete Verbindungsattribut verwenden, um sicherzustellen, dass eine Verschlüsselung durchgeführt wird. Anwendungseinstellungen senken nicht die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client-Konfigurations-Manager festgelegte Sicherheitsstufe, vielmehr stärken sie sie. Wenn beispielsweise **Protokollverschlüsselung erzwingen** nicht für den Client festgelegt ist, kann eine Anwendung die Verschlüsselung selbst anfordern. Um die Verschlüsselung sicherzustellen, selbst wenn kein Serverzertifikat bereitgestellt wurde, kann eine Anwendung die Verschlüsselung und "TrustServerCertificate" anfordern. Wenn "TrustServerCertificate" nicht in der Clientkonfiguration aktiviert ist, ist dennoch die Bereitstellung eines Serverzertifikats erforderlich. In der folgenden Tabelle werden alle Fälle beschrieben:  
  
|Protokollverschlüsselung erzwingen - Clienteinstellung|Dem Serverzertifikat vertrauen|Verbindungszeichenfolge-/Verbindungsattribut 'Verschlüsseln/Verschlüsselung für Daten verwenden'|Verbindungszeichenfolge/Verbindungsattribut 'Dem Serverzertifikat vertrauen'|Ergebnis|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|Nein|–|Nein (Standard)|Wird ignoriert.|Keine Verschlüsselung.|  
|Nein|–|Ja|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Nein|–|Ja|Ja|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Ja|Nein|Wird ignoriert.|Wird ignoriert.|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Ja|Ja|Nein (Standard)|Wird ignoriert.|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Ja|Ja|Ja|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Ja|Ja|Ja|Ja|Verschlüsselung wird immer durchgeführt, es kann jedoch ein selbstsigniertes Serverzertifikat verwendet werden.|  
||||||

> [!CAUTION]
> In der obigen Tabelle finden Sie lediglich einen Leitfaden für das Systemverhalten unter verschiedenen Konfigurationen. Für eine sichere Konnektivität müssen Sie dafür sorgen, dass sowohl der Client als auch der Server die Verschlüsselung erzwingen. Sorgen Sie außerdem dafür, dass der Server über ein verifizierbares Zertifikat verfügt und dass die Einstellung **TrustServerCertificate** für den Client auf FALSE festgelegt ist.

## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Verschlüsselung ohne Überprüfung durch Hinzufügen der SSPROP_INIT_TRUST_SERVER_CERTIFICATE Datenquellen-Initialisierungs Eigenschaft, die im DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satz implementiert ist. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, „TrustServerCertificate“, hinzugefügt. Gültig sind die Werte YES oder NO, wobei NO die Standardeinstellung ist. Wenn Dienstkomponenten verwendet werden, sind die Werte "true" und "false" gültig, wobei "false" die Standardeinstellung ist.  
  
 Weitere Informationen zu Verbesserungen am DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC-Treiber von Native Client unterstützt die Verschlüsselung ohne Überprüfung durch Ergänzungen der Funktionen [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) . SQL_COPT_SS_TRUST_SERVER_CERTIFICATE wurde hinzugefügt, um entweder SQL_TRUST_SERVER_CERTIFICATE_YES oder SQL_TRUST_SERVER_CERTIFICATE_NO anzunehmen, wobei SQL_TRUST_SERVER_CERTIFICATE_NO die Standardeinstellung ist. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, "TrustServerCertificate", hinzugefügt. Gültig sind die Werte "Ja" oder "Nein", wobei "Nein" die Standardeinstellung ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
