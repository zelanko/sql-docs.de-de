---
title: OpenSchema-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2080145e00c658288f9d34e3fa42ed335e0c1d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931865"
---
# <a name="openschema-method"></a>OpenSchema-Methode
Ruft Informationen über das Datenbankschema vom Anbieter ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, das Schemainformationen enthält. Die **Recordset** als schreibgeschützte, statische Cursor geöffnet wird. Die *QueryType* bestimmt, welche Spalten in angezeigt werden die **Recordset**.  
  
#### <a name="parameters"></a>Parameter  
 *QueryType*  
 Alle [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) -Wert, der den Typ des, die die auszuführende Schemaabfrage darstellt.  
  
 *Kriterien*  
 Optional. Ein Array von Abfrage-Einschränkungen für die einzelnen *QueryType* option gemäß [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *SchemaID*  
 Die GUID für eine Anbieter-Schema-Abfrage, die nicht vom OLE DB-Spezifikation definiert. Dieser Parameter ist erforderlich, wenn *QueryType* nastaven NA hodnotu **AdSchemaProviderSpecific**ist, andernfalls wird er nicht verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Die **OpenSchema** Methodenrückgabe selbsterklärende Informationen über die Datenquelle, z. B., welche Tabellen in der Datenquelle, die Spalten in den Tabellen enthalten sind und die Datentypen unterstützt.  
  
 Die *QueryType* Argument ist eine GUID, der angibt, die Spalten (Schemas) zurückgegeben. OLE DB-Spezifikation verfügt über eine vollständige Liste der Schemas.  
  
 Die *Kriterien* -Argument begrenzt die Ergebnisse einer Schemaabfrage. *Kriterien* gibt ein Array von Werten, die auftreten müssen in eine entsprechende Teilmenge der Spalten, namens Einschränkungsspalten, in der resultierenden **Recordset**.  
  
 Die Konstante **AdSchemaProviderSpecific** wird verwendet, für die *QueryType* Argument, wenn der Anbieter die eigene nicht dem Standard entsprechende Schemaabfragen außerhalb dieser definiert bereits aufgeführt. Wenn diese Konstante verwendet wird, die *SchemaID* Argument ist erforderlich, um die GUID der Schemaabfrage auszuführende übergeben. Wenn *QueryType* nastaven NA hodnotu **AdSchemaProviderSpecific** aber *SchemaID* ist nicht angegeben wird, ein Fehler zurückgegeben wird.  
  
 Anbieter sind nicht erforderlich, um alle Abfragen der OLE DB-standard-Schema unterstützen. Insbesondere nur **AdSchemaTables**, **AdSchemaColumns**, und **AdSchemaProviderTypes** OLE DB-Spezifikation erforderlich sind. Der Anbieter ist jedoch nicht erforderlich, zur Unterstützung der *Kriterien* Einschränkungen weiter oben aufgeführt, für diese Abfragen.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** der **OpenSchema** Methode ist nicht verfügbar für eine clientseitige [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
> [!NOTE]
>  In Spalten, die eine vier-Byte-Ganzzahl ohne Vorzeichen (DBTYPE UI4) in Visual Basic die **Recordset** zurückgegeben, die von der **OpenSchema** Methode für die **Verbindung** Objekt kann nicht verglichen Sie mit anderen Variablen werden. Weitere Informationen zu OLE DB-Datentypen, finden Sie unter [Datentypen in OLE DB (OLE DB)](https://msdn.microsoft.com/6039292f-74e0-49b2-b133-17bc117ebf6a) und [Anhang A: Datentypen](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6) in der Microsoft OLE DB Programmer's Reference.  
  
> [!NOTE]
>  **Visual C# /C++ Benutzer** clientseitigen Cursorn nicht verwendet werden, Abrufen von "ORDINAL_POSITION" eines Spalte-Schemas in ADO eine Variante des Typs VT_R8 in MDAC 2.7, MDAC 2.8 und Windows Data Access Components (Windows DAC) 6.0, bei dem verwendeten Typ zurückgibt MDAC 2.6 ist VT_I4. Programme für MDAC 2.6 geschrieben, die nur für eine Variante aussehen zurückgegebene des Typs VT_I4 erhalten würde, eine 0 (null) für jede Ordnungszahl, wenn unter MDAC 2.7, MDAC 2.8 und Windows DAC 6.0 ohne Änderungen ausgeführt. Diese Änderung wurde vorgenommen, da der Datentyp, den OLE DB gibt DBTYPE_UI4 ist, und in den Typ mit Vorzeichen VT_I4 ist nicht genügend Platz für alle möglichen Werte ungekürzt möglicherweise auftreten, und wodurch ein Verlust von Daten enthalten.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [OpenSchema-Methode – Beispiel (VB)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [OpenSchema-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
