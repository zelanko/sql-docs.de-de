---
title: CreateRecordset-Methode (RDS) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 791586badfeff0c1bde35b5cdf25ba750f79fe80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779028"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset-Methode (RDS)
Erstellt ein leeres getrennt [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Objekt*  
 Eine Objektvariable, steht ein [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oder [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *ColumnsInfos*  
 Ein **Variant** Array von Attributen, die jede Spalte definiert den **Recordset** erstellt. Jede Definition einer Spalte enthält ein Array von vier erforderlichen Attribute und ein optionales Attribut.  
  
|attribute|Description|  
|---------------|-----------------|  
|Name|Der Name des Spaltenheaders.|  
|Typ|Ganze Zahl des Datentyps.|  
|Größe|Ganze Zahl, der die Breite in Zeichen, unabhängig von Datentyp.|  
|NULL-Zulässigkeit|Boolescher Wert.|  
|Skalierung (Optional)|Dieses optionale Attribut definiert die Skala für numerische Felder. Wenn dieser Wert nicht angegeben ist, werden die numerische Werte zu drei Dezimalstellen abgeschnitten. Genauigkeit ist nicht betroffen, aber die Anzahl von Ziffern hinter dem Dezimaltrennzeichen abgeschnitten auf drei.|  
  
 Der Satz von Spaltenarrays wird dann in ein Array, das definiert gruppiert die **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Das serverseitige Geschäftsobjekt, das Auffüllen der resultierenden **Recordset** mit Daten aus einer nicht - OLE DB-Datenanbieter, wie z. B. ein Betriebssystem-Datei mit Aktienkurse.  
  
 Die folgende Tabelle enthält die [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) Werte, die von unterstützt die **CreateRecordset** Methode. Die Anzahl aufgeführt ist die Verweisnummer verwendet, um Felder zu definieren.  
  
 Jede der Datentypen ist fester oder variabler Länge. Typen mit fester Länge werden mit einer Größe von – 1 ist, definiert, weil die Größe wird und eine Definition der Größe nach wie vor erforderlich ist. Datentypen variabler Länge können eine Größe zwischen 1 und 32767.  
  
 Für einige der Variablen Datentypen kann der Typ in den in der Spalte "Substitution" angegebenen Typ umgewandelt werden. Sie werden feststellen, dass die Ersetzungen erst nach der **Recordset** erstellt und gefüllt ist. Anschließend können Sie für den tatsächlichen Datentyp, bei Bedarf überprüfen.  
  
|Länge|Konstante|Number|Ersetzung|  
|------------|--------------|------------|------------------|  
|Fest|**adTinyInt**|16||  
|Fest|**adSmallInt**|2||  
|Fest|**adInteger**|3||  
|Fest|**adBigInt**|20||  
|Fest|**adUnsignedTinyInt**|17||  
|Fest|**adUnsignedSmallInt**|18||  
|Fest|**adUnsignedInt**|19||  
|Fest|**adUnsignedBigInt**|21||  
|Fest|**adSingle**|4||  
|Fest|**adDouble**|5||  
|Fest|**adCurrency**|6||  
|Fest|**adDecimal**|14||  
|Fest|**adNumeric**|131||  
|Fest|**adBoolean**|11||  
|Fest|**adError**|10||  
|Fest|**adGuid**|72||  
|Fest|**adDate**|7||  
|Fest|**adDBDate**|133||  
|Fest|**adDBTime**|134||  
|Fest|**adDBTimestamp**|135|7|  
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
  
## <a name="see-also"></a>Siehe auch  
 [CreateRecordset-Methode – Beispiel (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [CreateRecordset-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject-Methode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



