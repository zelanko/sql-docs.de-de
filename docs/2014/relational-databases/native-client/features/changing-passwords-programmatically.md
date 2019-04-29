---
title: Programmgesteuertes Ändern von Kennwörtern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], password expiration
- SQL Server Native Client ODBC driver, passwords
- SQL Server Native Client OLE DB provider, passwords
- passwords [SQL Server], expiration
- SQLNCLI, password expiration
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- expired passwords [SQL Server Native Client]
- SQL Server Native Client, password expiration
- modifying passwords
ms.assetid: 624ad949-5fed-4ce5-b319-878549f9487b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ec1db8e0f88bea5a02eb54b94a88194882ad9ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046252"
---
# <a name="changing-passwords-programmatically"></a>Programmgesteuertes Ändern von Kennwörtern
  Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] konnte nur ein Administrator ein abgelaufenes Kennwort eines Benutzers zurücksetzen. Beginnend mit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt die Verwaltung von abgelaufenen Kennwörtern sowohl programmgesteuert über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und über Änderungen an der **SQL Server-Anmeldung** Dialogfelder.  
  
> [!NOTE]  
>  Fordern Sie, wenn möglich, Benutzer dazu auf, ihre Anmeldeinformationen zur Laufzeit einzugeben, um zu vermeiden, diese Informationen in einem persistenten Format speichern zu müssen. Wenn Sie die Anmeldeinformationen persistent speichern müssen, verschlüsseln Sie sie mit der [Win32 Crypto-API](https://go.microsoft.com/fwlink/?LinkId=64532). Weitere Informationen zur Verwendung von Kennwörtern finden Sie unter [Sichere Kennwörter](../../security/strong-passwords.md).  
  
## <a name="sql-server-login-error-codes"></a>Fehlercodes bei der SQL Server-Anmeldung  
 Wenn eine Verbindung aufgrund von Authentifizierungsproblemen nicht hergestellt werden kann, wird für die Anwendung einer der folgenden SQL Server-Fehlercodes bereitgestellt, um Diagnose und Wiederherstellung zu erleichtern.  
  
|SQL Server-Fehlercode|Fehlermeldung|  
|---------------------------|-------------------|  
|15113|Fehler bei der Anmeldung für Benutzer ' %. * ls. Ursache: Fehler bei der Kennwortüberprüfung. Das Konto ist gesperrt.|  
|18463|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Das Kennwort kann zurzeit nicht verwendet werden.|  
|18464|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Das Kennwort ist zu kurz und erfüllt daher nicht die Anforderungen der Richtlinie.|  
|18465|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Das Kennwort ist zu lang und erfüllt daher nicht die Anforderungen der Richtlinie.|  
|18466|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Das Kennwort ist nicht komplex genug und erfüllt daher nicht die Anforderungen der Windows-Richtlinie.|  
|18467|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Das Kennwort erfüllt nicht die Anforderungen der Kennwortfilter-DLL.|  
|18468|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Fehler bei der kennwortänderung. Unerwarteter Fehler während der Kennwortüberprüfung.|  
|18487|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Das Kennwort des Kontos ist abgelaufen.|  
|18488|Fehler bei der Anmeldung für den Benutzer '%.*ls'. Ursache: Das Kennwort des Kontos muss geändert werden.|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kennwörtern, über eine Benutzerschnittstelle und programmgesteuert.  
  
### <a name="ole-db-user-interface-password-expiration"></a>OLE DB-Benutzeroberfläche für abgelaufene Kennwörter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kennwörtern durch Änderungen an der **SQL Server-Anmeldung** Dialogfelder. Wenn der Wert DBPROP_INIT_PROMPT auf DBPROMPT_NOPROMPT festgelegt wird, schlägt der erste Verbindungsversuch fehl, wenn das Kennwort abgelaufen ist.  
  
 Wenn für DBPROP_INIT_PROMPT ein beliebiger anderer Wert festgelegt wurde, wird dem Benutzer ein Dialogfeld zur **SQL Server-Anmeldung** angezeigt, unabhängig davon, ob das Kennwort abgelaufen ist oder nicht. Der Benutzer kann dann auf die Schaltfläche **Optionen** klicken und **Kennwort ändern** aktivieren, um das Kennwort zu ändern.  
  
 Wenn der Benutzer auf OK klickt, und das Kennwort abgelaufen war, fordert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ihn dazu auf, im Dialogfeld **SQL Server-Kennwort ändern** ein neues Kennwort einzugeben und zu bestätigen.  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>OLE DB-Eingabeaufforderungsverhalten und gesperrte Konten  
 Verbindungsversuche schlagen möglicherweise fehl, weil das Konto gesperrt wurde. Falls dies nach der Anzeige des Dialogfelds **SQL Server-Anmeldung** geschieht, wird dem Benutzer die entsprechende Fehlermeldung des Servers ausgegeben, und die Verbindung wird abgebrochen. Dies geschieht unter Umständen auch nach der Anzeige des Dialogfelds **SQL Server-Kennwort ändern**, falls der Benutzer einen falschen Wert für das alte Kennwort eingibt. In diesem Fall wird dieselbe Fehlermeldung angezeigt, und der Verbindungsversuch wird abgebrochen.  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>OLE DB-Verbindungspooling, Ablauf von Kennwörtern und gesperrte Konten  
 Ein Konto kann gesperrt werden oder das dazugehörige Kennwort ablaufen, solange die Verbindung noch in einem Verbindungspool aktiv ist. Der Server überprüft bei zwei Gelegenheiten auf abgelaufene Kennwörter und gesperrte Konten. Zunächst findet eine Überprüfung statt, wenn eine Verbindung hergestellt wird. Die zweite Überprüfung wird nach dem Zurücksetzen einer Verbindung ausgeführt, wenn die Verbindung aus dem Verbindungspool entfernt wird.  
  
 Falls der Zurücksetzungsversuch fehlschlägt, wird die Verbindung aus dem Pool entfernt, und ein Fehler wird zurückgegeben.  
  
### <a name="ole-db-programmatic-password-expiration"></a>Programmgesteuerter Ablauf von Kennwörtern in OLE DB  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kennwörtern durch Hinzufügen der Eigenschaft SSPROP_AUTH_OLD_PASSWORD (vom Typ VT_BSTR), die dem DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz hinzugefügt wurde.  
  
 Die vorhandene Password-Eigenschaft verweist auf DBPROP_AUTH_PASSWORD und wird verwendet, um das neue Kennwort zu speichern.  
  
> [!NOTE]  
>  In der Verbindungszeichenfolge legt die "Old Password"-Eigenschaft SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
 Der Anbieter speichert den Wert dieser Eigenschaft nicht persistent. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter nicht den Verbindungspool für die erste Verbindung, da eine neue Verbindung hergestellt wird. Wenn die Kennwortänderung ordnungsgemäß vorgenommen werden konnte, kann die aktuelle Verbindung nicht wiederverwendet werden, da sie weiterhin das alte Kennwort verwendet, das nach der Kennwortänderung ungültig wird. Wenn die Anmeldung erfolgreich ist, löscht der Anbieter zudem diese Eigenschaft. Bei späteren Versuchen, das alte Kennwort abzurufen, wird VT_EMPTY zurückgegeben.  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD sollte nie persistent gespeichert werden, da es nur verwendet wird, wenn ein Kennwort abgelaufen ist.  
  
 Beachten Sie, dass der Anbieter jedes Mal, wenn die Old Password-Eigenschaft festgelegt ist, davon ausgeht, dass versucht wird, das Kennwort zu ändern, es sei denn, es ist auch die Windows-Authentifizierung angegeben, die immer Vorrang hat.  
  
 Wird die Windows-Authentifizierung verwendet, führt die Angabe des alten Kennworts entweder zu DB_E_ERRORSOCCURRED oder zu DB_S_ERRORSOCCURRED, abhängig davon, ob das alte Kennwort als REQUIRED (im ersten Fall) oder als OPTIONAL (im zweiten Fall) angegeben war. Der Statuswert von DBPROPSTATUS_CONFLICTINGBADVALUE wird in *dwStatus* zurückgegeben. Dies wird erkannt, wenn **IDBInitialize::Initialize** aufgerufen wird.  
  
 Wenn ein Versuch, das Kennwort zu ändern, unerwartet fehlschlägt, gibt der Server den Fehlercode 18468 zurück. Für den Verbindungsversuch wird ein Standard-OLEDB-Fehler zurückgegeben.  
  
 Weitere Informationen zum DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kennwörtern, über eine Benutzerschnittstelle und programmgesteuert.  
  
### <a name="odbc-user-interface-password-expiration"></a>ODBC-Benutzeroberfläche für abgelaufene Kennwörter  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt das Ablaufen von Kennwörtern durch Änderungen an der **SQL Server-Anmeldung** Dialogfelder.  
  
 Wenn [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) aufgerufen wird und der Wert der **DriverCompletion** auf SQL_DRIVER_NOPROMPT festgelegt, der erste Verbindungsversuch fehl, wenn das Kennwort abgelaufen ist. Der SQLSTATE-Wert 28000 und der systemeigene Fehlercodewert 18487 zurückgegeben, durch nachfolgende Aufrufe **SQLError** oder **SQLGetDiagRec**.  
  
 Wenn **DriverCompletion** festgelegt wurde auf einen anderen Wert, der Benutzer sieht die **SQL Server-Anmeldung** Dialogfeld, unabhängig davon, ob das Kennwort abgelaufen ist. Der Benutzer kann dann auf die Schaltfläche **Optionen** klicken und **Kennwort ändern** aktivieren, um das Kennwort zu ändern.  
  
 Wenn der Benutzer auf OK klickt und das Kennwort abgelaufen ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aufforderungen zur Eingabe und Bestätigung eines neuen Kennworts mithilfe der **SQL Server-Kennwort ändern** Dialogfeld.  
  
#### <a name="odbc-prompt-behavior-and-locked-accounts"></a>ODBC-Eingabeaufforderungsverhalten und gesperrte Konten  
 Verbindungsversuche schlagen möglicherweise fehl, weil das Konto gesperrt wurde. Falls dies nach der Anzeige des Dialogfelds **SQL Server-Anmeldung** geschieht, wird dem Benutzer die entsprechende Fehlermeldung des Servers ausgegeben, und die Verbindung wird abgebrochen. Dies geschieht unter Umständen auch nach der Anzeige des Dialogfelds **SQL Server-Kennwort ändern**, falls der Benutzer einen falschen Wert für das alte Kennwort eingibt. In diesem Fall wird dieselbe Fehlermeldung angezeigt, und der Verbindungsversuch wird abgebrochen.  
  
#### <a name="odbc-connection-pooling-password-expiry-and-locked-accounts"></a>ODBC-Verbindungspooling, Ablauf von Kennwörtern und gesperrte Konten  
 Ein Konto kann gesperrt werden oder das dazugehörige Kennwort ablaufen, solange die Verbindung noch in einem Verbindungspool aktiv ist. Der Server überprüft bei zwei Gelegenheiten auf abgelaufene Kennwörter und gesperrte Konten. Zunächst findet eine Überprüfung statt, wenn eine Verbindung hergestellt wird. Die zweite Überprüfung wird nach dem Zurücksetzen einer Verbindung ausgeführt, wenn die Verbindung aus dem Verbindungspool entfernt wird.  
  
 Falls der Zurücksetzungsversuch fehlschlägt, wird die Verbindung aus dem Pool entfernt, und ein Fehler wird zurückgegeben.  
  
### <a name="odbc-programmatic-password-expiration"></a>Programmgesteuerter Ablauf von Kennwörtern in ODBC  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt das Ablaufen von Kennwörtern durch Hinzufügen von das SQL_COPT_SS_OLDPWD-Attribut festgelegt ist, vor dem Herstellen einer Verbindung mit dem Server die [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) Funktion.  
  
 Das SQL_COPT_SS_OLDPWD-Attribut des Verbindungshandles verweist auf das abgelaufene Kennwort. Es gibt kein Verbindungszeichenfolgenattribut für dieses Attribut, da dies mit dem Verbindungspooling nicht übereinstimmen würde. Wenn die Anmeldung erfolgreich ist, löscht der Treiber zudem dieses Attribut.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt SQL_ERROR zurück, in vier Fälle für dieses Feature: Ablauf des Kennworts, Kennwort Richtlinienkonflikt, kontosperrung, und wenn die old Password-Eigenschaft bei der Verwendung von Windows-Authentifizierung festgelegt ist. Der Treiber die entsprechenden Fehlermeldungen an den Benutzer zurückgegeben. wenn [SQLGetDiagField](../../native-client-odbc-api/sqlgetdiagfield.md) aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
