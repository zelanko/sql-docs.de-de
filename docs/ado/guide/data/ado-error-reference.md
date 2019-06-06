---
title: ADO-Fehlerreferenz | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 05be5b1b9f3b23971017c74b5a6491f20ce4e49e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702783"
---
# <a name="ado-errors"></a>ADO-Fehler
Die **ErrorValueEnum** Konstante wird beschrieben, die Werte der ADO-Fehler. Eine vollständige Liste dieser Enumerationskonstanten, einschließlich der Werte finden Sie unter [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md). In diesem Abschnitt werden einige der interessanteren Fehler untersuchen und erläutert einige bestimmten Situationen, in denen sie oder Lösungen zum Beheben des Problems auslösen können. Sowohl die **ErrorValueEnum** Konstante und die kurze positive Dezimalzahl werden aufgeführt.

|Number|ErrorValueEnum-Konstante|Beschreibung/mögliche Ursachen|
|------------|-----------------------------|----------------------------------|
|**3000**|**adErrProviderFailed**|Anbieter konnte den angeforderten Vorgang auszuführen.|
|**3001**|**adErrInvalidArgument**|Argumente des falschen Typs sind, sind außerhalb des zulässigen Bereichs, oder in Konflikt miteinander stehen. Dieser Fehler wird häufig durch einen Tippfehler in einer SQL-SELECT-Anweisung verursacht. Dieser Fehler kann z. B. von einen falsch geschriebenen Feldname oder Tabellennamen generiert. Dieser Fehler kann auch auftreten, wenn ein Feld oder eine Tabelle mit dem Namen in einer SELECT-Anweisung nicht im Datenspeicher vorhanden ist.|
|**3002**|**adErrOpeningFile**|Datei konnte nicht geöffnet werden. Ein falsch geschriebenes Dateiname angegeben wurde, oder eine Datei verschoben, umbenannt oder gelöscht wurde. Über ein Netzwerk das Laufwerk ist möglicherweise vorübergehend nicht verfügbar, oder Netzwerkdatenverkehr möglicherweise verhindern, wenn Sie eine Verbindung.|
|**3003**|**adErrReadFile**|Datei konnte nicht gelesen werden. Der Name der Datei falsch angegeben wird, die Datei wurde möglicherweise verschoben oder gelöscht, oder die Datei ist möglicherweise beschädigt.|
|**3004**|**adErrWriteFile**|Datei konnte nicht beschrieben. Sie können eine Datei geschlossen haben, und versucht hat, um darin zu schreiben, oder die Datei ist möglicherweise beschädigt. Wenn die Datei auf einem Netzlaufwerk befindet, können vorübergehende Netzwerkprobleme verhindern, dass das Schreiben auf einem Netzlaufwerk.|
|**3021**|**adErrNoCurrentRecord**|Entweder **BOF** oder **EOF** ist "true" oder der aktuelle Datensatz wurde gelöscht. Der angeforderte Vorgang erfordert einen aktuellen Datensatz.<br /><br /> Es wurde versucht, zum Aktualisieren von Datensätzen mithilfe von **finden** oder **Seek** Zeiger für den Datensatz in der gewünschte Datensatz zu verschieben. Wenn der Datensatz nicht gefunden wird, **EOF** wird "true" sein. Dieser Fehler kann auch auftreten, nach einer fehlgeschlagenen **AddNew** oder **löschen** da kein aktueller Datensatz vorhanden ist, wenn diese Methoden zu Fehlern führen.|
|**3219**|**adErrIllegalOperation**|Vorgang wird in diesem Kontext nicht zulässig.|
|**3220**|**adErrCantChangeProvider**|Der angegebene Anbieter unterscheidet sich von den bereits in Verwendung.|
|**3246**|**adErrInTransaction**|**Verbindung** Objekt kann nicht in einer Transaktion explizit geschlossen werden. Ein **Recordset** oder **Verbindung** -Objekt, das derzeit in einer Transaktion beteiligt ist, kann nicht geschlossen werden. Rufen Sie entweder **RollbackTrans** oder **CommitTrans** vor dem Schließen des Objekts.|
|**3251**|**adErrFeatureNotAvailable**|Das Objekt oder der Anbieter ist nicht den angeforderten Vorgang ausführen kann. Einige Vorgänge hängen von einer bestimmten Anbieterversion ab.|
|**3265**|**adErrItemNotFound**|Element kann nicht in der Auflistung entspricht der angeforderte Name oder Ordinalzahl gefunden werden. Ein falscher Name für Feld oder eine Tabelle wurde angegeben.|
|**3367**|**adErrObjectInCollection**|Objekt ist bereits in der Auflistung. Kann nicht angefügt werden. Ein Objekt kann nicht zweimal dieselbe Sammlung hinzugefügt werden.|
|**3420**|**adErrObjectNotSet**|Objekt ist nicht mehr gültig.|
|**3421**|**adErrDataConversion**|Anwendung verwendet einen Wert des falschen Typs für den aktuellen Vorgang. Sie können eine Zeichenfolge, die einen Vorgang angegeben haben, die einen Stream, z. B. erwartet.|
|**3704**|**adErrObjectClosed**|Vorgang ist nicht zulässig, wenn das Objekt geschlossen wird. Die **Verbindung** oder **Recordset** wurde geschlossen. Beispielsweise kann eine andere Routine ein globales Objekt geschlossen haben. Sie können diesen Fehler verhindern, indem Sie überprüfen die **Zustand** Eigenschaft, bevor Sie, einen Vorgang versuchen.|
|**3705**|**adErrObjectOpen**|Vorgang ist nicht zulässig, wenn das Objekt geöffnet ist. Ein Objekt, das geöffnet ist, kann nicht geöffnet werden. Felder kann nicht angefügt werden, um ein offenes **Recordset**.|
|**3706**|**adErrProviderNotFound**|Anbieter wurde nicht gefunden. Es ist möglicherweise nicht ordnungsgemäß installiert.<br /><br /> Der Name des Anbieters möglicherweise nicht ordnungsgemäß angegeben werden, die der angegebene Anbieter möglicherweise nicht installiert werden, auf dem Computer, in denen Ihr Code ausgeführt wird, oder die Installation ist möglicherweise beschädigt.|
|**3707**|**adErrBoundToCommand**|Die **ActiveConnection** Eigenschaft eine **Recordset** -Objekt, das verfügt über eine **Befehl** Objekt als Quelle, nicht geändert werden. Die Anwendung hat versucht, ein neues weisen **Verbindung** -Objekt an eine **Recordset** , bei dem ein **Befehl** Objekt als Quelle.|
|**3708**|**adErrInvalidParamInfo**|**Parameter** Objekt ist nicht ordnungsgemäß definiert. Inkonsistente oder unvollständige Informationen wurden bereitgestellt.|
|**3709**|**adErrInvalidConnection**|Die Verbindung kann nicht verwendet werden, um diesen Vorgang auszuführen. Es ist entweder geschlossen oder in diesem Kontext ungültig.|
|**3710**|**adErrNotReentrant**|Vorgang kann nicht beim Verarbeiten des Ereignisses ausgeführt werden. Ein Vorgang kann nicht in einem Ereignishandler ausgeführt werden, die das Ereignis erneut ausgelöst. Z. B. Navigationsmethoden sollte nicht aufgerufen werden innerhalb einer **WillMove** -Ereignishandler.|
|**3711**|**adErrStillExecuting**|Vorgang kann nicht ausgeführt werden, während der asynchron ausgeführt wird.|
|**3712**|**adErrOperationCancelled**|Vorgang wurde vom Benutzer abgebrochen. Die Anwendung nennt die **CancelUpdate** oder **CancelBatch** -Methode und der aktuelle Vorgang wurde abgebrochen.|
|**3713**|**adErrStillConnecting**|Vorgang kann nicht ausgeführt werden, während eine asynchrone Verbindung.|
|**3714**|**adErrInvalidTransaction**|Koordinieren die Transaktion ist ungültig oder wurde nicht gestartet.|
|**3715**|**adErrNotExecuting**|Vorgang kann nicht ausgeführt werden, während der Ausführung nicht.|
|**3716**|**adErrUnsafeOperation**|Sicherheitseinstellungen dieses Computers lassen den Zugriff auf eine Datenquelle in einer anderen Domäne.|
|**3717**|**adWrnSecurityDialog**|Nur zur internen Verwendung. Verwenden Sie nicht. (Ein Metadateneintrag wurde aus Gründen der Vollständigkeit enthalten. Dieser Fehler sollte nicht in Ihrem Code angezeigt werden.)|
|**3718**|**adWrnSecurityDialogHeader**|Nur zur internen Verwendung. Verwenden Sie nicht. (Eintrag der Vollständigkeit halber enthalten. Dieser Fehler sollte nicht in Ihrem Code angezeigt werden.)|
|**3719**|**adErrIntegrityViolation**|Datenwert verursacht einen Konflikt mit den Einschränkungen der Integrität des Felds. Einen neuen Wert für eine **Feld** würde dazu führen, dass einen doppelten Schlüssel. Ein Wert, der eine Seite einer Beziehung zwischen zwei Datensätzen forms kann nicht aktualisiert werden.|
|**3720**|**adErrPermissionDenied**|Unzureichende Berechtigungen wird verhindert, dass das Schreiben in das Feld. Der Benutzer, die mit dem Namen in der Verbindungszeichenfolge verfügt nicht über die erforderlichen Berechtigungen zum Schreiben in eine **Feld**.|
|**3721**|**adErrDataOverflow**|Datenwert ist zu groß, um durch den Datentyp des Felds dargestellt werden. Ein numerischer Wert, der zu groß für das vorgesehene Feld zugewiesen wurde. Ein langer ganzzahliger Wert wurde z. B. ein short Integer-Wert-Feld zugewiesen.|
|**3722**|**adErrSchemaViolation**|Datenwert verursacht einen Konflikt mit dem Datentyp oder die Einschränkungen des Felds. Der Datenspeicher wurde validierungseinschränkungen, die von abweichen der **Feld** Wert.|
|**3723**|**adErrSignMismatch**|Fehler bei der Konvertierung, da der Datenwert mit Vorzeichen handelte und der vom Anbieter verwendeten Datentyp des Felds kein Vorzeichen hatte.|
|**3724**|**adErrCantConvertvalue**|Datenwert kann nicht für den Datenüberlauf stimmt nicht überein oder Daten konvertiert werden. Z. B. würden Konvertierung Daten abgeschnitten.|
|**3725**|**adErrCantCreate**|Datenwert kann nicht festgelegt oder abgerufen werden, da der Datentyp des Felds unbekannt ist, oder der Anbieter nicht genügend Ressourcen zum Ausführen des Vorgangs musste.|
|**3726**|**adErrColumnNotOnThisRow**|Datensatz enthält dieses Feld nicht. Wurde ein falscher Feldname angegeben oder ein Feld nicht in der **Felder** Auflistung von den aktuellen Datensatz wurde auf die verwiesen wird.|
|**3727**|**adErrURLDoesNotExist**|Entweder die Quell-URL oder das übergeordnete Element der Ziel-URL ist nicht vorhanden. Es ist Rechtschreibfehlern in der Quelle oder das Ziel-URL ein. Sie müssen möglicherweise `https://mysite/photo/myphoto.jpg` Wenn tatsächlich müssen Sie `https://mysite/photos/myphoto.jpg` stattdessen. Der Tippfehler in die übergeordnete URL (in diesem Fall *Foto* anstelle von *Fotos*) hat den Fehler verursacht.|
|**3728**|**adErrTreePermissionDenied**|Berechtigungen sind nicht ausreichend, um die Struktur oder Teilstruktur zugreifen. Der Benutzer, die mit dem Namen in der Verbindungszeichenfolge besitzt nicht die entsprechenden Berechtigungen.|
|**3729**|**adErrInvalidURL**|URL enthält ungültige Zeichen. Stellen Sie sicher, dass die URL richtig eingegeben wurde. Die URL folgt das Schema für den aktuellen Anbieter registriert (z. B. Internet Publishing-Anbieter für http registriert ist).|
|**3730**|**adErrResourceLocked**|Objekt, das dargestellt durch die angegebene URL wird von einem oder mehreren Prozessen gesperrt. Warten Sie, bis der Vorgang abgeschlossen wurde, und wiederholen Sie den Vorgang. Das Objekt, das Sie zugreifen möchten wurde von einem anderen Benutzer oder von einem anderen Prozess in Ihrer Anwendung gesperrt. Dies ist höchstwahrscheinlich in einer mehrbenutzerumgebung auftreten.|
|**3731**|**adErrResourceExists**|Copy-Vorgang kann nicht ausgeführt werden. Objekt mit dem Namen von Ziel-URL bereits vorhanden ist. Geben Sie **AdCopyOverwrite** auf das Objekt zu ersetzen. Wenn Sie keinen angeben **AdCopyOverwrite** beim Kopieren von Dateien in einem Verzeichnis, von der Kopiervorgang schlägt fehl, wenn Sie versuchen, ein Element zu kopieren, die bereits am Ziel vorhanden ist.|
|**3732**|**adErrCannotComplete**|Der Server kann nicht der Vorgang abgeschlossen. Dies kann sein, da der Server ausgelastet mit anderen Vorgängen ist oder ist es möglicherweise nicht über genügend Ressourcen.|
|**3733**|**adErrVolumeNotFound**|Anbieter wurde nicht gefunden für das Speichergerät, das von der URL angegeben. Stellen Sie sicher, dass die URL richtig eingegeben wurde. Die URL des Speichergeräts ist möglicherweise falsch, aber dieser Fehler kann aus anderen Gründen auftreten. Das Gerät ist möglicherweise offline, oder eine große Anzahl von Netzwerkdatenverkehr verhindern, dass die Verbindung ausgeführt wird.|
|**3734**|**adErrOutOfSpace**|Vorgang kann nicht ausgeführt werden. -Anbieter kann nicht genügend Speicherplatz verfügbar. Es ist möglicherweise nicht genügend Arbeitsspeicher oder Festplattenspeicherplatz für temporäre Dateien auf dem Server.|
|**3735**|**adErrResourceOutOfScope**|Quelle oder Ziel-URL ist außerhalb des Bereichs des aktuellen Datensatzes.|
|**3736**|**adErrUnavailable**|Vorgang konnte nicht abgeschlossen, und der Status ist nicht verfügbar. Das Feld darf nicht mehr verfügbar sein, oder der Vorgang wurde nicht gestartet. Ein anderer Benutzer möglicherweise geändert oder gelöscht des Felds, das Sie zugreifen möchten.|
|**3737**|**adErrURLNamedRowDoesNotExist**|Datensatz mit dem Namen der von dieser URL ist nicht vorhanden. Beim Öffnen einer Datei mit einem **Datensatz** Objekt entweder den Dateinamen oder den Pfad zu der Datei wurde falsch geschrieben.|
|**3738**|**adErrDelResOutOfScope**|Die URL des Objekts gelöscht werden soll, ist außerhalb des Bereichs des aktuellen Datensatzes.|
|**3747**|**adErrCatalogNotSet**|Vorgang erfordert, dass ein gültiger **ParentCatalog**.|
|**3748**|**adErrCantChangeConnection**|Verbindung wurde verweigert. Die neue Verbindung, die Sie angefordert hat, andere Merkmale als die bereits in Verwendung.|
|**3749**|**adErrFieldsUpdateFailed**|Fehler beim Aktualisieren der Felder. Weitere Informationen zu untersuchen der **Status** -Eigenschaft der einzelnen Felds-Objekte. Dieser Fehler kann in zwei Situationen auftreten: beim Ändern einer **Feld** Wert des Objekts gerade ändern oder Hinzufügen eines Datensatzes mit der Datenbank und beim Ändern der Eigenschaften der **Feld** Objekt selbst.<br /><br /> Die **Datensatz** oder **Recordset** Updatefehler aufgrund eines Problems mit einem der Felder im aktuellen Datensatz. Auflisten der **Felder** Sammlung und überprüfen Sie die **Status** Eigenschaft jedes Felds, um die Ursache des Problems zu ermitteln.|
|**3750**|**adErrDenyNotSupported**|Anbieter unterstützt keine freigabebeschränkungen. Es wurde versucht, die Dateifreigabe einzuschränken, und Ihr Anbieter unterstützt nicht das Konzept.|
|**3751**|**adErrDenyTypeNotSupported**|Anbieter unterstützt nicht die angeforderte Art der Freigabe der Einschränkung. Es wurde versucht, einen bestimmten Typ von der Dateifreigabe herstellen Einschränkung, die von Ihrem Anbieter nicht unterstützt wird. Finden Sie unter der Dokumentation des Anbieters zu bestimmen, welche Dateifreigabe Einschränkungen unterstützt werden.|
