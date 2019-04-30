---
title: Verwenden von Verschlüsselung ohne Validierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 443c6e0c556a7e69510796b1d58ab0f7b2567e6e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225491"
---
# <a name="using-encryption-without-validation"></a>Verwenden von Verschlüsselung ohne Überprüfung
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verschlüsselt stets Netzwerkpakete, die mit der Anmeldung verbunden sind. Wenn auf dem Server beim Start kein Zertifikat bereitgestellt wird, erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein selbstsigniertes Zertifikat, mit dem Anmeldungspakete verschlüsselt werden.  
  
 Anwendungen erfordern möglicherweise auch die Verschlüsselung des gesamten Netzwerkdatenverkehrs mit Verbindungszeichenfolgenschlüsselwörtern oder Verbindungseigenschaften. Die Schlüsselwörter lauten "Encrypt", ODBC und OLE DB aus, wenn eine Anbieterzeichenfolge mit **IDBInitialize:: Initialize**, oder "Use Encryption for Data" für ADO und OLE DB, wenn eine Initialisierungszeichenfolge mit **IDataInitialize** . Dies kann auch konfiguriert werden, indem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe von Configuration Manager die **Protokollverschlüsselung** Option. Standardmäßig ist für die Verschlüsselung des Netzwerkverkehrs für eine Verbindung die Bereitstellung eines Zertifikats auf dem Server erforderlich.  
  
 Informationen zu verbindungszeichenfolgeschlüsselwörtern finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Um die Verschlüsselung zu aktivieren, die verwendet werden soll, wenn kein Zertifikat auf dem Server bereitgestellt wurde, kann der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager zum Festlegen der Optionen **Protokollverschlüsselung erzwingen** und **Serverzertifikat vertrauen** verwendet werden. In diesem Fall wird bei der Verschlüsselung ein selbstsigniertes Serverzertifikat ohne Überprüfung verwendet, wenn kein überprüfbares Zertifikat auf dem Server bereitgestellt wurde.  
  
 Anwendungen können auch das Schlüsselwort "TrustServerCertificate" oder das zugeordnete Verbindungsattribut verwenden, um sicherzustellen, dass eine Verschlüsselung durchgeführt wird. Anwendungseinstellungen senken nicht die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client-Konfigurations-Manager festgelegte Sicherheitsstufe, vielmehr stärken sie sie. Wenn beispielsweise **Protokollverschlüsselung erzwingen** nicht für den Client festgelegt ist, kann eine Anwendung die Verschlüsselung selbst anfordern. Um die Verschlüsselung sicherzustellen, selbst wenn kein Serverzertifikat bereitgestellt wurde, kann eine Anwendung die Verschlüsselung und "TrustServerCertificate" anfordern. Wenn "TrustServerCertificate" nicht in der Clientkonfiguration aktiviert ist, ist dennoch die Bereitstellung eines Serverzertifikats erforderlich. In der folgenden Tabelle werden alle Fälle beschrieben:  
  
|Protokollverschlüsselung erzwingen - Clienteinstellung|Dem Serverzertifikat vertrauen|Verbindungszeichenfolge-/Verbindungsattribut 'Verschlüsseln/Verschlüsselung für Daten verwenden'|Verbindungszeichenfolge/Verbindungsattribut 'Dem Serverzertifikat vertrauen'|Ergebnis|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|Nein|Nicht zutreffend|Nein (Standard)|Wird ignoriert.|Keine Verschlüsselung.|  
|Nein|Nicht zutreffend|Ja|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Nein|Nicht zutreffend|Ja|Ja|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Ja|Nein|Wird ignoriert.|Wird ignoriert.|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Ja|Ja|Nein (Standard)|Wird ignoriert.|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Ja|Ja|Ja|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Ja|Ja|Ja|Ja|Verschlüsselung wird immer durchgeführt, es kann jedoch ein selbstsigniertes Serverzertifikat verwendet werden.|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die Verschlüsselung ohne Überprüfung durch das Hinzufügen der SSPROP_INIT_TRUST_SERVER_CERTIFICATE Initialisierungseigenschaft-Datenquellen, die in der Eigenschaft DBPROPSET_SQLSERVERDBINIT implementiert wird Legen Sie. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, „TrustServerCertificate“, hinzugefügt. Gültig sind die Werte YES oder NO, wobei NO die Standardeinstellung ist. Wenn Dienstkomponenten verwendet werden, sind die Werte "true" und "false" gültig, wobei "false" die Standardeinstellung ist.  
  
 Weitere Informationen zu Verbesserungen der DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt die Verschlüsselung ohne Überprüfung durch Hinzufügungen zu den [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) und [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md) Funktionen. SQL_COPT_SS_TRUST_SERVER_CERTIFICATE wurde hinzugefügt, um entweder SQL_TRUST_SERVER_CERTIFICATE_YES oder SQL_TRUST_SERVER_CERTIFICATE_NO anzunehmen, wobei SQL_TRUST_SERVER_CERTIFICATE_NO die Standardeinstellung ist. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, "TrustServerCertificate", hinzugefügt. Gültig sind die Werte "Ja" oder "Nein", wobei "Nein" die Standardeinstellung ist.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
