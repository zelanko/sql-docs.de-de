---
title: FieldStatusEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldStatusEnum
helpviewer_keywords:
- FieldStatusEnum enumeration [ADO]
ms.assetid: e06da1e2-303f-41b2-a3b0-61e233da152c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1ba7fe546f7ac8e1a036fc8fe7e5f523ebf09d4c
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719208"
---
# <a name="fieldstatusenum"></a>FieldStatusEnum
Gibt an, die [Status](../../../ado/reference/ado-api/status-property-ado-field.md) von einem [Feldobjekt](../../../ado/reference/ado-api/field-object.md).  
  
 Die **AdFieldPending\***  Werte geben an, den Vorgang, die aufgrund des Status festgelegt werden soll, und kann mit anderen Statuswerte kombiniert werden.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adFieldAlreadyExists**|26|Gibt an, dass das angegebene Feld ist bereits vorhanden.|  
|**adFieldBadStatus**|12|Gibt an, dass ein gültiger Wert von ADO, OLE DB-Anbieter gesendet wurde. Mögliche Ursachen, ein OLE DB-1.0 oder 1.1-Anbieter oder eine falsche Kombination von [Wert](../../../ado/reference/ado-api/value-property-ado.md) und [Status](../../../ado/reference/ado-api/status-property-ado-field.md).|  
|**adFieldCannotComplete**|20|Gibt an, dass der Server, der URL angegeben [Quelle](../../../ado/reference/ado-api/source-property-ado-record.md) den Vorgang konnte nicht abgeschlossen werden.|  
|**adFieldCannotDeleteSource**|23|Gibt an, dass bei einem Verschiebungsvorgang, eine Struktur oder ein Unterverzeichnis an einem neuen Speicherort verschoben wurde, aber die Quelle nicht gelöscht werden konnte.|  
|**adFieldCantConvertValue**|2|Gibt an, dass das Feld kann nicht abgerufen oder ohne Verlust von Daten gespeichert werden.|  
|**adFieldCantCreate**|7|Gibt an, dass das Feld nicht hinzugefügt werden konnte, da der Anbieter eine Einschränkung (z. B. die Anzahl der Felder zulässig) überschreiten.|  
|**adFieldDataOverflow**|6|Gibt an, dass die vom Anbieter zurückgegebenen Daten den Datentyp des Felds ist ein Überlauf aufgetreten.|  
|**adFieldDefault**|13|Gibt an, dass der Standardwert für das Feld, beim Festlegen der Daten verwendet wurde.|  
|**adFieldDoesNotExist**|16|Gibt an, dass das angegebene Feld nicht vorhanden ist.|  
|**adFieldIgnore**|15|Gibt an, dass dieses Feld bei der Einstellung Datenwerte in der Quelle übersprungen wurde. Der Anbieter legen Sie keinen Wert.|  
|**adFieldIntegrityViolation**|10|Gibt an, dass das Feld kann nicht geändert werden, da es sich um eine Entität berechneter oder abgeleiteter handelt.|  
|**adFieldInvalidURL**|17|Gibt an, dass die URL der Datenquelle ungültige Zeichen enthält.|  
|**adFieldIsNull**|3|Gibt an, dass der Anbieter einen VARIANT-Wert des Typs VT_NULL zurückgegeben und das Feld nicht leer ist.|  
|**adFieldOK**|0|Standard. Gibt an, dass das Feld wurde erfolgreich hinzugefügt oder gelöscht wurde.|  
|**adFieldOutOfSpace**|22|Gibt an, dass der Anbieter ist nicht genügend Speicherplatz zum Abschließen eines Verschiebe- oder Kopiervorgang zu erhalten.|  
|**adFieldPendingChange**|0x40000|Gibt an, entweder, der das Feld wurde gelöscht und anschließend erneut hinzugefügt, z. B. mit einem anderen Datentyp oder, die den Wert des Felds, das bisher einen Status von **AdFieldOK** hat sich geändert. Das endgültige Format des Felds ändert die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Sammlung nach der [Update](../../../ado/reference/ado-api/update-method.md) Methode wird aufgerufen.|  
|**adFieldPendingDelete**|0x20000|Gibt an, dass die **löschen** Vorgang verursacht hat, den Status festgelegt werden. Das Feld für die Löschung markiert die **Felder** Sammlung nach der **Update** Methode wird aufgerufen.|  
|**adFieldPendingInsert**|0x10000|Gibt an, dass die **Append** Vorgang verursacht hat, den Status festgelegt werden. Die **Feld** markiert, hinzugefügt werden soll die **Felder** Auflistung nach der **Update** Methode wird aufgerufen.|  
|**adFieldPendingUnknown**|0x80000|Gibt an, dass der Anbieter nicht bestimmen kann, welche Status des Vorgangs-Feld festgelegt werden.|  
|**adFieldPendingUnknownDelete**|0x100000|Gibt an, dass der Anbieter nicht bestimmen kann, welcher Vorgang verursacht hat, Feldstatus festgelegt werden, und das Feld aus gelöscht wird die **Felder** Sammlung nach der **Update** Methode wird aufgerufen.|  
|**adFieldPermissionDenied**|9|Gibt an, dass das Feld kann nicht geändert werden, da sie als schreibgeschützt definiert ist.|  
|**adFieldReadOnly**|24|Gibt an, dass das Feld in der Datenquelle als schreibgeschützt definiert ist.|  
|**adFieldResourceExists**|19|Gibt an, dass der Anbieter konnte nicht zum Ausführen des Vorgangs, da ein Objekt bereits vorhanden, an die Ziel-URL ist, und es nicht auf das Objekt überschrieben kann.|  
|**adFieldResourceLocked**|18|Gibt an, dass der Anbieter konnte nicht zum Ausführen des Vorgangs, da die Datenquelle durch mindestens eine andere Anwendung oder den Prozess gesperrt ist.|  
|**adFieldResourceOutOfScope**|25|Gibt an, dass eine Quelle oder Ziel-URL außerhalb des Bereichs des aktuellen Datensatzes.|  
|**adFieldSchemaViolation**|11|Gibt an, dass der Wert der Schema-Einschränkung für das Feld verletzt.|  
|**adFieldSignMismatch**|5|Gibt an, dass die vom Anbieter zurückgegebene Datenwert mit Vorzeichen handelte, aber der Datentyp des Feldwerts ADO kein Vorzeichen hatte.|  
|**adFieldTruncated**|4|Gibt an, dass die Daten mit variabler Länge abgeschnitten wurden, beim Lesen aus der Datenquelle.|  
|**adFieldUnavailable**|8|Gibt an, dass der Anbieter den Wert beim Lesen aus der Datenquelle nicht ermitteln konnte. Zum Beispiel die Zeile wurde gerade erstellt haben, der Standardwert für die Spalte war nicht verfügbar und ein neuer Wert mussten noch nicht angegeben wurde.|  
|**adFieldVolumeNotFound**|21|Gibt an, dass der Anbieter wurde nicht gefunden des Speichervolumes, die von der URL angegeben ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Status-Eigenschaft (ADO Field)](../../../ado/reference/ado-api/status-property-ado-field.md)
