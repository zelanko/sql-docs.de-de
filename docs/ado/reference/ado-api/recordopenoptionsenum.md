---
title: Recordopenoptionsenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d97a8cdf2f77f323f0897d7977a2c6945b46b87
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761898"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Gibt Optionen für das Öffnen eines [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)an. Diese Werte können mit oder kombiniert werden.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**addelta-fetchfields**|0x8000|Gibt dem Anbieter an, dass die dem **Datensatz** zugeordneten Felder anfänglich nicht abgerufen werden müssen, sondern beim ersten Versuch, auf das Feld zuzugreifen, abgerufen werden können. Das Standardverhalten, das durch das Fehlen dieses Flags angegeben wird, besteht darin, alle **Daten Satz** Objekt Felder abzurufen.|  
|**addelta-fetchstream**|0x4000|Gibt dem Anbieter an, dass der dem Datensatz zugeordnete Standard **Daten** Strom anfänglich nicht abgerufen werden muss. Das Standardverhalten, das durch das Fehlen dieses Flags angegeben ist, besteht darin, den dem **Datensatz** -Objekt zugeordneten Standardstream abzurufen.|  
|**adopendasync**|0x1000|Gibt an, dass das **Datensatz** -Objekt im asynchronen Modus geöffnet wird.|  
|**adopteexecutecommand**|0x10000|Gibt an, dass die Quell Zeichenfolge Befehls Text enthält, der ausgeführt werden soll. Dieser Wert entspricht der Option **adCmdText** für **Recordset. Open**.|  
|**adopendrecordunspezifiziert**|-1|Standard. Gibt an, dass keine Optionen angegeben.|  
|**adopendoutput**|0x800000|Gibt an, dass die Quelle auf einen Knoten verweist, der ein ausführbares Skript enthält (z. b.). ASP-Seite), dann enthält der geöffnete **Datensatz** die Ergebnisse des ausgeführten Skripts. Dieser Wert gilt nur für Datensätze, die keine Sammlung sind.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
