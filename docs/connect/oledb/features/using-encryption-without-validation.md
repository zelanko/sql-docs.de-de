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
ms.openlocfilehash: ef21cdb2a223aaa50b690f5b2b3c30696dd9e196
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988849"
---
# <a name="using-encryption-without-validation"></a>Verwenden von Verschlüsselung ohne Überprüfung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verschlüsselt stets Netzwerkpakete, die mit der Anmeldung verbunden sind. Wenn auf dem Server beim Start kein Zertifikat bereitgestellt wird, erstellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein selbstsigniertes Zertifikat, mit dem Anmeldungspakete verschlüsselt werden.  

Selbst signierte Zertifikate garantieren keine Sicherheit. Der verschlüsselte Handshake basiert auf dem NT-LAN-Manager (NTLM). Es wird dringend empfohlen, dass Sie ein überprüfbares Zertifikat auf SQL Server für sichere Konnektivität bereitstellen. TLS (Transport Security Layer) kann nur mit der Zertifikat Überprüfung sicher gemacht werden.

Anwendungen erfordern möglicherweise auch die Verschlüsselung des gesamten Netzwerkdatenverkehrs mit Verbindungszeichenfolgenschlüsselwörtern oder Verbindungseigenschaften. Die Schlüsselwörter lauten „Encrypt“ für OLE DB, wenn eine Anbieterzeichenfolge mit **IDbInitialize::Initialize** verwendet wird, oder „Use Encryption for Data“ für ADO und OLE DB, wenn eine Initialisierungszeichenfolge mit **IDataInitialize** verwendet wird. Dies kann auch durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager mithilfe der Option **Protokoll Verschlüsselung erzwingen** konfiguriert werden, und durch Konfigurieren des Clients, um verschlüsselte Verbindungen anzufordern. Standardmäßig ist für die Verschlüsselung des Netzwerkverkehrs für eine Verbindung die Bereitstellung eines Zertifikats auf dem Server erforderlich. Wenn Sie den Client so festlegen, dass das Zertifikat auf dem Server vertrauenswürdig ist, können Sie für man-in-the-Middle-Angriffe anfällig werden. Wenn Sie ein überprüfbares Zertifikat auf dem Server bereitstellen, stellen Sie sicher, dass Sie die Client Einstellungen für die Vertrauenswürdigkeit des Zertifikats auf false ändern.

Weitere Informationen zu Verbindungszeichenfolgen-Schlüsselwörtern finden Sie unter [Using Connection String Keywords with SQL Server Native Client (Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server)](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md ).  
  
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
> In der obigen Tabelle ist nur ein Leitfaden zum Systemverhalten unter verschiedenen Konfigurationen enthalten. Stellen Sie sicher, dass sowohl der Client als auch der Server eine Verschlüsselung erfordern. Stellen Sie außerdem sicher, dass der Server über ein überprüfbares Zertifikat verfügt und dass die **TrustServerCertificate** -Einstellung auf dem Client auf false festgelegt ist.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server 
 Der OLE DB-Treiber für SQL Server unterstützt die Verschlüsselung ohne Überprüfung durch Hinzufügen der SSPROP_INIT_TRUST_SERVER_CERTIFICATE-Initialisierungseigenschaft für Datenquellen, die in den DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz implementiert wird. Darüber hinaus wurde ein neues Verbindungszeichenfolgeschlüsselwort, „TrustServerCertificate“, hinzugefügt. Gültig sind die Werte YES oder NO, wobei NO die Standardeinstellung ist. Wenn Dienstkomponenten verwendet werden, sind die Werte "true" und "false" gültig, wobei "false" die Standardeinstellung ist.  
  
 Weitere Informationen zu Verbesserungen am DBPROPSET_SQLSERVERDBINIT-Eigenschaften Satz finden Sie unter [Initialisierungs-und Autorisierungs Eigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  

  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
