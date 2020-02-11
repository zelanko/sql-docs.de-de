---
title: Fieldstatus usenum | Microsoft-Dokumentation
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
ms.openlocfilehash: d3ad005a4c26a033f6c97d97def4cd55d867c14e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918665"
---
# <a name="fieldstatusenum"></a>FieldStatusEnum
Gibt den [Status](../../../ado/reference/ado-api/status-property-ado-field.md) eines [Feld Objekts](../../../ado/reference/ado-api/field-object.md)an.  
  
 Die **adfieldpending\* ** -Werte geben den Vorgang an, der bewirkt hat, dass der Status festgelegt wurde, und können mit anderen Status Werten kombiniert werden.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adfieldalread yexistiert**|26|Gibt an, dass das angegebene Feld bereits vorhanden ist.|  
|**adfieldbadstatus**|12|Gibt an, dass ein ungültiger Statuswert von ADO an den OLE DB-Anbieter gesendet wurde. Zu den möglichen Ursachen gehören ein OLE DB 1,0-oder 1,1-Anbieter oder eine falsche Kombination aus [Wert](../../../ado/reference/ado-api/value-property-ado.md) und [Status](../../../ado/reference/ado-api/status-property-ado-field.md).|  
|**adfieldcannotcomplete**|20|Gibt an, dass der Server der von der [Quelle](../../../ado/reference/ado-api/source-property-ado-record.md) angegebenen URL den Vorgang nicht beenden konnte.|  
|**adfieldcannotdelta etesource**|23|Gibt an, dass während eines Verschiebungs Vorgangs eine Struktur oder Teilstruktur an eine neue Position verschoben wurde, die Quelle jedoch nicht gelöscht werden konnte.|  
|**adfieldcantconvertvalue**|2|Gibt an, dass das Feld ohne Datenverlust nicht abgerufen oder gespeichert werden kann.|  
|**adfieldcantcreate**|7|Gibt an, dass das Feld nicht hinzugefügt werden konnte, da der Anbieter eine Einschränkung überschritten hat (z. b. die zulässige Anzahl von Feldern).|  
|**adfielddataoverflow**|6|Gibt an, dass die vom Anbieter zurückgegebenen Daten zu einem Überlauf des Datentyps des Felds geführt haben.|  
|**adfielddefault**|13|Gibt an, dass beim Festlegen von Daten der Standardwert für das Feld verwendet wurde.|  
|**adfielddoesnotexist**|16|Gibt an, dass das angegebene Feld nicht vorhanden ist.|  
|**adfieldignore**|15|Gibt an, dass dieses Feld übersprungen wurde, als Datenwerte in der Quelle festgelegt wurden. Der Anbieter hat keinen Wert festgelegt.|  
|**adfieldintegrityverletzungs**|10|Gibt an, dass das Feld nicht geändert werden kann, da es eine berechnete oder abgeleitete Entität ist.|  
|**adfieldinvalidurl**|17|Gibt an, dass die Datenquellen-URL ungültige Zeichen enthält.|  
|**adfieldisnull**|3|Gibt an, dass der Anbieter einen Variant-Wert vom Typ VT_NULL zurückgegeben hat und dass das Feld nicht leer ist.|  
|**adFieldOK**|0|Default. Gibt an, dass das Feld erfolgreich hinzugefügt oder gelöscht wurde.|  
|**adfieldouesleerraum**|22|Gibt an, dass der Anbieter nicht genügend Speicherplatz zum Durchführen eines verschiebe-oder Kopiervorgangs abrufen kann.|  
|**adfieldpdingchange**|0x40000|Gibt an, dass das Feld gelöscht und anschließend erneut hinzugefügt wurde, möglicherweise mit einem anderen Datentyp, oder dass sich der Wert des Felds, das zuvor den Status **adFieldOK** enthielt, geändert hat. In der endgültigen Form des Felds wird die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung geändert, nachdem die [Update](../../../ado/reference/ado-api/update-method.md) -Methode aufgerufen wurde.|  
|**adfieldpdingdelete**|0x20000|Gibt an, dass der **Lösch** Vorgang bewirkt hat, dass der Status festgelegt wurde. Nachdem die **Update** -Methode aufgerufen wurde, wurde das Feld zum Löschen aus der **Fields** -Auflistung markiert.|  
|**adfieldpdinginsert**|0x10000|Gibt an, dass der Anfüge Vorgang bewirkt hat, **dass der Status** festgelegt wurde. Das **Feld** wurde so gekennzeichnet, dass es der **Fields** -Auflistung hinzugefügt wird, nachdem die **Update** -Methode aufgerufen wurde.|  
|**adfieldpdingunknown**|0x80000|Gibt an, dass der Anbieter nicht ermitteln kann, welcher Vorgang das Festlegen des Feld Status bewirkt hat.|  
|**adfieldpdingunknowndelete**|0x100000|Gibt an, dass der Anbieter nicht ermitteln kann, welcher Vorgang den Feld Status festgelegt hat, und dass das Feld nach dem Aufrufen der **Update** -Methode aus der **Fields** -Auflistung gelöscht wird.|  
|**adfieldpermissiondenied**|9|Gibt an, dass das Feld nicht geändert werden kann, da es als schreibgeschützt definiert ist.|  
|**adfieldreadonly**|24|Gibt an, dass das Feld in der Datenquelle als schreibgeschützt definiert ist.|  
|**adfieldresourceist vorhanden**|19|Gibt an, dass der Anbieter den Vorgang nicht ausführen konnte, da ein Objekt bereits an der Ziel-URL vorhanden ist und es nicht in der Lage ist, das Objekt zu überschreiben.|  
|**adfieldresourcelocked**|18|Gibt an, dass der Anbieter den Vorgang nicht ausführen konnte, da die Datenquelle von mindestens einer anderen Anwendung oder einem anderen Prozess gesperrt ist.|  
|**adfieldresourceoutrof Scope**|25|Gibt an, dass eine Quell-oder eine Ziel-URL außerhalb des Gültigkeits Bereichs des aktuellen Datensatzes liegt.|  
|**adfieldschemaverletzung**|11|Gibt an, dass der Wert gegen die Schema Einschränkung der Datenquelle für das Feld verstoßen hat.|  
|**adfieldsignmismatch**|5|Gibt an, dass der vom Anbieter zurückgegebene Datenwert signiert wurde, der Datentyp des ADO-Feldwerts jedoch nicht signiert wurde.|  
|**adfieldtruncated**|4|Gibt an, dass Daten variabler Länge beim Lesen aus der Datenquelle abgeschnitten wurden.|  
|**adfieldunavailable**|8|Gibt an, dass der Anbieter den Wert beim Lesen aus der Datenquelle nicht ermitteln konnte. Beispielsweise wurde die Zeile soeben erstellt, der Standardwert für die Spalte war nicht verfügbar, und es wurde noch kein neuer Wert angegeben.|  
|**adfieldvolumeinotfound**|21|Gibt an, dass der Anbieter das durch die URL festgestellte Speicher Volume nicht finden kann.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Status-Eigenschaft (ADO-Feld)](../../../ado/reference/ado-api/status-property-ado-field.md)
