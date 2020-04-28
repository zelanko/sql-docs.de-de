---
title: Methode "samaterecordset" (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c65f7d415864b169b683e0c9ab858506d31783b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964513"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset-Methode (RDS)
Erstellt ein leeres, nicht verbundenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Object*  
 Eine Objekt Variable, die ein [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oder [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *ColumnsInfos*  
 Ein **Variant** -Array von Attributen, das jede Spalte im erstellten **Recordset** definiert. Jede Spaltendefinition enthält ein Array von vier erforderlichen Attributen und ein optionales Attribut.  
  
|Attribut|BESCHREIBUNG|  
|---------------|-----------------|  
|Name|Der Name des Spalten Headers.|  
|Typ|Ganzzahliger Wert des Datentyps.|  
|Size|Ganzzahlige Breite in Zeichen, unabhängig vom Datentyp.|  
|NULL-Zulässigkeit|Boolescher Wert.|  
|Skalieren (optional)|Dieses optionale Attribut definiert die Skala für numerische Felder. Wenn dieser Wert nicht angegeben wird, werden numerische Werte auf drei Dezimalstellen abgeschnitten. Die Genauigkeit ist nicht betroffen, aber die Anzahl der Ziffern nach dem Dezimaltrennzeichen wird auf drei gekürzt.|  
  
 Der Satz von Spalten Arrays wird dann in ein Array gruppiert, das das **Recordset**definiert.  
  
## <a name="remarks"></a>Bemerkungen  
 Das serverseitige Geschäftsobjekt kann das resultierende **Recordset** mit Daten aus einem nicht OLE DB Datenanbieter auffüllen, z. b. eine Betriebssystem Datei mit Kurs Anführungszeichen.  
  
 In der folgenden Tabelle **sind die von der Methode "** |-Methode" unterstützten [datatyetenum](../../../ado/reference/ado-api/datatypeenum.md) -Werte aufgeführt. Die aufgeführte Zahl ist die Verweis Nummer, die zum Definieren von Feldern verwendet wird.  
  
 Jeder Datentyp ist entweder eine mit fester oder variabler Länge. Typen mit fester Länge sollten mit einer Größe von-1 definiert werden, da die Größe vorgegeben ist und eine Größen Definition noch erforderlich ist. Datentypen mit variabler Länge lassen eine Größe zwischen 1 und 32767 zu.  
  
 Für einige der Variablen Datentypen kann der Typ in den Typ umgewandelt werden, der in der Ersetzungs Spalte angegeben ist. Die Ersetzungen werden erst angezeigt, nachdem das **Recordset** erstellt und gefüllt wurde. Anschließend können Sie ggf. den tatsächlichen Datentyp überprüfen.  
  
|Länge|Konstante|Anzahl|Ersetzung|  
|------------|--------------|------------|------------------|  
|Korrigiert|**adTinyInt**|16||  
|Korrigiert|**adSmallInt**|2||  
|Korrigiert|**adInteger**|3||  
|Korrigiert|**adBigInt**|20||  
|Korrigiert|**adUnsignedTinyInt**|17||  
|Korrigiert|**adUnsignedSmallInt**|18||  
|Korrigiert|**adUnsignedInt**|19||  
|Korrigiert|**adUnsignedBigInt**|21||  
|Korrigiert|**adSingle**|4||  
|Korrigiert|**adDouble**|5||  
|Korrigiert|**adCurrency**|6||  
|Korrigiert|**adDecimal**|14||  
|Korrigiert|**adNumeric**|131||  
|Korrigiert|**adBoolean**|11||  
|Korrigiert|**adError**|10||  
|Korrigiert|**adGuid**|72||  
|Korrigiert|**adDate**|7||  
|Korrigiert|**adDBDate**|133||  
|Korrigiert|**adDBTime**|134||  
|Korrigiert|**adDBTimestamp**|135|7|  
|Variable|**adBSTR**|8|130|  
|Variable|**adChar**|129|200|  
|Variable|**adVarChar**|200||  
|Variable|**adLongVarChar**|201|200|  
|Variable|**adWChar**|130||  
|Variable|**adVarWChar**|202|130|  
|Variable|**adLongVarWChar**|203|130|  
|Variable|**adBinary**|128||  
|Variable|**adVarBinary**|204||  
|Variable|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die Methode "kreaterecordset" (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Beispiel für die Methode "kreaterecordset" (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject-Methode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



