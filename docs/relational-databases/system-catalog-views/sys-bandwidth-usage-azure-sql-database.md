---
title: sys.bandwidth_usage (Azure SQL-Datenbank) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ea963c07a15cd5c2db3cca113680026d3100936b
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "67942577"
---
# <a name="sysbandwidth_usage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

> [!NOTE]
> Dies gilt [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]nur für V11.**  
  
 Gibt Informationen über die Netzwerkbandbreite zurück, die von jeder Datenbank in einem ** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11-Datenbankserver**verwendet wird . Jede Zeile, die für eine bestimmte Datenbank zurückgegeben wird, gibt eine einzelne Richtung und eine Verwendungsklasse über eine Stunde hinweg an.  
  
 **Dies wurde in einem [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]veraltet.**  
  
 Die **Ansicht sys.bandwidth_usage** enthält die folgenden Spalten.  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**time**|Die Stunde, als die Bandbreite verwendet wurde. Die Zeilen in dieser Sicht enthalten stündliche Angaben. Beispielsweise bedeutet 2009-09-19 02:00:00.000, dass die Bandbreite am 19. September 2009 zwischen 2:00 Uhr und 3:00 Uhr verwendet wurde.|  
|**database_name**|Der Name der Datenbank, die Bandbreite verwendet hat.|  
|**direction**|Der Typ der Bandbreite, der verwendet wurde. Dies kann eine der folgenden Optionen sein:<br /><br /> Ingress: Daten, die [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]in die .<br /><br /> Egress: Daten, die sich [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]aus der herausbewegen.|  
|**class**|Die Klasse der Bandbreite, die verwendet wurde. Dies kann eine der folgenden Optionen sein:<br />Intern: Daten, die innerhalb der Azure-Plattform übertragen werden.<br />Extern: Daten, die sich aus der Azure-Plattform verschieben.<br /><br /> Diese Klasse wird nur zurückgegeben, wenn die Datenbank in einer kontinuierlichen Kopienbeziehung zwischen Regionen ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]) ist. Wenn eine bestimmte Datenbank nicht an einer fortlaufenden Kopierbeziehung teilnimmt, werden "Interlink"-Zeilen nicht zurückgegeben. Weitere Informationen finden Sie im Abschnitt "Hinweise" weiter unten in diesem Thema.|  
|**time_period**|Der Zeitraum, in dem die Verwendung aufgetreten ist, ist entweder Peak oder OffPeak. Die Spitzenzeit basiert auf der Region, in der der Server erstellt wurde. Wenn ein -Server beispielsweise in der Region "US_Northwest" erstellt wurde, liegt die Spitzenzeit laut Definition zwischen 10:00 Uhr und 18:00 Uhr PST.|  
|**quantity**|Die Menge der verwendeten Bandbreite in KB.|  
  
## <a name="permissions"></a>Berechtigungen

 Diese Ansicht ist nur in der **Masterdatenbank** für die Prinzipalanmeldung auf Serverebene verfügbar.  
  
## <a name="remarks"></a>Bemerkungen  
  
### <a name="external-and-internal-classes"></a>Externe und interne Klassen

 Für jede Datenbank, die zu einem bestimmten Zeitpunkt verwendet wird, gibt die **Ansicht sys.bandwidth_usage** Zeilen zurück, die die Klasse und Richtung der Bandbreitennutzung anzeigen. Das folgende Beispiel zeigt Daten, die für eine bestimmte Datenbank verfügbar gemacht werden können. In diesem Beispiel ist der Zeitpunkt 2012-04-21 17:00:00, der im Zeitraum mit Spitzenwerten liegt. Der Datenbankname ist Db1. In diesem Beispiel hat **sys.bandwidth_usage** eine Zeile für alle vier Kombinationen der Eingangs- und Ausgangsrichtungen sowie der externen und internen Klassen wie folgt zurückgegeben:  
  
|time|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Eingehende Daten|Extern|Peak|66|  
|2012-04-21 17:00:00|Db1|Ausgehende Daten|Extern|Peak|741|  
|2012-04-21 17:00:00|Db1|Eingehende Daten|Intern|Peak|1052|  
|2012-04-21 17:00:00|Db1|Ausgehende Daten|Intern|Peak|3525|  
  
### <a name="interpreting-data-direction-for-ssgeodr"></a>Interpretieren der Datenrichtung für [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]

 Bei [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] sind die Bandbreitenverwendungsdaten in der logischen Masterdatenbank auf beiden Seiten einer kontinuierlichen Kopienbeziehung sichtbar. Daher müssen Sie die Eingangs- und Ausgangsrichtungsindikatoren aus der Perspektive der Datenbanken interpretieren, die Sie abfragen. Betrachten Sie beispielsweise einen Replikationsdatenstrom, der 1 MB Daten vom Quell- auf den Zielserver überträgt. In diesem Fall werden auf dem Quellserver die 1 MB auf die insgesamt gesendeten Daten angerechnet, und auf dem Zielserver wird der 1 MB als empfangene Daten aufgezeichnet.  
  
> [!NOTE]  
> Die vom Quell- auf den Zielserver übertragenen Massendaten werden in Richtung des Benutzerdatendatenflusses übertragen. Manche Daten müssen jedoch in die andere Richtung übertragen werden.  
