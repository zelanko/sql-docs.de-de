---
title: ADO-Fehler Referenz | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], number reference
- errors [ADO], ErrorValueEnum
- ErrorValueEnum enumeration [ADO]
ms.assetid: f653393e-d4b0-4c34-ad5f-2bdf56bc1305
author: rothja
ms.author: jroth
ms.openlocfilehash: 774a1c17f579c9274b700e4e1fea682cc462ed29
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761386"
---
# <a name="ado-errors"></a>ADO-Fehler
Die **ErrorValueEnum** -Konstante beschreibt die ADO-Fehler Werte. Eine umfassende Auflistung dieser Enumerationskonstanten, einschließlich der Werte, finden Sie unter [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md). In diesem Abschnitt werden einige der interessanteren Fehler erläutert und einige bestimmte Situationen erläutert, die Sie lösen können, oder Lösungen zur Behebung des Problems. Die " **ErrorValueEnum** "-Konstante und die kurze positive Dezimalzahl werden aufgelistet.

|Number|ErrorValueEnum-Konstante|Beschreibung/mögliche Ursachen|
|------------|-----------------------------|----------------------------------|
|**3000**|**aderrproviderfailed**|Der Anbieter konnte den angeforderten Vorgang nicht ausführen.|
|**3001**|**aderrinvalidargument**|Argumente weisen den falschen Typ auf, sind außerhalb des zulässigen Bereichs oder stehen in Konflikt zueinander. Dieser Fehler wird häufig durch einen typografischen Fehler in einer SQL-SELECT-Anweisung verursacht. Beispielsweise kann dieser Fehler durch einen falsch geschriebenen Feldnamen oder einen Tabellennamen generiert werden. Dieser Fehler kann auch auftreten, wenn ein Feld oder eine Tabelle in einer SELECT-Anweisung nicht im Datenspeicher vorhanden ist.|
|**3002**|**aderropingfile**|Die Datei konnte nicht geöffnet werden. Ein falsch geschriebener Dateiname wurde angegeben, oder eine Datei wurde verschoben, umbenannt oder gelöscht. Über ein Netzwerk ist das Laufwerk möglicherweise vorübergehend nicht verfügbar, oder der Netzwerk Datenverkehr verhindert eine Verbindung.|
|**3003**|**aderrinfofile**|Die Datei konnte nicht gelesen werden. Der Name der Datei ist falsch angegeben, die Datei wurde möglicherweise verschoben oder gelöscht, oder die Datei ist beschädigt.|
|**3004**|**aderrschreitedatei**|Fehler beim Schreiben in die Datei. Möglicherweise haben Sie eine Datei geschlossen und versucht, in Sie zu schreiben, oder die Datei ist beschädigt. Wenn sich die Datei auf einem Netzlaufwerk befindet, kann das Schreiben auf ein Netzwerklaufwerk durch vorübergehende Netzwerkbedingungen verhindert werden.|
|**3021**|**aderrnocurrentrecord**|**BOF** oder **EOF** ist true, oder der aktuelle Datensatz wurde gelöscht. Für den angeforderten Vorgang ist ein aktueller Datensatz erforderlich.<br /><br /> Es wurde versucht, Daten **Sätze mithilfe von** **Suchen oder suchen** zu aktualisieren, um den Daten Satz Zeiger in den gewünschten Datensatz zu verschieben. Wenn der Datensatz nicht gefunden wird, ist **EOF** true. Dieser Fehler kann auch nach einem fehlgeschlagenen **AddNew** -oder **Delete** -Vorgang auftreten, da kein aktueller Datensatz vorhanden ist, wenn diese Methoden fehlschlagen.|
|**3219**|**aderrillegaloperation**|Der Vorgang ist in diesem Kontext nicht zulässig.|
|**3220**|**aderrcantchangeprovider**|Der angegebene Anbieter unterscheidet sich von dem bereits verwendeten Anbieter.|
|**3246**|**aderrintransaction**|Das **Verbindungs** Objekt kann während einer Transaktion nicht explizit geschlossen werden. Ein **Recordset** oder **Verbindungs** Objekt, das zurzeit an einer Transaktion teilnimmt, kann nicht geschlossen werden. Vor dem Schließen des Objekts wird entweder " **RollbackTrans** " oder " **CommitTrans** " aufgerufen.|
|**3251**|**adErrFeatureNotAvailable**|Das Objekt oder der Anbieter ist nicht in der Lage, den angeforderten Vorgang auszuführen. Einige Vorgänge hängen von einer bestimmten Anbieter Version ab.|
|**3265**|**aderritemnotfound**|Das Element wurde in der Auflistung nicht gefunden, das dem angeforderten Namen oder der Ordinalzahl entspricht. Ein fehlerhafter Feld-oder Tabellenname wurde angegeben.|
|**3367**|**aderrobjectincollection**|Das Objekt ist bereits in der Sammlung vorhanden. Anfügen nicht möglich. Ein Objekt kann nicht zweimal zur gleichen Sammlung hinzugefügt werden.|
|**3420**|**aderrobjectnotset**|Das Objekt ist nicht mehr gültig.|
|**3421**|**aderrdataconversion**|Die Anwendung verwendet einen Wert des falschen Typs für den aktuellen Vorgang. Möglicherweise haben Sie eine Zeichenfolge für einen Vorgang bereitgestellt, der beispielsweise einen Stream erwartet.|
|**3704**|**aderrobjectclosed**|Der Vorgang ist nicht zulässig, wenn das Objekt geschlossen wird. Die **Verbindung** oder das **Recordset** wurde geschlossen. Beispielsweise kann eine andere Routine ein globales Objekt geschlossen haben. Sie können diesen Fehler vermeiden, indem Sie die **State** -Eigenschaft überprüfen, bevor Sie einen Vorgang versuchen.|
|**3705**|**aderrobjectopen**|Der Vorgang ist nicht zulässig, wenn das Objekt geöffnet ist. Ein Objekt, das geöffnet ist, kann nicht geöffnet werden. Felder können nicht an ein geöffnetes **Recordset**angehängt werden.|
|**3706**|**aderrprovidernotfound**|Der Anbieter wurde nicht gefunden. Er ist möglicherweise nicht ordnungsgemäß installiert.<br /><br /> Möglicherweise ist der Name des Anbieters falsch angegeben, der angegebene Anbieter ist möglicherweise nicht auf dem Computer installiert, auf dem der Code ausgeführt wird, oder die Installation wurde beschädigt.|
|**3707**|**aderrboundto-Befehl**|Die **ActiveConnection** -Eigenschaft eines **Recordset** -Objekts, das über ein **Command** -Objekt als Quelle verfügt, kann nicht geändert werden. Die Anwendung hat versucht, ein neues **Verbindungs** Objekt einem **Recordset** zuzuweisen, das über ein **Command** -Objekt als Quelle verfügt.|
|**3708**|**aderrinvalidparaminfo**|Das **Parameter** Objekt ist nicht ordnungsgemäß definiert. Es wurden inkonsistente oder unvollständige Informationen bereitgestellt.|
|**3709**|**aderrinvalidconnection**|Die Verbindung kann nicht verwendet werden, um diesen Vorgang auszuführen. Er ist in diesem Kontext entweder geschlossen oder ungültig.|
|**3710**|**aderrnotreentrant**|Der Vorgang kann nicht während der Verarbeitung des Ereignisses ausgeführt werden. Ein Vorgang kann nicht innerhalb eines Ereignis Handlers ausgeführt werden, der bewirkt, dass das Ereignis erneut ausgelöst wird. Beispielsweise sollten Navigationsmethoden nicht innerhalb eines **WillMove** -Ereignis Handlers aufgerufen werden.|
|**3711**|**aderrstillexecuting**|Der Vorgang kann nicht ausgeführt werden, wenn asynchron ausgeführt wird.|
|**3712**|**aderroperationabgeb Rochen**|Der Vorgang wurde vom Benutzer abgebrochen. Die Anwendung hat die **CancelUpdate** -oder **CancelBatch** -Methode aufgerufen, und der aktuelle Vorgang wurde abgebrochen.|
|**3713**|**aderrstillverbindung**|Der Vorgang kann nicht ausgeführt werden, während die Verbindung asynchron hergestellt wird|
|**3714**|**aderrinvalidtransaction**|Die koordinierende Transaktion ist ungültig oder wurde nicht gestartet.|
|**3715**|**aderrnotexecuting**|Der Vorgang kann nicht ausgeführt werden.|
|**3716**|**aderrunsafeoperation**|Die Sicherheitseinstellungen auf diesem Computer verhindern den Zugriff auf eine Datenquelle in einer anderen Domäne.|
|**3717**|**adwrnsecuritydialog**|Nur zur internen Verwendung. Verwenden Sie nicht. (Der Eintrag wurde aus Gründen der Vollständigkeit eingeschlossen. Dieser Fehler sollte nicht in Ihrem Code angezeigt werden.)|
|**3718**|**adwrnsecuritydialogheader**|Nur zur internen Verwendung. Verwenden Sie nicht. (Der Eintrag ist aus Gründen der Vollständigkeit enthalten. Dieser Fehler sollte nicht in Ihrem Code angezeigt werden.)|
|**3719**|**aderrintegrityverstoß**|Der Datenwert steht in Konflikt mit den Integritäts Einschränkungen des Felds. Ein neuer Wert für ein **Feld** führt zu einem doppelten Schlüssel. Ein Wert, der eine Seite einer Beziehung zwischen zwei Datensätzen bildet, ist möglicherweise nicht aktualisierbar.|
|**3720**|**aderrpermissiondenied**|Unzureichende Berechtigungen verhindern das Schreiben in das Feld. Der Benutzer, der in der Verbindungs Zeichenfolge benannt ist, verfügt nicht über die erforderlichen Berechtigungen, um in ein **Feld**zu schreiben.|
|**3721**|**aderrdataoverflow**|Der Datenwert ist zu groß, um durch den Feld Datentyp dargestellt zu werden. Ein numerischer Wert, der für das vorgesehene Feld zu groß ist, wurde zugewiesen. Ein Long Integer-Wert wurde z. b. einem kurzen ganzzahligen Feld zugewiesen.|
|**3722**|**aderrschemaverletzung**|Der Datenwert steht in Konflikt mit dem Datentyp oder den Einschränkungen des Felds. Der Datenspeicher weist Validierungs Einschränkungen auf, die sich vom **Feldwert** unterscheiden.|
|**3723**|**aderrsignmismatch**|Fehler bei der Konvertierung, da der Datenwert signiert wurde und der vom Anbieter verwendete Feld Datentyp nicht signiert wurde.|
|**3724**|**aderrcantconvertvalue**|Der Datenwert kann nicht konvertiert werden, wenn keine Vorzeichen übereinstimmen oder ein Datenüberlauf vorliegt. Beispielsweise würden bei der Konvertierung Daten abgeschnitten werden.|
|**3725**|**aderrcantcreate**|Der Datenwert kann nicht festgelegt oder abgerufen werden, weil der Feld Datentyp unbekannt war, oder der Anbieter verfügte nicht über genügend Ressourcen, um den Vorgang auszuführen.|
|**3726**|**aderrcolumnnotonthisrow**|Der Datensatz enthält dieses Feld nicht. Es wurde ein falscher Feldname angegeben, oder es wurde auf ein Feld verwiesen, das nicht in der **Fields** -Auflistung des aktuellen Datensatzes liegt.|
|**3727**|**aderrurldoesnotexist**|Entweder die Quell-URL oder das übergeordnete Element der Ziel-URL ist nicht vorhanden. Ein typografischer Fehler ist entweder in der Quell-oder der Ziel-URL aufgetreten. Sie verfügen möglicherweise über eine solche, die `https://mysite/photo/myphoto.jpg` Sie stattdessen verwenden sollten `https://mysite/photos/myphoto.jpg` . Der typografische Fehler in der übergeordneten URL (in diesem Fall *Foto* anstelle von *Fotos*) hat den Fehler verursacht.|
|**3728**|**aderrtreepermissiondenied**|Die Berechtigungen reichen nicht aus, um auf die Struktur oder Unterstruktur zuzugreifen. Der Benutzer, der in der Verbindungs Zeichenfolge benannt ist, verfügt nicht über die entsprechenden Berechtigungen.|
|**3729**|**aderrinvalidurl**|Die URL enthält ungültige Zeichen. Stellen Sie sicher, dass die URL ordnungsgemäß eingegeben wurde. Die URL folgt dem Schema, das für den aktuellen Anbieter registriert ist (z. b. wenn der Internet Publishing Provider für http registriert ist).|
|**3730**|**aderrresourcelocked**|Das durch die angegebene URL dargestellte Objekt wird von mindestens einem Prozess gesperrt. Warten Sie, bis der Prozess abgeschlossen wurde, und wiederholen Sie dann den Vorgang. Das Objekt, auf das Sie zugreifen möchten, wurde von einem anderen Benutzer oder einem anderen Prozess in der Anwendung gesperrt. Dies wird höchstwahrscheinlich in einer Umgebung mit mehreren Benutzern auftreten.|
|**3731**|**aderrresourceist vorhanden.**|Der Kopiervorgang kann nicht ausgeführt werden. Das von der Ziel-URL benannte Objekt ist bereits vorhanden. Geben Sie **AdCopyOverwrite** an, um das Objekt zu ersetzen. Wenn Sie **AdCopyOverwrite** beim Kopieren der Dateien in einem Verzeichnis nicht angeben, tritt beim Kopieren ein Fehler auf, wenn Sie versuchen, ein Element zu kopieren, das bereits am Ziel Speicherort vorhanden ist.|
|**3732**|**aderrcannotcomplete**|Der Server kann den Vorgang nicht fertigstellen. Der Grund hierfür könnte sein, dass der Server mit anderen Vorgängen ausgelastet ist oder nicht über ausreichend Ressourcen verfügt.|
|**3733**|**aderrvolumumotfound**|Der Anbieter kann das durch die URL gekennzeichnete Speichergerät nicht finden. Stellen Sie sicher, dass die URL ordnungsgemäß eingegeben wurde. Die URL des Speichergeräts ist möglicherweise falsch, aber dieser Fehler kann aus anderen Gründen auftreten. Das Gerät ist möglicherweise offline, oder es kann eine große Menge an Netzwerk Datenverkehr verhindern, dass die Verbindung hergestellt wird.|
|**3734**|**aderrouesleerraum**|Der Vorgang kann nicht ausgeführt werden. Der Anbieter kann nicht genügend Speicherplatz abrufen. Auf dem Server ist möglicherweise nicht genügend RAM oder Festplatten Speicherplatz für temporäre Dateien vorhanden.|
|**3735**|**aderrresourceouumsscope**|Die Quell-oder Ziel-URL liegt außerhalb des Gültigkeits Bereichs des aktuellen Datensatzes.|
|**3.736**|**aderrunavailable**|Der Vorgang konnte nicht ausgeführt werden, und der Status ist nicht verfügbar. Das Feld ist möglicherweise nicht verfügbar, oder der Vorgang wurde nicht versucht. Möglicherweise hat ein anderer Benutzer das Feld, auf das Sie zugreifen möchten, geändert oder gelöscht.|
|**3737**|**aderrurlnamedrowdoesnotexist**|Der von dieser URL benannte Datensatz ist nicht vorhanden. Beim Versuch, eine Datei mithilfe eines **Datensatz** -Objekts zu öffnen, wurde entweder der Dateiname oder der Pfad zur Datei falsch geschrieben.|
|**3738**|**aderrdelta resouumsscope**|Die URL des zu löschenden Objekts liegt außerhalb des Gültigkeits Bereichs des aktuellen Datensatzes.|
|**3747**|**aderrcatalognotset**|Für den Vorgang ist ein gültiger " **Parser Catalog**" erforderlich.|
|**3748**|**aderrcantchangeconnection**|Die Verbindung wurde verweigert. Die von Ihnen angeforderte neue Verbindung weist andere Eigenschaften auf als die bereits verwendete.|
|**3749**|**aderrfieldsupdatefailed**|Fehler beim Aktualisieren der Felder. Weitere Informationen finden Sie unter Überprüfen der **Status** -Eigenschaft einzelner Feld Objekte. Dieser Fehler kann in zwei Situationen auftreten: beim Ändern des Werts eines **Feld** Objekts beim Ändern oder Hinzufügen eines Datensatzes zur Datenbank. und wenn die Eigenschaften des **Feld** Objekts selbst geändert werden.<br /><br /> Das **Datensatz** -oder **recordsetupdate** ist aufgrund eines Problems mit einem der Felder im aktuellen Datensatz fehlgeschlagen. Auflisten der **Fields** -Auflistung und Überprüfen der **Status** -Eigenschaft jedes Felds, um die Ursache des Problems zu ermitteln.|
|**3750**|**aderrdenynotsupported**|Der Anbieter unterstützt keine Freigabe Einschränkungen. Es wurde versucht, die Dateifreigabe einzuschränken, und Ihr Anbieter unterstützt das Konzept nicht.|
|**3751**|**aderrdenytypotsupported**|Der Anbieter unterstützt die angeforderte Art der Freigabe Einschränkung nicht. Es wurde versucht, eine bestimmte Art von Dateifreigabe Einschränkung einzurichten, die von Ihrem Anbieter nicht unterstützt wird. In der Dokumentation des Anbieters können Sie feststellen, welche Einschränkungen für die Dateifreigabe unterstützt werden.|
