---
title: Programmgesteuertes Ändern von Kennwörtern | Microsoft-Dokumentation
description: Ändern von Kennwörtern programmgesteuert mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], password expiration
- OLE DB Driver for SQL Server, passwords
- passwords [SQL Server], expiration
- MSOLEDBSQL, password expiration
- expiration [OLE DB Driver for SQL Server]
- passwords [SQL Server], modifying
- expired passwords [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, password expiration
- modifying passwords
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a37f5a10f6b594a00c068fd61be1b7903bd097cc
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024569"
---
# <a name="changing-passwords-programmatically"></a>Programmgesteuertes Ändern von Kennwörtern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] konnte nur ein Administrator ein abgelaufenes Kennwort eines Benutzers zurücksetzen. Beginnend mit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], OLE DB-Treiber für SQL Server unterstützt die Verwaltung von abgelaufenen Kennwörtern, programmgesteuert über OLE DB-Treiber und über Änderungen an der **SQL Server-Anmeldung** Dialogfelder.  
  
> [!NOTE]  
>  Fordern Sie, wenn möglich, Benutzer dazu auf, ihre Anmeldeinformationen zur Laufzeit einzugeben, um zu vermeiden, diese Informationen in einem persistenten Format speichern zu müssen. Wenn Sie die Anmeldeinformationen persistent speichern müssen, verschlüsseln Sie sie mit der [Win32 Crypto-API](http://go.microsoft.com/fwlink/?LinkId=64532). Weitere Informationen zur Verwendung von Kennwörtern finden Sie unter [Sichere Kennwörter](../../../relational-databases/security/strong-passwords.md).  
  
## <a name="sql-server-login-error-codes"></a>Fehlercodes bei der SQL Server-Anmeldung  
 Wenn eine Verbindung aufgrund von Authentifizierungsproblemen nicht hergestellt werden kann, wird für die Anwendung einer der folgenden SQL Server-Fehlercodes bereitgestellt, um Diagnose und Wiederherstellung zu erleichtern.  
  
|SQL Server-Fehlercode|Fehlermeldung|  
|---------------------------|-------------------|  
|15113|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortüberprüfung. Das Konto ist gesperrt.|  
|18463|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Das Kennwort kann zurzeit nicht verwendet werden.|  
|18464|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Das Kennwort ist zu kurz und erfüllt daher nicht die Anforderungen der Richtlinie.|  
|18465|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Das Kennwort ist zu lang und erfüllt daher nicht die Anforderungen der Richtlinie.|  
|18466|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Das Kennwort ist nicht komplex genug und erfüllt daher nicht die Anforderungen der Windows-Richtlinie.|  
|18467|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Das Kennwort erfüllt nicht die Anforderungen der Kennwortfilter-DLL.|  
|18468|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der Kennwortänderung. Unerwarteter Fehler während der Kennwortüberprüfung.|  
|18487|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Das Kennwort des Kontos ist abgelaufen.|  
|18488|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Das Kennwort des Kontos muss geändert werden.|  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server unterstützt das Ablaufen von Kennwörtern, über eine Benutzerschnittstelle und programmgesteuert.  
  
### <a name="ole-db-user-interface-password-expiration"></a>OLE DB-Benutzeroberfläche für abgelaufene Kennwörter  
 Der OLE DB-Treiber für SQL Server unterstützt die Verwaltung von abgelaufenen Kennwörtern durch Änderungen, die an den Dialogfeldern zur **SQL Server-Anmeldung** vorgenommen wurden. Wenn der Wert DBPROP_INIT_PROMPT auf DBPROMPT_NOPROMPT festgelegt wird, schlägt der erste Verbindungsversuch fehl, wenn das Kennwort abgelaufen ist.  
  
 Wenn für DBPROP_INIT_PROMPT ein beliebiger anderer Wert festgelegt wurde, wird dem Benutzer ein Dialogfeld zur **SQL Server-Anmeldung** angezeigt, unabhängig davon, ob das Kennwort abgelaufen ist oder nicht. Der Benutzer kann dann auf die Schaltfläche **Optionen** klicken und **Kennwort ändern** aktivieren, um das Kennwort zu ändern.  
  
 Wenn der Benutzer auf OK klickt, und das Kennwort abgelaufen war, fordert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ihn dazu auf, im Dialogfeld **SQL Server-Kennwort ändern** ein neues Kennwort einzugeben und zu bestätigen.  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>OLE DB-Eingabeaufforderungsverhalten und gesperrte Konten  
 Verbindungsversuche schlagen möglicherweise fehl, weil das Konto gesperrt wurde. Falls dies nach der Anzeige des Dialogfelds **SQL Server-Anmeldung** geschieht, wird dem Benutzer die entsprechende Fehlermeldung des Servers ausgegeben, und die Verbindung wird abgebrochen. Dies geschieht unter Umständen auch nach der Anzeige des Dialogfelds **SQL Server-Kennwort ändern**, falls der Benutzer einen falschen Wert für das alte Kennwort eingibt. In diesem Fall wird dieselbe Fehlermeldung angezeigt, und der Verbindungsversuch wird abgebrochen.  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>OLE DB-Verbindungspooling, Ablauf von Kennwörtern und gesperrte Konten  
 Ein Konto kann gesperrt werden oder das dazugehörige Kennwort ablaufen, solange die Verbindung noch in einem Verbindungspool aktiv ist. Der Server überprüft bei zwei Gelegenheiten auf abgelaufene Kennwörter und gesperrte Konten. Zunächst findet eine Überprüfung statt, wenn eine Verbindung hergestellt wird. Die zweite Überprüfung wird nach dem Zurücksetzen einer Verbindung ausgeführt, wenn die Verbindung aus dem Verbindungspool entfernt wird.  
  
 Falls der Zurücksetzungsversuch fehlschlägt, wird die Verbindung aus dem Pool entfernt, und ein Fehler wird zurückgegeben.  
  
### <a name="ole-db-programmatic-password-expiration"></a>Programmgesteuerter Ablauf von Kennwörtern in OLE DB  
 Der OLE DB-Treiber für SQL Server unterstützt das Ablaufen von Kennwörtern durch die SSPROP_AUTH_OLD_PASSWORD-Eigenschaft (vom Typ VT_BSTR), die dem DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz hinzugefügt wurde.  
  
 Die vorhandene Password-Eigenschaft verweist auf DBPROP_AUTH_PASSWORD und wird verwendet, um das neue Kennwort zu speichern.  
  
> [!NOTE]  
>  In der Verbindungszeichenfolge legt die "Old Password"-Eigenschaft SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
 Der Anbieter speichert den Wert dieser Eigenschaft nicht persistent. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter nicht den Verbindungspool für die erste Verbindung, da eine neue Verbindung hergestellt wird. Wenn die Kennwortänderung ordnungsgemäß vorgenommen werden konnte, kann die aktuelle Verbindung nicht wiederverwendet werden, da sie weiterhin das alte Kennwort verwendet, das nach der Kennwortänderung ungültig wird. Wenn die Anmeldung erfolgreich ist, löscht der Anbieter zudem diese Eigenschaft. Bei späteren Versuchen, das alte Kennwort abzurufen, wird VT_EMPTY zurückgegeben.  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD sollte nie persistent gespeichert werden, da es nur verwendet wird, wenn ein Kennwort abgelaufen ist.  
  
 Beachten Sie, dass der Anbieter jedes Mal, wenn die Old Password-Eigenschaft festgelegt ist, davon ausgeht, dass versucht wird, das Kennwort zu ändern, es sei denn, es ist auch die Windows-Authentifizierung angegeben, die immer Vorrang hat.  
  
 Wird die Windows-Authentifizierung verwendet, führt die Angabe des alten Kennworts entweder zu DB_E_ERRORSOCCURRED oder zu DB_S_ERRORSOCCURRED, abhängig davon, ob das alte Kennwort als REQUIRED (im ersten Fall) oder als OPTIONAL (im zweiten Fall) angegeben war. Der Statuswert von DBPROPSTATUS_CONFLICTINGBADVALUE wird in *dwStatus* zurückgegeben. Dies wird erkannt, wenn **IDBInitialize::Initialize** aufgerufen wird.  
  
 Wenn ein Versuch, das Kennwort zu ändern, unerwartet fehlschlägt, gibt der Server den Fehlercode 18468 zurück. Für den Verbindungsversuch wird ein Standard-OLEDB-Fehler zurückgegeben.  
  
 Weitere Informationen zum DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  

  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
