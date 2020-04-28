---
title: Errorvalueerum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ErrorValueEnum
helpviewer_keywords:
- ErrorValueEnum enumeration [ADO]
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18117be8dccc64f7ed2583170cf062145836f337
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932876"
---
# <a name="errorvalueenum"></a>ErrorValueEnum
Gibt den Typ des ADO-Lauf Zeit Fehlers an.  
  
 Drei Formen der Fehlernummer sind aufgeführt:  
  
-   Positives Dezimaltrennzeichen: die unteren zwei Bytes der vollständigen Zahl im Dezimal Format. Diese Zahl wird im Dialogfeld Standard-Visual Basic Fehlermeldung angezeigt. Beispiel: Laufzeitfehler "3707".  
  
-   Negatives Dezimaltrennzeichen: die Dezimal Übersetzung der vollständigen Fehlernummer.  
  
-   Hexadezimal-die hexadezimale Darstellung der vollständigen Fehlernummer. Der Windows-Einrichtungs Code ist in der vierten Ziffer. Der Einrichtungs Code für ADO-Fehlernummern ist *ein*. Beispiel: 0x800***A***0e7b.  
  
> [!NOTE]
>  OLE DB Fehler können an Ihre ADO-Anwendung übermittelt werden. Diese können in der Regel durch einen Windows-Einrichtungs Code von *4*identifiziert werden. Beispiel: 0x800***4***.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**aderrboundto-Befehl**|3707-2146824581 0x800a0e7b|Die **ActiveConnection** -Eigenschaft eines **Recordset** -Objekts, das über ein **Command** -Objekt als Quelle verfügt, kann nicht geändert werden.|  
|**aderrcannotcomplete**|3732-2146824556 0x800a0e94|Der Server kann den Vorgang nicht beenden.|  
|**aderrcantchangeconnection**|3748-2146824540 0x800a0ea4|Die Verbindung wurde verweigert. Die von Ihnen angeforderte neue Verbindung weist andere Eigenschaften auf als die, die bereits verwendet werden.|  
|**aderrcantchangeprovider**|3220-2146825068 0x800a0c94|Der angegebene Anbieter unterscheidet sich von dem bereits verwendeten Anbieter.|  
|**aderrcantconvertvalue**|3724-2146824564 0x800a0e8c|Der Datenwert kann nicht konvertiert werden, wenn keine Vorzeichen übereinstimmen oder ein Datenüberlauf vorliegt. Beispielsweise würden bei der Konvertierung Daten abgeschnitten werden.|  
|**aderrcantcreate**|3725-2146824563 0x800a0e8d|Der Datenwert kann nicht festgelegt oder abgerufen werden, weil der Feld Datentyp unbekannt war, oder der Anbieter verfügte nicht über genügend Ressourcen, um den Vorgang auszuführen.|  
|**aderrcatalognotset**|3747-2146824541 0x800a0ea3|Für den Vorgang ist ein gültiger " **Parser Catalog**" erforderlich.|  
|**aderrcolumnnotonthisrow**|3726-2146824562 0x800a0e8e|Der Datensatz enthält dieses Feld nicht.|  
|**aderrdataconversion**|3421-2146824867 0x800a0d5d|Die Anwendung verwendet einen Wert des falschen Typs für den aktuellen Vorgang.|  
|**aderrdataoverflow**|3721-2146824567 0x800a0e89|Der Datenwert ist zu groß, um durch den Feld Datentyp dargestellt zu werden.|  
|**aderrdelta resouumsscope**|3738-2146824550 0x800a0e9a|Die URL des zu löschenden Objekts liegt außerhalb des Gültigkeits Bereichs des aktuellen Datensatzes.|  
|**aderrdenynotsupported**|3750-2146824538 0x800a0ea6|Der Anbieter unterstützt keine Freigabe Einschränkungen.|  
|**aderrdenytypotsupported**|3751-2146824537 0x800a0ea7|Der Anbieter unterstützt die angeforderte Art der Freigabe Einschränkung nicht.|  
|**adErrFeatureNotAvailable**|3251-2146825037 0x800a0cb3|Das Objekt oder der Anbieter kann den angeforderten Vorgang nicht ausführen.|  
|**aderrfieldsupdatefailed**|3749-2146824539 0x800a0ea5|Fehler beim Aktualisieren der Felder. Weitere Informationen finden Sie unter Überprüfen der **Status** -Eigenschaft einzelner Feld Objekte.|  
|**aderrillegaloperation**|3219-2146825069 0x800a0c93|Der Vorgang ist in diesem Kontext nicht zulässig.|  
|**aderrintegrityverstoß**|3719-2146824569 0x800a0e87|Der Datenwert steht in Konflikt mit den Integritäts Einschränkungen des Felds.|  
|**aderrintransaction**|3246-2146825042 0x800a0cae|Das **Verbindungs** Objekt kann während einer Transaktion nicht explizit geschlossen werden.|  
|**aderrinvalidargument**|3001-2146825287 0x800a0bb9|Argumente weisen den falschen Typ auf, sind außerhalb des zulässigen Bereichs oder stehen in Konflikt zueinander.|  
|**aderrinvalidconnection**|3709-2146824579 0x800a0e7d|Die Verbindung kann nicht verwendet werden, um diesen Vorgang auszuführen. Er ist in diesem Kontext entweder geschlossen oder ungültig.|  
|**aderrinvalidparaminfo**|3708-2146824580 0x800a0e7c|Das **Parameter** Objekt ist falsch definiert. Es wurden inkonsistente oder unvollständige Informationen bereitgestellt.|  
|**aderrinvalidtransaction**|3714-2146824574 0x800a0e82|Die koordinierende Transaktion ist ungültig oder wurde nicht gestartet.|  
|**aderrinvalidurl**|3729-2146824559 0x800a0e91|Die URL enthält ungültige Zeichen. Stellen Sie sicher, dass die URL ordnungsgemäß eingegeben wurde.|  
|**aderritemnotfound**|3265-2146825023 0x800a0cc1|Das Element wurde in der Auflistung nicht gefunden, das dem angeforderten Namen oder der Ordinalzahl entspricht.|  
|**aderrnocurrentrecord**|3021-2146825267 0x800a0bcd|**BOF** oder **EOF** ist true, oder der aktuelle Datensatz wurde gelöscht. Für den angeforderten Vorgang ist ein aktueller Datensatz erforderlich.|  
|**aderrnotexecuting**|3715-2146824573 0x800a0e83|Der Vorgang kann nicht ausgeführt werden.|  
|**aderrnotreentrant**|3710-2146824578 0x800a0e7e|Der Vorgang kann nicht während der Verarbeitung des Ereignisses ausgeführt werden.|  
|**aderrobjectclosed**|3704-2146824584 0x800a0e78|Der Vorgang ist nicht zulässig, wenn das Objekt geschlossen wird.|  
|**aderrobjectincollection**|3367-2146824921 0x800a0d27|Das Objekt ist bereits in der Sammlung vorhanden. Anfügen nicht möglich.|  
|**aderrobjectnotset**|3420-2146824868 0x800a0d5c|Das Objekt ist nicht mehr gültig.|  
|**aderrobjectopen**|3705-2146824583 0x800a0e79|Der Vorgang ist nicht zulässig, wenn das Objekt geöffnet ist.|  
|**aderropingfile**|3002-2146825286 0x800a0bba|Die Datei konnte nicht geöffnet werden.|  
|**aderroperationabgeb Rochen**|3712-2146824576 0x800a0e80|Der Vorgang wurde vom Benutzer abgebrochen.|  
|**aderrouesleerraum**|3734-2146824554 0x800a0e96|Der Vorgang kann nicht ausgeführt werden. Der Anbieter kann nicht genügend Speicherplatz abrufen.|  
|**aderrpermissiondenied**|3720-2146824568 0x800a0e88|Unzureichende Berechtigungen verhindern das Schreiben in das Feld.|  
|**aderrproviderfailed**|3000-2146825288 0x800a0bb8|Der Anbieter hat den angeforderten Vorgang nicht durchgeführt.|  
|**aderrprovidernotfound**|3706-2146824582 0x800a0e7a|Der Anbieter wurde nicht gefunden. Er ist möglicherweise nicht ordnungsgemäß installiert.|  
|**aderrinfofile**|3003-2146825285 0x800a0bbb|Die Datei konnte nicht gelesen werden.|  
|**aderrresourceist vorhanden.**|3731-2146824557 0x800a0e93|Der Kopiervorgang kann nicht ausgeführt werden. Das von der Ziel-URL benannte Objekt ist bereits vorhanden. Geben Sie **AdCopyOverwrite** an, um das Objekt zu ersetzen.|  
|**aderrresourcelocked**|3730-2146824558 0x800a0e92|Das durch die angegebene URL dargestellte Objekt wird von mindestens einem Prozess gesperrt. Warten Sie, bis der Prozess abgeschlossen wurde, und wiederholen Sie dann den Vorgang.|  
|**aderrresourceouumsscope**|3735-2146824553 0x800a0e97|Die Quell-oder Ziel-URL liegt außerhalb des Gültigkeits Bereichs des aktuellen Datensatzes.|  
|**aderrschemaverletzung**|3722-2146824566 0x800a0e8a|Der Datenwert steht in Konflikt mit dem Datentyp oder den Einschränkungen des Felds.|  
|**aderrsignmismatch**|3723-2146824565 0x800a0e8b|Fehler bei der Konvertierung, da der Datenwert signiert wurde und der vom Anbieter verwendete Feld Datentyp nicht signiert wurde.|  
|**aderrstillverbindung**|3713-2146824575 0x800a0e81|Der Vorgang kann nicht ausgeführt werden, während die Verbindung asynchron hergestellt wird|  
|**aderrstillexecuting**|3711-2146824577 0x800a0e7f|Der Vorgang kann nicht ausgeführt werden, wenn asynchron ausgeführt wird.|  
|**aderrtreepermissiondenied**|3728-2146824560 0x800a0e90|Die Berechtigungen reichen nicht aus, um auf die Struktur oder Unterstruktur zuzugreifen.|  
|**aderrunavailable**|3736-2146824552 0x800a0e98|Der Vorgang wurde nicht beendet, und der Status ist nicht verfügbar. Das Feld ist möglicherweise nicht verfügbar, oder der Vorgang wurde nicht versucht.|  
|**aderrunsafeoperation**|3716-2146824572 0x800a0e84|Die Sicherheitseinstellungen auf diesem Computer verhindern den Zugriff auf eine Datenquelle in einer anderen Domäne.|  
|**aderrurldoesnotexist**|3727-2146824561 0x800a0e8f|Entweder die Quell-URL oder das übergeordnete Element der Ziel-URL ist nicht vorhanden.|  
|**aderrurlnamedrowdoesnotexist**|3737-2146824551 0x800a0e99|Der von dieser URL benannte Datensatz ist nicht vorhanden.|  
|**aderrvolumumotfound**|3733-2146824555 0x800a0e95|Der Anbieter kann das durch die URL gekennzeichnete Speichergerät nicht finden. Stellen Sie sicher, dass die URL ordnungsgemäß eingegeben wurde.|  
|**aderrschreitedatei**|3004-2146825284 0x800a0bbc|Fehler beim Schreiben in die Datei.|  
|**adwrnsecuritydialog**|3717-2146824571 0x800a0e85|Nur zur internen Verwendung. Darf nicht verwendet werden.|  
|**adwrnsecuritydialogheader**|3718-2146824570 0x800a0e86|Nur zur internen Verwendung. Darf nicht verwendet werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
 Es werden nur die folgenden Teilmengen von ADO/WFC-äquivalenten definiert.  
  
|Konstante|  
|--------------|  
|Adoenumerations. ERRORVALUE. boundto-Befehl|  
|Adoerums. ERRORVALUE. dataconversion|  
|Adoerums. ERRORVALUE. featurenotavailable|  
|Adoerums. ERRORVALUE. illegaloperation|  
|Adoerums. ERRORVALUE. InTransaction|  
|Adoerums. ERRORVALUE. invalidargument|  
|Adoerums. ERRORVALUE. invalidconnection|  
|Adoerums. ERRORVALUE. invalidparaminfo|  
|Adoerums. ERRORVALUE. ItemNotFound|  
|Adoerums. ERRORVALUE. nocurrentrecord|  
|Adoerums. ERRORVALUE. notexecuting|  
|Adoerums. ERRORVALUE. notreentrant|  
|AdoEnums. ERRORVALUE. objectclosed|  
|Adoerums. ERRORVALUE. objectincollection|  
|AdoEnums. ERRORVALUE. objectnotset|  
|Adoerums. ERRORVALUE. objectopen|  
|Adoerums. ERRORVALUE. operationabgeb Rochen|  
|Adoerums. ERRORVALUE. providernotfound|  
|Adoerums. ERRORVALUE. stillverbindung|  
|Adoerums. ERRORVALUE. StillExecuting|  
|Adoerums. ERRORVALUE. unsafeoperation|  
  
## <a name="applies-to"></a>Gilt für  
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Fehlercodes](../../../ado/guide/appendixes/ado-error-codes.md)
