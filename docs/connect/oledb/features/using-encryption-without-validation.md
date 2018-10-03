---
title: Verwenden von Verschlüsselung ohne Validierung | Microsoft-Dokumentation
description: Verwenden von Verschlüsselung ohne Überprüfung
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], encryption
- cryptography [OLE DB Driver for SQL Server]
- MSOLEDBSQL, encryption
- encryption [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, encryption
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 41aa355de39aabc266e798b6870a8f43ceca4110
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814724"
---
# <a name="using-encryption-without-validation"></a>Verwenden von Verschlüsselung ohne Überprüfung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verschlüsselt stets Netzwerkpakete, die mit der Anmeldung verbunden sind. Wenn auf dem Server beim Start kein Zertifikat bereitgestellt wird, erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein selbstsigniertes Zertifikat, mit dem Anmeldungspakete verschlüsselt werden.  

Selbstsignierte Zertifikate sind Sicherheit kann nicht garantiert. Der verschlüsselte Handshake basiert auf NT LAN Manager (NTLM). Es wird dringend empfohlen, dass Sie ein überprüfbares Zertifikat auf SQL Server für die sichere Konnektivität bereitstellen. Transport Security Layer (TLS) können nur mit der Überprüfung des Zertifikats sicher vorgenommen werden.

Anwendungen erfordern möglicherweise auch die Verschlüsselung des gesamten Netzwerkdatenverkehrs mit Verbindungszeichenfolgenschlüsselwörtern oder Verbindungseigenschaften. Die Schlüsselwörter lauten „Encrypt“ für OLE DB, wenn eine Anbieterzeichenfolge mit **IDbInitialize::Initialize** verwendet wird, oder „Use Encryption for Data“ für ADO und OLE DB, wenn eine Initialisierungszeichenfolge mit **IDataInitialize** verwendet wird. Dies kann auch konfiguriert werden, indem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe von Configuration Manager die **Protokollverschlüsselung** aus, und durch Konfigurieren des Clients zum Anfordern verschlüsselter Verbindungen. Standardmäßig ist für die Verschlüsselung des Netzwerkverkehrs für eine Verbindung die Bereitstellung eines Zertifikats auf dem Server erforderlich. Wenn Sie Ihrem Client, um das Zertifikat auf dem Server als vertrauenswürdig festlegen, können Sie anfällig für Man-in-the-Middle-Angriffe werden. Wenn Sie ein überprüfbares Zertifikat auf dem Server bereitstellen, stellen Sie sicher, dass Sie die Clienteinstellungen über die Vertrauenswürdigkeit des Zertifikats auf "false" ändern.

Weitere Informationen zu Verbindungszeichenfolgen-Schlüsselwörtern finden Sie unter [Using Connection String Keywords with SQL Server Native Client (Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server)](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md ).  
  
 Um die Verschlüsselung zu aktivieren, die verwendet werden soll, wenn kein Zertifikat auf dem Server bereitgestellt wurde, kann der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager zum Festlegen der Optionen **Protokollverschlüsselung erzwingen** und **Serverzertifikat vertrauen** verwendet werden. In diesem Fall wird bei der Verschlüsselung ein selbstsigniertes Serverzertifikat ohne Überprüfung verwendet, wenn kein überprüfbares Zertifikat auf dem Server bereitgestellt wurde.  
  
 Anwendungen können auch das Schlüsselwort "TrustServerCertificate" oder das zugeordnete Verbindungsattribut verwenden, um sicherzustellen, dass eine Verschlüsselung durchgeführt wird. Anwendungseinstellungen senken nicht die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client-Konfigurations-Manager festgelegte Sicherheitsstufe, vielmehr stärken sie sie. Wenn beispielsweise **Protokollverschlüsselung erzwingen** nicht für den Client festgelegt ist, kann eine Anwendung die Verschlüsselung selbst anfordern. Um die Verschlüsselung sicherzustellen, selbst wenn kein Serverzertifikat bereitgestellt wurde, kann eine Anwendung die Verschlüsselung und "TrustServerCertificate" anfordern. Wenn "TrustServerCertificate" nicht in der Clientkonfiguration aktiviert ist, ist dennoch die Bereitstellung eines Serverzertifikats erforderlich. In der folgenden Tabelle werden alle Fälle beschrieben:  
  
|Protokollverschlüsselung erzwingen - Clienteinstellung|Dem Serverzertifikat vertrauen|Verbindungszeichenfolge-/Verbindungsattribut 'Verschlüsseln/Verschlüsselung für Daten verwenden'|Verbindungszeichenfolge/Verbindungsattribut 'Dem Serverzertifikat vertrauen'|Ergebnis|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|nein|–|Nein (Standard)|Wird ignoriert.|Keine Verschlüsselung.|  
|nein|–|Benutzerkontensteuerung|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|nein|–|Benutzerkontensteuerung|Benutzerkontensteuerung|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Benutzerkontensteuerung|nein|Wird ignoriert.|Wird ignoriert.|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein (Standard)|Wird ignoriert.|Verschlüsselung wird immer durchgeführt, es wird jedoch z. B. ein selbstsigniertes Serverzertifikat verwendet.|  
|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein (Standard)|Eine Verschlüsselung findet nur statt, wenn ein überprüfbares Serverzertifikat vorliegt, anderenfalls schlägt der Verbindungsversuch fehl.|  
|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Verschlüsselung wird immer durchgeführt, es kann jedoch ein selbstsigniertes Serverzertifikat verwendet werden.|  
||||||

> [!CAUTION]
> Die obigen Tabelle bietet eine Anleitung nur auf das Verhalten des Systems bei unterschiedlichen Konfigurationen. Für sichere Konnektivität stellen Sie sicher, dass dem Client und Server Verschlüsselung erforderlich ist. Stellen Sie außerdem sicher, dass der Server ein überprüfbares Zertifikat, und dass die **TrustServerCertificate** Einstellungen auf dem Client auf "false" festgelegt ist.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server 
 Der OLE DB-Treiber für SQL Server unterstützt die Verschlüsselung ohne Überprüfung durch Hinzufügen der SSPROP_INIT_TRUST_SERVER_CERTIFICATE-Initialisierungseigenschaft für Datenquellen, die in den DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz implementiert wird. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, „TrustServerCertificate“, hinzugefügt. Gültig sind die Werte YES oder NO, wobei NO die Standardeinstellung ist. Wenn Dienstkomponenten verwendet werden, sind die Werte "true" und "false" gültig, wobei "false" die Standardeinstellung ist.  
  
 Weitere Informationen zu Verbesserungen der DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  

  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
