---
description: Programm gesteuertes ändern von SQL Server Native Client Kennwörtern
title: Programmgesteuertes Ändern von Kennwörtern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.reviewer: ''
ms.prod: sql
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 54eaac3f4b8a5e8cc8ab6de6c0b0c75fb54c22c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428182"
---
# <a name="changing-sql-server-native-client-passwords-programmatically"></a>Programm gesteuertes ändern von SQL Server Native Client Kennwörtern
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] konnte nur ein Administrator ein abgelaufenes Kennwort eines Benutzers zurücksetzen. Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt Native Client die programmgesteuerte Verarbeitung des Kenn Wort Ablaufs sowohl über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter als auch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über den Native Client-ODBC-Treiber und durch Änderungen an den **SQL Server Anmelde** Dialogfeldern.  
  
> [!NOTE]  
>  Fordern Sie, wenn möglich, Benutzer dazu auf, ihre Anmeldeinformationen zur Laufzeit einzugeben, um zu vermeiden, diese Informationen in einem persistenten Format speichern zu müssen. Wenn Sie die Anmeldeinformationen persistent speichern müssen, verschlüsseln Sie sie mit der [Win32 Crypto-API](https://go.microsoft.com/fwlink/?LinkId=64532). Weitere Informationen zur Verwendung von Kennwörtern finden Sie unter [Sichere Kennwörter](../../../relational-databases/security/strong-passwords.md).  
  
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
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kenn Wörtern über eine Benutzeroberfläche und Programm gesteuert.  
  
### <a name="ole-db-user-interface-password-expiration"></a>OLE DB-Benutzeroberfläche für abgelaufene Kennwörter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kenn Wörtern durch Änderungen an den Dialogfeldern **SQL Server Anmeldung** . Wenn der Wert DBPROP_INIT_PROMPT auf DBPROMPT_NOPROMPT festgelegt wird, schlägt der erste Verbindungsversuch fehl, wenn das Kennwort abgelaufen ist.  
  
 Wenn für DBPROP_INIT_PROMPT ein beliebiger anderer Wert festgelegt wurde, wird dem Benutzer ein Dialogfeld zur **SQL Server-Anmeldung** angezeigt, unabhängig davon, ob das Kennwort abgelaufen ist oder nicht. Der Benutzer kann dann auf die Schaltfläche **Optionen** klicken und **Kennwort ändern** aktivieren, um das Kennwort zu ändern.  
  
 Wenn der Benutzer auf OK klickt, und das Kennwort abgelaufen war, fordert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ihn dazu auf, im Dialogfeld **SQL Server-Kennwort ändern** ein neues Kennwort einzugeben und zu bestätigen.  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>OLE DB-Eingabeaufforderungsverhalten und gesperrte Konten  
 Verbindungsversuche schlagen möglicherweise fehl, weil das Konto gesperrt wurde. Falls dies nach der Anzeige des Dialogfelds **SQL Server-Anmeldung** geschieht, wird dem Benutzer die entsprechende Fehlermeldung des Servers ausgegeben, und die Verbindung wird abgebrochen. Dies geschieht unter Umständen auch nach der Anzeige des Dialogfelds **SQL Server-Kennwort ändern**, falls der Benutzer einen falschen Wert für das alte Kennwort eingibt. In diesem Fall wird dieselbe Fehlermeldung angezeigt, und der Verbindungsversuch wird abgebrochen.  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>OLE DB-Verbindungspooling, Ablauf von Kennwörtern und gesperrte Konten  
 Ein Konto kann gesperrt werden oder das dazugehörige Kennwort ablaufen, solange die Verbindung noch in einem Verbindungspool aktiv ist. Der Server überprüft bei zwei Gelegenheiten auf abgelaufene Kennwörter und gesperrte Konten. Zunächst findet eine Überprüfung statt, wenn eine Verbindung hergestellt wird. Die zweite Überprüfung wird nach dem Zurücksetzen einer Verbindung ausgeführt, wenn die Verbindung aus dem Verbindungspool entfernt wird.  
  
 Falls der Zurücksetzungsversuch fehlschlägt, wird die Verbindung aus dem Pool entfernt, und ein Fehler wird zurückgegeben.  
  
### <a name="ole-db-programmatic-password-expiration"></a>Programmgesteuerter Ablauf von Kennwörtern in OLE DB  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt den Ablauf von Kenn Wörtern durch Hinzufügen der Eigenschaft SSPROP_AUTH_OLD_PASSWORD (Type VT_BSTR), die dem DBPROPSET_SQLSERVERDBINIT Eigenschaften Satz hinzugefügt wurde.  
  
 Die vorhandene Password-Eigenschaft verweist auf DBPROP_AUTH_PASSWORD und wird verwendet, um das neue Kennwort zu speichern.  
  
> [!NOTE]  
>  In der Verbindungszeichenfolge legt die "Old Password"-Eigenschaft SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
 Der Anbieter speichert den Wert dieser Eigenschaft nicht persistent. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter nicht den Verbindungspool für die erste Verbindung, da eine neue Verbindung hergestellt wird. Wenn die Kennwortänderung ordnungsgemäß vorgenommen werden konnte, kann die aktuelle Verbindung nicht wiederverwendet werden, da sie weiterhin das alte Kennwort verwendet, das nach der Kennwortänderung ungültig wird. Wenn die Anmeldung erfolgreich ist, löscht der Anbieter zudem diese Eigenschaft. Bei späteren Versuchen, das alte Kennwort abzurufen, wird VT_EMPTY zurückgegeben.  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD sollte nie persistent gespeichert werden, da es nur verwendet wird, wenn ein Kennwort abgelaufen ist.  
  
 Beachten Sie, dass der Anbieter jedes Mal, wenn die Old Password-Eigenschaft festgelegt ist, davon ausgeht, dass versucht wird, das Kennwort zu ändern, es sei denn, es ist auch die Windows-Authentifizierung angegeben, die immer Vorrang hat.  
  
 Wird die Windows-Authentifizierung verwendet, führt die Angabe des alten Kennworts entweder zu DB_E_ERRORSOCCURRED oder zu DB_S_ERRORSOCCURRED, abhängig davon, ob das alte Kennwort als REQUIRED (im ersten Fall) oder als OPTIONAL (im zweiten Fall) angegeben war. Der Statuswert von DBPROPSTATUS_CONFLICTINGBADVALUE wird in *dwStatus* zurückgegeben. Dies wird erkannt, wenn **IDBInitialize::Initialize** aufgerufen wird.  
  
 Wenn ein Versuch, das Kennwort zu ändern, unerwartet fehlschlägt, gibt der Server den Fehlercode 18468 zurück. Für den Verbindungsversuch wird ein Standard-OLEDB-Fehler zurückgegeben.  
  
 Weitere Informationen zum DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz finden Sie unter [Initialisierungs- und Autorisierungseigenschaften](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Ablaufen von Kenn Wörtern über eine Benutzeroberfläche und Programm gesteuert.  
  
### <a name="odbc-user-interface-password-expiration"></a>ODBC-Benutzeroberfläche für abgelaufene Kennwörter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt den Ablauf von Kenn Wörtern durch Änderungen, die an den Dialogfeldern **SQL Server Anmeldung** vorgenommen wurden  
  
 Wenn [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) aufgerufen wird und der Wert von **DriverCompletion** auf SQL_DRIVER_NOPROMPT festgelegt ist, schlägt der anfängliche Verbindungsversuch fehl, wenn das Kennwort abgelaufen ist. Der SQLSTATE-Wert 28000 und der Native Fehler Codewert 18487 werden durch nachfolgende Aufrufe von **SQLError** oder **SQLGetDiagRec**zurückgegeben.  
  
 Wenn für " **DriverCompletion** " ein beliebiger anderer Wert festgelegt wurde, wird dem Benutzer das **SQL Server Anmelde** Dialogfeld angezeigt, unabhängig davon, ob das Kennwort abgelaufen ist. Der Benutzer kann dann auf die Schaltfläche **Optionen** klicken und **Kennwort ändern** aktivieren, um das Kennwort zu ändern.  
  
 Wenn der Benutzer auf OK klickt und das Kennwort abgelaufen ist, werden Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Eingabe und Bestätigung eines neuen Kennworts mithilfe des Dialog Felds **SQL Server Kennwort ändern** aufgefordert.  
  
#### <a name="odbc-prompt-behavior-and-locked-accounts"></a>ODBC-Eingabeaufforderungsverhalten und gesperrte Konten  
 Verbindungsversuche schlagen möglicherweise fehl, weil das Konto gesperrt wurde. Falls dies nach der Anzeige des Dialogfelds **SQL Server-Anmeldung** geschieht, wird dem Benutzer die entsprechende Fehlermeldung des Servers ausgegeben, und die Verbindung wird abgebrochen. Dies geschieht unter Umständen auch nach der Anzeige des Dialogfelds **SQL Server-Kennwort ändern**, falls der Benutzer einen falschen Wert für das alte Kennwort eingibt. In diesem Fall wird dieselbe Fehlermeldung angezeigt, und der Verbindungsversuch wird abgebrochen.  
  
#### <a name="odbc-connection-pooling-password-expiry-and-locked-accounts"></a>ODBC-Verbindungspooling, Ablauf von Kennwörtern und gesperrte Konten  
 Ein Konto kann gesperrt werden oder das dazugehörige Kennwort ablaufen, solange die Verbindung noch in einem Verbindungspool aktiv ist. Der Server überprüft bei zwei Gelegenheiten auf abgelaufene Kennwörter und gesperrte Konten. Zunächst findet eine Überprüfung statt, wenn eine Verbindung hergestellt wird. Die zweite Überprüfung wird nach dem Zurücksetzen einer Verbindung ausgeführt, wenn die Verbindung aus dem Verbindungspool entfernt wird.  
  
 Falls der Zurücksetzungsversuch fehlschlägt, wird die Verbindung aus dem Pool entfernt, und ein Fehler wird zurückgegeben.  
  
### <a name="odbc-programmatic-password-expiration"></a>Programmgesteuerter Ablauf von Kennwörtern in ODBC  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt den Ablauf von Kenn Wörtern durch das Hinzufügen des SQL_COPT_SS_OLDPWD Attributs, das festgelegt wird, bevor eine Verbindung mit dem Server mithilfe der [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) -Funktion hergestellt  
  
 Das SQL_COPT_SS_OLDPWD-Attribut des Verbindungshandles verweist auf das abgelaufene Kennwort. Es gibt kein Verbindungszeichenfolgenattribut für dieses Attribut, da dies mit dem Verbindungspooling nicht übereinstimmen würde. Wenn die Anmeldung erfolgreich ist, löscht der Treiber zudem dieses Attribut.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber gibt SQL_ERROR in vier Fällen für dieses Feature zurück: Kenn Wort Ablauf, Kenn Wort Richtlinien Konflikt, Kontosperrung und Zeitpunkt der Festlegung der alten Kenn Wort Eigenschaft bei Verwendung der Windows-Authentifizierung. Der Treiber gibt die entsprechenden Fehlermeldungen an den Benutzer zurück, wenn [SQLGetDiagField](../../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md) aufgerufen wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
